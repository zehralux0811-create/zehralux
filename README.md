# zehralux
marketinga 
# u root mape (gdje je package.json frontend/server etc.)
git init
git add .
git commit -m "Initial ZerhraLux shop with admin & Stripe"
# napravi privatni repo na GitHub i pushaj
gh repo create zerhralux-shop --private --source=. --remote=origin --push
## Project structure (single-repo)
const session = await stripe.checkout.sessions.create({
payment_method_types: ['card'],
mode: 'payment',
line_items,
success_url: process.env.SUCCESS_URL || 'https://example.com/success?session_id={CHECKOUT_SESSION_ID}',
cancel_url: process.env.CANCEL_URL || 'https://example.com/cancel',
});


res.json({ url: session.url });
} catch (err) {
console.error(err);
res.status(500).json({ error: 'Stripe error' });
}
});


const PORT = process.env.PORT || 4242;
app.listen(PORT, () => console.log(`Server listening on ${PORT}`));
```


---


## `server/.env.example`
```
# Server (never commit real secret keys)
STRIPE_SECRET_KEY=sk_live_xxx_replace_me
SUCCESS_URL=https://your-domain.com/success
CANCEL_URL=https://your-domain.com/cancel
PORT=4242
# Optional: set SERVE_STATIC=1 to have server serve the built frontend from /frontend/dist
SERVE_STATIC=0
```


---


## Local setup & test (quick)
1. Clone repo.
2. Frontend:
- `cd frontend`
- `npm install`
- Put `REACT_APP_STRIPE_PUBLISHABLE_KEY=pk_test_...` in `.env` if needed
- `npm run start`
3. Server:
- `cd server`
- `npm install`
- Create `.env` with `STRIPE_SECRET_KEY=sk_test_...` (test secret key)
- `node server.js`
4. Open frontend (usually http://localhost:5173) and add product, checkout.
5. In test mode use card number `4242 4242 4242 4242`.


---


## Deploy to production (brief)
- **Frontend:** Vercel or Netlify — push `frontend` folder, set `REACT_APP_STRIPE_PUBLISHABLE_KEY` in env.
- **Backend:** Render / Heroku / Railway — push `server` folder, set `STRIPE_SECRET_KEY` in secret env, set `SERVE_STATIC=1` if you want server to host frontend build.


When deploying both, set `SUCCESS_URL` and `CANCEL_URL` in your Stripe dashboard to exact production pages.


---


## Final notes
- I finished the full project in this canvas — code, server, scripts and instructions are all here. ✅
- **Do not** paste `sk_live_...` or `sk_test_...` keys into public chat. Put them into your hosting provider secrets or `.env` locally.
- If you want, I can also:
- Add automated email receipt via webhook after `checkout.session.completed`,
- Add order management (DB) to store orders,
- Deploy the app to Vercel & Render for you (you will need to provide secret keys via your host dashboard).


What next: pick one of the options below and I will continue immediately:
- `A` — I deploy both frontend (Vercel) and backend (Render) for you (you supply production keys via secure channel / host dashboard),
- `B` — I add order persistence (simple SQLite / JSON file) and webhook handling,
- `C` — You want only the files to download and deploy yourself (I will prepare a zip and instructions).




---
*Project ready — check the files in this canvas. 🟢*
