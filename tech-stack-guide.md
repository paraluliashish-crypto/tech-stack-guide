# Tech Stack Guide

Reference for architecture decisions by project type. Use this when selecting technologies to ensure consistency and best-in-class choices.

---

## Web Application (SaaS / Dashboard)

| Layer | Recommended | Alternative |
|---|---|---|
| Framework | Next.js 14 (App Router) | Remix |
| Language | TypeScript | — |
| Styling | Tailwind CSS + shadcn/ui | Styled Components |
| State | Zustand + React Query | Redux Toolkit |
| API | tRPC or REST (Express/Fastify) | GraphQL |
| Auth | NextAuth.js / Clerk | Auth0 |
| Database | PostgreSQL (Neon/Supabase) | PlanetScale (MySQL) |
| ORM | Prisma | Drizzle |
| Cache | Redis (Upstash) | Vercel KV |
| Deploy | Vercel | Railway / Fly.io |
| Monitoring | Sentry + Vercel Analytics | Datadog |

---

## Mobile Application

| Layer | Recommended | Alternative |
|---|---|---|
| Framework | React Native (Expo) | Flutter |
| Navigation | Expo Router | React Navigation |
| State | Zustand | Redux Toolkit |
| API Client | React Query + Axios | SWR |
| Auth | Clerk / Supabase Auth | Firebase Auth |
| Storage | MMKV | AsyncStorage |
| Push Notifications | Expo Notifications | Firebase FCM |
| Deploy | EAS Build | Fastlane |

---

## API / Microservices

| Layer | Recommended | Alternative |
|---|---|---|
| Runtime | Node.js (Fastify) | Python (FastAPI) |
| Language | TypeScript | Python |
| API Style | REST + OpenAPI spec | GraphQL |
| Auth | JWT + refresh tokens | OAuth 2.0 |
| Validation | Zod | Joi / Yup |
| Queue | BullMQ (Redis) | RabbitMQ |
| Container | Docker + Kubernetes | Docker Compose (small scale) |
| Service Mesh | Istio (large scale) | — |
| Deploy | AWS ECS / GKE | Railway |

---

## AI-Powered Application

| Layer | Recommended | Alternative |
|---|---|---|
| LLM Provider | Anthropic Claude API | OpenAI |
| Orchestration | LangChain.js / LlamaIndex | Custom agents |
| Vector DB | Pinecone | Weaviate / pgvector |
| Embeddings | OpenAI text-embedding-3 | Cohere |
| Streaming | Vercel AI SDK | Custom SSE |
| File Parsing | LlamaParse | Unstructured.io |
| Memory | Redis | Zep |
| Eval | LangSmith | Promptfoo |

---

## Real-Time Application (Chat / Collab / Gaming)

| Layer | Recommended | Alternative |
|---|---|---|
| Protocol | WebSockets (Socket.io) | Server-Sent Events |
| Backend | Node.js + Fastify | Go (for extreme scale) |
| Real-time DB | Supabase Realtime | Firebase Firestore |
| Presence | Redis Pub/Sub | Ably |
| CRDT (collab) | Yjs | Automerge |
| Deploy | Fly.io (global edge) | Railway |

---

## Data Pipeline / Analytics

| Layer | Recommended | Alternative |
|---|---|---|
| Ingestion | Kafka | AWS Kinesis |
| Processing | Apache Spark / dbt | Pandas (small scale) |
| Warehouse | BigQuery | Snowflake |
| Orchestration | Airflow | Prefect |
| BI | Metabase | Grafana |
| ML Platform | MLflow | Weights & Biases |

---

## Selection Principles

1. **Default to managed services** — reduce ops burden unless scale demands otherwise
2. **TypeScript everywhere** — eliminates entire classes of bugs at the boundary
3. **Postgres first** — handles 90% of use cases; only deviate with clear reason
4. **Vercel/Railway for speed** — own infra only when cost or compliance demands it
5. **Observability from day 1** — Sentry + structured logging before launch, not after
6. **Auth is not a weekend project** — use Clerk/NextAuth unless you have a security team
