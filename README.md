# The Riemann Hypothesis as the Avoidance of an Information Entropy Collapse

Code and results for the paper by Ridwan Sakidja (Missouri State University),
"The Riemann Hypothesis as the Avoidance of an Information Entropy Collapse:
the Riemann zeros as the discarded second moment of the primes" (November 2026).

The Riemann hypothesis as a closed quantum system: the entropy over the zeros is conserved
only when the evolution is unitary.

## What is here

| Path | Content |
| --- | --- |
| `scripts/ri_campaign.py` | Main classical run: invariant by window, primes by interference, spacing, count variance, reciprocal space ramp, restoring force. Sections 3 to 6 of the paper. |
| `scripts/ri_campaign2.py` | Second campaign: the ramp rebuilt from the primes alone (Section 5.4), the entropy over modes with the true weights and the random walk tests on the true primes by sieve to 1e9 (Section 3). |
| `scripts/qtest1.py` | Quantum register (8 qubits and 1 ancilla): primes from the X reading; post selection and entropy over modes off the line. Sections 7.1 and 7.3. |
| `scripts/qramp.py` | Quantum register: the ramp from the X and Y readings. Section 7.2. |
| `scripts/force.py` | Restoring force with 2,000 zeros (the single run quoted in Section 6.1). |
| `scripts/qtest2.py` | Spacing and count variance on gammas.npy (first check of Section 5). |
| `scripts/qtest3.py` | Reciprocal space ramp on gammas.npy (first check of Section 5.3). |
| `scripts/make_gammas.py` | Writes gammas.npy (first N zeros) with mpmath. |
| `scripts/get_zeros.sh` | Downloads Odlyzko's tables zeros1, zeros3, zeros4, zeros5. |
| `scripts/submit_campaign.sh` | Slurm submit file used on NERSC Perlmutter. |
| `results/ri_campaign_60857063.out` | Output of the campaign job (job 60857063). |
| `results/ri_campaign_results.json` | The same numbers in machine readable form. |
| `scripts/submit_campaign2.sh` | Slurm submit file for the second campaign. |
| `results/ri_campaign2_60868222.out` | Output of the second campaign (job 60868222). |
| `results/ri_campaign2_results.json` | The same numbers in machine readable form. |
| `scripts/ri_probe_height.py` | The ramp rebuilt from the primes alone at five heights, with errors (Section 5.4). |
| `scripts/ri_dh.py` | The Davenport and Heilbronn function: its zeros to height 2,000, variance by window, entropy over modes, and the arithmetic side (Section 8). |
| `scripts/submit_campaign3.sh` | Slurm submit file for the third campaign. |
| `results/ri_campaign3_60869745.out` | Output of the third campaign (job 60869745). |
| `results/ri_probe_height_results.json`, `results/ri_dh_results.json` | The same numbers in machine readable form. |
| `scripts/ri_lpair.py` | The two Dirichlet L functions modulo 5 that make up the Davenport and Heilbronn function, measured one at a time: zeros, variance, entropy, primes, pair statistics. |
| `scripts/submit_campaign4.sh` | Slurm submit file for the fourth campaign. |
| `scripts/ri_figdata.py` | The numbers behind Figures 8 to 11, from the zeros already found: entropy over modes and variance by window out to log x = 100, share of each mode against log x, modulus of the three functions across the critical strip. Writes `ri_figdata_results.json` and `ri_figdata_arrays.npz`. |
| `scripts/ri_derived.py` | Prints the means, ratios and counts quoted in the text, read from the result files of campaigns 1 to 4. |
| `scripts/ri_steps.py` | The variance of the Davenport and Heilbronn function term by term, the rate of growth 2⟨δ⟩, and where the lead passes from one mode to the next; writes `ri_steps_results.json` and `figures/fig8_steps.png`. Reads the result files of campaigns 3 and 4. Section 8.2 and Figure 12; a few seconds, no job. |
| `scripts/ri_layers.py` | The layers of the Davenport and Heilbronn function (modes with one common weight), the share of each layer, and the entropy split by Shannon's grouping rule into the part between layers and the part inside the layer of the line; checks itself against campaign 5; writes `ri_layers_results.json` and `figures/fig9_layers.png`. Reads the result file of campaign 3. Section 8.2, Table 20 and Figure 13; a few seconds, no job. |
| `scripts/ri_register_figs.py` | Draws the register of Section 7 from the job outputs: the entropy and the success probability of the post selection against the entropy theorem, and the ramp read from one ancilla. Reads the tables printed by `qtest1.py` and `qramp.py`; computes nothing else. |
| `scripts/ri_circuit_fig.py` | Draws the schematic of the Hadamard test circuit of Section 7 (Figure 4). It reads no file and computes no number. |
| `scripts/ri_paircorr.py` | The pair correlation of the first 100,000 zeros, measured in bins of the separation, against the unitary class (the same function as free fermions in one dimension) and against no stiffness. Reads `zeros1`. Writes `ri_paircorr_results.json` and the figure `fig_paircorr`. |
| `scripts/submit_campaign5.sh` | Slurm submit file for the fifth campaign: `qtest1.py`, `force.py`, `ri_figdata.py`, `ri_derived.py`, `make_figures.py`. |
| `scripts/make_figures.py` | Draws Figures 1, 3 and 7 to 11 (files `fig1` to `fig7`). It only reads result files; nothing is computed in it. |
| `figures/` | The figures (PNG and PDF). |
| `results/ri_campaign4_60873848.out`, `results/ri_lpair_results.json` | Output of the fourth campaign (job 60873848). |
| `results/ri_campaign5_60881952.out`, `results/ri_figdata_results.json`, `results/ri_figdata_arrays.npz` | Output of the fifth campaign (job 60881952). |
| `paper/` | The paper (Word). |

## Where each table and figure comes from

Every number in a table and every point in a figure is printed or written by a script in `scripts/`, run as a job on NERSC Perlmutter.

| Item in the paper | Script | Job output or result file |
| --- | --- | --- |
| Table 1, the prime fluctuation as a quantum system | none: the correspondence of Section 1 | |
| Table 2, sets of zeros | Odlyzko's tables (`get_zeros.sh`) | heights printed in `ri_campaign_60857063.out`, part 3 |
| Table 3, earlier work | none: citations | |
| Table 4, variance by window | `ri_campaign.py`, part 1 | `ri_campaign_60857063.out` |
| Table 5, share of a moved mode | `ri_campaign2.py`, part B | `ri_campaign2_60868222.out` |
| Table 6, random walk | `ri_campaign2.py`, part C | `ri_campaign2_60868222.out` |
| Table 7, primes by interference | `ri_campaign.py`, part 2 | `ri_campaign_60857063.out` |
| Table 8, spacings | `ri_campaign.py`, part 3 | `ri_campaign_60857063.out` |
| Table 9, count variance | `ri_campaign.py`, part 3; the column of means by `ri_derived.py` | `ri_campaign_60857063.out`; `ri_campaign5_60881952.out` |
| Table 10, the ramp | `ri_campaign.py`, part 3 | `ri_campaign_60857063.out` |
| Table 11, the ramp from the primes | `ri_campaign2.py`, part A | `ri_campaign2_60868222.out` |
| Table 12, five heights | `ri_probe_height.py` | `ri_campaign3_60869745.out` |
| Table 13, stiffness of the well | `ri_campaign.py`, part 4 | `ri_campaign_60857063.out` |
| Table 14, two neighbours | `ri_campaign.py`, part 4 | `ri_campaign_60857063.out` |
| Section 6.1, the run with 2,000 zeros | `force.py` | `ri_campaign5_60881952.out` |
| Table 15, the X reading | `qtest1.py` | `ri_campaign5_60881952.out` |
| Table 16, the ramp from X and Y | `qramp.py 100` | `ri_campaign_60857063.out` |
| Table 17, post selection | `qtest1.py` | `ri_campaign5_60881952.out` |
| Table 18, Davenport and Heilbronn | `ri_dh.py`, part B | `ri_campaign3_60869745.out` |
| Table 19, component and combination | `ri_lpair.py`, part B | `ri_campaign4_60873848.out` |
| Table 20, the entropy split by the grouping rule | `ri_layers.py`, part B | `ri_layers.out` |
| Tables 21 to 23 | none: they quote the tables above and the cited work | |
| Means, ratios and counts quoted in the text | `ri_derived.py` | `ri_campaign5_60881952.out` |
| Figure 1 | `make_figures.py` | `ri_campaign_results.json`, `ri_campaign2_results.json`, `ri_dh_results.json` |
| Figure 3 | `make_figures.py` | `ri_probe_height_results.json` |
| Figure 7 | `make_figures.py` | `ri_dh_results.json` |
| Figure 8 | `ri_figdata.py`, part A, then `make_figures.py` | `ri_figdata_results.json` (job 60881952) |
| Figure 9 | `ri_lpair.py`, `ri_figdata.py`, part A, then `make_figures.py` | `ri_lpair_results.json`, `ri_figdata_results.json` (job 60881952) |
| Figure 10 | `ri_figdata.py`, part B, then `make_figures.py` | `ri_figdata_arrays.npz` (job 60881952) |
| Figure 11 | `ri_figdata.py`, part C, then `make_figures.py` | `ri_figdata_arrays.npz` (job 60881952) |
| Section 8.2, Table 20, Figure 13: the layers and the grouping rule | `ri_layers.py` | `ri_layers.out`, `ri_layers_results.json` (run without a job, 5 November 2026) |
| Section 7, Figures 5 and 6: the ramp read from one ancilla, and one mode off the line on the register | `ri_register_figs.py` | `ri_register_figs.out`, `ri_register_figs_results.json` (run without a job, 5 November 2026); it reads `ri_campaign_60857063.out` and `ri_campaign5_60881952.out` |
| Section 5.1, Figure 2: the pair correlation of the zeros | `ri_paircorr.py` | `ri_paircorr.out`, `ri_paircorr_results.json` (run without a job, 6 November 2026); it reads `zeros1` |
| Section 7, Figure 4: the circuit diagram | `ri_circuit_fig.py` | none: a schematic |
| Section 8.2, Figure 12: the terms, the rate of growth, where the lead passes | `ri_steps.py` | `ri_steps.out`, `ri_steps_results.json` (run without a job, 5 November 2026) |

## How to reproduce

```
pip install numpy scipy mpmath qiskit matplotlib
cd scripts
bash get_zeros.sh              # Odlyzko's tables
python make_gammas.py 2000     # gammas.npy for the quantum scripts
python ri_campaign.py          # 10 to 15 minutes
python ri_campaign2.py 1e9     # 6 minutes, about 30 GB of memory; use 1e8 on a small machine
python qtest1.py
python qramp.py 100
python force.py
python ri_probe_height.py 1e9
python ri_dh.py 2000 1e6
python ri_lpair.py 2000 1e6
python ri_figdata.py 100   # needs the result files of ri_dh.py and ri_lpair.py, and zeros1
python ri_derived.py
python make_figures.py     # draws from the result files only
python ri_layers.py        # Table 20 and Figure 13; needs the result file of ri_dh.py
python ri_register_figs.py   # Figures 5 and 6; needs the job outputs of campaign 1 and campaign 5
python ri_circuit_fig.py      # Figure 4, the circuit diagram; needs nothing
python ri_paircorr.py         # Figure 2, the pair correlation of Section 5.1; needs zeros1
python ri_steps.py         # Figure 12; needs the result files of ri_dh.py and ri_lpair.py
```

The quantum circuits are evaluated by statevector simulation in Qiskit (tested with 2.6.1), which is exact at this size,
and the shots are sampled from the exact probabilities.

## Main numbers

| Result | Value |
| --- | --- |
| Variance of the scaled prime fluctuation, 100,000 zeros, eight windows up to log x = 30 | 0.0460, spread 0.0010 (closed form 0.046191) |
| Growth of one mode moved off the line by delta, per window of 3 in log x | matches exp(6 delta) within half a percent |
| Spikes at the 25 prime powers up to 60, measured over predicted | 0.9995, scatter 0.0006 |
| Saturated count variance: first 100,000 zeros; near zero number 10^12, 10^21, 10^22 | 0.357, 0.481, 0.518, 0.522 (predicted 0.362, 0.466, 0.527, 0.532) |
| Stiffness of the harmonic well, measured over predicted, zeros 1 to 300 | 0.994 to 1.010 |
| Entropy over modes, 256 zeros, one mode off the line by 0.20 | 5.48, 4.38, 1.33, 0.18 at log x = 6, 12, 18, 24 (maximum 5.545) |
| Entropy over modes of the Davenport and Heilbronn function, windows of log x from 2 to 100 | 3.01, largest 3.20, down to 0.092 (zeta function: 4.039 in every window) |


## Data

The zeros are from A. M. Odlyzko, Tables of zeros of the Riemann zeta function,
https://www-users.cse.umn.edu/~odlyzko/zeta_tables

## Acknowledgements

This research used resources of the National Energy Research Scientific Computing Center (NERSC),
a U.S. Department of Energy Office of Science User Facility, under allocation m4675 as part of the
QIS@Perlmutter benchmarking program.

AI (LLM) assistance (Claude, Anthropic) was used in preparing code and text. The framework,
calculations and analysis are the author's, and the author takes full responsibility for the
scientific content.

## Citation

Please cite the paper and this repository. See `CITATION.cff`.

## License

MIT. See `LICENSE`.

## Second campaign (job 60868222)

- The squared prime sum, with no zero in it, rebuilds the ramp of zeros 1,001 to 100,000 to within 0.006 (rms, 15 bins below tau = 0.8); the zeros lie 0.029 from the unitary ramp and the primes reproduce that departure (correlation 0.89).
- Entropy over modes with the true weights 1/|rho_n|^2: H = 4.234 on the line; measured and predicted shares of a moved mode agree within 0.01 in 64 of 72 windows and within 0.032 in all.
- True primes by sieve to 1e9: variance of (psi(x) - x)/sqrt(x) is 0.0461 with spread 0.0013 over five windows (closed form 0.0462); random primes are 338 times louder in the window of log x from 15 to 18.
- Moebius sum: variance of M(x)/sqrt(x) is 0.0289 with spread 0.0007; random signs on the same squarefree integers give 0.61.

## Third campaign (job 60869745)

- The ramp from the primes alone, with errors: up to zero number 1e12 the zeros agree with the prime sum within the error (mean squared deviation 0.75, 0.79, 1.31 in units of the error) and not with the unitary ramp (16, 262, 11). Near 1e21 and 1e22 the predicted departure is below the error and the zeros agree with both.
- The Davenport and Heilbronn function (same functional equation, no product over primes): 2,029 zeros below height 2,000, of which 84 pairs are off the line. Variance of the scaled fluctuation grows from 0.197 to 103.6 between log x of 2 and 20; entropy over modes goes from 3.01 to 1.51; the zeta function stays at 0.04 and 4.039. The arithmetic side, with no zeros, gives the same growth (correlation 0.996 to 0.982). Without the product over primes it is an open quantum system: a mode off the line at σ = 1/2 + δ carries the weight e^(δt) and leaks by that δ. That is why its evolution is not unitary, and that is why it loses the line and its entropy collapses.

## Fourth campaign (job 60873848)

- The layers of the combination (`ri_layers.py`, `ri_steps.py`): the 1,861 zeros on the line are one layer whose internal entropy is 2.917215 at every log x from 2 to 100; Shannon's grouping rule, H = H between layers + share of each layer x entropy inside it, holds to 7e-15; the lead passes from the line to 0.8085 + 85.70 i at log x = 9.2 and to 0.8695 + 240.40 i at 17.0; the rate of growth 2<delta> rises from 0.005 to 0.728 by log x = 40 and ends at 0.7391.

The Davenport and Heilbronn function is a fixed combination of two Dirichlet L functions modulo 5. `ri_lpair.py` measures the two components one at a time.

- Zeros below height 2,000: 2,028 and 2,029, together 4,057 against the smooth count 4,057.1, none off the line.
- Variance of each component: 0.179 to 0.226 by window, around the closed form log(5/pi) - gamma_E + 2 Re L'(1,chi)/L(1,chi) = 0.203222. Entropy over modes: 3.5524 in every window. The combination grows from 0.197 to 103.6 and its entropy is not conserved.
- From the primes alone (no zeros): the same variance within 1.4 percent, correlation 0.996 to 0.998.
- Pair statistics of the components: mean squared deviation 0.87 against the sum over their primes, 59 against the unitary ramp.

## Figures

`python scripts/make_figures.py` reads `results/` and writes `figures/` (PNG at 300 dpi and PDF). It needs numpy and matplotlib.

The file names are the ones the scripts write. The figure number in the paper is in the second column; the paper numbers its figures in the order they appear.

| File | Figure in the paper |
|---|---|
| `fig1_variance` | 1. Variance by window: zeta zeros, true primes, random primes, Davenport and Heilbronn |
| `fig2_pairs` | 3. Form factor of the zeros at five heights against the primes and the ramp |
| `fig3_dh_zeros` | 7. Zeros of the Davenport and Heilbronn function below height 2,000 |
| `fig4_entropy` | 8. Entropy over modes: zeta and Davenport and Heilbronn |
| `fig5_components` | 9. The two components and their combination: variance, entropy, pair statistics |
| `fig6_mode_shares` | 10. Heat map of the share of the variance carried by each mode |
| `fig7_strip` | 11. Heat map of the modulus of each function across the critical strip |
| `fig8_steps` | 12. The variance of the combination term by term, and its rate of growth |
| `fig9_layers` | 13. The share of each layer, and the entropy split by Shannon's grouping rule |
| `fig10_register_ramp` | 5. The ramp read from one ancilla |
| `fig11_register_entropy` | 6. One mode off the line on the register: entropy and success probability against the entropy theorem |
| `fig_circuit_hadamard` | 4. The Hadamard test circuit of the quantum readout |
| `fig_paircorr` | 2. The pair correlation of the first 100,000 zeros against the unitary class (free fermions) and no stiffness |

Figures 1, 3 and 7 to 11 are drawn by `make_figures.py` from the result files alone. Figures 12 and 13 are drawn by `ri_steps.py` and `ri_layers.py`, each from the result file it has just written.
