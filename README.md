# Playground

Este repositório contém o código que faz funcionar o **Playground** de programação web, um editor de código com visualizador em tempo real. Ele funciona para códigos HTML, CSS e Javascript, e pode incorporar outros recursos se for customizado. Ele foi criado para aulas de programação web e Processing, para facilitar um contato imediato com estas linguages sem a necessidade prévia de instalações, configurações, compliladores, máquinas virtuais, ou quaisquer outras parafernalhas que um iniciante terá medo de saber o que são.

## Aviso

Entenda que este código foi construído utilizando as piores práticas de programação imagináveis, POGs infinitas, e tudo que não deveria ser feito em um código. Ele funciona, mas usando magia negra. Erros disparando no console do navegador foram todos considerados irrelevantes no processo de construção deste código.

Obviamente, o código praticamente não possui comentários, para (não) facilitar a sua vida, ou a minha, já que quando volto a mexer nele, não entendo mais nada do que eu mesmo fiz (e continuo sem tempo para colocar os comentários).

## Dependências

Este código utiliza três recursos importantes para funcionar:
1. JQuery
2. Ace Editor
3. Processing.js (caso use a versão modificada para Processing)

Ambos já estão sendo automaticamente incorporados nas linhas 54, 56 e 58, sendo o Jquery vindo do servidor do Google, e o ACE Editor do meu próprio site.

Você pode baixar ambos e carregá-los do lugar de sua preferência, ou mesmo atualizá-los caso novos recursos pareçam úteis. O ACE está disponível em https://ace.c9.io/ , o JQuery em https://jquery.com/ e o Processing.js em http://processingjs.org/

Você não precisa instalar Node, nenhum compilador SASS, nenhum framework maluco, ou fazer qualquer peripécia em um servidor para que o código funcione. Um dia irei cortar até o JQuery. Para mim, quanto menos penduricalho, melhor.

## Arquivos

Na pasta **v3** está o código que roda a versão *pura* do playground, para edição de código HTML/CSS/JS. Na pasta **processing** está uma versão modificada que também incorpora o Processing.js. A versão modificada escreve um cabeçalho em tempo real na visualização, carregando o Processing.js (linhas 671 - 690 para que isso funcione).

## Recursos

É possível fazer um monte de coisas através das variáveis de URL.

- Carregar arquivos externos no editor:
```
index.html?file=http://www.meusite.com/meuarquivo.html
```

- Carregar um arquivo de fundo no visualizador (como se você trabalhasse em um papel vegetal por cima de uma outra coisa)
```
index.html?exemplo=http://www.meusite.com/meuarquivo.html

```

- Mudar o tema (cor) do editor (ACE):
```
index.html?theme=XCode
```

- Tirar os botões do editor da tela:
```
index.html?embed=minimal
index.html?embed=plain
```

- Definir um site para consultas de referência que roda dentro de uma haba do editor:
```
index.html?ref=http://www.w3schools.com
```

- Definir tamanhos (%) iniciais para o editor ou para a haba de referência 
```
index.html?refheight=50&psize=80
```

### Recrusos que é melhor você evitar, ou repensar como estão no código

Há alguns recursos que incluí por que queria integrar ao editor outras coisas que possuo nos meus sistemas. Eles estão lá, mas dependem de um bando de outras coisas. O editor pode enviar o conteúdo via **AJAX** para um serviço/código server side. Uso isso para arquivar os trabalhos dos meus alunos em um MySQL em meu site. Para fazer isso, você precisará criar esse Handler por conta própria. Nas linhas 369-380 estão definidas as condições e o endereço para a chamada http que envia os dados do editor via POST para algum endereço. Para ativar esta opção, você deve utilizar também
```
index.html?sync=true
```

Eu utilizo *cookies* para registrar quem são os alunos e qual é o registro deles no banco de dados (lembre-se: este código foi escrito utilizando as piores práticas de programação imagináveis), e é por isso que as condições no trecho indicado verificam se há registros de nome, email, disciplina e atividade, e se estes valores forem incluídos como variáveis de URL, o editor irá buscar os dados via AJAX quando for iniciado.

Também é possível alterar o layout do editor. Estes foram testes experimentais para ver se ele funcionaria melhor em outra configuração. Para modificar isso e ver os resultados, use:
```
index.html?panels=1
index.html?panels=2
```
Mas já adianto que não funcionaram muito bem. O layout original ainda me parece melhor.


### Exemplos

Aqui estão aluns links com este editor funcionando:
- Editor puro de HTML com um guia de referência de HTML/CSS
https://www.ranoya.com/aulas/tryit/v3/index.html?embed=slides&lang=html&editorstartsopen=true&ref=https://www.ranoya.com/p/refweb&refheight=65

- Editor de Processing com um guia de referência (de Processing, claro!):
https://www.ranoya.com/aulas/tryit/processing/index.html?embed=slides&ref=https://www.ranoya.com/aulas/designgenerativo/playgroundDocs/refprocessing.php&psize=70&editorstartsopen=true

- Editor puro de HTML com guia de referência HTML/CSS e uma página por trás com a marcação do que o aluno deveria construir (lembre-se: este editor foi construído para ser uma ferramenta de aula):
https://www.ranoya.com/aulas/tryit/v3?exemplo=https://www.ranoya.com/aulas/webdesign/exemplos/responsive.html&embed=slides&editorstartsopen=true&lang=html&ref=https://www.ranoya.com/p/refweb&refheight=70

- Sketch de Processing rodando em tela inteira do navegador com o botão para abrir a haba de código (e alterá-lo):
https://www.ranoya.com/aulas/tryit/processing/?file=https://www.ranoya.com/aulas/designgenerativo/exemplos/linesfollow.pde&embed=minimal&psize=22

### Uso

Divirta-se. Copie, modifique, distribua, incorpore em seu site, e faça o que achar melhor com ele. Sou professor universitário, e construí essa ferramenta para poder realizar meu trabalho. Uma citação será apreciada, mas não é necessária. Uma citação ao pessoal do Processing.js, do JQuery e do ACE Editor é recomendada... eles é que fizeram o trabalho pesado.

Onde você ler "Copyright", subentenda por "Copyleft". Não há nenhum Copyright realmente ;-) .





