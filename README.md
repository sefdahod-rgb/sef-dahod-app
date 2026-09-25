# SEF Dahod - Rainbow Public School App

Live Domain: www.sefdahod.in (GoDaddy)
Hosting: Vercel
Database: Supabase
Payment: Razorpay Live Key: rzp_live_SeDR91zuvNa9fG
Students: 79 Loaded

## Deploy Steps
1. Upload this folder to GitHub: sef-dahod-app
2. Go to Vercel.com -> Add New Project -> Import GitHub repo
3. Deploy
4. In Vercel Settings -> Domains -> Add sefdahod.in and app.sefdahod.in
5. Update GoDaddy DNS: A record @ -> 76.76.21.21 and CNAME www -> cname.vercel-dns.com

## Razorpay Fix for api.razorpay.com refused to connect
Add these domains in Razorpay Dashboard -> Settings -> Website & App:
- sefdahod.in
- www.sefdahod.in
- your-vercel-url.vercel.app

The error happens only in preview (container://). On real https domain it works.

## Supabase Setup
Create tables:
```sql
create table students (admission_no text primary key, student_name text, class text, father_name text, mobile text, annual_fees int, rte text);
create table payments (id uuid primary key default gen_random_uuid(), admission_no text, quarter text, amount int, razorpay_payment_id text, status text, created_at timestamp default now());
```

Import students_data.json into Supabase.

## Login
Admin: admin / admin
Parent: Admission No / Admission No (e.g., 52 / 52)
