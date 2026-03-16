# TypeScript POO E-commerce – Sistema de Carrinho de Compras

![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?logo=typescript)
![Node](https://img.shields.io/badge/Node.js-20-green?logo=node.js)
![POO](https://img.shields.io/badge/Paradigma-POO-orange)
![Status](https://img.shields.io/badge/status-estudo-blue)
![License](https://img.shields.io/badge/license-MIT-green)

# Sobre o projeto

Este projeto é uma **simulação simples da lógica de um sistema de e-commerce**, desenvolvido utilizando **TypeScript** e conceitos de **Programação Orientada a Objetos (POO)**.

A aplicação modela algumas estruturas básicas presentes em plataformas de e-commerce, como:

- categorias de produtos  
- produtos  
- usuários com diferentes permissões  
- carrinho de compras  

O principal objetivo da atividade é demonstrar o uso de **tipagem forte do TypeScript**, organização de código e utilização de **High Order Functions** para manipulação de dados.

O sistema permite adicionar produtos ao carrinho, controlar quantidades e calcular automaticamente o valor total da compra.

## Estrutura do Projeto

A organização do projeto segue uma separação simples entre **models**, **classes** e o **ponto de entrada da aplicação**, facilitando a manutenção e leitura do código.

    ts-poo-ecommerce/
    ├─ src/
    │   ├─ classes/
    │   │   ├─ Cart.ts
    │   │   └─ User.ts
    │   ├─ models/
    │   │   ├─ CartItem.ts
    │   │   ├─ Category.ts
    │   │   └─ Product.ts
    │   └─ index.ts
    ├─ .gitignore
    ├─ LICENSE
    ├─ package-lock.json
    ├─ package.json
    ├─ README.md
    └─ tsconfig.json

### Organização

- **models/** → contém as interfaces que definem a estrutura dos dados.
- **classes/** → contém as classes responsáveis pela lógica da aplicação.
- **index.ts** → ponto de entrada do projeto e exemplo de execução.
- **tsconfig.json** → configuração do TypeScript.
- **package.json** → dependências e scripts do projeto.
- **README.md** → documentação do projeto.

Essa separação ajuda a manter o projeto mais organizado e facilita futuras manutenções.

# Tecnologias utilizadas

Este projeto foi desenvolvido utilizando:

- TypeScript  
- Node.js  
- Programação Orientada a Objetos (POO)  
- Interfaces e Enums do TypeScript  
- High Order Functions do JavaScript  

# Estrutura das Models

O sistema utiliza **interfaces do TypeScript** para definir a estrutura dos dados.

### Category

Representa a categoria de um produto.

    interface Category {
      id: number;
      name: string;
    }

### Product

Representa um produto do sistema.

    interface Product {
      id: number;
      name: string;
      price: number;
      category: Category;
    }

# Gerenciamento de usuários

Para controlar os tipos de usuários foi utilizado um **Enum do TypeScript**.

    enum UserRole {
      ADMIN = "ADMIN",
      CUSTOMER = "CUSTOMER",
    }

Isso garante que apenas esses dois valores sejam aceitos pelo sistema.

A classe `User` representa um usuário da aplicação:

    class User {
      id: number;
      username: string;
      email: string;
      role: UserRole;

      constructor(id: number, username: string, email: string, role: UserRole) {
        this.id = id;
        this.username = username;
        this.email = email;
        this.role = role;
      }
    }

# Lógica do carrinho de compras

O carrinho armazena produtos utilizando a interface `CartItem`.

    interface CartItem {
      product: Product;
      quantity: number;
    }

A classe `Cart` é responsável por gerenciar os itens do carrinho.

## Adicionando produtos

O método `addItem()` utiliza **.some()** para verificar se o produto já existe no carrinho.

Se o produto já estiver presente, apenas **aumenta a quantidade**, evitando duplicação de itens.

    addItem(product: Product, quantity: number): void

## Total de itens

O método `getTotalItems()` calcula o total de unidades utilizando **.reduce()**.

    getTotalItems(): number

## Valor total da compra

O método `getFinalPrice()` também utiliza **.reduce()** para calcular o valor total da compra.

    getFinalPrice(): number

# Exemplo de funcionamento

O exemplo abaixo demonstra a criação de categorias, produtos, usuário e carrinho.

    const instrumentos: Category = { id: 1, name: "Instrumentos Musicais" };
    const roupas: Category = { id: 2, name: "Roupas" };

    const guitarra: Product = {
      id: 1,
      name: "Guitarra",
      price: 400,
      category: instrumentos,
    };

    const camiseta: Product = {
      id: 2,
      name: "Camiseta",
      price: 100,
      category: roupas,
    };

Criando um usuário:

    const usuario = new User(
      1,
      "isaiasoliveira",
      "isaiaswebnet@gmail.com",
      UserRole.CUSTOMER
    );

Adicionando produtos ao carrinho:

    carrinho.addItem(guitarra, 1);
    carrinho.addItem(camiseta, 2);
    carrinho.addItem(guitarra, 1);

Resultado esperado:

    Total de itens: 4
    Valor total: R$ 1000.00

# Como executar o projeto

Clone o repositório:

    git clone https://github.com/skynetsites/ts-poo-ecommerce

Entre na pasta do projeto:

    cd ts-poo-ecommerce

Instale as dependências:

    npm install

Execute o projeto:

    npm run start:prod

# Aprendizados

Durante o desenvolvimento desta atividade foi possível praticar:

- Tipagem forte utilizando TypeScript  
- Criação de interfaces para modelar dados  
- Uso de Enum para controle de permissões  
- Aplicação de Programação Orientada a Objetos  
- Manipulação de arrays com `.some()` e `.reduce()`  
- Organização básica de projetos TypeScript  

# Objetivo educacional

Este projeto foi desenvolvido como **atividade prática de estudo**, com o objetivo de aplicar conceitos fundamentais de **TypeScript e Programação Orientada a Objetos** dentro de um cenário simples de e-commerce.

# Contribuição

Se quiser contribuir com feedback ou sugestões, fique à vontade para abrir uma **[Issue](https://github.com/skynetsites/ts-poo-ecommerce/issues)** ou **[enviar ideias](https://github.com/skynetsites/ts-poo-ecommerce/pulls)**. 

# Licença

Este projeto está licenciado sob a **Licença MIT**.

Veja o arquivo **[LICENSE](./LICENSE)** para mais detalhes.

# Autor

Projeto desenvolvido por **Isaias Oliveira**.  
Conecte-se comigo no **[in/skynetsites](https://www.linkedin.com/in/skynetsites/)**