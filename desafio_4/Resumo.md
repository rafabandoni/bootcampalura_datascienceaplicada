# Tema: Previsão do número de infecções por COVID-19 no Brasil utilizando a taxa reprodutiva estimada do vírus.  
Autor: Rafael Bandoni    
Dados utilizados: Dados de COVID extraídos do [portal do governo](https://covid.saude.gov.br/).  

## Resumo  
Utilizando os algoritmos preditivos ARIMA e Prophet, tentei buscar o número possível de infectados por COVID-19 no Brasil nos próximos 30 dias. Para fazer isso, utilizei uma metodologia diferente, ao invés de tentar prever o número de casos, trabalhei com a taxa reprodutiva estimada do vírus (Re).  
Esse valor mostra o número de pessoas que pode ser contaminada, em méda, por outra pessoa - Re = 2 signiica que um contaminado infecta até duas pessoas. Sendo assim, Re > 1 significa infecção em crescimento e Re < 1 significa infecção em declínio. Para o cálculo dessa variável foi usado o modelo ```epyestim```, uma reimplementação em python do pacote em R chamado ```EpiEstim``` [1].  
Esse método é baseado no artigo de Huisman et al. [2], e utiliza inferência estatística como destacado por Cori et al. [3].  

## Resultados:
Para escopo do trabalho, foram escolhidos os estados de Rio de Janeiro, São Paulo e Minas Gerais. Inicialmente, o estado do Espírito Santo também estava considerado, mas não foi possível calcular o Re por conta de uma incongruência na base de dados.  

Os resultados observados foram:  

Como observado nas previsões, o método ARIMA mostrou:
- Um pico de 1,25 nos próximos 40 dias em Minas Gerais;
- Um pico entre 1,35 e 1,2 nos próximos 40 dias em São Paulo;
- Um pico entre 1,35 e 1,2 nos próximos 40 dias no Rio de Janeiro.

Para as previsões Prophet tivemos:
- Pico de 1,3 em Minas Gerais;
- Pico de 1,5 em São Paulo;
- Pico de 1,4 no Rio de Janeiro.

E, com isso, podemos ter os seguintes outputs:
- Minas Gerais, da última vez que alcançou um Re entre 1,25 e 1,3, passou por 3 meses onde foram confirmados de 2.000 a 3.000 casos por dia em média móvel de 7 dias.
- São Paulo, da última vez que alcançou picos de 1,5 em Re, confirmava mais de 10.000 casos por dia durante um mês. E com o Re de 1,3 alcançava entre 6.000 e 8.000 confirmados por dia durante 2 meses.
- E o Rio de Janeiro, da última vez que alcançou picos entre 1,2 e 1,4 confirmava entre 2.000 e 2.500 por dia durante 2 meses.

### Referências

[1] EpiEstim CRAN package: https://cran.r-project.org/web/packages/EpiEstim/index.html

[2] Jana S. Huisman, Jeremie Scire, Daniel Angst, Richard Neher, Sebastian Bonhoeffer, Tanja Stadler: A method to monitor the effective reproductive number of SARS-CoV-2 https://ibz-shiny.ethz.ch/covid-19-re/methods.pdf

[3] Anne Cori, Neil M. Ferguson, Christophe Fraser, Simon Cauchemez: A New Framework and Software to Estimate Time-Varying Reproduction Numbers During Epidemics, American Journal of Epidemiology, Volume 178, Issue 9, 1 November 2013, Pages 1505–1512, https://doi.org/10.1093/aje/kwt133
