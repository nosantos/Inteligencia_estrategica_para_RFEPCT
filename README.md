# Inteligencia_estrategica_para_RFEPCT
**🗺️ Painel de Inteligência Territorial para Institutos Federais (IFs)**

> **Status:** Concluído | **Modelo:** K-Means (K=7) | **Acurácia de Aderência:** Validada

**🎯 Objetivo**
Este projeto utiliza Machine Learning para agrupar os 5.570 municípios brasileiros com base em sua **vocação econômica real** (PIB, Emprego e Setores), com o objetivo de **otimizar a oferta de cursos técnicos** da Rede Federal. A meta é alinhar o gasto público educacional com a demanda do mercado de trabalho local.

**📊 Dados Utilizados**
O modelo foi treinado com indicadores socioeconômicos cruzados (Fonte: IBGE/CAGED - Base consolidada):
* **Escala:** PIB Total, Estoque de Empregos Formais.
* **Vocação:** Tempo de Emprego (Agro/Indústria), Valor a preços correntes por Setor.
* **Dinâmica:** Saldos de Contratação e Variação Relativa de Emprego.

**🧠 Metodologia**
1.  **Pré-processamento:** Padronização e remoção de *outliers* extremos na etapa de treino.
2.  **Modelagem:** Algoritmo **K-Means** com `n_clusters=7`.
    * *Hiperparâmetros Otimizados:* `init='k-means++'`, `algorithm='lloyd'`, `n_init=10`.
    * *Blindagem:* Prevenção de *Data Leakage* garantindo treino apenas com features originais.
3.  **Explicabilidade:** Validação via Árvore de Decisão (`max_depth=5`) para extração de regras de negócio.

**📍 Resultados: Os 7 Perfis Econômicos**
O Brasil foi segmentado nos seguintes clusters de vocação:
1.  **Metrópole Global (Serviços e Tecnologia):** Hubs financeiros e de serviços.
2.  **Polo Industrial Consolidado:** Cidades com alta retenção de mão de obra fabril (>15 anos).
3.  **Polo Agropecuário Profissionalizado:** Cidades onde o Agro é carreira, não safra temporária.
4.  **Centro Econômico Diversificado:** Classes médias altas com serviços e comércio fortes.
5.  **Polo Regional de Gestão e Serviços:** Capitais e cidades onde o setor público/saúde domina.
6.  **Economia Local Mista (Pequeno Porte):** Pequenas cidades com comércio de subsistência e serviços básicos.
7.  **Economia de Subsistência / Alta Dependência:** Municípios de alta vulnerabilidade e dependência pública.

**🚀 Como Executar**
1.  Carregue o dataset base no notebook.
2.  Execute o pipeline de tratamento e normalização.
3.  Instancie o modelo com `random_state=42` (para reprodutibilidade).
4.  Gere o arquivo `Painel_Estrategico_IFs.csv` com as recomendações de cursos.

**📈 Possíveis aplicações**
* **Avaliar oferta atual:** Analisar aderência ou desalinhamento dos eixos tecnológicos ofertados pelos IFs com os eixos prioritários indicados pelo modelo.
* **Avaliar oferta futura:** Analisar o perfil econômico e opções de oferta de eixos tecnológicos onde ainda não há IFs.
