# MINIGUIA DE ESTUDO

## Python para Análise e Automação de Dados

Este documento sintetiza os princípios fundamentais e as técnicas avançadas de Python voltadas para a análise de dados, processamento numérico e visualização estatística, baseando-se nas práticas e bibliotecas padrão da indústria.


--------------------------------------------------------------------------------


### 1. Fundamentos de Python

O Python consolidou-se como a linguagem principal para a ciência de dados devido à sua sintaxe concisa e ao vasto ecossistema de bibliotecas especializadas. O aprendizado sólido começa pelas estruturas principais e evolui para as melhorias das versões mais recentes, como o Python 3.14.

#### Estruturas de Base e Sintaxe

As fundações do Python para análise de dados envolvem a manipulação de listas, operadores e controle de fluxo, que permitem a automação de tarefas repetitivas e a construção de pipelines de dados.

| Conceito |	Descrição |
| ----------| ------ |
| Operadores e Expressões	| Realizam cálculos e avaliações lógicas fundamentais. |
| Loops (For/While)	| Essenciais para iterar sobre coleções de dados. |
| Keyword continue |	Utilizada para pular iterações específicas dentro de um loop. |
| Listas | Contêineres heterogêneos versáteis para armazenamento de sequências. |
| Funções Funcionais	| Técnicas que permitem aplicar lógica a coleções de forma eficiente.|

Exemplos Práticos (1 linha):

* Operadores: resultado = (10 + 5) * 2 / 3
* Loops: for item in [1, 2, 3]: print(item)
* Continue: for i in range(5): if i == 2: continue
* Listas: minha_lista = [1, "dado", 3.14]
* Programação Funcional: map(lambda x: x**2, [1, 2, 3])

#### Novidades e Ferramentas Modernas (Python 3.14+):

A evolução da linguagem foca em performance e clareza para o desenvolvedor, com melhorias no REPL e mensagens de erro.

* Lazy Annotations: Avaliação preguiçosa de anotações de tipo para melhorar a performance.
* T-Strings: Novos templates de strings que oferecem maior controle sobre a interpolação.
* Gerenciamento com uv: Uma ferramenta extremamente rápida escrita em Rust para gerenciar pacotes e dependências, substituindo o pip em fluxos modernos.

Exemplos Práticos (1 linha):

* T-Strings (exemplo conceitual): f"Resultado: {valor:.2f}"
* Instalação com uv: uv pip install pandas numpy seaborn


--------------------------------------------------------------------------------


### 2. NumPy (Processamento Numérico):

A biblioteca NumPy (Numerical Python) é a base para a computação científica em Python. Ela introduz o ndarray, uma estrutura de array n-dimensional homogênea que é muito mais eficiente em memória e performance do que as listas nativas para grandes volumes de dados.

#### Criação e Atributos de Arrays

Os arrays NumPy possuem tipo fixo e formato retangular.

| Método/Atributo	| Função |
| ------------- | ------ |
| np.array()	| Cria um array a partir de uma sequência (como uma lista). |
| np.zeros()	| Inicializa um array preenchido com zeros. |
| np.ones()	| Inicializa um array preenchido com uns. |
| np.arange()	| Cria um array com um intervalo de valores. |
| np.linspace()	| Gera valores linearmente espaçados em um intervalo. |
| ndim	| Retorna o número de dimensões (eixos) do array. |
| shape	| Retorna uma tupla com o tamanho de cada dimensão. |

Exemplos Práticos (1 linha):

* array: arr = np.array([1, 2, 3])
* zeros: arr0 = np.zeros((2, 3))
* ones: arr1 = np.ones((3, 3))
* arange: arr_range = np.arange(0, 10, 2)
* linspace: arr_lin = np.linspace(0, 1, 5)
* ndim: dim = arr.ndim
* shape: formato = arr.shape

#### Manipulação e Operações

O NumPy permite reestruturar dados sem copiar a memória subjacente através de "views".

* Reshape: Altera o formato do array (ex: de 1D para 2D).
* Concatenate: Une dois ou mais arrays ao longo de um eixo.
* Broadcasting: Mecanismo que permite operações aritméticas entre arrays de diferentes formatos compatíveis.
* Transpose (.T): Inverte os eixos de uma matriz.

Exemplos Práticos (1 linha):

* reshape: novo_arr = arr.reshape((3, 1))
* concatenate: unido = np.concatenate((arr1, arr2))
* transpose: transposta = matriz.T
* flip: invertido = np.flip(arr, axis=0)
* ravel: achatado = arr.ravel()


--------------------------------------------------------------------------------


### 3. Pandas (Análise e Manipulação de Dados)

O Pandas é a biblioteca padrão para manipulação de tabelas numéricas e séries temporais. Seus principais objetos são a Series (1D) e o DataFrame (2D).

#### Importação e Exploração Inicial

O Pandas suporta diversos formatos, como CSV, Excel, JSON e SQL.

| Método	| Finalidade |
| ------- | -------- |
| read_csv()	| Carrega dados de um arquivo de valores separados por vírgula. |
| head()	| Exibe as primeiras 5 linhas do conjunto de dados. |
| info()	| Fornece um resumo conciso do DataFrame (tipos e valores nulos). |
| describe()	| Gera estatísticas descritivas (média, desvio padrão, quartis). |
| isna().sum()	| Detecta e quantifica valores ausentes por coluna. |

Exemplos Práticos (1 linha):

* read_csv: df = pd.read_csv('dados.csv')
* head: print(df.head(10))
* info: df.info()
* describe: estatisticas = df.describe()
* isna: nulos = df.isna().sum()

#### Limpeza e Transformação

Lidar com dados ausentes e reorganizar a estrutura da tabela são etapas críticas.

* Dropna: Remove linhas ou colunas com valores nulos.
* Fillna: Preenche valores ausentes com uma constante ou estatística.
* Loc/ILoc: Seleção de dados baseada em rótulos (loc) ou posições inteiras (iloc).
* Melt: Transforma o DataFrame de um formato largo para um formato longo.
* Pivot: Cria uma nova tabela a partir de valores de colunas (formato longo para largo).

Exemplos Práticos (1 linha):

* dropna: df_limpo = df.dropna()
* fillna: df_preenchido = df.fillna(method='bfill')
* loc: subset = df.loc[0:10, ['Coluna1', 'Coluna2']]
* iloc: subset = df.iloc[0:5, 0:3]
* melt: df_longo = pd.melt(df, id_vars=['ID'], value_vars=['A', 'B'])
* pivot: df_largo = df.pivot(index='Data', columns='Var', values='Valor')

#### Análise e Agregação

O poder do Pandas reside na sua capacidade de agrupar e combinar dados complexos.

| Função	| Descrição |
| ----- | ----- |
| GroupBy	| Divide os dados em grupos com base em critérios definidos. |
| Merge	| Realiza junções de bancos de dados (similar ao JOIN do SQL). |
| Concat	| Concatena objetos pandas ao longo de um eixo específico. |
| Apply |	Aplica uma função ao longo de um eixo do DataFrame. |

Exemplos Práticos (1 linha):

* groupby: media_grupo = df.groupby('Categoria')['Preço'].mean()
* merge: combinado = pd.merge(df1, df2, on='id', how='inner')
* concat: empilhado = pd.concat([df1, df2], axis=0)
* apply: df['Nova'] = df['Valor'].apply(lambda x: x * 1.1)


--------------------------------------------------------------------------------


### 4. Visualização de Dados

A visualização de dados em Python é liderada pelo Matplotlib (nível inferior/customização) e Seaborn (nível superior/estatístico).

#### Matplotlib: A Estrutura Base

O Matplotlib utiliza uma hierarquia de objetos: Figure (a janela completa), Axes (a área do gráfico) e Axis (as linhas de escala).

Exemplos Práticos (1 linha):

* plot: plt.plot(x, y, label='Tendência')
* subplots: fig, ax = plt.subplots()
* set_title: ax.set_title('Meu Gráfico Estatístico')
* legend: plt.legend()
* savefig: plt.savefig('grafico.png')

#### Seaborn: Gráficos Estatísticos Declarativos

O Seaborn integra-se ao Pandas e lida internamente com o mapeamento semântico e a agregação estatística (como intervalos de confiança via bootstrapping).

| Função Seaborn	| Aplicação |
| ------ | ------ |
| relplot()	| Visualiza relações estatísticas (dispersão ou linha). |
| displot()	| Representa distribuições de dados (histogramas, KDE). |
| catplot()	| Focada em dados categóricos (swarm, boxplot, barplot). |
| lmplot()	| Desenha um modelo de regressão linear sobre um gráfico de dispersão. |
| jointplot() |	Mostra a relação entre duas variáveis e suas distribuições marginais. |
| pairplot()	| Exibe relações pareadas em um conjunto de dados completo. |

Exemplos Práticos (1 linha):

* relplot: sns.relplot(data=df, x='total', y='gorjeta', hue='dia')
* displot: sns.displot(data=df, x='idade', kind='kde')
* catplot: sns.catplot(data=df, x='dia', y='total', kind='box')
* lmplot: sns.lmplot(data=df, x='tamanho', y='preço')
* jointplot: sns.jointplot(data=df, x='x', y='y')
* pairplot: sns.pairplot(df)
* set_theme: sns.set_theme(style="darkgrid")
