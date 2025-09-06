# Coordinated Control of a Three-Level T-Type Inverter (3LT2I)

This repository accompanies the paper **“Coordinated Control of Three-Level T-Type Inverter for Renewable Energy Applications: Integrating Predictive Control with External RLC Estimation.”** It demonstrates fast and accurate current control with balanced DC-link capacitor voltages for a 3-level T-type inverter in renewable-energy interfaces.

> **Paper:** https://ieeexplore.ieee.org/document/10674957/

## Overview (what this work does)
- **Combines Finite-Control-Set Model Predictive Control (FCS-MPC) with an external RLC estimator.** The estimator refreshes load parameters online so MPC predictions stay accurate even when the plant changes.
- **Balances the neutral-point (DC-link) voltages** while tracking three-phase currents, addressing a common challenge in T-type inverters.
- **Verifies performance in simulation** under operating changes and parameter mismatch.

![Overview of the proposed method](./Overview%20of%20Proposed%20Method.jpg)

## Why it matters
- **Low THD and fast dynamics:** Predictive control with online parameter updates improves current quality and transient response.
- **Robust to model errors:** Periodic RLC re-identification reduces MPC sensitivity to parameter drift/aging.
- **Renewables-ready:** The 3LT2I topology offers high efficiency and lower device stress than 2-level inverters, suitable for PV, wind, and storage.

## How it works (at a glance)
1. **FCS-MPC current control:** At each sampling instant, the controller evaluates candidate switching states (27 vectors) using a cost function that trades off current tracking and capacitor-voltage balancing.
2. **External RLC estimation:** An auxiliary routine infers R, L, C and feeds them back to the MPC model to keep predictions aligned with the real system.

## What’s in this repo
- `Conventional_MPC_10khz_DEMO1.slx` – baseline FCS-MPC demo model.
- `Conventional_MPC_Cap_Balance_CMV_Reduct_....slx` – baseline with capacitor-balance / common-mode-voltage reduction (model name shortened here).
- `Overview of Proposed Method.jpg` – one-page schematic of the proposed approach.
- `Presentation_MPC_T_TYPE_INVERTER_WITH_....pptx` – slide deck (file name shortened here).

> Tip: If you rename files, update the links above accordingly. The image link expects the file to be at the repo root and keeps the exact name with spaces URL-encoded.

## Quick start
1. Open a `.slx` model in MATLAB/Simulink (R2020b or newer recommended).
2. Press **Run** to simulate. Inspect measured currents, predicted states, and DC-link capacitor voltages.
3. Compare the baseline vs. proposed settings to see current-tracking quality and neutral-point voltage balance.

## Reference
Lu T. T., Nguyen T. K. D., Ly T. T., Pham T. D. Q., Le N. A., and Pham M. D., “Coordinated Control of Three-Level T-Type Inverter for Renewable Energy Applications: Integrating Predictive Control with External RLC Estimation,” in *Proc. 2024 7th International Conference on Green Technology and Sustainable Development (GTSD)*, p
