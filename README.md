# Low Power VLSI Design (TSMC 180nm)

This repository contains transistor-level SPICE simulations investigating low-power CMOS architectures, specifically focusing on data path optimization, multi-voltage domain interfacing, and SRAM cell design. All simulations are modeled using the TSMC 180nm technology node in LTspice.

## Project Structure & Investigations

### 📁 Q1_Adder_Architectures
An investigation into how architectural transformations facilitate supply voltage ($V_{dd}$) scaling to reduce dynamic power without sacrificing baseline throughput.
* **Part A (Baseline):** A 4-bit Ripple Carry Adder (RCA) built with 120-transistor Transmission Gate Full Adders. (Critical Path: 1.63ns, Power: 180 μW).
* **Part B (Pipelined):** A 2-stage pipelined RCA using Positive-Edge Master-Slave D-Flip-Flops. The critical path is reduced to 1.29ns, demonstrating how the introduction of slack time allows for $V_{dd}$ scaling.
* **Part C (Parallel):** A dual-unit parallel RCA utilizing Toggle-FFs and 2:1 Output Multiplexers. This allows the system frequency to be halved (maintaining throughput), enabling drastic $V_{dd}$ scaling for quadratic power savings.

### 📁 Q2_Level_Converter
A demonstration of static power reduction in multi-voltage domains. 
* Interfaces a $1V$ logic domain with a $1.8V$ logic domain operating at 500MHz.
* Compares a direct inverter connection vs. a Cross-Coupled PMOS Level Converter.
* **Result:** The Level Converter successfully eliminates short-circuit current in the 1.8V domain, reducing average power consumption by roughly **40x** (from ~40.1 μW down to ~0.97 μW).

### 📁 Q3_SRAM_Cell
Transistor-level design and verification of a standard 6T SRAM Cell.
* Implements cross-coupled inverters and NMOS access transistors.
* Verified for stable Read/Write operations via Word Line (WL) and Bit Line (BL/BLB) pulsing.
* Evaluates standby leakage power ($\approx 0.969 \mu W$) during data retention.

## Tools Used
* **Simulator:** LTspice (macOS)
* **Technology:** TSMC 180nm CMOS (BSIM3 Models)
