# Agentic Finance Flippening

**Place your bet.** When will agent-to-agent payment volume exceed human-to-human?

Live prediction market / wisdom-of-the-crowd dashboard built in reply to [Brian Armstrong's question](https://x.com/brian_armstrong/status/2084019794257301679).

## Features

- Big, mobile-first "Place Your Bet" flow
- Year selector (2027–2040) with pills + slider
- Optional X handle + one-line reason
- Live crowd stats: median, % early/late, distribution chart
- Recent bets feed
- Share-to-X button after betting
- Works immediately with localStorage
- Optional Supabase backend for shared global leaderboard (see comments in `index.html`)

## Deploy

### Vercel (recommended)

1. Import this repo at [vercel.com/new](https://vercel.com/new)
2. Deploy

Or drag the folder onto Vercel Drop.

### Local

Just open `index.html` in a browser.

## Optional: Shared Database (Supabase)

To make predictions global instead of per-browser:

1. Create a free project at [supabase.com](https://supabase.com)
2. Run this in the SQL editor:

```sql
CREATE TABLE predictions (
  id uuid DEFAULT gen_random_uuid() PRIMARY KEY,
  year int NOT NULL,
  handle text,
  reason text,
  created_at timestamptz DEFAULT now()
);

ALTER TABLE predictions ENABLE ROW LEVEL SECURITY;
CREATE POLICY "Allow public insert" ON predictions FOR INSERT WITH CHECK (true);
CREATE POLICY "Allow public read" ON predictions FOR SELECT USING (true);
```

3. Copy Project URL + anon public key into the two constants at the top of `index.html`
4. Redeploy

## Base Case View

Collapsed research section inside the app:
- Transaction *count* flip ≈ 2029–2030
- Value volume flip base case ≈ **2032**
