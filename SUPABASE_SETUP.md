# Supabase Backend Integration Guide

## Overview
This guide will help you set up Supabase as the backend for authentication, product management, cart, orders, and blog posts for your Sithaphal website.

## Steps

### 1. Create a Supabase Project
- Go to [https://supabase.com/](https://supabase.com/) and sign up.
- Create a new project and note your API keys and project URL.

### 2. Set Up Database Tables
- **Users**: For authentication (Supabase Auth handles this).
- **Products**: id, name, description, price, image_url, stock
- **Orders**: id, user_id, items (JSON), total, status, created_at
- **Cart**: id, user_id, items (JSON)
- **Blog**: id, title, content, author_id, created_at

You can use Supabase's Table Editor or SQL to create these tables.

### 3. Enable Authentication
- Go to Authentication > Settings in Supabase dashboard.
- Enable email/password sign-in.

### 4. Connect Frontend to Supabase
- Install Supabase JS client:
  ```html
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js"></script>
  ```
- Initialize in your JS:
  ```js
  const supabase = supabase.createClient('https://njljzwkgsijqqgurxgpw.supabase.co', 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im5qbGp6d2tnc2lqcXFndXJ4Z3B3Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTU4ODIzMjEsImV4cCI6MjA3MTQ1ODMyMX0.MrZRLrpvH3oG1yn1TETVlo5Vy1-IIUit7guqgWw0hyM');
  ```

### 5. Implement Features
- **Sign Up / Login**: Use `supabase.auth.signUp` and `supabase.auth.signInWithPassword`.
- **Product Management**: CRUD operations on `products` table.
- **Cart**: Store cart items per user in `cart` table.
- **Orders**: Create order records when users checkout.
- **Blog**: CRUD for blog posts.

### 6. Real-Time Updates
- Use Supabase's real-time subscriptions for product and cart updates.

### 7. Security
- Use Row Level Security (RLS) policies to protect user data.

## Example Usage
```js
// Fetch products
const { data, error } = await supabase.from('products').select('*');
```

## Next Steps
- Add Supabase client code to your `script.js` for authentication and data operations.
- Update UI to reflect real-time changes.

Refer to [Supabase Docs](https://supabase.com/docs) for more details.