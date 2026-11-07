# eksamensrettleiar-pakkar

Signed subject packs for Eksamensrettleiar's open period on app.sporlaus.no. Not a product
repo — just the files the app fetches during the open month:

- `periode.json` — the signed period window (period ID, start date, end date, signature).
- `pakkar.json` — the subject list the app shows (subject code, name, version, filename, size,
  sha256 for the app's own download-integrity check).
- `*.fagpakke` — the six signed subject packs themselves.

Each pack carries its own Ed25519 signature over its content and period ID; `periode.json`
carries a separate signature over the period's dates. Both are verified client-side before a
pack is used — see `app/periode.js` in the Eksamensrettleiar app repo.

This repo is served publicly only for the open period. After it ends, the app's
`PAKKE_BASIS_URL` moves back behind Cloudflare Access with a one-line change, and this repo's
contents stop being needed.

Maintained by sporlaus.no. Questions: Roger Kløvtveit.
