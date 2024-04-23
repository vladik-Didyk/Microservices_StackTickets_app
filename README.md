# Stack Tickets Project

<div align="center">
  <code><img width="100" src="https://user-images.githubusercontent.com/25181517/183890598-19a0ac2d-e88a-4005-a8df-1ee36782fde1.png" alt="TypeScript" title="TypeScript"/></code>
  <code><img width="100" src="https://user-images.githubusercontent.com/25181517/183859966-a3462d8d-1bc7-4880-b353-e2cbed900ed6.png" alt="Express" title="Express"/></code>
	<code><img width="100" src="https://github.com/marwin1991/profile-technology-icons/assets/136815194/5f8c622c-c217-4649-b0a9-7e0ee24bd704" alt="Next.js" title="Next.js"/></code>
  <code><img width="100" src="https://user-images.githubusercontent.com/25181517/183898054-b3d693d4-dafb-4808-a509-bab54cf5de34.png" alt="Bootstrap" title="Bootstrap"/></code>
	<code><img width="100" src="https://user-images.githubusercontent.com/25181517/187955005-f4ca6f1a-e727-497b-b81b-93fb9726268e.png" alt="Jest" title="Jest"/></code>
	<code><img width="100" src="https://user-images.githubusercontent.com/25181517/182884894-d3fa6ee0-f2b4-4960-9961-64740f533f2a.png" alt="redis" title="redis"/></code>
	<code><img width="100" src="https://user-images.githubusercontent.com/25181517/182884177-d48a8579-2cd0-447a-b9a6-ffc7cb02560e.png" alt="mongoDB" title="mongoDB"/></code>
  <code><img width="100" src="https://user-images.githubusercontent.com/25181517/117207330-263ba280-adf4-11eb-9b97-0ac5b40bc3be.png" alt="Docker" title="Docker"/></code>
	<code><img width="100" src="https://user-images.githubusercontent.com/25181517/182534006-037f08b5-8e7b-4e5f-96b6-5d2a5558fa85.png" alt="Kubernetes" title="Kubernetes"/></code>
<code><img width="120" src="https://user-images.githubusercontent.com/25181517/183868728-b2e11072-00a5-47e2-8a4e-4ebbb2b8c554.png" alt="CI/CD" title="CI/CD"/></code>
<img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*ebK75QCh_mXBRx6VQjcebg.png" alt="Logo" data-canonical-src="https://nats.io/img/logo.png" style="width: 30%">
</div>

## Status

![tests-auth](https://github.com/sRayen/Ticketing-Microservices/workflows/tests-auth/badge.svg)
![tests-payments](https://github.com/sRayen/Ticketing-Microservices/workflows/tests-payments/badge.svg)

### 📑 Table of Contents
- [📝 Introduction](#introduction)
- [📘 Description](#description)
- [🧩 Features](#features)
- [🚀 Environment Variables](#environment-varaibles)
- [🏗️ Architecture](#architecture)
- [⏹️ Development](#development)
- [🎬 Screenshots](#screenshots)

## 📘 Introduction <a name="introduction"></a>

 **This web application enables users to book and buy tickets for various events.**

## 📘 Description <a name="description"></a>


The Ticketing App Microservices Backend, built on Node.js and Typescript, **operates as a Backend** (with a simple Next.js front-end designed for demonstration and testing) utilizing **microservices architecture** to deliver a scalable and robust user interface. It consists of multiple microservices, each tasked with a distinct function, including:


* ➡️ **Auth**: Manages user authentication and authorization.
* ➡️ **Expiration**: Utilizes the Bull package to assign expiration times for tickets and introduces a 15-minute delay following order placement.
* ➡️ **Common**: A shared npm package that offers event interfaces.
* ➡️ **Order**: Manages the creation and cancellation of orders, and triggers events to inform other services.
* ➡️ **Payment**: Processes payments through Stripe.
* ➡️ **Ticket**: Oversees ticket issuance and updates.
  
⭐ The backend employs **NATS Streaming Server** for service-to-service communication, a light messaging service based on NATS.

🌟 The application’s codebase is organized and maintainable, made possible through the use of **Typescript** which incorporates interfaces, classes, and generators.

🌟 ☸ **Kubernetes** facilitates the deployment of each service along with its database, and also manages the NATS Streaming service setup and ingress configuration.

💥 This backend provides a dependable and effective solution for ticket application requirements, incorporating **Mongoose version numbers** to address **concurrency challenges** among **services**.

## Features 🧩 <a name="features"></a>

This application offers capabilities such as:

* ✔ User registration and login
* ✔ Listing a ticket for sale (seller)
* ✔ Adding a ticket to the cart (buyer) and marking it 'reserved' for 15 min
* ✔ Creating an Order
* ✔ Completing purchase and payment for an order

## Environment Variables 🔑  <a name="environment-varaibles"></a>

 `JWT_KEY` : string, JSON web token secret <string> (Example: JwtKey)

`STRIPE_KEY`: your stripe API key to handle the payment 

## Development	<a name="development"></a>

For managing Docker containers within the Kubernetes cluster and optimizing the development process, the project utilizes Skaffold.

Ensure Docker, Kubernetes, and Skaffold are installed locally to run the app in a development setting.

Before initiating the app, set the environment variables within the Kubernetes cluster using the following commands:

```bash
# kubectl create secret generic stripe-secret --from-literal=STRIPE_KEY=<your_stripe_key>

# kubectl create secret generic jwt-secret --from-literal=JWT_KEY=<your_jwt_key>
```

Be sure to expose the ingress-nginx-controller with:

```bash
# kubectl expose deployment ingress-nginx-contoller --target-port=80 --type=NodePort -n kube-system
```

👉 Start the app with `skaffold dev`.

🔍 [Skaffold ](https://skaffold.dev/) manages the workflow for building, pushing, and deploying your application, allowing you to concentrate on coding.


##  Architecture 🏗️🔨 <a name="architecture"></a>

![architecture](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/702adccc-3fb4-4410-acd1-957d639ef7f4)

##  Screenshots 🎬 <a name="screenshots"></a>

### <ins>Deployments</ins>:
![deployments](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/e8b5fb9e-c042-4a1b-ad27-354cd2e77792)

### <ins>SignUp</ins>:
![SignUp](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/24e87bba-7af6-49da-bcfd-84c78c3cdf25)

### <ins>Tickets</ins>:
![Tickets](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/3b187359-8ad3-4b51-8786-c83745abc58a)

### <ins>Purchase Ticket</ins>:
![Purchase Ticket](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/1ebc80eb-661e-429f-be4b-b4bfaa881f86)

### <ins>Orders</ins>:
![orders](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/a289bd53-fc73-4ea5-b71f-5fe10bb8ae93)

### <ins>Microservices logs</ins>:
![logs](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/3df3fc8e-d2d5-4d58-8ec6-eddb7ff97854)

### <ins>Stripe Payments</ins>:
![stripe_payments](https://github.com/SRayen/Ticketing-Microservices/assets/13922445/533b9e7c-ebd5-4c09-94f7-72f650dd04b5)

## Dedication

📌 My heartfelt thanks to Stephen Grider, the instructor of the Microservices with Node JS and React course on Udemy.
📌 Stephen's profound knowledge and steady mentorship were instrumental in realizing this project.
📌 This project stands as a testament to my growth as a Software Engineer and the priceless insights gained through this remarkable educational experience.
📌 I am excited to present this project to you, celebrating Stephen Grider's excellent teaching and mentorship.




