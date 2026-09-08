# jfxmbdss

## OpenTwin MBDSS --- Open Maritime Decision Support & Simulation

> Open-source reference architecture and technology compendium for
> MBSE-driven maritime digital twins, distributed simulation,
> interoperable C2 research, AI-assisted decision support, training,
> lifecycle engineering, and multi-domain experimentation.

**jfxmbdss** consolidates an open engineering architecture around
**MBSE, OpenTwin, Modelica/FMI, DEVS, HLA, C2SIM, OARIS, ROS 2/DDS,
multi-agent simulation, AI, synthetic environments, and modular digital
twins**.

The project is intended for research, education, engineering analysis,
training, interoperability experiments, humanitarian/logistics
scenarios, and non-operational simulation. It is not an operational
command system, weapon-control system, targeting system, or substitute
for qualified professional decision-making.

## Vision

``` text
MBSE + Open Standards + Physics Simulation
                  +
       Distributed Simulation
                  +
          OpenTwin Core
                  +
       AI / Data / Analytics
                  =
Open Maritime Digital-Twin Ecosystem
```

The architecture favors stable, technology-neutral interfaces so
vessels, ports, subsea assets, sensors, environmental models, simulation
engines, and analytical services remain replaceable.

## Objectives

-   Apply MBSE to maritime system-of-systems engineering.
-   Provide modular OpenTwin interfaces for maritime digital twins.
-   Separate model semantics from simulation implementations.
-   Support multi-fidelity physical, discrete-event, and multi-agent
    simulation.
-   Support Modelica and FMI/FMU for portable multidomain subsystem
    models.
-   Support HLA-oriented distributed simulation.
-   Support C2SIM/OARIS-oriented interoperability research where
    appropriate.
-   Integrate ROS 2/DDS for modular robotics and autonomy experiments.
-   Enable repeatable scenarios, telemetry recording, replay, and
    validation.
-   Provide AI-assisted analytics with human oversight.
-   Support lifecycle, maintenance, logistics, training, humanitarian,
    and engineering scenarios.
-   Separate required dependencies, optional integrations, and research
    references.

## Reference Architecture

``` text
                      USERS
                        |
       Engineer / Instructor / Analyst
                        |
               Experience Layer
        Dashboards / 3D / XR / GIS
                        |
                AI & Analytics
                        |
                OpenTwin MBDSS
                        |
           Digital Twin Interface Bus
                        |
 +----------+-----------+----------+-----------+
 |          |           |          |           |
Asset     Mission    Telemetry   Health    Environment
Twin       Twin        Twin       Twin        Twin
 +----------+-----------+----------+-----------+
                        |
             Simulation & Interop Bus
                        |
 +--------+--------+--------+--------+---------+
 |        |        |        |        |         |
FMI     HLA      DEVS     ROS 2     DDS    C2SIM/OARIS
 |        |        |        |        |         |
 +--------+--------+--------+--------+---------+
                        |
               MBSE / UAF / Arcadia
```

## OpenTwin Maritime Digital Twin

OpenTwin MBDSS synchronizes physical, simulated, synthetic, and
analytical representations through a common semantic and interface
layer.

``` text
Physical / Simulated Asset
           |
 Sensors / Simulation State
           |
      Adapter Layer
           |
      Semantic Model
           |
   OpenTwin Interface Bus
           |
   State / Health / Events
           |
       Twin Core
           |
 Analytics / Simulation / Visualization
           |
       Human Review
```

A twin may represent a vessel, research submarine, autonomous surface or
underwater research platform, port, dock, logistics node, sensor
network, environmental region, training asset, or fully synthetic
entity.

## Modular Digital Twin Interfaces

### Asset

Identity, type, version, configuration, geometry reference,
capabilities, lifecycle state, model references, and health.

### State

`initialize()`, `configure()`, `update_state()`, `get_state()`,
`checkpoint()`, `restore()`, `reset()`, and `shutdown()`.

### Hydrodynamics

Replaceable CFD, reduced-order, and engineering hydrodynamic models with
geometry, boundary-condition, environment, force, moment, and flow
interfaces.

### Structural

Structural loads, deformation, fatigue-oriented research, and coupling
to other engineering domains.

### Propulsion

Technology-neutral interface for conventional, electric,
hybrid-electric, battery, fuel-cell, and conceptual research propulsion
systems.

### Electrical

Generation, distribution, storage, loads, converters, and energy
management.

### Thermal

Heat loads, cooling, temperatures, thermal networks, and subsystem
thermal state.

### Fluid Systems

Pumps, tanks, piping, hydraulic services, and other fluid-network
abstractions.

### Sensors

Canonical sensor identity, reference frame, timestamp, measurement,
uncertainty, and health metadata.

### Environment

Bathymetry, currents, waves, wind, weather, visibility, temperature,
salinity, coastline, port infrastructure, and synthetic environmental
events.

### Telemetry

``` text
asset.position.*
asset.attitude.*
asset.velocity.*
propulsion.*
energy.*
sensor.*
environment.*
mission.*
health.*
simulation.*
```

### Health

Overall and subsystem health, anomalies, confidence, and recommended
engineering inspection.

### Mission

Objectives, phases, routes, constraints, events, resources, and
evaluation criteria.

### Scenario

``` text
scenario/
├── manifest.yaml
├── assets/
├── environment/
├── missions/
├── events/
├── models/
├── scoring/
└── metadata/
```

### AI Agent

AI services may produce forecasts, anomaly scores, classifications,
simulation hypotheses, recommendations, scenario adaptations, and
training feedback. Outputs remain advisory and auditable.

### FMI / FMU

Portable multidomain subsystem boundary for electrical, propulsion,
thermal, mechanical, fluid, energy, and control models.

### HLA

``` text
Federation
├── Vessel Federate
├── Subsea Federate
├── Port Federate
├── Environment Federate
├── Sensor Federate
├── Mission Federate
├── AI Federate
├── Instructor Federate
├── Recorder Federate
└── Visualization Federate
```

### ROS 2 / DDS

Modular robotics, sensor integration, autonomy research, and
publish/subscribe middleware.

### Visualization

3D clients, dashboards, GIS, notebooks, XR training clients, replay, and
after-action analysis.

### Model Registry

Each model should record ID, version, domain, fidelity, interface
version, provenance, license, validation status, and compatibility.

## MBSE and Architecture Engineering

``` text
Stakeholder Needs
       |
Operational Analysis
       |
System Context
       |
Capabilities
       |
Logical Architecture
       |
Interfaces
       |
Physical Architecture
       |
 CAD / Geometry + Simulation Models
       |
   OpenTwin MBDSS
       |
Verification / Analysis
```

Possible approaches include SysML-oriented workflows, UAF viewpoints,
and Arcadia/Capella. Interfaces should remain independent of a specific
modeling tool whenever practical.

## Modeling and Simulation

jfxmbdss treats simulation as a federation of replaceable models rather
than one monolithic simulator.

Domains can include hydrodynamics, structures, propulsion, electrical,
thermal, fluid networks, sensors, environment, logistics, maintenance,
human operators, multi-agent behavior, ports, and infrastructure.

``` text
Conceptual Model
      |
Reduced-Order Model
      |
Engineering Model
      |
High-Fidelity Simulation
```

Every model should declare assumptions, fidelity, validation status,
provenance, and computational cost.

## Distributed Simulation

``` text
                 Scenario Manager
                        |
          Vessel / Subsea / Port
                        |
                 HLA / Event Bus
                        |
 Environment / Sensors / AI / Recorder / Visualization
```

Federations should explicitly document time management, coordinate
systems, units, ownership, publish/subscribe contracts, event ordering,
deterministic replay, synchronization, and schema compatibility.

## Interoperability

Candidate interfaces and standards include HLA, FMI, DDS, ROS 2,
C2SIM-oriented simulation interoperability, OARIS-oriented maritime
interoperability, UAF-oriented architecture exchange, OGC geospatial
standards, REST/OpenAPI, AsyncAPI, JSON Schema, Protocol Buffers, and
MQTT where appropriate.

External standards should be isolated behind adapters rather than
embedded into the OpenTwin core.

## Multi-Agent Simulation

Multi-agent experiments can represent synthetic vessels, port services,
logistics resources, rescue assets, traffic, environmental actors,
autonomous research platforms, instructors, and simulated operators.
Policies should be reproducible, versioned, and clearly distinguished
from real operational behavior.

## AI and Decision Support

Potential research uses include anomaly detection, predictive
maintenance, resource forecasting, simulation surrogate models, scenario
classification, synthetic-data generation, trajectory analysis, model
calibration, optimization, training assessment, RAG-based engineering
knowledge, and automated reporting.

``` text
Telemetry + Simulation + Scenario + Metadata
                    |
                 Data Layer
                    |
              AI / Analytics
          Detect / Forecast / Recommend
                    |
             Explain / Validate
                    |
               Human Review
```

For consequential real-world decisions, AI output must not be treated as
automatically authoritative.

## Maritime and Subsea Simulation

The architecture can support civilian, research, training, humanitarian,
logistics, environmental, and engineering scenarios involving surface
vessels, research submarines, subsea vehicles, autonomous research
platforms, ports, docks, offshore infrastructure, logistics vessels,
environmental monitoring, disaster-response simulation,
search-and-rescue training, lifecycle analysis, and virtual
commissioning.

Use original or appropriately licensed models and avoid reproducing
restricted or proprietary platform specifications.

## Modelica and FMI

Modelica can represent propulsion, electrical, energy storage, thermal,
mechanical, fluid, actuation, control, and auxiliary systems. FMI/FMU
provides a standardized replaceable boundary between OpenTwin and those
subsystem models.

## Open-Source Technology Compendium

These are candidate integrations or research references, not automatic
runtime dependencies.

  Domain                      Candidate technology / standard   Potential role
  --------------------------- --------------------------------- ------------------------------------
  MBSE                        Capella / Arcadia                 Architecture engineering
  Physical modeling           OpenModelica / Modelica           Multidomain simulation
  Model exchange              FMI / FMU                         Portable subsystem models
  CFD                         OpenFOAM                          Hydrodynamics/environment research
  Multibody                   Project Chrono                    Mechanical simulation
  Structural                  CalculiX                          Structural research
  Robotics                    ROS 2                             Modular robotics integration
  Messaging                   DDS                               Publish/subscribe
  Distributed simulation      HLA-compatible RTI                Simulation federation
  Discrete-event simulation   DEVS ecosystem                    Event-driven modeling
  3D                          Blender                           Geometry and visualization
  Interactive visualization   Godot                             Open 3D client
  GIS                         QGIS                              Geospatial analysis
  Database                    PostgreSQL / PostGIS              Operational and spatial data
  Dashboards                  Grafana                           Monitoring
  Analysis                    Jupyter                           Engineering notebooks
  ML                          PyTorch / TensorFlow              Optional machine learning
  ML lifecycle                MLflow                            Experiment tracking
  XR                          OpenXR                            VR/AR interoperability
  Containers                  Docker                            Reproducible services
  Orchestration               Kubernetes                        Distributed deployment
  APIs                        OpenAPI / AsyncAPI                Interface contracts

Verify current licenses, maintenance, security, and compatibility before
adopting any third-party component.

## User Guide

1.  Define the engineering, training, or simulation objective.
2.  Capture requirements through MBSE.
3.  Define canonical OpenTwin interfaces.
4.  Select asset and environment models.
5.  Select appropriate fidelity.
6.  Configure Modelica/FMU components where required.
7.  Configure distributed simulation when multiple simulators
    participate.
8.  Configure scenario and mission packages.
9.  Execute and record simulation state, events, telemetry, and model
    versions.
10. Apply optional analytics or AI.
11. Visualize results.
12. Conduct human review and after-action analysis.
13. Archive scenario and validation metadata for reproducibility.

## Installation Guide

jfxmbdss is primarily a reference architecture and technology
compendium; it does not require every catalogued technology.

``` bash
git clone https://github.com/robotics-intelligent-systems/jfxmbdss.git
cd jfxmbdss
```

Conceptual environment:

``` text
Architecture       -> Capella / Arcadia
Physical Models    -> OpenModelica
Model Exchange     -> FMI / FMU
CFD                -> OpenFOAM
Distributed Sim    -> HLA-compatible RTI
Robotics/Messaging -> ROS 2 / DDS
AI / Analytics     -> Python ecosystem
Data               -> PostgreSQL / PostGIS
Visualization      -> Grafana / Jupyter / Blender / Godot
Containers         -> Docker
```

Executable modules should document tested OS versions, SDKs, compilers,
package managers, dependency versions, build order, runtime
configuration, tests, sample datasets, and security assumptions.

## Dependencies

### Required Dependencies

Only software strictly required by an executable module.

### Optional Integrations

Replaceable simulation engines, Modelica/FMI runtimes, HLA RTIs, ROS
2/DDS, databases, visualization, XR, and AI frameworks.

### Research References

Standards, papers, frameworks, commercial systems, and historical
technologies used for architectural comparison but not required to
execute jfxmbdss.

Each integration should document name, version, purpose,
required/optional status, interface, license, source, tested platforms,
and validation status.

## Recommended Repository Structure

``` text
jfxmbdss/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── docs/
├── mbse/
├── opentwin/
│   ├── core/
│   ├── state/
│   ├── health/
│   ├── registry/
│   └── adapters/
├── interfaces/
│   ├── asset/
│   ├── hydrodynamics/
│   ├── structural/
│   ├── propulsion/
│   ├── electrical/
│   ├── thermal/
│   ├── fluid/
│   ├── sensors/
│   ├── environment/
│   ├── telemetry/
│   ├── mission/
│   ├── scenario/
│   ├── fmi/
│   ├── hla/
│   ├── ros2/
│   └── visualization/
├── simulation/
│   ├── continuous/
│   ├── discrete-event/
│   ├── multi-agent/
│   └── distributed/
├── modelica/
├── ai/
├── data/
├── scenarios/
├── visualization/
├── deployment/
└── tests/
```

## Roadmap

### Phase 1 --- Architecture Consolidation

-   [x] BID-inspired documentation structure.
-   [x] OpenTwin MBDSS architecture.
-   [x] Modular digital-twin interface catalog.
-   [x] Required/optional/research dependency separation.
-   [ ] Normalize repository metadata and licenses.

### Phase 2 --- Minimal OpenTwin Core

-   [ ] Canonical asset schema.
-   [ ] Twin-state API.
-   [ ] Event model.
-   [ ] Health interface.
-   [ ] Model registry.
-   [ ] Telemetry recorder.

### Phase 3 --- Maritime Simulation

-   [ ] Generic vessel model.
-   [ ] Environment interface.
-   [ ] Hydrodynamics adapter.
-   [ ] Port/infrastructure twin.
-   [ ] Scenario package format.
-   [ ] Replay pipeline.

### Phase 4 --- Modelica / FMI

-   [ ] Electrical reference model.
-   [ ] Energy reference model.
-   [ ] Thermal reference model.
-   [ ] Propulsion reference model.
-   [ ] FMU adapter.
-   [ ] Co-simulation example.

### Phase 5 --- Distributed Simulation

-   [ ] HLA adapter.
-   [ ] Time synchronization.
-   [ ] Multi-federate example.
-   [ ] ROS 2/DDS bridge.
-   [ ] Recorder/replay federate.

### Phase 6 --- AI & Analytics

-   [ ] Anomaly-detection example.
-   [ ] Predictive-maintenance experiment.
-   [ ] Explainable recommendation interface.
-   [ ] Simulation surrogate experiment.
-   [ ] Human-review workflow.

### Phase 7 --- Training and Lifecycle

-   [ ] Virtual commissioning scenario.
-   [ ] Maintenance training scenario.
-   [ ] Port logistics scenario.
-   [ ] Humanitarian-response scenario.
-   [ ] Environmental-monitoring scenario.
-   [ ] XR visualization experiment.

## How to Contribute

Contributions are welcome in MBSE, maritime simulation, Modelica/FMI,
digital twins, HLA/distributed simulation, DEVS, ROS 2/DDS, data
engineering, AI/analytics, visualization, GIS, interoperability,
testing, validation, and documentation.

``` bash
git checkout -b feature/my-contribution
git add .
git commit -m "Add: description of contribution"
git push origin feature/my-contribution
```

Pull requests should describe the problem, solution, affected
interfaces, introduced dependencies, licensing implications, validation
method, tests/simulation results, and documentation changes.

Do not commit secrets, sensitive operational data, proprietary
engineering data, classified information, or restricted material.

## Code of Conduct

Contributors are expected to maintain a professional, respectful,
inclusive, and collaborative environment. A dedicated
`CODE_OF_CONDUCT.md` should be maintained at repository root.

## Authors and Maintainers

Maintained by the **Robotics Intelligent Systems** open-source
initiative.

Project repository: `robotics-intelligent-systems/jfxmbdss`

Third-party projects, standards, technologies, and trademarks remain the
property of their respective authors and organizations.

## Intellectual Property and Open Design

jfxmbdss promotes original, modular, standards-oriented engineering.
Prefer sufficiently abstract interfaces and original reference models
over reproducing proprietary implementations.

Open-design principles:

-   use documented open interfaces;
-   prefer openly licensed components where practical;
-   isolate optional proprietary integrations behind adapters;
-   record model provenance and licenses;
-   use original reference geometries and synthetic datasets;
-   keep model semantics independent of vendors;
-   minimize technology lock-in.

**Patent note:** open source does not automatically mean patent-free. An
architecture or software license cannot guarantee worldwide freedom from
third-party patent rights. Contributors and deployers remain responsible
for appropriate intellectual-property review for their jurisdiction and
use case.

Do not incorporate confidential specifications, classified or controlled
information, proprietary engineering drawings without permission,
restricted operational datasets, copied proprietary vehicle geometry, or
incompatible third-party source code.

## Disclaimer

jfxmbdss is a **research, educational, engineering, and experimental
simulation project**. It is not an operational command-and-control
system, weapon-control or targeting system, authority-approved maritime
navigation system, certified training device, safety-certified control
system, or substitute for qualified operators, engineers, instructors,
or authorities.

Simulation, optimization, and AI outputs can contain errors and
uncertainty and must not be the sole basis for safety-critical, legal,
navigational, emergency-response, or operational decisions.

Real-world deployment requires independent verification, validated
models, cybersecurity review, safety engineering, applicable
certification, professional oversight, and compliance with relevant
laws, regulations, standards, and procedures.

The BID repository template is used solely as a documentation-structure
reference. jfxmbdss does not claim BID funding, endorsement, catalog
membership, sponsorship, or institutional affiliation.

## License

The applicable jfxmbdss software license should remain in the repository
root as `LICENSE` or its existing equivalent.

Third-party software, models, datasets, standards, documentation, and
assets retain their respective licenses and terms. Do not automatically
apply an IDB/BID license, copyright notice, funding disclaimer, or
institutional attribution merely because its documentation template
informed the README structure.

## Open Engineering Principles

**Open Standards · Modular Interfaces · Digital Twins · MBSE ·
Modelica/FMI · Distributed Simulation · Reproducibility · Human
Oversight**

> Define interfaces before implementations.\
> Separate standards from products.\
> Model before integration.\
> Simulate before deployment.\
> Validate before relying on results.\
> Keep every replaceable component replaceable.
