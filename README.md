# 🧠 Claude Skills Collection

A personal collection of custom Claude skills — purpose-built, production-grade, and opinionated.  
Each skill turns Claude into a specialist: sharper reasoning, structured outputs, and no hand-waving.

> **What's a Claude Skill?**  
> Skills are instruction files that extend Claude with a specific persona, methodology, and output format. Install them once, trigger them naturally in conversation.

---

## 📦 Skills in This Repo

| Skill | Trigger | What It Does |
|-------|---------|-------------|
| [`system-designer`](#-system-designer) | "design a system for...", "architect a...", "how would you build..." | Senior staff-engineer AI for full system and product design |
| [`techyg`](#-techyg) | "best X under budget", "compare A vs B", "should I buy..." | Data-driven tech & appliance recommendation engine |

---

## 🏗️ system-designer

**Role:** Senior AI and system design engineer  
**Best for:** Backend systems, ML pipelines, SaaS platforms, APIs, cloud infrastructure, DevOps/MLOps architecture

### What It Does

Transforms Claude into a staff-level architect who designs real-world systems from scratch — not just high-level diagrams, but actionable, production-oriented blueprints. Every response covers the full lifecycle: from requirements gathering to rollout and rollback.

No hand-waving. No vague "it depends." Every major decision comes with a *why*.

### Trigger Phrases

```
"Design a system for X"
"Architect a Y"
"How would you build Z"
"What's the best architecture for..."
"How would Netflix / Stripe / Google solve..."
"Help me design the backend for..."
"System design for a [product]"
```

### Output Structure

Every design follows a consistent 16-section format:

```
 1. Problem Summary
 2. Assumptions and Clarifying Questions
 3. Requirements (Functional + Non-Functional)
 4. Proposed Architecture
 5. Core Components
 6. Data Model / Storage Strategy
 7. API Design or Interface Design
 8. AI Strategy and Workflow
 9. Security and Compliance
10. Cost Optimization
11. Scalability and Reliability
12. Observability and Operations
13. Build / Test / Deploy Plan
14. Risks, Tradeoffs, and Alternatives
15. Human-in-the-Loop Design (when applicable)
16. Final Recommendation
```

### Example Prompts

```
"Design a real-time fraud detection system for a fintech app"
"Architect a multi-tenant SaaS platform with role-based access control"
"How would you build an ML feature store for a recommendation engine?"
"Design the backend for a real-time collaborative document editor like Notion"
"What's the best architecture for a high-throughput event ingestion pipeline?"
```

### Key Behaviors

- **Asks sharp questions** when the problem is too vague — never more than necessary
- **Labels assumptions clearly** when proceeding without full context
- **Always includes tradeoffs** between chosen approach and realistic alternatives
- **Escalates to human-in-the-loop design** automatically for healthcare, payments, identity, legal, and moderation systems
- **Includes a Quick Reference table** for 10 common system archetypes (ML systems, SaaS, payments, auth, search, etc.)

### Design Standards Applied

| Area | What the Skill Enforces |
|------|------------------------|
| Security | Auth, encryption, least-privilege, audit logs — first class, not afterthought |
| Cost | Rough cost model + top cost drivers + optimization levers in every design |
| Reliability | Retries, circuit breakers, graceful degradation, SLA targets |
| AI/ML | Model choices, inference strategy, feedback loop, fallback design |
| Compliance | GDPR, SOC 2, HIPAA, PCI flagged where relevant |

---

## 🛒 techyg

**Role:** Sharp, no-BS tech advisor  
**Best for:** Buying decisions for phones, laptops, ACs, TVs, audio gear, gaming hardware, home appliances — any consumer electronics

### What It Does

Runs a full 5-phase analysis before recommending anything. No list dumps, no "here are some options." It scores products with a weighted model, catches benchmark inflation vs real-world performance, flags risks, and gives you a ranked top 5 with honest caveats.

Think of it as asking a friend who happens to benchmark gadgets for fun and has no incentive to upsell you.

### Trigger Phrases

```
"Best phone under ₹30,000"
"Should I buy X or Y?"
"Compare A vs B for gaming"
"Suggest a good laptop for video editing under ₹80K"
"Is [product] worth it?"
"/techyg [product or category]"
```

Also triggers when you **upload a product image, spec sheet, or comparison screenshot** and ask for advice.

### How It Works — The 5 Phases

```
Phase 1 → Parse your query (category, budget, use cases, constraints, ecosystem)
Phase 2 → Research (live web search — never relies on stale training data)
Phase 3 → Weighted Scoring Model (8 dimensions, weights adjusted to your priorities)
Phase 4 → Analysis layers (Use case matrix, benchmark vs reality, value, risk, sentiment)
Phase 5 → Dashboard-style output with ranked cards + comparison table + verdict
```

### Weighted Scoring Model

| Dimension | Default Weight |
|-----------|---------------|
| Performance (benchmarks) | 20% |
| Real-world Performance | 15% |
| Value for Money | 20% |
| Build Quality & Longevity | 10% |
| Ecosystem Fit | 10% |
| User Reviews (aggregated) | 10% |
| After-Sales / Support | 5% |
| Risk Score (inverted) | 10% |

Weights shift automatically based on your stated priorities (e.g., gaming → +10% real-world performance).

### Output Format (per recommendation)

Each of the top 5 picks renders as a structured card:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 #1  Product Name                Score: 87/100
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 💰 Price  |  📊 Score Breakdown  |  ✅ Use Case Fit
 💡 Why This?  |  ⚠️ Reality Check  |  🔴/🟡/🟢 Risk
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Followed by a head-to-head comparison table and a blunt final verdict.

### Example Prompts

```
"Best smartphone under ₹35K for camera and battery"
"Compare Samsung Galaxy S25 vs iPhone 16 for a heavy user"
"I need a laptop for ML/AI work, budget ₹1.2L"
"Best 1.5-ton inverter AC under ₹40K — I'm in Bangalore"
"[uploads product image] Is this a good deal?"
```

### Covered Categories

📱 Smartphones · 💻 Laptops · ❄️ Air Conditioners · 📺 TVs · 🎧 Audio (headphones, earbuds, speakers) · 📷 Cameras · 🎮 Gaming Gear · 🏠 Home Appliances (washing machines, refrigerators, etc.)

---

## 🚀 Installation

### Option 1 — Install from `.skill` file (Claude.ai)

1. Download the `.skill` file for the skill you want
2. In Claude.ai, go to **Settings → Skills**
3. Click **Install from file** and select the `.skill` file
4. Start a new conversation and use the trigger phrases above

### Option 2 — Manual install

1. Clone this repo
2. Copy the skill folder (e.g., `system-designer/`) to your Claude skills directory
3. Reload Claude

---

## 🗂️ Repo Structure

```
claude-skills/
├── README.md
├── system-designer/
│   └── SKILL.md          # Full 16-section system design methodology
├── techyg/
│   └── SKILL.md          # 5-phase tech recommendation engine
└── (more skills coming...)
```

---

## 🧭 When to Use Which

| Situation | Use |
|-----------|-----|
| You're architecting a new product or backend system | `system-designer` |
| You're doing a system design interview | `system-designer` |
| You want to compare cloud architecture approaches | `system-designer` |
| You're shopping for a phone, laptop, or appliance | `techyg` |
| You want an honest second opinion on a purchase | `techyg` |
| Someone sent you a product recommendation and you're skeptical | `techyg` |

---

## 🛠️ Built With

- [Claude Skills](https://docs.claude.ai) — Anthropic's skill system for extending Claude
- [skill-creator](https://github.com/anthropics/claude-skills) — The meta-skill used to build and iterate these skills

---

## 📝 License

MIT — use freely, adapt as needed, attribution appreciated but not required.

---

> Built by someone learning DevOps, MLOps, and AI one system at a time. 🚀
