# 4-Bit Full Adder Using CMOS Logic 
## Overview

This project implements a **4-bit full adder** using basic CMOS logic gates (AND, OR, XOR), manually connected to form a **ripple-carry adder**. All simulations were carried out using **Cadence Spectre** with a 1.8V supply and **SCL 180nm standard cells**. Delay metrics and transient analysis validate the design.

---

## Project Objectives

- Design **1-bit and 4-bit full adder** blocks from scratch using **CMOS logic**
- Implement using **SCL 180nm PDK** in **Cadence Virtuoso**
- Verify logic functionality with **transient simulations**
- Extract and analyze **propagation delay**

---

## Tools and Technology Stack

| Tool/Tech               | Purpose                                           |
|------------------------|----------------------------------------------------|
| **Cadence Virtuoso**   | Schematic Entry, Circuit Design                    |
| **Spectre Simulator**  | SPICE-level analog/transient simulations           |
| **Virtuoso ADE XL**    | Parametric analysis and delay sweeps               |
| **SCL 180nm PDK**      | Process Design Kit for standard CMOS cells         |
| **Linux**              | Workstation environment                            |


---

## Digital Logic Fundamentals

### 1-Bit Full Adder Logic:
- `Sum = A ⊕ B ⊕ Cin`
- `Cout = (A • B) + (Cin • (A ⊕ B))`

### 4-Bit Full Adder Construction:
- Cascade 4 × 1-bit Full Adders
- Ripple-Carry Architecture
- Input: `A[3:0], B[3:0], Cin`
- Output: `S[3:0], Cout`
---

## Design Architecture

### 1-Bit Full Adder Block:
- 2 × XOR Gates (for Sum)
- 2 × AND Gates + 1 × OR Gate (for Carry)
- VDD: 1.8V  
- Technology: SCL 180nm CMOS

### 4-Bit Adder Top-Level:
- 4× Full Adders in ripple structure
- Sum and Carry-out validated via simulation
---

## Simulation & Verification

| Simulation Type         | Tool             | Description                              |
|-------------------------|------------------|------------------------------------------|
| Transient Analysis      | Spectre          | Validate sum/carry logic timing          |
| DC Operating Point      | Virtuoso         | Node stability, signal swing             |
| Delay Measurement       | ADE XL + Manual  | A→Sum, Cin→Cout propagation              |

### Sample Outputs:
- Logic-level waveform output of Sum and Carry
- All 16 combinations of inputs verified
- Transient delays analyzed with scope markers

---

## Delay Metrics

| Path           | Gate Composition            | Delay (ps) |
|----------------|-----------------------------|------------|
| A → Sum        | XOR → XOR                   | ~271.7     |
| Cin → Cout     | XOR → AND → OR              | ~310+      |

> **Critical Path**: `Cin → Cout`  
> **Sum Path Delay** corresponds to contamination delay  
> Delay computed using **Spectre markers and waveform measurements**

---

## Physical Design Readiness (Next Steps)

While this project covers the full schematic design flow, the next planned steps include:

-  Layout design in **Virtuoso Layout Editor**
-  DRC/LVS verification using **Assura or Calibre**
-  Parasitic extraction (PEX)
-  Post-layout delay analysis
-  GDSII export

> This will help transition this 4-bit adder from functional design to silicon-ready block.

---
