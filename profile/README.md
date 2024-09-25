## Hi there 👋, SOAT FIAP Grupo #71

## Tech challenge deliverables
- You can find all Phase 1 deliverables on the [Wiki page](https://github.com/soat-fiap/FIAP.TechChallenge.ByteMeBurger/wiki)
- Phase 2 Deliverables
   - [Business requirements](https://github.com/soat-fiap/FIAP.TechChallenge.ByteMeBurger/wiki/Business-Requirements-Document)
   - [Infrastructure](https://github.com/soat-fiap/FIAP.TechChallenge.ByteMeBurger/wiki/Kubernetes-Infrastructure-Requirements)
   - Diagrams
     - [Sequence Diagram (Main Flow)](https://github.com/soat-fiap/FIAP.TechChallenge.ByteMeBurger/wiki/Main-flow-sequence-Diagrams-(Phase-2))
   - [Testing locally](#running-with-kubernetes-locally)
      -  to get some help with application flow testing, click [here](https://github.com/soat-fiap/FIAP.TechChallenge.ByteMeBurger?tab=readme-ov-file#testing)
   - [Video](https://www.youtube.com/watch?v=34ffDcUoUTg)
 - Phase 3 Deliverables
    - **Implement an API Gateway and a serverless function for client authentication using CPF (Brazilian ID number).**
        - Integrate with the authentication system to identify the client.

    - **Implement CI/CD best practices, separating code into distinct repositories:**
      - **Repository 1:** [Lambda function code](https://github.com/soat-fiap/bmb.authenticator)
      - **Repository 2:** [Kubernetes infrastructure defined with Terraform](https://github.com/soat-fiap/bmb.infra)
      - **Repository 3:** [Managed database infrastructure defined with Terraform](https://github.com/soat-fiap/bmb.database)
      - **Repository 4:** [Application code deployed to Kubernetes](https://github.com/soat-fiap/FIAP.TechChallenge.ByteMeBurger)
      - ***Repository 5:** [Process domain events asynchronously](https://github.com/soat-fiap/bmb.events.processor)
      - ***Repository 6:** [Segregated repository for User management (AWS Cognito)](https://github.com/soat-fiap/bmb.users)

    - **Configure automated deployments to the cloud account using actions for each repository:**
      - Protect `main`/`master` branches to prevent direct commits. 
      - Enforce pull requests for all code changes.

    - **Improve the chosen database's structure:**
      - Document the database design following data modelling standards.
      - Provide a justification for the chosen database technology.

    - **You are free to choose your preferred cloud provider but must utilize serverless services:**
      - **Functions:** AWS Lambda, Azure Functions, or Google Cloud Functions (or similar).
      - **Managed Databases:** AWS RDS, Azure SQL Database, Google Cloud SQL (or similar).
      - **Authentication Systems:** AWS Cognito, Microsoft Azure Active Directory, Google Cloud Identity Platform (or similar).
    - [Video](https://www.youtube.com/watch?v=J2rRSJy24kM)

<details>
   <summary>Pipeline flow</summary>
         
  ```mermaid
           graph TD
       subgraph Infrastructure
           bmb.infra["bmb.infra"]
       end
   
       subgraph Storage
           bmb.database["bmb.database"]
           bmb.users["bmb.users"]
       end
   
       subgraph API
           bmb.api["bmb.api"]
       end
   
       subgraph Integration
           bmb.authenticator["bmb.authenticator"]
           bmb.events.processor["bmb.events.processor"]
       end
   
       bmb.api --> bmb.users
       bmb.api --> bmb.database
       bmb.api --> bmb.infra
       bmb.database --> bmb.infra
       bmb.authenticator --> bmb.api
       bmb.events.processor --> bmb.api
   ```
  </details>

## Current infrastructure
![Current infrastructure](https://github.com/user-attachments/assets/c5325ee8-7856-4d85-86e9-5428ae7049f1)


<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
