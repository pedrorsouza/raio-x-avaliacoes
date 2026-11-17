# Raio-X de Avaliações

Ferramenta com IA generativa que transforma avaliações de clientes de um restaurante de delivery em diagnóstico, plano de ação e respostas sugeridas.

**Demo:** abra o `index.html` publicado no GitHub Pages (link na descrição do repositório).

## Problema
Um restaurante recebe dezenas de avaliações por semana. Ler uma a uma, separar por assunto e responder os casos urgentes toma horas do dono, e os padrões (ex.: atrasos recorrentes) passam despercebidos.

## Solução
O dono cola as avaliações e recebe:
- **Painel:** % de negativas, nota média e um gráfico de elogios × reclamações por tema
- **Achado principal:** a reclamação nº 1, calculada a partir das contagens
- **Plano de ação:** 3 a 5 ações priorizadas por impacto e esforço
- **Respostas sugeridas:** rascunhos para as avaliações urgentes, que o dono revisa antes de publicar
- **Tabela:** todas as avaliações classificadas, com filtro por tema e sentimento

## Como funciona
1. **Entrada:** uma avaliação por linha, com nota opcional (`4 | Muito bom`)
2. **IA classifica:** sentimento, temas de uma lista fixa de 7 e urgência, com resposta em JSON
3. **Código valida e conta:** descarta temas fora da lista e calcula os KPIs e o gráfico
4. **IA recomenda:** recebe só os números agregados e devolve o plano de ação e as respostas
5. **Pessoa revisa:** nada é publicado automaticamente

### Decisões de projeto
- A IA cuida da linguagem e o código cuida das contas, então os números do painel são exatos e auditáveis.
- Temas fechados deixam a análise comparável semana a semana.
- Duas chamadas separadas (classificar e recomendar): um erro numa não contamina a outra.

### Limitações
- Ironia e avaliações muito curtas podem ser mal classificadas. A tabela permite conferir uma a uma.
- Não inclua dados pessoais de clientes (LGPD).

### Próximos passos
- Coletar avaliações automaticamente e rodar toda semana (n8n + planilha)
- Alertar quando um tema disparar em relação à semana anterior
- Medir a acurácia da classificação com um conjunto de avaliações rotuladas à mão

## Stack
HTML, CSS e JavaScript puro · LLM Claude (Anthropic) · construído com desenvolvimento assistido por IA

A versão pública mostra uma análise de exemplo já processada. Os dados de exemplo são fictícios.

---
Pedro Antônio Rosa de Souza · Engenharia da Computação (UFES)
