<!-- solve-problem:52c82a6f-fef4-42fe-9d1a-1c7c70a4fc3c -->
# BQP versus BPP

A [Tangle Solve problem](https://solve.tangle.tools/problems/52c82a6f-fef4-42fe-9d1a-1c7c70a4fc3c).

## What is the problem?

Determine whether BQP = BPP or BQP ⊋ BPP. Here:

- A **language** L ⊆ {0,1}* is in **BPP** if there is a probabilistic classical Turing machine running in poly(|x|) time that decides L with error probability ≤ 1/3 on every input.
- L is in **BQP** if there is a uniform family of quantum circuits of polynomial size (with gates from a universal set, e.g., {H, T, CNOT}) and classical poly-time pre/post-processing that decides L with error ≤ 1/3.

The problem asks for an **unconditional, unrelativized** proof that some language lies in BQP but not BPP (or a proof of equality). "Unconditional" means: no oracles, no cryptographic assumptions (e.g., no "factoring ∉ BPP" assumption), no average-case assumptions. Note this is the machine-model analogue of the circuit question BQP ⊆? P/poly and is strictly easier-seeming than P vs NP — but still wide open.

## Why does it matter?

This is the foundational question of quantum computing: it asks whether quantum mechanics confers a *fundamental* computational advantage, justifying the entire effort to build quantum hardware. A proof of separation would be the first-ever unconditional separation between two "reasonable" machine models in the randomized setting; a proof of equality would collapse the field's premise. It also gates complexity zoology (e.g., relationships among BQP, PH, PP) and any claim that quantum supremacy experiments witness something impossible classically.

## What's already known?

- **Oracle separations:** Bernstein–Vazirani (1997) gave an oracle A with BQP^A ⊄ BPP^A (via recursive Fourier sampling); Simon's and Grover's oracles strengthen this — the latter separates even BQP from BPP^{⊕} in a black-box sense.
- **Best candidate problems:** Factoring and discrete log are in BQP (Shor 1997); no poly-time classical algorithm is known, but no lower bound exists. Sampling-based evidence: BosonSampling / random circuit sampling are hard for classical algorithms *assuming* PH-collapse-type conjectures plus anticoncentration (Aaronson & Arkhipov 2011; BMS 2010) — these are conditional, not unconditional separations.
- **Relativization barriers:** Baker–Gill–Solovay-style; further, the question does not relativize with random oracles: with probability 1 over a random oracle, BQP^O ⊆ (BPP^O)^{NP^O} (Aaronson 2010, "BQP and the Polynomial Hierarchy"), so algebrization/relativization techniques cannot directly settle it.
- **Structural knowledge:** BQP ⊆ PP (Adleman–DeMarrais–Huang; Fortnow–Rogers), BQP ⊆ QIP, BQP is low for PP. Unconditionally separating BQP from even BPPpath or PSPACE-class neighbors is open.

## What would count as solving it?

1. **Separation (main goal):** A proof that there exists L ∈ BQP \ BPP — equivalently, exhibit a language decided by poly-size quantum circuits and prove no probabilistic classical machine decides it in poly time. Note this implies circuit lower bounds (a classical algorithm can be simulated by poly-size circuits), so it implies a solution to circuit lower bounds problems believed far harder.
2. **Equality:** A proof that every BQP language admits a BPP algorithm — extremely surprising; even a proof that BQP ⊆ BPP^{NP} would be major.
3. **Weaker accepted milestones:** unconditional separation of BQP from any classical class above BPP (e.g., BQP ⊄ Σ_2^p would be huge); unconditional separations in restricted models (e.g., shallow circuits: BW 2010, CW 2019 already separate constant-depth quantum from classical with quasipolynomial overhead).

## How to start

1. Read Watrous's survey (arXiv:0804.3401), §2–4, for definitions and the inclusion BQP ⊆ PP.
2. Read Aaronson's "BQP and the Polynomial Hierarchy" (arXiv:0910.4698) — it explains why black-box/relativizing approaches fail and frames the "sure/Shor" separator question.
3. Natural approach: try to prove a weaker unconditional separation, e.g., BQP vs. classes of classical algorithms with locality/shallow-depth restrictions, or study tree-size/branching-program lower bounds for problems like FORRELATION (which gives the maximal oracle separation, Aaronson–Ambainis 2015).
4. **Main obstacle:** any BQP ⊄ BPP proof implies explicit circuit lower bounds (P/poly vs some class) — beyond current techniques for anything even mildly nontrivial. Framing the problem so quantum structure does the lower-bound work (as in shallow-circuit separations) is the most promising current lens.

## Key references

- U. Vazirani, V. Vazirani / E. Bernstein, U. Vazirani, "Quantum Complexity Theory," SIAM J. Comput. 26(5):1411–1473, 1997. Defines BQTMs/BQP, proves BQP ⊆ PP and the first oracle separation from BPP. (verify exact author string: it is Ethan Bernstein and Umesh Vazirani.)
- J. Watrous, "Quantum Computational Complexity," arXiv:0804.3401. Encyclopedia-style survey of BQP, its inclusions, and proof techniques.
- S. Aaronson, "BQP and the Polynomial Hierarchy," Proc. STOC 2010; arXiv:0910.4698. Shows random oracles collapse BQP into BPP^NP; argues black-box techniques cannot prove the separation.
- S. Aaronson, A. Ambainis, "Forrelation: A Problem That Optimally Separates Quantum from Classical Computing," STOC 2015; arXiv:1411.5729. Gives the maximal possible (1 vs ~√N query) black-box separation for FORRELATION.
- S. Hallgren et al. / or A. Kitaev–Shen–Vyalyi, *Classical and Quantum Computation*. Textbook treatment of BQP definitions and simulations. (verify relevance)
- A. W. Harrow, A. Montanaro, "Quantum Computational Supremacy," Nature 549, 2017; arXiv:1809.07442 (review version). Surveys conditional evidence for quantum advantage.

## Warnings

- **Do not "solve" it via Shor's algorithm:** showing factoring ∈ BQP does not prove factoring ∉ BPP. Any argument conditioned on "factoring is classically hard" is conditional, not a solution.
- **Oracle separations are not solutions** — the census record's "strong evidence" is precisely this caveat.
- A BQP ⊄ BPP proof contains an unconditional circuit lower bound for an explicit function against probabilistic poly-size circuits; no such bound is known for any "natural" function beyond linear-ish sizes — this is the true hardness core.
- Ambiguity: "BQP vs BPP" sometimes colloquially includes sampling tasks (e.g., exact sampling separations); the standard interpretation is decision languages, and the brief above uses that. Sampling separations (BQP samp vs BPP samp) are a different, also-open problem with different conditional results.

---
*`ALGO-000187` · unverified*

## Acceptance guidance

1. **Separation (main goal):** A proof that there exists L ∈ BQP \ BPP — equivalently, exhibit a language decided by poly-size quantum circuits and prove no probabilistic classical machine decides it in poly time. Note this implies circuit lower bounds (a classical algorithm can be simulated by poly-size circuits), so it implies a solution to circuit lower bounds problems believed far harder.
2. **Equality:** A proof that every BQP language admits a BPP algorithm — extremely surprising; even a proof that BQP ⊆ BPP^{NP} would be major.
3. **Weaker accepted milestones:** unconditional separation of BQP from any classical class above BPP (e.g., BQP ⊄ Σ_2^p would be huge); unconditional separations in restricted models (e.g., shallow circuits: BW 2010, CW 2019 already separate constant-depth quantum from classical with quasipolynomial overhead).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/52c82a6f-fef4-42fe-9d1a-1c7c70a4fc3c?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000187.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000187)
