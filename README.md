

Este projeto foi desenvolvido como parte da disciplina de **Arquitetura de Software**, com o objetivo prático de implementar e consolidar os conceitos do padrão arquitetural **MVC (Model-View-Controller)** utilizando o framework **Spring Boot** em Java.

## Explicação da Arquitetura

O foco principal deste projeto é demonstrar a separação de responsabilidades. Adotamos o princípio de que a **separação física de arquivos reflete a separação arquitetural**, facilitando a manutenção, evolução e testabilidade do software.

### O Padrão MVC

A aplicação está dividida em três componentes fundamentais:

1. **Model (Modelo) - `Aluno.java`**:
   - Contém os dados, o estado e as **regras de negócio** essenciais da aplicação.
   - É completamente independente de protocolos HTTP ou de interfaces gráficas HTML.
   - Implementa validações diretamente na entidade (como a validação de obrigatoriedade do nome).

2. **View (Visão) - `alunos-form.html` e `alunos-lista.html`**:
   - Responsável estritamente pela **apresentação e interface com o usuário**.
   - Não executa regras de negócio e não valida lógica complexa.
   - Utiliza o motor de templates **Thymeleaf** para renderizar dinamicamente os dados enviados pelo Controller.

3. **Controller (Controlador) - `AlunoController.java`**:
   - Atua como o **coordenador central** do fluxo da aplicação.
   - Intercepta as requisições HTTP (`@GetMapping` e `@PostMapping`), gerencia os dados que entram e saem, aciona o Model correspondente e decide qual View deve ser apresentada ao usuário.
   - Não renderiza HTML diretamente e não cria regras de negócio próprias, apenas delega.

###  Módulos, Camadas e Componentes
- **Módulos**: O projeto é estruturado de forma modularizada através de pacotes bem definidos (`model`, `controller`).
- **Camadas**: Existe um isolamento claro de camadas onde a interface (View) interage apenas com a camada de controle (Controller), que por sua vez manipula e valida as regras de negócio (Model).

---

