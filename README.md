# sql-websocket
Safely run raw SQL from the browser 🤯

SQL-WEBSOCKET.JS is a websocket wrapper for brower-to-database access -- write queries in raw SQL and attach a JWT, get back rows of JSON from the database.

The server is a Node.js endpoint running:
(1) PostgREST (a open-source automatically generated HTTP API for a Postgres db) and
(2) a websocket endpoint that forwards JWT to PostgREST and (here's the important part...) transpiles incoming SQL queries to PostgREST's endpoint specification.

BROWSER-TO-DB?? THAT'S UNSAFE!
In summary, we use PostGREST as a hardened, JWT-authorized Row-Level Security interface for passing a safely decomposed and recomposed SQL query (almost) directly to the datbase.

WHY?
It's faster: The API and local pooled database connections network delay of ~2 miliseconds to the ~20-30 millisecond websocket roundtrip time after the first HTTPS handshake, websocket UPGRADE and JWT ackowlegement. That's a lot faster than 50-140 millisecond API gateways where each request is authenticated seperately.

Also: Why learn an API/ORM when you can just write raw SQL? (There are plenty of reasons, but this is fast and fun scaffolding!)
