<!--- Picture references -->
[logo]: pics/AGCO_Logo.png "Logo"
[eu_logo]: pics/EU_Logo.png "EU Logo"
[pic001]: pics/Picture_001.png "Picture 001"
[pic002]: pics/Picture_002.png "Picture 002"
[pic003]: pics/Picture_003.png "Picture 003"
[pic004]: pics/Picture_004.png "Picture 004"
[pic005]: pics/Picture_005.png "Picture 005"
[pic006]: pics/Picture_006.png "Picture 006"
[pic007]: pics/Picture_007.png "Picture 007"
[pic008]: pics/Picture_008.png "Picture 008"
[pic009]: pics/Picture_009.png "Picture 009"
[pic010]: pics/Picture_010.png "Picture 010"
[pic011]: pics/Picture_011.png "Picture 011"
[pic012]: pics/Picture_012.png "Picture 012"
[pic013]: pics/Picture_013.png "Picture 013"
[pic014]: pics/Picture_014.png "Picture 014"
[pic015]: pics/Picture_015.png "Picture 015"
[pic016]: pics/Picture_016.png "Picture 016"
[pic017]: pics/Picture_017.png "Picture 017"
[pic018]: pics/Picture_018.png "Picture 018"
[pic019]: pics/Picture_019.png "Picture 019"
[pic020]: pics/Picture_020.png "Picture 020"
[pic021]: pics/Picture_021.png "Picture 021"
[pic022]: pics/Picture_022.png "Picture 022"
[pic023]: pics/Picture_023.png "Picture 023"
[pic024]: pics/Picture_024.png "Picture 024"
[pic025]: pics/Picture_025.png "Picture 025"
[pic026]: pics/Picture_026.png "Picture 026"
[pic027]: pics/Picture_027.png "Picture 027"
[pic028]: pics/Picture_028.png "Picture 028"
[pic029]: pics/Picture_029.png "Picture 029"
[pic030]: pics/Picture_030.png "Picture 030"
[pic031]: pics/Picture_031.png "Picture 031"
[pic032]: pics/Picture_032.png "Picture 032"
[pic033]: pics/Picture_033.png "Picture 033"
[pic034]: pics/Picture_034.png "Picture 034"
[pic035]: pics/Picture_035.png "Picture 035"
[pic036]: pics/Picture_036.png "Picture 036"
[pic037]: pics/Picture_037.png "Picture 037"
[pic038]: pics/Picture_038.png "Picture 038"
[pic039]: pics/Picture_039.png "Picture 039"
[pic040]: pics/Picture_040.png "Picture 040"
[pic041]: pics/Picture_041.png "Picture 041"
[pic042]: pics/Picture_042.png "Picture 042"
[pic043]: pics/Picture_043.png "Picture 043"
[pic044]: pics/Picture_044.png "Picture 044"
[pic045]: pics/Picture_045.png "Picture 045"
[pic046]: pics/Picture_046.png "Picture 046"
[pic047]: pics/Picture_047.png "Picture 047"
[pic048]: pics/Picture_048.png "Picture 048"
[pic049]: pics/Picture_049.png "Picture 049"
[pic050]: pics/Picture_050.png "Picture 050"
[pic051]: pics/Picture_051.png "Picture 051"

<!--- Header -->
![alt text][logo]
# SAP AI ENABLEMENT/USE CASES AT AGCO
A comprehensive, how-to guide to setup AI scenarios in SAP Cloud Business Technology Platform

Created by: Halmai, Gabor 2024
LinkedIn: https://www.linkedin.com/in/gabor-halmai/

<!--- Main Content -->
# Contents 
1. [Scope of this Document](#scope-of-this-document)
2. [General](#general)
3. [Development options on SAP BTP](#development-options-on-sap-btp)
4. [Setup configuration for BTP regards SAP AI Core/Launchpad](#setup-configuration-for-btp-regards-sap-ai-corelaunchpad)
    1. [Subaccount creation](#subaccount-creation)
5. [Tools/CLIs](#toolsclis-technical)
    1. [Docker](#docker)
    2. [Github](#github)
    3. [Microsoft VS Code](#microsoft-vs-code)
    4. [AWS S3 Bucket](#aws-s3-bucket)
        1. [Upload the datasets to AWS S3 Storage](#upload-the-datasets-to-aws-s3-storage)
    5. [BTP Cloud Foundry](#btp-cloud-foundry)
    6. [Setup an Account -- SAP AI Core Launchpad Demo](#setup_an_account)
    7. [Cloud Foundry API Endpoint](#cloud-foundry-api-endpoint)
    8. [Login to BTP Cloud Foundry (w/ or w/o SSO - Global/company account)](#login-to-btp-cloud-foundry-w-or-wo-sso-globalcompany-account)
    9. [Login to BTP Cloud Foundry (w/ or w/o SSO) (Trial (Free) account)](#login-to-btp-cloud-foundry-w-or-wo-sso-trial-free-account)
6. [Get BTP Cloud Foundry Marketplace Services](#get-btp-cloud-foundry-marketplace-services)
    1. [Create an instance of the service](#create-an-instance-of-the-service)
    2. [List the service instance](#list-the-service-instance)
    3. [Create a service key](#create-a-service-key)
    4. [Get service key credentials](#get-service-key-credentials)
    5. [Bind your application with the service key](#bind-your-application-with-the-service-key)
    6. [Bind your application](#bind-your-application)
7. [BTP Object Store Service](#btp-object-store-service)
8. [SAP AI Core](#sap-ai-core)
9. [How to Integrate a Python App with SAP Business Application Studio for an SAP S/4HANA Cloud System](#how-to-integrate-a-python-app-with-sap-business-application-studio-for-an-sap-s4hana-cloud-system)
10. [Upload Microsoft Word documents to SAP AI Core](#upload-microsoft-word-documents-to-sap-ai-core)
    1. [Install Python](#install-python)
    2. [Installing Packages](#installing-packages-httpspackaging.python.orgenlatesttutorialsinstalling-packages)
    3. [PyPI · The Python Package Index](#pypi-the-python-package-index)
    4. [ai-core-sdk · PyPI](#ai-core-sdk-pypi)
    5. [Local Documentation](#local-documentation)
    6. [Installing Python extension](#installing-python-extension)
    7. [Microsoft Visual Studio Code (VS Code)](#microsoft-visual-studio-code-vs-code-httpscode.visualstudio.comdocslanguagespython)
11. [Issues](#issues)
12. [Copyrights](#copyrights)

***
# Scope of this Document
AI is crucial also in the SAP world because it enhances business
processes by bringing **automation, intelligent insights, and predictive
capabilities** to core enterprise functions. By integrating AI into SAP systems, businesses can:

-   **Automate repetitive tasks** (e.g., invoice processing, data entry) with technologies like **RPA (Robotic Process Automation)**, increasing efficiency and reducing errors.

-   **Improve decision-making** by leveraging **predictive analytics** and **machine learning** to forecast trends, optimize supply chains, and personalize customer experiences (that is the focus of this pilot project regarding AI enablement/possible use-cases at AGCO).

-   **Enhance user experiences** with AI-driven chatbots and digital assistants (like SAP CoPilot), providing real-time assistance and reducing manual effort.

-   **Unlock insights from data** by analyzing large volumes of business data across the enterprise for better insights and operational improvements.

In a nutshell, AI in the SAP world enables businesses to become more **agile, efficient, and data-driven**, leading to smarter operations and innovation at scale.

# General

**SAP Business Technology Platform (BTP)**

SAP BTP (Business Technology Platform) is a comprehensive suite of integrated cloud services and solutions designed to help organizations accelerate digital transformation. It combines technologies for database management, application development, analytics, integration, and intelligent technologies, enabling businesses to innovate, integrate, and extend SAP and third-party applications.

A detailed breakdown of SAP BTP's core components:

**1. Database and Data Management:**

-   **SAP HANA Cloud**: A scalable, in-memory cloud database that enables real-time analytics and applications. It provides data processing capabilities and integration with on-premise systems.

-   **SAP Data Intelligence**: This solution helps manage data from multiple sources, improving data quality, governance, and compliance.

-   **SAP BW/4HANA**: A data warehouse solution optimized for the SAP HANA platform, enabling advanced analytics on large volumes of data.

**2. Application Development and Integration:**

-   **SAP Extension Suite**: This allows businesses to customize and extend their existing SAP applications or create new cloud-native applications. It offers pre-built templates, tools, and integration options for faster development.

-   **SAP Integration Suite**: A suite of tools and connectors for integrating SAP systems with third-party systems, on-premise or in the cloud. It includes API management, event streaming, and more.

**3. Analytics:**

-   **SAP Analytics Cloud**: A cloud-based solution combining business intelligence, planning, and predictive analytics. It provides interactive dashboards, reports, and machine learning-driven insights.

-   **SAP Data Warehouse Cloud**: A business-ready data warehouse that combines data management with built-in analytics, enabling collaboration across departments.

**4. Intelligent Technologies:**

-   **Machine Learning**: SAP BTP offers machine learning models and tools, such as SAP AI Core and SAP AI Foundation, which can be integrated into applications to deliver intelligent insights and automation.

-   **IoT (Internet of Things)**: SAP IoT services on BTP enable businesses to connect, manage, and analyze data from devices, helping optimize processes and business outcomes.

-   **Robotic Process Automation (RPA)**: With SAP Intelligent RPA, companies can automate repetitive tasks, improve efficiency, and reduce errors.

**5. Business Process Management (BPM):**

-   **SAP Workflow Management**: This allows organizations to design, implement, and manage workflows that automate business processes across multiple systems.

-   **Business Rules**: These allow for dynamic changes in decision-making processes without needing to alter the application logic, enhancing flexibility.

**6. Security and Compliance:**

-   **Identity Management**: SAP BTP offers identity and access management capabilities to secure users and applications.

-   **Governance and Compliance**: Built-in tools ensure that businesses meet industry standards and regulations like GDPR, ensuring data protection and privacy.

**7. Multi-Cloud and Hybrid Capabilities:**

SAP BTP is designed to work across multiple cloud environments (such as AWS, Azure, and Google Cloud) as well as hybrid setups. This allows businesses flexibility in deployment and management of their applications and data.

**8. Key Benefits of SAP BTP:**

-   **Innovation and Agility**: Provides tools to build, extend, and integrate applications quickly, fostering innovation.

-   **Scalability**: BTP services are cloud-native and scalable, allowing businesses to adapt to changing requirements.

-   **Data-Driven Decisions**: With embedded analytics and intelligent technologies, BTP helps businesses leverage data for better decision-making.

-   **Seamless Integration**: Offers pre-built connectors and integration flows, allowing for easy integration with SAP ERP, S/4HANA, and third-party systems.

In essence, SAP BTP enables businesses to transform their processes,
develop custom applications, and harness the power of data while maintaining integration with SAP's core ERP systems. It is particularly suited for organizations looking to leverage cloud-based solutions while ensuring continuity with their existing SAP infrastructure.

**SAP Business Application Studio (BAS)**

**SAP Business Application Studio** (BAS) is a modern, integrated
development environment (IDE) tailored for SAP developers to design and
extend applications on SAP's cloud platform, particularly within **SAP Business Technology Platform (BTP)**. It provides a comprehensive toolset for developing, testing, debugging, and deploying cloud-native
SAP applications and extensions.

Detailed overview of SAP Business Application Studio:

**1. Purpose and Key Features:**

-   **Cloud-based Development Environment**: SAP BAS is cloud-native, meaning developers can access it through a web browser without needing local installation or setup. It's designed to work seamlessly in the SAP BTP environment.

-   **Multiple Programming Languages**: It supports a wide range of programming languages such as Java, JavaScript, Node.js, HTML5, and more, allowing for diverse application development.

-   **Pre-configured Dev Spaces**: BAS offers **Dev Spaces**, which are tailored environments set up for specific development scenarios (e.g., SAP Fiori, CAP, SAP HANA, or full-stack development). These Dev Spaces come pre-configured with the relevant tools, libraries, and configurations, saving developers time.

-   **Low-Code and Pro-Code Development**: While BAS is geared toward professional developers, it also includes tools that cater to low-code development, empowering both technical and non-technical users to build or extend applications.

-   **Integration with Git**: For version control, BAS is integrated with Git, allowing developers to manage code changes and collaborate with team members using standard Git workflows.

**2. Development Scenarios:**

-   **SAP Fiori Applications**: BAS is optimized for creating SAP Fiori apps, which are user-centric interfaces for SAP applications. Developers can build, test, and deploy SAP Fiori elements and freestyle applications.

-   **Cloud Application Programming (CAP) Model**: BAS supports CAP, SAP's framework for developing cloud-native applications. CAP allows developers to focus on the business logic while abstracting the complexities of infrastructure and integration.

-   **SAP HANA and Database Development**: BAS provides an environment for modeling and developing applications on top of SAP HANA databases. Developers can build data models, manage schemas, and create calculation views with ease.

-   **Full-Stack Development**: It supports full-stack application development, where developers can create the front end (e.g., using Fiori or HTML5) and back end (e.g., using Node.js or CAP) within the same environment.

**3. Pre-built Templates and Wizards:**

-   **Project Wizards**: BAS comes with pre-configured wizards to quickly generate projects for different SAP scenarios, such as SAP Fiori, CAP applications, or integration projects.

-   **Code Assistants**: Code templates and generators help reduce manual coding and improve productivity, especially in scenarios like creating Fiori Elements applications.

-   **UI5 Controls and Previews**: BAS provides access to SAPUI5 controls, along with an integrated preview tool for live visualization of the user interface (UI) being developed.

**4. Integration with SAP BTP Services:**

-   **Seamless BTP Integration**: BAS is deeply integrated with SAP BTP, allowing developers to access various services like SAP HANA, SAP Analytics Cloud, SAP Integration Suite, etc. directly from the IDE.

-   **Business Application Extension**: Developers can extend existing SAP applications (e.g., SAP S/4HANA) by using SAP BTP services and integrating them with other cloud services or on-premise systems.

**5. Debugging, Testing, and Deployment:**

-   **Integrated Debugging**: BAS offers integrated debugging tools for different programming languages, including breakpoints, step-through execution, and error tracking.

-   **Unit Testing and Validation**: Tools within BAS help developers create and run unit tests to validate their code, ensuring high-quality application delivery.

-   **CI/CD Pipelines**: BAS supports continuous integration and deployment (CI/CD) pipelines, enabling automated testing and seamless deployment of applications across environments.

-   **Deployment to Cloud Foundry**: Developers can deploy their applications to the SAP BTP Cloud Foundry environment directly from the IDE, facilitating rapid deployment and iteration.

**6. Collaboration and Extensions:**

-   **Collaboration Tools**: BAS supports features for team collaboration, allowing developers to work together in real-time on the same project using shared Dev Spaces or Git.

-   **Extensibility through Plugins**: Like many modern IDEs, BAS is highly extensible, allowing developers to add plugins and extensions to customize the environment to their workflow and needs.

**7. Comparison with SAP Web IDE:**

**SAP Business Application Studio** is the successor to **SAP Web IDE**,
which was previously used for developing SAP applications. Some key
improvements BAS brings over Web IDE include:

-   A more modern and flexible architecture based on open-source technologies (e.g., Eclipse Theia).

-   Dev Spaces, which allow developers to set up customized environments tailored to specific development tasks.

-   Better support for cloud-native application development, including the CAP model and more integration with SAP BTP services.

-   A more performant, responsive, and user-friendly interface compared to SAP Web IDE.

**8. Security and Access Control:**

-   **Role-based Access**: BAS incorporates role-based access control (RBAC), ensuring that only authorized users can access and modify specific environments or applications.

-   **Authentication and Authorization**: Integrated with SAP Identity Authentication Services (IAS) to provide secure login and access management.

**Summary of Key Benefits:**

-   **Faster Development**: Pre-configured Dev Spaces, wizards, and templates accelerate development and reduce setup times.

-   **Customization and Flexibility**: Developers can customize the IDE with plugins and Dev Spaces to fit their specific requirements.

-   **Cloud-Native**: As a cloud-native solution, BAS supports the development of scalable, flexible applications that can leverage SAP's cloud ecosystem.

-   **Unified Platform**: It provides a single environment for building, testing, and deploying various SAP applications, from Fiori apps to full-stack cloud applications.

In essence, SAP Business Application Studio is designed to make it easier and more efficient to develop enterprise applications, particularly in the SAP ecosystem. It provides both the power and flexibility to meet the needs of modern SAP development workflows.

For Cloud SAP related developments, use SAP Business Application Studio (BAS) on SAP Business Technology Platform (BTP). This tool has a similar UI as the standalone VS Code, extensions can be added here too.

For local Python related developments, use Microsoft Visual Studio (VS Code).

In essence, **VSCode** is more flexible and general-purpose, appealing to a wide variety of developers across different industries, while **SAP
Business Application Studio** is specifically optimized for SAP ecosystem development with deep integration into **SAP BTP**.

  ---------------------------------------------------------------------------
**Summary of Key Points:**
  | **Feature** | **SAP Business Application Studio (BAS)** | **Visual Studio Code (VSCode)** |
| ------------- |:-------------:| -----:|
| **Primary Use Case** |	SAP-specific development (Fiori, CAP, SAP HANA, etc.)	| General-purpose development |
| **Cloud-Native**	| Yes (fully web-based)	| No (desktop-based, but browser version exists) |
| **Pre-configured Dev Spaces**	| Yes (for specific SAP scenarios) | No (requires manual setup) |
| **Integration with SAP BTP** | Yes (native integration) | No (needs extensions) |
| **Extensions** | VSCode-compatible | Extensive marketplace |
| **Wizards/Project Templates**	| SAP-specific templates (e.g., Fiori, CAP)	| General templates available |
| **Pricing** | Subscription/usage-based via SAP BTP |	Free and open-source |
| **Security and Compliance** | Enterprise-grade, SAP-compliant | Depends on implementation |
| **Offline Development** | No | Yes |

 ---------------------------------------------------------------------------
 
# Development options on SAP BTP
  | **Criteria** | **SAP AI Core/AI Launchpad** | **Cloud Foundry with Python Scripts** |
| ------------- |:-------------:| -----:|
| **Primary Purpose** |	AI/ML lifecycle management (training, deploying, monitoring)	| General-purpose application deployment platform |
| **AI/ML Workflow Support**	| Native support for model orchestration, training, inference	| No native AI/ML support (requires manual setup) |
| **Infrastructure**	| Managed infrastructure tailored for AI/ML | Custom infrastructure management for AI tasks |
| **Scalability** | Auto-scaling for AI models | Custom scaling configuration |
| **Deployment Process** | Deploy models and pipelines easily through AI Core | Deploy standalone applications (manual setup for AI services) |
| **Monitoring**	| AI-specific tools for model performance and monitoring	| General app monitoring (no AI-specific tools) |
| **Automation** | Orchestration of pipelines, training, and retraining |	No built-in orchestration (manual or external tools needed) |
| **Versioning** | Built-in model versioning and tracking | No built-in versioning for AI/ML (requires external tooling) |
| **Cost** | Optimized for AI workloads | Potentially higher for AI apps due to infrastructure requirements |
| **Deployment Targets** | AI models, training pipelines, inference services | General applications, APIs, or microservices |
| **Customization** | Focused on AI/ML workflows | Highly customizable but requires manual setup for AI workloads |

**Summary:**
- SAP AI Core/AI Launchpad is ideal for companies looking to streamline and automate AI/ML workflows with managed infrastructure and native AI capabilities.
- Cloud Foundry with Python Scripts provides more flexibility for deploying various types of applications, but requires more manual effort for managing AI/ML workflows and infrastructure.

# Setup configuration for BTP regards SAP AI Core/Launchpad

## Subaccount creation

- In SAP Business Technology Platform (BTP), a subaccount is a logical entity that helps you organize and manage resources within your overall SAP BTP account. It is part of the hierarchical structure in SAP BTP, which includes global accounts, subaccounts, and spaces (for Cloud Foundry environments).
- AGCO ABAP Team specific Subaccount: AGCO Corporation-\>**SAP Dev Sandbox**
* Parameters:
  Subdomain: sap-dev-sandbox-bagm1u0e
  Tenant ID: ca52da14-3909-46b2-b577-0ed527128474
  Subaccount ID: ca52da14-3909-46b2-b577-0ed527128474
  Provider: Amazon Web Services (AWS)
  Region: ![alt text][eu_logo] Europe (Frankfurt)
  Environment: Multi-Environment

![alt text][pic001]

## **Cloud Foundry Environment creation**
The **Cloud Foundry Environment** in SAP Business Technology Platform (BTP) provides a flexible, open platform-as-a-service (PaaS) environment for developing, deploying, and managing cloud-native applications. It supports multiple programming languages and frameworks, allowing developers to build and run applications in various languages like **Java, Node.js, Python**, etc.

So, the **Cloud Foundry Environment** in SAP BTP is designed to provide developers with the tools to build, deploy, and scale cloud applications in an open, flexible, and integrated platform.

**Parameters:**
API Endpoint: <https://api.cf.eu10-004.hana.ondemand.com> (Region!)
Org Name: **Agco Corporation_sap-dev-sandbox-bagm1u0e**
Org ID: **9d70fd51-2577-434d-93a6-6b4387dfd05d**

![alt text][pic002]

Our deployed test AI applications are stored in **"dev"** space with the corresponding Service Instances.

Once, the instance for the corresponding application is started, then the Deployed Applications can be run, by clicking it on their names:

![alt text][pic003]

## Entitlements

In **SAP Business Technology Platform (BTP)**, **entitlements** are the **permissions** or **service quotas** allocated to subaccounts that define what services and resources (like databases, APIs, or storage) can be used.

They control which services are available and how many of them can be used by different subaccounts, ensuring efficient resource allocation and governance.

For SAP AI enablement, AI Core and AI Launchpad entitlements must be activated by the admin of SAP BTP Platform.

**SAP AI Core** is the **backend engine** that powers the technical operations of AI models.

**SAP AI Launchpad** is the **frontend** or **dashboard** that allows users to easily manage and monitor those AI models.

![alt text][pic004]

Once, the Entitlements are avaible, the corresponding services (SAP AI Core - aicore_extended) can be created under our Subaccount:

![alt text][pic005]

**Set-Up SAP AI Core with Boosters:** in SAP BTP it simplifies and accelerates the implementation of specific business scenarios by providing pre-configured, best-practice solutions, enabling
organizations to innovate faster.

Requires a Global (company) Account: **SAP AI Core** as a pre-requisite must be enabled before!

![alt text][pic006]

![alt text][pic007]

**Authentication:** **Service Keys** are crucial for authenticating and authorizing access to services within SAP BTP, ensuring secure and efficient integration between applications and SAP resources:

![alt text][pic008]

![alt text][pic009]

It's advisable to store the Service Keys!

**Set-Up SAP AI Launchpad with Boosters:**
Works with the same analogy as described for SAP AI Core (Subaccount, Org., Space must be selected).

No Instance but Subscription is created:

![alt text][pic010]

**Set-Up Tools** (SAP AI Launchpad, Postman, SAP AI Core SDK, AI API client SDK)

Based on the **SAP AI Core Keys** SAP AI Launchpad can be set up with adding a new AI API Connection:

![alt text][pic011]

![alt text][pic012]

Issues/Tickets to SAP:

![alt text][pic013]

![alt text][pic014]

# Tools/CLIs (technical)
## Docker
* Personal access token

Build Docker image (pl.: hello-aicore-code)
```
docker build -t
\<DOCKER_REGISTRY\>/\<YOUR_DOCKER_USERNAME\>/\<IMAGE_NAME\>:\<TAG_NAME\>\
(e.g.: docker build -t docker.io/gaborhalmai/house-price:01)
```
Authentication
```
docker login docker.io
```
Upload Docker Image to the cloud
```
docker push
\<DOCKER_REGISTRY\>/\<YOUR_DOCKER_USERNAME\>/\<IMAGE_NAME\>:\<TAG_NAME\>\
(e.g.: docker push docker.io/gaborhalmai/house-price:01)
```
Connect your local system to a Docker account
```
docker login docker.io
```
## Github
(!) Unique executable ID: running number must be defined for every application!
```
(pl.: \"first-pipeline-0001\")
```
Personal access token

Connect SAP AI Solutions with GIT:
![alt text][pic015]

## Microsoft VS Code

User System Installer instead of the general one:\
[https://code.visualstudio.com/Download#](https://code.visualstudio.com/Download)

## AWS S3 Bucket

Install or update to the latest version of the AWS CLI

<https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html>

Configure settings for your CWS CLI
```
aws configure
```
Parameters:
\"access_key_id\": \"AKIAQNIFRLAASUYKC57D\",
\"secret_access_key\": \"pFH8LB5I34MrkFZUCBeKm7XCOwKpXPNej9/6EH3D\",
\"region\": \"eu-central-1\",
Default output format: JSON
S3 Endpoint:

V1
```
s3://AKIAQNIFRLAASUYKC57D:pFH8LB5I34MrkFZUCBeKm7XCOwKpXPNej9%2F6EH3D@s3-eu-central-1.amazonaws.com/hcp-dd8e89bb-6dc9-4bdc-aab3-a6530f5177ec
```
V2
```
s3-eu-central-1.amazonaws.com/hcp-dd8e89bb-6dc9-4bdc-aab3-a6530f5177ec

{

\"AWS_ACCESS_KEY_ID\": \"AKIAQNIFRLAASUYKC57D\",

\"AWS_SECRET_ACCESS_KEY\": \"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\"

}
```
## Upload the datasets to AWS S3 Storage
```
\"bucket\": \"hcp-dd8e89bb-6dc9-4bdc-aab3-a6530f5177ec\",
```
```
aws s3 cp train.csv
s3://hcp-dd8e89bb-6dc9-4bdc-aab3-a6530f5177ec/example-dataset/house-price-toy/data/jan/train.csv

Folder: jan

Folder: feb
```
## BTP Cloud Foundry

## Cloud Foundry API Endpoint

>   (!) Accounts might be stucked when using Trial (Free) and Global account parallely, always log-out

> Using direct („S") user names shall be considered to distiungish between BTP accounts.

-   CLI command (cf7, cf8, etc.) may vary, depending on the recent version

Global (AGCO) endpoint: <https://api.cf.eu10.hana.ondemand.com>
Trial (Free) endpoint: <https://api.cf.us10-001.hana.ondemand.com>

## Login to BTP Cloud Foundry (w/ or w/o SSO) (Global/company account)
```
cf7 login -a \<URL\>
```
```
cf7 login -a API-URL -u USERNAME -p PASSWORD -o ORG -s SPACE
```
```
cf7 login -sso -a API-URL -u USERNAME -p PASSWORD -o ORG -s SPACE
```
```
cf7 login -sso -a <https://api.cf.eu10.hana.ondemand.com>
(pl.: cf7 login -sso -a https://api.cf.eu20-001.hana.ondemand.com -u
\"\<USERNAME\>\" -p \"\<PASSWORD\>\" target -o \"Agco
Corporation_ac-dev-oxsxx3zs_ext\" -s DEV)
```
## Login to BTP Cloud Foundry (w/ or w/o SSO) (Trial (Free) account)
```
cf7 login -sso -a <https://api.cf.us10-001.hana.ondemand.com>
```
## Get BTP Cloud Foundry Marketplace Services
```
cf7 marketplace Service: objectstore Plans: standard Description: Objectstore service
```
```
cf7 marketplace -e objectstore
```
## Create an instance of the service
```
cf7 create-service objectstore s3-standard object_store_dev
```
## List the service instance
```
cf7 services
```
## Create a service key
```
cf7 create-service-key object_store_dev os_dev_key
```
## Get service key credentials
```
cf7 service-key object_store_dev os_dev_key
```
## Bind your application with the service key
Create a user provided service
```
cf7 create-user-provided-service
```
## Bind your application
```
cf7 bind-service \<applicationName\> ups_dev
```
# BTP Object Store Service
**Object Store Secret**
```
Role: \"aicore_admin_objectstoresecret_editor\"
```
SAP AI Launchpad -\> Workspaces
<https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/add-object-store-secret>

**Configure Object Store to use Amazon Simple Storage Service**
<https://help.sap.com/docs/object-store/object-store-service-on-sap-btp/configure-object-store-to-use-amazon-simple-storage-service>

**Register a Dataset**
Role: artifact_register role (Role collection:
ailaunchpad_mloperations_editor)

<https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/register-dataset>

**Roles and Authorizations (artifact_register)**
<https://help.sap.com/docs/ai-launchpad/sap-ai-launchpad/roles-and-authorizations>

**Install or update to the latest version of the AWS CLI**
<https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html>

**Set the AWS CLI output format**
<https://docs.aws.amazon.com/cli/v1/userguide/cli-usage-output-format.html#:~:text=JSON%20is%20the%20default%20output%20format%20of%20the%20AWS%20CLI>.

# SAP AI Core

**California Housing dataset (sample dataset)**
<https://scikit-learn.org/stable/datasets/real_world.html#california-housing-dataset>

<https://github.com/scikit-learn/scikit-learn/blob/872124551/sklearn/datasets/_california_housing.py#L54>

<https://raw.githubusercontent.com/sap-tutorials/Tutorials/master/tutorials/ai-core-data/train.csv>

<https://github.com/sap-tutorials/Tutorials/tree/master/tutorials/ai-core-data>

**AI Core/BTP/HANA/CAP, etc. SAP tutorials**
<https://github.com/sap-tutorials/Tutorials/tree/master/tutorials>

# How to Integrate a Python App with SAP Business Application Studio for an SAP S/4HANA Cloud System
#### Good to know
- **Bash scripting**
  - Bash scripting refers to **writing scripts** using the **Bash (Bourne Again Shell)** language. Bash is a command-line interpreter found in Unix-based systems like Linux and macOS. A **Bash script** is essentially a sequence of commands written in a text file, which the Bash shell executes sequentially.
  - Common Uses of Bash Scripting:
    - Automating repetitive tasks
    - Managing system administration tasks (e.g., backups, updates)
    - Performing file manipulations
    - Simplifying complex command sequences
    - Creating custom command-line utilities
- Cheat sheet
  https://devhints.io/bash
  https://github.com/RehanSaeed/Bash-Cheat-Sheet
- **```pip```**
  - ```pip``` is the package installer for Python. It is used to install, manage, and uninstall Python packages (modules or libraries) from the Python Package Index (PyPI), which is the official repository of third-party Python packages.
  - ```pip``` simplifies the process of managing Python packages, making it easy to integrate libraries and tools into Python projects.
- **NPM**
  - **NPM (Node Package Manager)** is a package manager specifically for JavaScript and Node.js environments, not Python. It serves a similar purpose to pip in Python but is designed for managing **JavaScript** packages, libraries, and tools.
- **touch**
  - The **touch** command is not specific to Python but is commonly used in Unix-based operating systems like Linux or macOS from the terminal. It is not a built-in Python function but rather a shell command used for file manipulation.
- A **YAML** (YAML Ain't Markup Language) or YML file is a human-readable data format used for configuration files. In Python, YAML files are commonly used to define configurations, settings, or structured data for applications or frameworks, especially in web development, data science, and machine learning projects.
- **Flask** is a lightweight and easy-to-use web framework for Python. It is designed to help developers build web applications quickly and with minimal code. Flask is considered a micro-framework, meaning it provides the basic tools to get started with web development but leaves the choice of additional libraries and tools (like databases or authentication) up to the developer.
#### 1. Create a Dev Space:
- In BAS, create a new **Dev Space** and choose a suitable development environment such as **Full-Stack Cloud Application** or **Basic** with extension **Python Tools**.
- **Activate the Dev Space** after it’s created.
![alt text][pic035]

#### 2. Install Python Tools in BAS (if you forgot to select it earlier)
- Open the Dev Space:
After the Dev Space is active, open it to begin working.
- Install Python:
Open the **Terminal** and install Python tools and dependencies if needed by running:
```
sudo apt update
sudo apt install python3 python3-pip
```

- Install Additional Python Libraries:
  - Install any necessary Python libraries (such as **requests** for making HTTP requests to SAP S/4HANA Cloud APIs) by running:
```
pip3 install requests
```

#### 3. Create a new Project
- MTA app is unnecessary, we only use a basic app
![alt text][pic036]

#### 4. Create Python Environment
- From command palette, set default python runtime. The default runtime is "/home/user/.asdf-inst/shims/python".
See "Runtime Version Management" for further detail.
  - This step might be unnecessary, since I choose the same path when creating a python virtual environment.

![alt text][pic037]

#### 5. Create Virtual Environment for Python
- Select ```".venv"```

![alt text][pic038]

#### 6. Create Virtual Environment for Python
- Select ```"~/.asdf-inst/shims/python3"```

![alt text][pic039]

#### 7. Implement simple python rest api app based on Flask REST API
- Use pip to install the package (you can access terminal with command ```>```)

![alt text][pic041]

#### 8. app.py
- file names are case sensitive!
 ```python
 from flask import Flask
import os

app = Flask(__name__)
# Port number is required to fetch from env variable
# http://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html#PORT

cf_port = os.getenv("PORT")

# Only get method by default
@app.route('/')
def hello():
    return 'Hello World'

if __name__ == '__main__':
	if cf_port is None:
		app.run(host='0.0.0.0', port=5000, debug=True)
	else:
		app.run(host='0.0.0.0', port=int(cf_port), debug=True)
```

#### 9. Test the app
- In terminal, run "python app.py" and click on "Open in a New Tab" button

![alt text][pic042]
![alt text][pic043]

"Hello World" is displayed in a new tab on port 5000:
![alt text][pic044]

#### 10. Deployment of the application to BTP Cloud Foundry
- You can run it also as part of an automated process using a **scheduler** or as a part of a **CI/CD** pipeline
#### 10.1 manifest.yml
```yml
---
applications:
- memory: 128MB 
  disk_quota: 512MB
  random-route: true
----
```

#### 10.2 Procfile
- Target python application
```
   web: python app.py
```

#### 10.3 runtime.txt
- Target python version
```
   python-3.11.X
```

#### 10.4 requirements.txt
- Necessary python packages
```
   Flask
```

#### 10.5 .cfignore
- ```".venv"``` is unnecessary to run cf app, so list up the directory
```
   .venv
```
#### 10.6 Deploy
- Deploy the app to cloud foundry
- AGCO login target is eu10-004
```
   cf login -a https://api.cf.eu10-004.hana.ondemand.com/
   cf push <app name>
```
![alt text][pic045]
![alt text][pic046]
![alt text][pic047]
![alt text][pic048]
![alt text][pic049]
![alt text][pic050]
![alt text][pic051]

#### 10.6 Delete the app
- If you don't need the app on cloud foundry, just delete the app
```
cf delete <app name>
```

#### 11. Debugging and Logs
- Use Logs for Debugging:
  - Utilize ```print()``` statements or use the **debugger** in SAP Business Application Studio to troubleshoot any connection or data retrieval issues.
#### 8. Deploy or Further Develop
- Further Development:
You can extend your Python app to perform other actions, such as creating sales orders, updating data, or processing business events.
- Deployment:
If necessary, you can deploy the Python app to SAP BTP, or run it as part of an automated process using a scheduler or as a part of a CI/CD pipeline.
#### Summary:
- Set up the SAP Business Application Studio environment.
- Install Python and required libraries.
- Set up SAP S/4HANA Cloud API access.
- Write Python code to interact with the SAP S/4HANA Cloud API.
- Test and debug your Python application.
- Use OAuth or Basic Authentication for secure API access.

# Upload Microsoft Word documents to SAP AI Core

## Install Python
https://www.python.org/downloads

## Installing Packages
<https://packaging.python.org/en/latest/tutorials/installing-packages/>

## PyPI · The Python Package Index
<https://pypi.org/>

## ai-core-sdk · PyPI
<https://pypi.org/project/ai-core-sdk/>

![alt text][pic016]

## Local Documentation
```
[file:///\[drive\]:/\[python](file:///[drive]:/%5bpython)
directory\]/Doc/html/installing/index.html
```
## Installing Python extension
![alt text][pic017]

## Microsoft Visual Studio Code (VS Code)
<https://code.visualstudio.com/docs/languages/python>
<https://code.visualstudio.com/docs/python/python-quick-start>
<https://www.w3schools.com/python/default.asp>

**Overview:**
- VS Code is a lightweight, open-source code editor developed by Microsoft, and it has gained widespread popularity among developers.

**Pros:**
- Highly customizable with a rich ecosystem of extensions, including Python-specific extensions.
- Integrated terminal and debugging capabilities.
- Excellent support for various programming languages and tools.
- Frequent updates and active community support.

**Cons:**
- Requires installation of extensions for full Python support (e.g., Python extension by Microsoft).

**How to Get Started:**
1. Download and install VS Code from the [official website](https://code.visualstudio.com/).

2. Install the Python extension from the VS Code marketplace.

# Issues
- Object Store Secret -- Endpoint name is wrong
![alt text][pic018]

**Error code:** „Error (exit code 1): artifact housedataset failed to
load: failed to create new S3 client: Endpoint url cannot have fully
qualified path"

<https://github.com/cloudlena/s3manager/issues/7>

<https://community.sap.com/t5/technology-q-a/error-could-not-connect-to-the-endpoint-url-while-deploying-tutorial-model/qaq-p/12802972>

**Solution:**
Old endpoint:
s3-eu-central-1.amazonaws.com/hcp-dd8e89bb-6dc9-4bdc-aab3-a6530f5177ec

New endpoint: s3-eu-central-1.amazonaws.com

- Missing Role **artifact_register** (artifact.register in the help)
    from Role Collection **ailaunchpad_mloperations_editor**.

![alt text][pic019]

![alt text][pic020]

![alt text][pic021]

### SAP AI Launchpad - Creating Dataset

![alt text][pic022]

![alt text][pic023]

- BTP introduction ()
- Captions/labels to images
- Consistency
  
### Copyrights
Redistribution of this document in any form is prohibited. The material can only be used by students who participated in the education.
© Halmai Gábor, 2024
Last update: 24.09.2024
