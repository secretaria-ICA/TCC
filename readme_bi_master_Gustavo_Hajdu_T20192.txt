# Maximização do match total baseado em % de aderência entre perfis de candidatos e perfis de oportunidades internas

#### Aluno: [Gustavo Hajdu](https://github.com/GustavoHajdu/TCC)
#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- [Link para o código](TCC BI Master 2019.2 Gustavo Hajdu - Otimização de match total de Candidatos e Oportunidades - 20211017-A.xlsx)

---

### Resumo

Um desafio para a Área de R&S (Recrutamento & Seleção) interna do RH de uma empresa de grande porte é estabelecer a melhor aderência total ("match") entre os perfis de empregados-candidatos e os perfis de oportunidades ou vagas internas, considerando-se um grande volume de movimentações internas, envolvendo centenas ou até milhares de empregados. Este cenário decorre dentre outros fatores da estratégia da empresa, da busca pelo desenvolvimento de competências críticas à sua sustentabilidade e adaptabilidade e da gestão ativa do portfólio de ativos da empresa, com diversos desinvestimentos e novos investimentos, sendo necessário mobilizar e, eventualmente, requalificar grande contingente de empregados em período relativamente curto. Individualmente, este processo ocorre através de análises curriculares, entrevistas, eventuais testes, sendo possível identificar o melhor candidato para determinada vaga. O problema surge com a perspectiva de grande volume de movimentações. Este trabalho apresenta uma solução de otimização que maximiza a aderência total de um conjunto de candidatos (empregados) e um conjunto de oportunidades (vagas internas) de acordo com as restrições estabelecidas.

### 1. Introdução

No futuro próximo, há previsão de movimentação interna de milhares de empregados em uma empresa de grande porte, fruto de sua estratégia, envolvendo um plano de resiliência, a gestão ativa de portfólio, a política de desinvestimentos e o foco em ativos de maior retorno. Por um lado, há grande quantidade de saídas previstas, por exemplo, através dos Programas de Demissão Voluntária ofertados e, por outro, excedentes de efetivo oriundos de ativos em desinvestimento. Em um processo de Recrutamento & Seleção individualizado com candidatos disputando uma única oportunidade ou mesmo poucas vagas, normalmente se promove um período de análises curriculares, seguidas de entrevistas e eventuais provas de conhecimento e dinâmicas de grupo, sendo possível chegar ao melhor candidato indicado para a oportunidade, aquele cujo perfil apresenta a maior aderência com o perfil requerido para o preenchimento da vaga. Para promover a movimentação adequada de um grande contingente de empregados, capaz de sustentar a estratégia da empresa, deve-se também buscar a melhor aderência entre cada par candidato-oportunidade mas o desafio passa a ser a obtenção do melhor match global, tendo-se como objetivo a maximização da aderência total entre um conjunto de candidatos e um conjunto de oportunidades. Neste caso, para ilustrar de forma clara o problema, apresenta-se a seguir dois cenários de realocação de 3 candidatos a 3 oportunidades em que o segundo apresenta o melhor match global.
Cenário 1
   Candidato 1 - 100% aderente à Oportunidade 1
   Candidato 2 -  80% aderente à Oportunidade 2
   Candidato 3 -   0% aderente à Oportunidade 3
Cenário 2
   Candidato 1 - 80% aderente à Oportunidade 2
   Candidato 2 - 70% aderente à Oportunidade 3
   Candidato 3 - 75% aderente à Oportunidade 1
Considerando o grande volume de movimentações e uma capacidade limitada da Área de R&S para promover a melhor alocação com um processo individualizado, uma solução de suporte à decisão que otimize esta aderência global tem grande potencial de geração de valor para a empresa. Em conjunto com a Gerente da Área de R&S foram definidas as restrições para o problema, envolvendo a necessidade de se evitar casos de oportunidades sem candidatos e vice-versa, aderência mínima entre candidato e oportunidade de forma a evitar a insatisfação dos gestores com eventual baixa aderência dos candidatos e também as localidades preferenciais dos candidatos (as oportunidades estão associadas a uma localidade, ativo/imóvel da empresa e os candidatos devem ordenar as localidades de acordo com suas preferências).
Mesmo com os dados totalmente descaracterizados, o contexto aqui relatado deve ser tratado com bastante discrição em função de potenciais questões sindicais e relacionadas.

### 2. Modelagem

O modelo é composto por uma matriz 20x20 que apresenta a aderência entre os perfis de cada par candidato x oportunidade. Apesar da mobilização prevista de centenas de empregados, esta movimentação é definida em conjuntos menores de empregados de acordo com ênfase/cargo e, segundo a Gerente de R&S, esta dimensão atenderá a maioria absoluta dos casos.
As variáveis são representadas pelas oportunidades associadas a cada candidato. Desta associação, resulta uma determinada aderência.
As restrições definidas são:
   i. cada par candidato x oportunidade deve ser distinto, ou seja, cada candidato deverá ter uma oportunidade distinta associada, não havendo repetição entre os pares nem uma oportunidade sem candidato;
  ii. a aderência entre candidato e oportunidade deve ser igual ou superior a 70%;
 iii. a localidade associada à oportunidade deve privilegiar a 1a. ou a 2a. opção do candidato, descartando-se a 3a.
A função-objetivo visa a maximização do somatório das aderências dos pares candidato x oportunidade.

### 3. Resultados

O arquivo se encontra neste mesmo repositório e contém 5 execuções realizadas conforme detalhamento a seguir.
Guia 0 -> Definição das variáveis, construção da matriz 20 x 20 e associação inicial das oportunidades, sem as restrições definidas e apresentando valor da função-objetivo = 1001 e 12 candidatos com aderência < 70%
Guia 1 -> 1a. rodada, ainda sem as restrições estabelecidas, já apresentando valor da função-objetivo = 1728 e apenas 3 candidatos com aderência < 70%
Guia 2 -> 2a. rodada, incluída a restrição de aderência mínima de 70% para 90% dos candidatos (18 em 20), apresentando o valor da função-objetivo = 1748 e nenhum candidato com aderência < 70%
Guia 3 -> 3a. rodada, ajustada a restrição de aderência mínima de 70% para 100% dos candidatos, apresentando o valor da função-objetivo = 1778 e nenhum candidato com aderência < 70%
Guia 4 -> 4a. rodada, alterada a associação inicial das oportunidades, apresentando o valor da função-objetivo = 1818 e nenhum candidato com aderência < 70%
Guia 5 -> 5a. rodada, incluídas as matrizes de Localidades das Oportunidades e de Ordenação Preferencial das Localidades pelos candidatos e a restrição de localidade, apresentando o valor da função-objetivo = 1740, nenhum candidato com aderência < 70% e todas as localidades associadas à 1a. ou 2a. opção definidas pelos candidatos

### 4. Conclusões

Os resultados obtidos com a solução são extremamente promissores. O resultado ligeiramente inferior obtido na 5a. rodada é perfeitamente compreensível diante da restrição adicional de localidade e ainda assim muito bom.
A solução é de aplicação prática imediata com previsão de atendimento a demandas reais já no próximo mês e já foi apresentada à Gerente de R&S e à Coordenadora responsável pela Mobilidade na empresa com grande entusiasmo manifestado.
Concluímos que a solução de otimização atende à necessidade descrita com enorme potencial de geração de valor para a empresa, apresentando soluções viáveis para o problema, baseadas em alocações muito boas dos candidatos às oportunidades de acordo com uma maior aderência global entre estes.

---

Matrícula: 192.671.062

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
