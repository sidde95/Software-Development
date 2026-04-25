
# Introduction to Modern System Design

## Understanding System Design

**System Design** is the discipline of planning how a software product will work end-to-end under real-world conditions.It's where we decide:
- What building blocks the system will use (clients, services, databases, caches, querues, CDNs).
- How those block interact (APIs, communication patterns data flow).
- How the system behaves at scale (traffic spikes, failures, slow networks, regional outages).
- Which trade-offs do we accept (cost, vs reliability, latency vs consistency, simplicity vs flexibity)?

---

## Why System Design matters

Every successful technology company eventually faces the challenge of scale. Without a deliberate architectureal strategy, an application that workds for 1,000 users will likely fail the load of 1,000,000 (a million) users.

System, Design directly address these challenges by focusing on building systems that are not only functional but also resilient and efficient at a massive scale.

Thoughful design anticipates and solves complex problems before they impact service quality. This means focusing on key system qualities:
- **Scalability**: The ability to handle massive user loads by distributing request so no single server is overwhelmed.
- **Availibility**: ensuring the system remains operational and accessible to users even if some of its components crach.
- **Low Latency**: Responding to user requests quickly, regardless of their location, to create a fast and responsive experience.
- **Consistency**: Making sure data is reliable and accuracte across the entire distributed system.

---

## Common Architectural Pattern

![alt text](image-1.png)

*A load balancer distributes incoming trafic, multiple servers handle requests in parallel, a cache accelerates data access, and a replicated database ensures that information remains both durable and quickly retrievable. Each component represents a deliberate choice within the system design process.*

---

## How is System Design related with coding?

Think of it like building a house. System Design is the blueprint; it defines the shape of the house, how rooms connect, where plummbing and wiring must be installed and how the structure remains safe under stress. Coding is the construction work: writing the concrete instrcutions that make part real and executable.

| **Focus Area** | **Code-Centric Approach** | **System design Approach** |
|---|---|---|
| **Scope** | Algorithms, classes, functions and modules | Services, APIs, data flows, infrastructure, etc. |
| **Typical Tasks** | Writing clean code, debugging, and running different tests, such as unti testing | Defining service boundaries, choosing databases, and designing caching strategies, etc. |
| **Failure Modes** | Null pointer exceptions, logic errors, infinite loops, etc. | Service outages, cascading failures, data corruption, latency spikes, etc. |
| **Success Metrics** | Code correctness, performance of a single function etc. | System uptime, scalability, reliability and low latency, etc.|

## System Design across software roles

System Design is not the exclusive domain of a single "architect" role. It is a collaborative process that involves engineers and stake holders across different functions. Each role brings a unique perspective and set of responsibilities.

- **Back-end Engineers**: They design the APIs, data models, and business logic for specific services, focusing on performance and security within the larger system.
- **Front-end Engineers**: Ensure the client-facing side of the system is efficient, reliable and scalable. Their choices around rendering (e.g., client-side vs server-side), caching and API suage not only affect user-perceived latency but also shape backend design and overall system performance.
- **System architects**: These individuals focus on the end-to-end architecture, defing the overall structure and selecting core tehnologies.
- **Site Reliability Engineers (SREs)**: SREs bring an operational perspective and advocate for features like monitoring , automated failover and disaster recovery planning.
- **Product Engineers**: Their input on user experience constraints is crucial for making trade-offs, such as choosing between strong and eventual data consistency for a feature.


![alt text](image-2.png)

---

# System Design vs Software Architecture

*In software engineering, System Design and Software Arhitecture are two essential blueprints. While connected, they address different layers of planning. For a beginner, confusing them is like mistaking a city map for the floor plan fo a single building. Both are necessary, bu they server very different purpose.*

**System Design** is the process of defing the components, modules interfaces and data for asystem to meet its requirements. It offfers a high level view that includes hardware, software, network infraftructure, and the services that connect them. Think of it as deciding you need a web server, a database, and a caching layer, and determing how they will interact with each other.

**Software Architecture**, on the other hand, is a subset of System Design. If focuses on the internal strcutre of the software itself. It involves organizing code into modules, defing how they interact and choosing architectural patterns. Suppose System Design decides that you need a database. In that case, Software Architecure determines how the code will interact with it, which data models to use and how to structure the code for maintainibility and performance.

![alt text](image-3.png)

## What is Software Architecture?

The primary goal os Software Architecture is to manage an application's internal complexity. It acheives this by specifying how ocde is organized into modules, how those modules intact, and what principles guide their construction.

To acheive its gial of managing complexity and enabling future developmment, Software Architecture involves several key responsibilities:
- **Structuring Code**: Organizing the application into layers (e.g., presentation, business logic, data access) or modules with clear responsibilities.
- **Managing dependecies**: Ensuing components interact through well-defines interfaces with minimal coupling.
- **Choosing architectural patterns**: Applying proven solutions for common problems. For example, many web apps use the *Model View Controller (MVC)* pattern to keepo their code organized.
- **Enforcing standards**: Establishing conventions, tools, and platforms for consistency across the codebase.

A good architecture imporves maintainibility, enagances testability, and lays the groundwork for perfromance and scalability, through acheiving scale in production is ultimately a System Design conern. Software Architecture alone cannot gurantee a system's success at scale.

Applications must run wihtin a larger ecosystem of services, databases and infrastucture. This is where System Design comes in.

## Where System Design and architecture instersect and diverge

When building a photo-sharing app, here's how the concerns are divided:

| **Software Architecture** | **System Design** |
|---|---|
|How is the application code structure?\n(e.g., choose layered architecture: API layer, business logic, data access)| Where will photos be stored?\n(e.g., cloud object storage like Amazon S3 with life cycle rules)|
|Hwo are users authenticated?\n(e.g., `userservice` module with clear interfaces)| How will the sytem scale to over 10 million users?\n(e.g.,, multiple app servers + load balancer)|
|What language and framework should be used?\n(e.g., Python with Django, Node.js with express)|How can we deliver photos globally with low latency?\n(e.g., CDN to cache images near users)|
|How do modules interact internally?\n(e.g., dependency management, clear interfaces)| What databases suit different data types?\n(e.g., SQL for users, NoSQL for metadata)|

*For instance, choosing a microservice architecture, which involves breaking an application into many small, independent services, has significant implications for system design, It requires a service discovery mechanism, an API gateway, and a strategy for inter-service communication.*

*Conversely, a System dsign requirement for extremenly low latency might push the Software Architecture towards a mmore performant, through more complex, internal design.*



