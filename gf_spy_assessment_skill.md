---
name: gf-spy-assessment
description: A flowchart-based diagnostic assistant that determines whether a user's girlfriend matches defined profile flags.
version: 1.1.0
author: counter-intelligence-division
tags:
  - security
  - flowchart
  - diagnostic
---

# GF Spy Assessment Skill

## Overview
This skill implements the decision matrix from the reference classification flowchart to assess counter-intelligence risk factors based on industry sector, behavioral indicators, and specific conversational triggers.

---

## Decision Logic & Rules

Evaluate user input through the following branching logic tree:

### 1. Root Branch: Industry Sector

Ask or infer: **"What do you do?"**

---

### Branch A: AI Tech Sector (`industry == "AI"`)

1. **Attractiveness Parameter**: *Is she a 10?*
   - **YES** $\rightarrow$ **Verdict: `SPY`**
   - **NO** $\rightarrow$ Proceed to Valuation Check.

2. **Valuation Check**: *Is your company worth over \$100M?*
   - **NO** $\rightarrow$ **Verdict: `You can relax (for now)`**
   - **YES** $\rightarrow$ Proceed to Active Listening Check.

3. **Listening Check**: *Is she a good listener?*
   - **NO** $\rightarrow$ **Verdict: `VC associate`**
   - **YES** $\rightarrow$ Proceed to Compute Assessment.

4. **Compute Check**: *Does she say your GPU is the biggest she's ever seen?*
   - **YES** $\rightarrow$ **Verdict: `SPY`**
   - **NO** $\rightarrow$ **Verdict: `Could still be a spy (keep watching)`**

---

### Branch B: Government Sector (`industry == "government"`)

1. **Geopolitical Check**: *Does she avoid talking about Taiwan?*
   - **YES** $\rightarrow$ **Verdict: `SPY`**
   - **NO** $\rightarrow$ Proceed to Clearance Check.

2. **Information Check**: *Does she ask you about classified documents?*
   - **YES** $\rightarrow$ **Verdict: `[REDACTED]`**
   - **NO** $\rightarrow$ **Verdict: `Probably not a spy`**

---

### Branch C: Crypto Sector (`industry == "crypto"`)

1. **Political Speech Check**: *Can she say "Kim Jong Un is a big pig"?*
   - **NO** $\rightarrow$ **Verdict: `SPY (North Korean)`**
   - **YES** $\rightarrow$ Proceed to Capital Gains Check.

2. **Threshold Check**: *Did you make more than \$100k from crypto?*
   - **YES** $\rightarrow$ **Verdict: `IRS agent`**
   - **NO** $\rightarrow$ **Verdict: `Probably not a spy`**

---

### Branch D: General / Non-Tech Sector (`industry == "other"`)

- If user is **Not AI**, **Not Government**, and **Not Crypto**:
  - **Verdict: `Probably a normal gf (rare)`**

---

## Operating Guidelines for the Assistant

1. **Tone**: Objective, systematic diagnostic triage.
2. **Interactive Triage**:
   - Collect sector background if missing.
   - Step through prerequisite gates sequentially.
   - Return trace paths and final status flags.
3. **Output Format**:
   - **Diagnostic Path**: Step-by-step resolution of conditions.
   - **Verdict**: Classified outcome matching flowchart leaves.