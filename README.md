# SaaS Subscription & Metered Usage Telemetry Platform (Netlify & Vercel Ready)

A full-stack, production-grade **SaaS Billing and Telemetry Management Platform** designed to run on serverless environments. This application features user authentication, metered API rate limits, interactive usage telemetry dashboards, invoice generation, role-based administrative panels, and a dual **Stripe Live Test Mode + Simulated Sandbox Engine** allowing full checkout testing without API configuration.

This project is fully configured for deployment on **Netlify** using Next.js serverless functions and a cloud **PostgreSQL** database (like Neon or Supabase).

---

## 🚀 Resume Bullet Points (Copy & Paste)
* **Full-Stack SaaS Architecture**: Architected a Next.js App Router application integrating Prisma ORM and PostgreSQL to handle subscription states, user authentication, and metered API usage tracking.
* **Serverless SQL Integration**: Integrated PostgreSQL database pools into Netlify Serverless Functions via Prisma Client, ensuring stable connection reuse and zero socket exhaustion on high-traffic routing.
* **Stripe Payment & Webhook Engineering**: Implemented real Stripe Checkout and Customer Portal flows alongside a custom-built payment simulator to handle subscription creation, billing cycles, and automated webhook database syncs.
* **Custom SVG Data Telemetry**: Coded zero-dependency, responsive SVG line charts and circular progress gauges in React to map request rates and bandwidth consumption, optimizing page weights and avoiding charting library conflicts.
* **Role-Based Admin Console**: Designed an administrative control panel allowing real-time monitoring of platform MRR, user status management, and manual override controls for user API quotas and role privileges.

---

## 🛠️ Tech Stack & Architecture

| Layer | Technology | Details |
|---|---|---|
| **Frontend Framework** | **Next.js 16 (App Router)** | Runs on standard Node.js serverless runtimes. |
| **Database ORM** | **Prisma 6** | Schema modeling, relationship queries, and native PostgreSQL connectors. |
| **Database Host** | **PostgreSQL (Neon or Supabase)** | Serverless cloud SQL database with instant autoscaling. |
| **Authentication** | **JWT & Jose** | Edge-runtime compatible JSON Web Token parsing, secure HTTP-only cookies. |
| **Styling** | **Vanilla CSS** | Modern custom theme variables, dark mode by default, glassmorphism, flexbox/grid. |
| **Billing Integration** | **Stripe SDK & Webhooks** | Subscription checkout sessions, customer billing portal, webhook parser. |

---

## 💻 Getting Started (Local Run)

### 1. Clone & Install Dependencies
```bash
git clone <your-github-repo-link>
cd saas-subscription-manager
npm install
```

### 2. Configure Database & Migrations
1. Create a free serverless database on **[Neon.tech](https://neon.tech)** (takes 10 seconds).
2. Create a `.env` file in the root of your project:
   ```env
   DATABASE_URL="postgresql://username:password@your-neon-subdomain.neon.tech/neondb?sslmode=require"
   JWT_SECRET="generate-any-long-secure-random-string-here"
   ```
3. Run migrations to initialize the tables on the cloud database:
   ```bash
   npx prisma db push
   ```

### 3. Seed Mock Accounts
Populate the cloud database with pre-configured developer accounts and historical invoices:
```bash
npm run seed
```

### 4. Fire up the Dev Server
```bash
npm run dev
```
Open **[http://localhost:3000](http://localhost:3000)** in your browser.

---

## 🔑 Pre-seeded Demo Accounts
Skip sign-up and log in immediately using these credentials:

* **Administrator Panel Demo**:
  * **Email**: `admin@saas.com`
  * **Password**: `adminpassword`
  * *Features*: Access to global MRR tracker, adjust rate limits, toggle user roles.

* **Developer Portal Demo**:
  * **Email**: `user@saas.com`
  * **Password**: `userpassword`
  * *Features*: Telemetry charts, metered gauge, billing invoice list, checkout options.

---

## ⚡ Deployment to Netlify (Get Your Live Link)
Get your live production link to paste on your Resume/LinkedIn for free:

1. Push your project to a new repository on **GitHub**.
2. Log in to your **[Netlify Dashboard](https://app.netlify.com/)** and click **Import from Git**.
3. Select your GitHub repository.
4. Set the **Build settings**:
   - **Build Command**: `npm run build`
   - **Publish Directory**: `.next`
5. Click **Add Environment Variables** and add:
   - `DATABASE_URL`: *(Your Neon PostgreSQL Connection URL)*
   - `JWT_SECRET`: *(Your random secret string)*
6. Click **Deploy Site**. Netlify will compile the code, host the website, and provide you a live URL like `https://your-site-name.netlify.app`!
