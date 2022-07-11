### Processo Seletivo Assessoria VIP

# Lista de repositórios do GitHub

## Descrição

Nesse projeto você deverá desenvolver um site simples em que seja possível acessar a página de um usuário e visualizar seus repositórios públicos, além de poder favoritar/remover repositórios dos favoritos.

## Requisitos

- [ ] Uma barra de pesquisa para acessar a página de um usuário
- [ ] Uma página do usuário, mostrando suas informações e sua lista de repositórios
- [ ] **NÃO OBRIGATÓRIO** A lista de repositórios deverá conter uma paginação com rolagem infinita, ou seja, mais repositórios serão carregados conforme o usuário rola a página para baixo até que não haja mais repositórios (estilo Facebook, Instagram, Twitter, etc.)
- [ ] Possibilidade de favoritar e remover repositórios dos favoritos (utilizar vuex)
- [ ] Listar repositórios favoritos

## Layout

Desenvolver o site baseado nesse [protótipo](https://www.figma.com/file/NPsgIQuNZEv46Jy9u1d90E/Processo-Seletivo?node-id=0%3A1).

## Tecnologias obrigatórias

- Vue 2
- Vuex (gerenciar favoritos)
- Vue Apollo (requisições à API GraphQL do GitHub)<br>

**Sinta-se livre para adicionar qualquer outra tecnologia, desde que utilize as tecnologias obrigatórias.**

## Informações úteis

#### Sobre a API do GitHub

A API GraphQL do GitHub requer uma autenticação. Você deverá gerar um token de acesso pessoal no seu GitHub e utilizá-lo no projeto.<br>
Caso não queira deixar o seu token visível em seu repositório, disponibilize um guia em seu **README** sobre onde substituir o token.<br>
Para mais detalhes sobre como gerar um token, acesse o [guia de autenticação com GraphQL do GitHub](https://docs.github.com/pt/graphql/guides/forming-calls-with-graphql#authenticating-with-graphql).

#### Exemplo de requisição para listagem dos repositórios

- login - corresponde ao nome do usuário no GitHub
- first - um número que limita a quantidade de repositórios trazidas pela requisição. Por exemplo, se passar um `first: 10`, serão trazidos somente **10 repositórios** na requisição.
- after - funciona como um offset, sendo o ponto de partida para a listagem dos itens. O **after** deverá ser o valor do **cursor** do último repositório exibido. Ou seja, se o último repositório da lista tiver um cursor equivalente à `"abc"`, a próxima requisição da paginação deverá ser feita com `after: "abc"`<br>
  _Para mais detalhes sobre a paginação, veja a [documentação do Vue Apollo sobre pagination](https://apollo.vuejs.org/guide/apollo/pagination.html)_

```gql
query ($login: String!, $first: Int!, $after: String) {
  user(login: $login) {
    id
    name
    login
    avatarUrl
    bio
    repositories(first: $first, after: $after) {
      totalCount
      edges {
        cursor
        node {
          id
          name
          description
          updatedAt
          primaryLanguage {
            id
            name
          }
        }
      }
    }
  }
}
```

## Sobre a entrega

- Clone esse repositório (ou copie o README)
- Desenvolva seu projeto atualizando seu repositório
- Envie o link do seu repositório para **maycon@assessoriavip.com.br**

## Links

[Documentação da API GraphQL do GitHub](https://docs.github.com/pt/graphql/overview/about-the-graphql-api)<br>
[GitHub GraphQL Explorer](https://docs.github.com/pt/graphql/overview/explorer) (para testar a API GraphQL)<br>
[Documentação Vue Apollo](https://apollo.vuejs.org/guide/)
