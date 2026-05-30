# 📊 Dashboard de Cancelamento de Clientes — Análise de Churn

## 📌 Sobre o projeto

Este projeto tem como objetivo analisar o cancelamento de clientes, também conhecido como **churn**, utilizando uma base fictícia de clientes.

A análise foi desenvolvida para identificar padrões de cancelamento, entender quais planos apresentam maior taxa de churn, avaliar o impacto financeiro da receita perdida e analisar o comportamento dos clientes de acordo com NPS, tempo de relacionamento e localização.

O dashboard foi construído no **Power BI**, com preparação inicial da base no **Excel**, utilizando fórmulas como **PROCV**, **PROCX**, classificações de NPS, cálculo de tempo de cliente, receita perdida e risco de churn.

---

## 🎯 Objetivo da análise

O principal objetivo do projeto é responder perguntas de negócio como:

- Quantos clientes estão ativos e quantos cancelaram?
- Qual é a taxa geral de churn?
- Qual plano possui maior volume de cancelamentos?
- Qual plano apresenta maior taxa de churn?
- Quanto de receita foi perdida com clientes cancelados?
- Clientes detratores cancelam mais?
- Em qual faixa de tempo os clientes mais cancelam?
- Quais regiões concentram mais clientes ativos e cancelados?

---

## 🛠️ Ferramentas utilizadas

- **Excel Online**
- **Power BI**
- **Power Query**
- **DAX**
- **PROCV**
- **PROCX**

---

## 🧾 Base de dados

A base utilizada é fictícia e foi criada para fins de estudo e portfólio.

Ela contém informações como:

- ID do cliente
- Nome do cliente
- Cidade
- UF
- Idade
- Segmento
- Canal de aquisição
- Plano contratado
- Valor do plano
- Data de entrada
- Status do cliente
- Data de cancelamento
- NPS
- Tempo de cliente
- Classificação de NPS
- Receita perdida
- Risco de churn

---

## 🧮 Tratamentos realizados no Excel

Antes da construção do dashboard, foram criadas colunas auxiliares no Excel para enriquecer a análise.

### Tempo de cliente em dias

```excel
=SE(M2="Cancelado";N2-K2;HOJE()-K2)

Faixa de tempo do cliente
=SE(O2<=30;"Até 30 dias";SE(O2<=90;"31 a 90 dias";SE(O2<=180;"91 a 180 dias";SE(O2<=365;"181 a 365 dias";"Mais de 1 ano"))))

Churn
=SE(M2="Cancelado";1;0)

Receita perdida
=SE(Q2=1;J2;0)

Classificação NPS
=SE(R2<=6;"Detrator";SE(R2<=8;"Neutro";"Promotor"))

Risco de churn
=SE(Q2=1;"Alto risco";SE(R2<=6;"Alto risco";SE(R2<=8;"Médio risco";"Baixo risco")))

Também foram utilizadas fórmulas como PROCV e PROCX para buscar dados entre tabelas, como informações dos planos dos clientes.

📐 Medidas DAX criadas no Power BI
Total de clientes
Total Clientes = COUNT(Base_Clientes[ID_Cliente])

Clientes ativos
Clientes Ativos = 
CALCULATE(
    [Total Clientes],
    Base_Clientes[Status] = "Ativo"
)
Clientes cancelados
Clientes Cancelados = 
CALCULATE(
    [Total Clientes],
    Base_Clientes[Status] = "Cancelado"
)
Taxa de churn
Taxa Churn = 
DIVIDE(
    [Clientes Cancelados],
    [Total Clientes],
    0
)

Receita perdida
Receita Perdida = 
SUM(Base_Clientes[Receita_Perdida])

NPS médio
NPS Médio = 
AVERAGE(Base_Clientes[NPS])

Ticket médio
Ticket Médio = 
AVERAGE(Base_Clientes[Valor_Plano])

Tempo médio de cliente
Tempo Médio Cliente = 
AVERAGE(Base_Clientes[Tempo_Cliente_Dias])

📊 Indicadores do dashboard
O dashboard apresenta os seguintes indicadores:

Total de clientes
Clientes ativos
Clientes cancelados
Taxa de churn
Receita perdida
NPS médio
Cancelamentos por plano
Taxa de churn por plano
Cancelamentos por classificação NPS
Receita perdida por plano
Cancelamentos por tempo de cliente
Ativos x cancelados por localização

📷 Preview do dashboard

🔎 Principais insights

Durante a análise, foi possível observar que:

A taxa geral de churn ficou em aproximadamente 29,40%.
O plano Basic Mensal concentrou o maior volume de cancelamentos.
Clientes classificados como Detratores apresentaram maior volume de cancelamento.
A maior parte dos cancelamentos ocorreu entre clientes com mais de 1 ano de relacionamento.
A receita perdida total foi de aproximadamente R$ 25,68 mil.
A análise por localização ajuda a visualizar a distribuição entre clientes ativos e cancelados por cidade.
💡 Aprendizados do projeto

Com este projeto, foi possível praticar:

Limpeza e preparação de dados no Excel;
Uso de PROCV e PROCX;
Criação de colunas auxiliares para análise;
Transformação de dados no Power Query;
Criação de medidas DAX;
Construção de dashboard no Power BI;
Análise de churn;
Storytelling com dados;
Interpretação de indicadores de negócio.

🚀 Como visualizar o projeto

Baixe o arquivo .pbix disponível na pasta dashboard.
Abra o arquivo no Power BI Desktop.
Caso necessário, atualize a fonte de dados apontando para o arquivo Excel da pasta base.

👩‍💻 Autora

Thaís Menezes
Analista de Dados em desenvolvimento





