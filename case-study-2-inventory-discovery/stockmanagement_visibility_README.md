# Case Study 2: Inventory & Stock Visibility — Product Discovery

## Overview
A product discovery exercise focused on a core operational problem: **stock visibility across manufacturing labs.** Rather than jumping to a solution, this case study shows the structured discovery process used to understand the problem space, the stakeholders, and the workflow before scoping any feature.

## The Problem Statement
> "If I understand correctly, today there is no stock visibility in labs. I want to understand more."

This was the opening framing for discovery — deliberately stated as a hypothesis to validate with stakeholders, not an assumption to build from.

## 1. Business Process Flow — Understanding the Landscape
Before designing a solution, I mapped the labs and process types involved to understand where inventory decisions actually happen:

- **Lab types identified:** Sampling Lab, Creation Lab, Production Lab, Quality Lab, Warehouse/Distribution Center, Regional Labs, Manufacturing Plant
- **Key discovery questions:**
  - Do all labs follow the same process?
  - Are there regional differences?
  - Does every lab maintain inventory independently?
  - What does "inventory" mean in each context (raw materials, finished flavor, packaging, chemicals, samples/trial batches)?
  - What units do labs track in (e.g. liters, bottles, or country/region-specific units)?

This mapping revealed that **each lab follows a different process** and **maintains inventory independently**, with **no shared, updated system of record** — a foundational finding that shaped everything downstream.

![Discovery Thread Map](images/discovery_thread_map.png)

## 2. Clarifying Questions — Structured by Theme
Rather than asking scattered questions, I organized discovery around a repeatable framework:

**Business Goal**
- Why is this important now?

**Users & Workflow**
- Who needs stock visibility, and who are the primary users of this information?
- Could you walk me through how inventory is managed today?
- What usually triggers someone to check stock? Is it proactive or reactive — manual or automated?
- Is it real-time, updated daily/weekly, or manually updated?
- Are there different processes across lab technicians vs. warehouse staff?

**Systems & Data**
- Which systems are used today (Excel, ERP/SAP, manual log books, phone calls, email)?
- Where does the data come from, and how confident are users in its accuracy?

**Pain Points & Friction**
- Which part of the process is most time-consuming or frustrating?
- Where do delays or mistakes happen most often?
- Can you share an example where limited stock visibility caused a real issue (e.g. low stock, expiring stock, dead stock)?

**Decisions & Workarounds**
- What decisions depend on having accurate stock visibility?
- What existing workarounds do people use when the system doesn't give them what they need?

**Constraints**
- Are there operational or regulatory constraints to keep in mind (batch traceability, expiry dates, hazardous materials, compliance/audit requirements)?

**Future State & Success**
- If we could solve this perfectly, what would the ideal experience look like? ("I want to know instantly whether Lab A or Lab B has enough stock, or I want alerts before we run out.")
- How would we know this feature succeeded six months after launch — fewer stockouts, reduced manual calls, faster planning, less excess inventory, better fulfillment rates?
- **If we could solve only one inventory problem first, which would create the biggest impact?** — This question was used specifically to identify the Minimum Viable Product (MVP).

## 3. Product Vision Discovery Framework
To make this discovery process repeatable across future initiatives, I distilled it into a 4-stage framework that moves from context to a measurable future state:

![Product Vision Discovery Framework](images/discovery_framework_flow.png)

The framework is designed to be walked left to right in a stakeholder conversation: establish **context** before diagnosing the **current state**, surface **problems** only once the current state is understood (to avoid jumping to solutions), and close on a **future state** with a way to measure success — which is what makes the final "if we could solve only one problem first" question so effective, since by that point the real priorities are already visible.

## Why This Approach
Rather than starting with "what feature should we build," this discovery process deliberately front-loads three things:
1. **Process mapping** — understanding that labs operate independently before assuming a single unified solution would even fit
2. **Structured, themed questioning** — so nothing critical (compliance, regional variance, existing workarounds) gets missed
3. **A single MVP-forcing question** — "if we could solve only one problem first" — to avoid scope creep before a solution is even defined

---

## From Discovery to Roadmap
*The sections below extend the discovery findings above into a prioritized product plan — the natural next step after this research.*

## 4. Stakeholder Pain Point Matrix
Mapped pain points by stakeholder group to make sure the solution served everyone who touches inventory, not just the loudest voice:

![Stakeholder Pain Point Matrix](images/cs2_pain_point_matrix.png)

## 5. Prioritization Framework (RICE-style)
Scored candidate features using the same RICE model as Case Study 1, so priorities are ranked by evidence rather than opinion:

![RICE Prioritization](images/cs2_rice_prioritization.png)

Low-stock & expiry alerts scored highest (6.0) — the discovery interviews consistently linked this directly to real business pain (stockouts, expired batches). Automated data sync scored lowest (1.7) on its own merits, but it's a **dependency**: the dashboard and alerts can't be reliable without a real data feed, so it's sequenced first despite the lower score — the same "foundation before features" logic used in Case Study 1.

## 6. Roadmap
![Roadmap Timeline](images/cs2_roadmap_timeline.png)

| Phase | Focus | RICE Score |
|---|---|---|
| Phase 1 — Foundation | Automated data sync from lab systems | 1.7 |
| Phase 2 — MVP | Centralized, real-time stock dashboard | 5.0 |
| Phase 3 — Proactive | Low-stock and expiry alerts | 6.0 |
| Backlog | Cross-lab search & reporting | 4.0 |

## 7. Options Considered
| Option | Description | Trade-off |
|---|---|---|
| Option 1 | Lightweight dashboard fed by manual exports from each lab's existing spreadsheets | Fast to build, but not real-time and still depends on manual uploads |
| Option 2 | Full ERP rollout (e.g. SAP) standardized across every lab | Solves the problem long-term, but high cost, long timeline, disruptive to labs already mid-process |
| Option 3 | **Selected** — Integration layer that syncs data from each lab's existing system (Excel, ERP, manual logs) into one real-time dashboard | Doesn't require ripping out lab systems already in use; faster time-to-value while still solving the core visibility gap |

**Decision: Option 3** — meets labs where they are today instead of forcing a disruptive standardization project before any value is delivered.

## 8. User Stories
- **As a lab technician**, I want to see real-time stock levels across all labs, so I can check availability without calling around.
- **As a production planner**, I want low-stock alerts, so I can reorder materials before a stockout happens.
- **As a regional/warehouse manager**, I want expiry tracking, so I can redistribute or use stock before it's wasted.
- **As a quality/compliance officer**, I want centralized batch traceability, so audits don't require chasing down scattered logs.

## Outcome / Projected Impact
*(Framed as projected impact from a discovery/concept exercise — flag clearly if this was applied to a live project.)*

| Metric | Before | Target After Phase 3 | Why |
|---|---|---|---|
| Stock visibility | No shared visibility; manual calls/emails between labs | Real-time cross-lab dashboard | Directly addresses the core discovery finding |
| Stockout incidents | Reactive, discovered after the fact | Reduced via proactive alerts | Alerts trigger before stock runs out |
| Expired/dead stock | Discovered too late to use or redistribute | Tracked and flagged before expiry | Enables redistribution instead of waste |
| Manual stock-check effort | High — phone calls, emails, spreadsheets | Self-serve dashboard | Removes the manual workaround entirely |
| Planning cycle time | Slowed by manual data gathering | Faster, data-driven decisions | Centralized reporting replaces ad hoc checks |

## Key Takeaways
- Discovery started with a hypothesis stated explicitly ("today there is no stock visibility"), not an assumption baked silently into requirements
- Mapped process variation across labs *before* proposing a solution, avoiding a one-size-fits-all design for a genuinely fragmented process
- Built a reusable discovery framework (4-stage flow across 15 guiding questions) that can be applied to future product areas, not just this one
- Used a single forcing question to identify the MVP rather than trying to scope everything at once
- Prioritized with RICE, but overrode pure score ranking to sequence a lower-scoring foundational dependency (data sync) first — mirroring the same "infrastructure before features" logic applied in Case Study 1
- Chose an integration-layer approach over a full ERP rollout to deliver value faster without disrupting labs' existing workflows
