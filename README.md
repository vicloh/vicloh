<h1 align="center">Victor Lohan</h1>

<p align="center">
  <strong>Desenvolvedor Full Stack</strong><br/>
  React · Next.js · TypeScript · React Native &nbsp;|&nbsp; Java · Quarkus · Spring Boot · Python · Django<br/>
  Do componente ao banco: eu desenho a tela, a API e o schema do mesmo sistema.
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/victor-lohan/"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="mailto:victorelup@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <img src="https://img.shields.io/badge/AWS%20Certified-Cloud%20Practitioner-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white" alt="AWS Certified Cloud Practitioner">
</p>

---

### Sobre mim

- Cursando **Engenharia de Software** no Instituto Federal de Goiás (IFG).
- **Full stack**: construo a interface em **React / Next.js / TypeScript** e a API em **Java (Quarkus, Spring Boot)** ou **Python (Django REST, FastAPI)**, sobre **PostgreSQL**. Também levo para o mobile com **React Native / Expo**.
- Venho de **QA** — passei pela Compass UOL construindo automação de testes, e isso mudou como eu escrevo código: teste, cobertura e pipeline entram junto com a feature, não depois.
- **AWS Certified Cloud Practitioner (CLF-C02)**.

---

### Tecnologias

<p align="center"><em>Frontend e mobile</em></p>
<p align="center">
  <img src="https://skillicons.dev/icons?i=typescript,javascript,react,nextjs,tailwindcss,vite,html,css" alt="Frontend"/>
</p>

<p align="center"><em>Backend e dados</em></p>
<p align="center">
  <img src="https://skillicons.dev/icons?i=java,spring,python,django,fastapi,nodejs,postgresql,mysql,mongodb" alt="Backend"/>
  <br/>
  <img src="https://img.shields.io/badge/Quarkus-4695EB?style=flat-square&logo=quarkus&logoColor=white" alt="Quarkus">
  <img src="https://img.shields.io/badge/Hibernate%20Panache-59666C?style=flat-square&logo=hibernate&logoColor=white" alt="Hibernate Panache">
  <img src="https://img.shields.io/badge/Expo-000020?style=flat-square&logo=expo&logoColor=white" alt="Expo">
  <img src="https://img.shields.io/badge/Realm-39477F?style=flat-square&logo=mongodb&logoColor=white" alt="Realm">
</p>

<p align="center"><em>Cloud, DevOps e qualidade</em></p>
<p align="center">
  <img src="https://skillicons.dev/icons?i=docker,aws,cloudflare,githubactions,git,maven,gradle,selenium,opencv" alt="DevOps"/>
  <br/>
  <img src="https://img.shields.io/badge/JUnit%205-25A162?style=flat-square&logo=junit5&logoColor=white" alt="JUnit 5">
  <img src="https://img.shields.io/badge/Mockito-78A641?style=flat-square" alt="Mockito">
  <img src="https://img.shields.io/badge/Testcontainers-291A2E?style=flat-square" alt="Testcontainers">
  <img src="https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white" alt="pytest">
  <img src="https://img.shields.io/badge/Robot%20Framework-000000?style=flat-square&logo=robotframework&logoColor=white" alt="Robot Framework">
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" alt="Playwright">
</p>

---

### Projetos

Boa parte do meu trabalho está em repositório privado — TCC com cliente real e produtos ainda não lançados. Abaixo está o que construí, a arquitetura e os números. Os públicos estão linkados no fim.

<br/>

#### Pescra — Monitoramento de Pesca para Turismo de Base Comunitária
`privado` · `TCC + cliente real` · `em desenvolvimento`

Plataforma para guias indígenas e ribeirinhos registrarem capturas **em campo, sem internet**, gerando dados científicos para órgãos reguladores (IBAMA/FUNAI). O app guarda tudo localmente e reconcilia com o servidor quando a rede volta.

```mermaid
flowchart LR
    APP["App React Native / Expo<br/>Realm offline-first"] -->|fila de sincronizacao| API
    PAINEL["Painel Next.js + MUI<br/>landing + administrativo"] --> API
    API["Django REST Framework<br/>JWT - multi-tenant"] --> DB[("PostgreSQL<br/>+ PostGIS")]
    API --> R2["Cloudflare R2<br/>fotos"]
    CF["Cloudflare Worker<br/>roteamento"] --> API
    CF --> PAINEL
```

- Time de 5 pessoas, fluxo de **Pull Request com code review** — sou um dos revisores.
- **Isolamento multi-tenant** por mixins, coberto por teste.
- **Catraca de cobertura no CI** (`pytest --cov-fail-under`), elevada de 75% para 79%.
- Minha atuação principal é a **API e o painel web**; participei também de features do app mobile.

**Stack:** Django 5.2 · Django REST Framework · SimpleJWT · PostgreSQL + PostGIS · Cloudflare R2 · Next.js 16 · MUI · React Native · Expo · Realm · pytest · Docker

<br/>

#### AvaliaAI — Correção automatizada de cartões-resposta
`privado` · `em dupla` · `cliente real`

Gera, lê e corrige cartões-resposta escolares. O professor sobe a folha — ou manda por e-mail — e recebe a correção. A leitura é **visão computacional (OMR)**: alinhamento por marcadores fiduciais, QR Code por aluno, detecção de bolhas por contorno.

```mermaid
flowchart LR
    FE["Next.js 16 + React 19<br/>TypeScript"] --> API
    MAIL["Cloudflare Email Worker<br/>correcao por e-mail"] --> API
    API["Quarkus + Panache<br/>JWT"] --> DB[("PostgreSQL 16")]
    API -->|evento CDI assincrono| IA["FastAPI + OpenCV<br/>pipeline OMR"]
    IA --> DB
```

- No front: estado de autenticação global via **Context API** e **refresh automático de token** por interceptor Axios.
- No back: **processamento assíncrono** por eventos CDI e migrations SQL idempotentes.
- Projeto planejado e construído **em dupla**, os dois na mesma tela.

**Stack:** Java 21 · Quarkus · Panache · PostgreSQL 16 · JWT · Next.js 16 · React 19 · TypeScript · FastAPI · OpenCV · Docker Compose

<br/>

#### InDexa — Geração automatizada de laudos técnicos
`privado` · `em desenvolvimento`

Reescrita completa de um sistema anterior meu ([auto-laudo](https://github.com/vicloh/auto-laudo), público), com duas decisões de arquitetura: saiu MongoDB/GridFS e entrou **PostgreSQL com Panache**; a geração de PDF saiu de dentro do código e virou **serviço dedicado com Gotenberg**.

```mermaid
flowchart LR
    FE["React + TypeScript<br/>Tailwind - Vite"] --> API
    API["Quarkus + Panache<br/>REST Client - OpenAPI"] --> DB[("PostgreSQL")]
    API --> PDF["pdf-engine<br/>Gotenberg"]
    API --> EXT["Integracoes externas<br/>via REST Client"]
```

- Separação de **teste unitário e de integração** no build (Surefire / Failsafe).
- Documentação de API gerada por **OpenAPI**.

**Stack:** Java 21 · Quarkus · Panache · PostgreSQL · Gotenberg · React · TypeScript · Tailwind · Vite · Docker

<br/>

#### Sistema de gestão para barbearias
`privado` · `em dupla` · `em desenvolvimento`

Projeto onde fui responsável pela **esteira de qualidade**: escrevi o pipeline de **CI/CD em GitHub Actions** e a **suíte de testes de integração** do backend, e atuo revisando e integrando os Pull Requests.

```mermaid
flowchart LR
    FE["Next.js"] --> API["Quarkus + Panache<br/>JWT"]
    API --> DB[("PostgreSQL")]
    FLY["Flyway<br/>migrations versionadas"] --> DB
    CI["GitHub Actions<br/>CI + CD"] -->|"JUnit 5 - Mockito<br/>Testcontainers - JaCoCo"| API
```

**Stack:** Java 21 · Quarkus · Panache · PostgreSQL · Flyway · JUnit 5 · Mockito · Testcontainers · JaCoCo · REST Assured · Next.js · Docker Compose

---

### Repositórios públicos

| Projeto | O que é | Stack |
|---|---|---|
| [auto-laudo](https://github.com/vicloh/auto-laudo) | API REST de laudos técnicos em PDF, deploy no Railway, integração com a BrasilAPI | Java 21 · Quarkus · MongoDB · GridFS · Docker |
| [challenge-final-PB-CompassUol](https://github.com/vicloh/challenge-final-PB-CompassUol) | Suíte E2E de **92 testes** — 100% dos endpoints e 100% das User Stories, 92% de sucesso | Robot Framework · Playwright · Python |
| [Classificador-de-Email](https://github.com/vicloh/Classificador-de-Email) | Classificação automática de e-mails com IA generativa e geração de resposta | Python · FastAPI · Google Gemini |
| [terminalJava](https://github.com/vicloh/terminalJava) | Simulador de terminal Linux — exercício de POO | Java |
| [teste-tecnico-java](https://github.com/vicloh/teste-tecnico-java) | Desafio técnico para vaga de estágio | Java |
| [Faculdade-Engenharia-De-Software](https://github.com/vicloh/Faculdade-Engenharia-De-Software) | Exercícios da graduação — beecrowd e calculadora algébrica | C |
