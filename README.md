# Diagrama Entidade-Relacionamento de uma oficina fictícia

### Dando continuidade aos estudos do **Bootcamp Randstad - Análise de Dados (2025)**, da DIO, concluí mais esse projeto para praticar os conceitos de modelagem de dados que vi nas aulas ✅ 

Assim como no projeto anterior (veja o repo [dio-der-ecommerce](https://github.com/victoreuclides/dio-der-ecommerce)), eu fiz o _DER_ na plataforma [_dbdiagram.com_](https://dbdiagram.io/home). Gosto bastante de lá pela praticidade e liberdade em criar, refazer e testar. 

Aqui embaixo segue o código que digitei para produção do diagrama. Se quiser ver o modelo pronto, ele também está na sessão de arquivos desse repo. 

```
// Criação das Tables

Table Cliente {
  cpf int [pk]
  nome varchar
  telefone varchar
  endereco varchar
}

Table Veiculo {
  id int [pk]
  placa varchar
  modelo varchar
  ano int 
  cor varchar
  cliente_cpf int
}

Table OrdemServico {
  id int [pk]
  data_solicitacao date
  prazo_entrega date
  status varchar
  valor_total varchar
  cliente_cpf int
  veiculo_id int
  peca_id int
  servico_id int
}

Table Peca {
  id int [pk]
  valor_peca varchar
}

Table Servico {
  id int [pk]
  valor_mao_obra varchar
  especialidade_permitida varchar
}

Table Tipo_OS {
  tipo_OS_id int
  equipe_id int
  descricao varchar
  descricao_tipo_os varchar
}

Table OS_Peca {
  OS_id int
  peca_id int
}

Table OS_Servico {
  OS_id int
  servico_id int
}

Table Equipe {
  id int [pk]
  especialidade_id int
}

Table Mecanico {
  id int [pk]
  nome varchar
  endereco varchar
  especialidade_mecanico varchar
  especialidade_id int
  equipe_id int
}

Table Especialidade {
  id int [pk]
  titulo varchar
  descricao varchar
}

// Relação entre Cliente e Veiculo
Ref: Veiculo.cliente_cpf > Cliente.cpf

// Especificações de OrdemServico
Ref: OrdemServico.cliente_cpf < Cliente.cpf
Ref: Tipo_OS.tipo_OS_id - OrdemServico.id
Ref: Tipo_OS.equipe_id - Equipe.id

// Relação de OS_Peca com as Tables
Ref: OS_Peca.OS_id > OrdemServico.id
Ref: OS_Peca.peca_id > Peca.id

// Relação entre OS_Servico e as Tables
Ref: OS_Servico.OS_id > OrdemServico.id
Ref: OS_Servico.servico_id > Servico.id


// Relação de Mecanico com Equipe e Especialidade
Ref: Mecanico.equipe_id < Equipe.id
Ref: Mecanico.especialidade_id - Especialidade.id
```

Ainda planejo revisitar essa atividade mais para a frente para conferir no que melhorei e o quanto me aprofundei em conhecimento e experiência até lá. Dá para aprimorar bastante esse projeto ainda (como adicionar uma tabela _"Estoque"_ para _"Peca"_, por exemplo). 

No mais, é isso! E sugestões são bem-vindas. Até mais 👋