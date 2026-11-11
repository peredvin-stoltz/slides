# GQM across the course books

How five architecture books' concepts map onto Goal–Question–Metric (GQM). Used in the GQM workshop: slide 13 of the "GQM Workshop Slides" deck and the two-page "GQM Across the Books" handout.

GQM: Basili & Weiss (1984); Basili, Caldiera & Rombach (1994). Define top-down, interpret bottom-up.

## Mapping table

| GQM | Building Evolutionary Architectures | The Art of Systems Architecting | Continuous Architecture in Practice | Computer Networks | Software Architecture in Practice |
|---|---|---|---|---|---|
| Goal | Architectural characteristic | Client purpose, value judgement | Quality attribute focus | QoS target, at most | Business goal, quality attribute |
| Question | Holistic fitness function | Heuristics; purpose turned into criteria | Which decision is pending? | Where is delay or loss caused? | Scenario stimulus and environment; tactics |
| Metric | Atomic fitness function | Performance model, certification criteria | Operational and feedback-loop data | Throughput, RTT, jitter, loss | Response measure |
| Select | Which checks to automate | Satisficing | Delay until data justifies it | Exact metric definitions | Utility tree ranking |
| Feedback | Emergent fitness functions, pipeline | Progressive refinement | Feedback loops | Network monitoring | Evaluation, ATAM risks |

## Per book

### Building Evolutionary Architectures (Ford, Parsons, Kua & Sadalage)
Concepts: architectural characteristics, fitness functions (atomic/holistic, triggered/continuous, static/dynamic, automated/manual, intentional/emergent), incremental and guided change, architectural quantum, connascence, deployment pipelines, automated governance.
- A fitness function is a metric with a threshold, run automatically. GQM supplies the goal that says why it exists.
- Atomic fitness functions are single metrics; holistic ones answer questions that combine several.
- Automating a check moves a metric from "collect" to "have".
- Emergent fitness functions are GQM's feedback step.

### The Art of Systems Architecting (Maier & Rechtin)
Concepts: client, purpose orientation, value judgements, ill-structured problems, heuristics, views and models, progressive refinement, certification, satisficing.
- Purpose orientation is the goal; the client is the goal's viewpoint.
- Turning a qualitative purpose into testable criteria is the Goal → Question → Metric chain.
- Certification needs agreed measures; fuzzy goals make subjective metrics legitimate. Satisficing is the selection step.

### Continuous Architecture in Practice (Erder, Pureur & Woods)
Concepts: six principles (quality attributes first, delay decisions, architect for change, architect for build/test/deploy/operate, …), decision logs, QA scenarios and utility trees, technical debt, feedback loops, fitness functions.
- "Focus on quality attributes" is the workshop's starting point: one NFR as the goal.
- Delaying a decision works only if you know which data would settle it; the cost column says if waiting is affordable.
- Feedback loops are GQM's bottom-up half. Log which question each decision depends on.

### Computer Networks (Tanenbaum, Feamster & Wetherall)
Concepts: bandwidth vs throughput, delay components, RTT, jitter, packet loss, bandwidth-delay product, QoS, congestion and flow control, protocol layers, network management (SNMP).
- Supplies the metric level: exact definitions, units, tools.
- QoS parameters are ready-made metrics; delay breakdown and layers structure "where is it caused?" questions.
- Network metrics are often proxies for the user-facing goal.

### Software Architecture in Practice (Bass, Clements & Kazman), closest fit
Concepts: quality attributes, QA scenarios (source, stimulus, artifact, environment, response, response measure), tactics, utility tree, ATAM (sensitivity and trade-off points, risks), QAW, business goals.
- Business goal + quality attribute = the GQM goal; the scenario's environment is the goal's context.
- The response measure is a ready-made metric; a good scenario is nearly a question–metric pair.
- Utility tree importance ≈ question value (its difficulty is about building, not the cost of data). Tactics give cause questions.

## Workshop task
Each group translates one picked question–metric pair into its book's terms: a QA scenario (SAiP / Continuous Architecture), a fitness function (Evolutionary Architectures), a precise metric definition (Computer Networks), or a certification criterion (Art of Systems Architecting).

Example, one metric three ways:
- GQM: "How fast is checkout at peak?" → p95 latency per endpoint.
- QA scenario: 500 users/s place orders during peak; the order API responds; p95 under 800 ms.
- Fitness function: nightly load test fails the build if p95 exceeds 800 ms.
