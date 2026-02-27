# Server

Simple Express + Mongoose server for products.

Quick start

1. Install dependencies:

```powershell
cd C:\Repos\server
npm install
```

2. Copy the example env and set your MongoDB URI (Atlas or local):

```powershell
copy .env.example .env
# Edit .env and set MONGO_URI to your connection string
```

3. Start the server:

```powershell
npm start
```

Health check

- GET http://localhost:5000/health should return `{ "status": "ok" }`.

In-memory DB

- If `MONGO_URI` is not set in `.env`, the server will automatically start an in-memory MongoDB (via `mongodb-memory-server`) so the app works without installing MongoDB or using Atlas. This is intended for local development and tests only.

DB-status health endpoint

- `GET /health/db` returns JSON with the mongoose connection state, whether the DB is connected, and which backend is in use (`in-memory`, `local`, or `atlas`). Example:

```
GET /health/db

{
	"status": "ok",
	"db": { "connected": true, "state": "connected", "uri": "in-memory" }
}
```

Security note

- Do not commit `.env` to version control. `.env` is listed in `.gitignore` in this project. Keep real Atlas credentials out of the repository.

Notes

- Do not commit real credentials. Use `.env` for sensitive values.
