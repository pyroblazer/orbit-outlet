# <img src="https://github.com/Pyroblazer/orbit-outlet/blob/main/ecommerce-store/public/logo-black.png" width=250px height=auto alt="Logo">

OrbitOutlet combines real-time store management with an elegant and efficient e-commerce platform.

## Features

- **Admin Dashboard:** Extensive functionalities for modifying size, color, main billboard, and category options
- **Product Management:** Create products with various variants
- **Order Management:** Manage orders for future employees
- **Client Store Site:** Includes product page, quick view, filtered categories, search bar, cart, and summary checkout

## Tech Stack

**Client:** React, Next.js, TailwindCSS, shadcn/ui

**Server:** Prisma

**Other:** Stripe, Clerk

## Installation

To install this project, you need to run both instances (Admin Dashboard and Store) on separate servers. Download the entire repository and follow the instructions below:

### 1. Admin Dashboard

1. Navigate to the admin directory:

   ```bash
   cd ecommerce-admin
   npm install
   ```

2. Configure your **.env** file with your own keys from Clerk, PlanetScale, Cloudinary, and Stripe:

   ```env
   # Clerk
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
   CLERK_SECRET_KEY=
   NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
   NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
   NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
   NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/

   # Database URL (Aiven or any other provider)
   DATABASE_URL=

   # Cloudinary
   NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=

   # Stripe
   STRIPE_API_SECRET_KEY=
   FRONTEND_STORE_URL=
   STRIPE_WEBHOOK_SECRET=
   ```

3. Generate Prisma client and push database schema:

   ```bash
   npx prisma generate
   npx prisma db push
   npm run dev
   ```

4. The server should run on `localhost:3000`.

### 2. Store Configuration

1. Navigate to the store directory:

   ```bash
   cd ecommerce-store
   npm install
   ```

2. Create a store and copy the `NEXT_PUBLIC_API_URL` from the Settings page. Then create an **.env** file in the `ecommerce-store` folder with the appropriate data:

   ```env
   NEXT_PUBLIC_API_URL=https://localhost:3000/api/[your_store]
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

Both the server and the store should now be properly connected.

_Note: If you are using Stripe webhook with a local environment, use a local client for accurate results._
