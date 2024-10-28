function gerarCNPJ() {
    // Gera os 12 primeiros dígitos aleatórios
    $cnpj = '';
    for ($i = 0; $i < 12; $i++) {
        $cnpj .= rand(0, 9);
    }

    // Calcula o primeiro dígito verificador
    $soma = 0;
    for ($i = 0; $i < 12; $i++) {
        $soma += intval($cnpj[$i]) * (5 - ($i % 8));
    }
    $primeiroDigito = $soma % 11;
    $primeiroDigito = $primeiroDigito < 2 ? 0 : 11 - $primeiroDigito;
    $cnpj .= $primeiroDigito;

    // Calcula o segundo dígito verificador
    $soma = 0;
    for ($i = 0; $i < 13; $i++) {
        $soma += intval($cnpj[$i]) * (6 - ($i % 8));
    }
    $segundoDigito = $soma % 11;
    $segundoDigito = $segundoDigito < 2 ? 0 : 11 - $segundoDigito;
    $cnpj .= $segundoDigito;

    return $cnpj;
}

// Exemplo de uso
$cnpjGerado = gerarCNPJ();
echo "CNPJ gerado: " . $cnpjGerado;
