# Reading Between the Lines: How Much Information Remains After Fitting a Stellar Spectrum?

**An audit of the information remaining in 7087 GALAH spectra after subtracting their best-fitting stellar models.**

Authors: Sven Buder (ANU), Tomasz Różánski (ANU), David W. Hogg (CCA, MPIA, NYU)

> **Manuscript to be submitted to *The Open Journal of Astrophysics***

Quicklinks: [Residual-peak catalogue](data/peak_inspection_table.fits) · [Individual peak diagnostics](residual_inspection/) · [Paper figures](figures/)

## Abstract

What if we could model 100% of a stellar spectrum? Modern surveys infer stellar properties by comparing observed spectra with synthetic models, yet even the best fits leave structured residuals. We analyse 7087 GALAH spectra and ask what information remains after subtracting each best-fitting model. Across 99 million residual pixels, 4.6 million exceed $3\sigma$, far above the 0.3 million expected from Gaussian noise. We map the amplitude, significance, sign, and recurrence of these residuals and identify 380 significant regions. Comparison with stellar atlases, line lists, diffuse interstellar bands, and sky diagnostics links most regions to plausible causes: 63% are candidate line-strength or line-profile mismatches, while others trace missing or unidentified lines, interstellar absorption, sky emission, or broader reduction structure. We then train data-driven models on the residual spectra themselves. Residual-only models recover $T_\mathrm{eff}$ to $80-150\mathrm{K}$ and $[\mathrm{Fe/H}]$ to $0.059-0.086\mathrm{dex}$, depending on sample quality, and retain weaker, partly indirect information about elemental abundances. Extinction-related coefficients recover the strongest known interstellar features, whereas chromospheric activity leaves plausible Balmer-line signatures but is not recovered robustly out of sample. Most strikingly, the 6% of pixels excluded from the GALAH optimisation recover stellar labels almost as well as the full residual spectrum and better than the remaining 94% alone. Residuals are therefore not merely imperfections to discard: they map missing line data, incomplete physics, unfitted astrophysical components, and observational systematics. Reading between the lines turns one spectroscopist's trash into another one's treasure, and provides a practical route toward extracting more of the information already present in stellar spectra.

## Main results

### 1. The residuals are not random

Residual structure is present throughout all four GALAH wavelength bands. Many residuals recur across a large fraction of the sample and are preferentially signed.

Observed spectra that are systematically deeper than the synthesis point towards missing or underestimated opacity, omitted blends, or inaccurate line-formation physics. Observed spectra that are systematically shallower can indicate overestimated opacity, line-core emission, continuum-normalisation errors, or reduction artefacts.

<img
src="figures/significance_residual_flux_percentiles_m1.png"
alt="Residual significance across the four GALAH wavelength bands. Curves show the 16th, 50th, and 84th percentiles of the absolute difference between observed and synthetic flux divided by the reported flux uncertainty across 7087 spectra. Numerous narrow and broad peaks demonstrate recurrent model–data disagreement."
width="100%"
/>

The direction of the residual provides information about how the spectral model would need to change.

<img
src="figures/percentage_3sigma_residual_flux_percentiles_m1.png"
alt="Fraction of the 7087 GALAH spectra with residuals larger than three times the reported flux uncertainty as a function of wavelength. Separate curves show regions where the observed spectra are systematically shallower or deeper than the synthetic spectra."
width="100%"
/>

### 2. The catalogue maps recurrent residual structure

We identified and visually inspected 380 recurrent residual regions. Each region was assigned a primary classification using its wavelength, width, recurrence, residual direction, and proximity to features in stellar atlases, the GALAH line list, catalogues of diffuse interstellar bands, telluric absorption, and sky-emission spectra.

<img
src="figures/percentage_3sigma_residual_flux_percentiles_m1_classified.png"
alt="Classification map of recurrent signed residual structure across the four GALAH wavelength bands. Curves show the fractions of spectra for which the observed flux is more than three times the reported uncertainty shallower or deeper than the synthesis. Coloured horizontal bars mark 380 catalogue regions and distinguish candidate line-strength and line-profile mismatches, insignificant regions, sky emission, interstellar absorption, and missing, unidentified, or ambiguous features."
width="100%"
/>

The adopted classifications include:

* transition strengths that are probably too high;
* transition strengths that are probably too low;
* line-profile or line-formation mismatches;
* known transitions missing from the synthesis;
* unidentified absorption features;
* interstellar absorption;
* sky-emission residuals;
* insignificant residuals;
* ambiguous or blended regions.

These classifications are plausibility assessments rather than definitive identifications. Nevertheless, the sign and morphology of a residual often indicate directly how the physical model or input line data would need to change.

### 3. Representative residual regions

The following examples illustrate the nine main classifications used in the catalogue. Each diagnostic combines the GALAH residual statistics with relevant external information, including Solar and Arcturus spectra, GALAH line-list entries, telluric absorption, and sky-emission measurements.

<table>
  <tr>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_7845.31.png"
        alt="Diagnostic plot of the residual region near 7845.31 angstrom, classified as a candidate transition whose logarithmic oscillator strength is too high. The observed absorption is systematically shallower than the spectral synthesis."
        width="100%"
      />
      <br><strong>A. log(gf) too high</strong>
    </td>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_7799.96.png"
        alt="Diagnostic plot of the residual region near 7799.96 angstrom, classified as a candidate transition whose logarithmic oscillator strength is too low. The observed absorption is systematically deeper than the spectral synthesis."
        width="100%"
      />
      <br><strong>B. log(gf) too low</strong>
    </td>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_5700.27.png"
        alt="Diagnostic plot of the residual region near 5700.27 angstrom, classified as a line-profile mismatch because the synthesis does not reproduce the detailed shape of the observed absorption feature."
        width="100%"
      />
      <br><strong>C. Line profile</strong>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_6651.02.png"
        alt="Diagnostic plot of the residual region near 6651.02 angstrom, classified as insignificant because the apparent mismatch is dominated by weak or broad background residual structure."
        width="100%"
      />
      <br><strong>D. Insignificant</strong>
    </td>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_7853.25.png"
        alt="Diagnostic plot of the residual region near 7853.25 angstrom, classified as a skyline residual through comparison with measured night-sky emission."
        width="100%"
      />
      <br><strong>E. Skyline</strong>
    </td>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_5779.64.png"
        alt="Diagnostic plot of the residual region near 5779.64 angstrom, classified as interstellar absorption because its wavelength, width, and behaviour are consistent with absorption by material between the star and the observer."
        width="100%"
      />
      <br><strong>F. Interstellar</strong>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_4831.41.png"
        alt="Diagnostic plot of the residual region near 4831.41 angstrom, classified as an unknown stellar line because the feature appears to be real but no satisfactory atomic identification is available."
        width="100%"
      />
      <br><strong>G. Unknown line</strong>
    </td>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_5714.17.png"
        alt="Diagnostic plot of the residual region near 5714.17 angstrom, classified as a known missing feature because a plausible transition is present in external line information but absent from the spectral synthesis."
        width="100%"
      />
      <br><strong>H. Known missing</strong>
    </td>
    <td width="33%" valign="top">
      <img
        src="residual_inspection/residual_region_4799.85.png"
        alt="Diagnostic plot of the residual region near 4799.85 angstrom, classified as unclear because the available stellar, atomic, interstellar, telluric, and sky-emission diagnostics do not support a unique interpretation."
        width="100%"
      />
      <br><strong>I. Unclear</strong>
    </td>
  </tr>
</table>

The complete set of diagnostic plots is available in [`residual_inspection/`](residual_inspection/).

### 4. Residual spectra retain information

We trained a quadratic model with **The Cannon** to test whether the residual spectra still contain information about the stellar labels used to construct the original synthesis.

All results were evaluated using five-fold cross-validation: each model was trained on 80% of the spectra and evaluated on the remaining 20%, such that every spectrum was evaluated out of sample exactly once.

<p align="center">
  <img
    src="figures/recovery_model1_teff_kfold.png"
    alt="Cross-validated recovery of effective temperature from residual spectra. The inferred temperature difference is shown against the GALAH reference effective temperature for 7087 spectra."
    width="32%"
  />
  <img
    src="figures/recovery_model1_logg_kfold.png"
    alt="Cross-validated recovery of surface gravity from residual spectra. The inferred surface-gravity difference is shown against the GALAH reference surface gravity."
    width="32%"
  />
  <img
    src="figures/recovery_model1_fe_h_kfold.png"
    alt="Cross-validated recovery of metallicity from residual spectra. The inferred metallicity difference is shown against the GALAH reference iron abundance."
    width="32%"
  />
</p>

The complete residual spectrum recovers:

| Stellar label         | Out-of-sample recovery scale | Label spread in the sample |
| --------------------- | ---------------------------: | -------------------------: |
| Effective temperature |                        150 K |                      660 K |
| Surface gravity       |                     0.19 dex |                   0.94 dex |
| Metallicity           |                    0.086 dex |                  0.286 dex |

The residuals also retain information about individual elemental abundances and interstellar extinction. The current activity model identifies genuine activity-sensitive features, particularly Hα and Hβ, but does not yet recover the activity indicator robustly out of sample.


<img
src="figures/cannon_linear_coefficients_joint_kfold.png"
alt="Relevant linear coefficients of the different Cannon models."
width="100%"
/>

### 5. The excluded pixels contain disproportionately strong information

GALAH excluded 793 wavelength pixels from its final stellar-label optimisation because these regions were considered less reliable or more strongly affected by model–data disagreement.

Although these pixels account for only approximately 6% of the available spectrum, they recover almost as much stellar-parameter information as the complete residual spectrum. They also outperform the remaining 13,134 optimisation pixels for all three global stellar labels.

<table>
  <thead>
    <tr>
      <th>Label</th>
      <th>793 pixels excluded from the optimisation</th>
      <th>13,134 pixels included in the optimisation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Effective temperature</td>
      <td>
        <img
          src="figures/recovery_model5_teff_kfold.png"
          alt="Cross-validated effective-temperature recovery using only the 793 wavelength pixels excluded from the GALAH optimisation."
          width="100%"
        />
      </td>
      <td>
        <img
          src="figures/recovery_model6_teff_kfold.png"
          alt="Cross-validated effective-temperature recovery using the 13,134 wavelength pixels included in the GALAH optimisation."
          width="100%"
        />
      </td>
    </tr>
    <tr>
      <td>Surface gravity</td>
      <td>
        <img
          src="figures/recovery_model5_logg_kfold.png"
          alt="Cross-validated surface-gravity recovery using only the 793 wavelength pixels excluded from the GALAH optimisation."
          width="100%"
        />
      </td>
      <td>
        <img
          src="figures/recovery_model6_logg_kfold.png"
          alt="Cross-validated surface-gravity recovery using the 13,134 wavelength pixels included in the GALAH optimisation."
          width="100%"
        />
      </td>
    </tr>
    <tr>
      <td>Metallicity</td>
      <td>
        <img
          src="figures/recovery_model5_fe_h_kfold.png"
          alt="Cross-validated metallicity recovery using only the 793 wavelength pixels excluded from the GALAH optimisation."
          width="100%"
        />
      </td>
      <td>
        <img
          src="figures/recovery_model6_fe_h_kfold.png"
          alt="Cross-validated metallicity recovery using the 13,134 wavelength pixels included in the GALAH optimisation."
          width="100%"
        />
      </td>
    </tr>
  </tbody>
</table>

The corresponding recovery scales are:

| Stellar label         | Complete spectrum | Excluded pixels | Optimisation pixels |
| --------------------- | ----------------: | --------------: | ------------------: |
| Effective temperature |             150 K |           160 K |               190 K |
| Surface gravity       |          0.19 dex |        0.22 dex |            0.22 dex |
| Metallicity           |         0.086 dex |       0.095 dex |            0.12 dex |

The excluded-pixel model uses approximately 17 times fewer pixels than the optimisation-pixel model. The number of pixels is therefore not a useful proxy for the information remaining in a residual spectrum.

## Repository contents

| Path                                                                 | Description                                                                                                                                                       |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`data/peak_inspection_table.fits`](data/peak_inspection_table.fits) | Machine-readable catalogue of the 380 residual regions, including measurements, classifications, possible identifications, and inspection comments.               |
| [`residual_inspection/`](residual_inspection/)                       | Individual diagnostic figures for all residual regions.                                                                                                           |
| [`figures/`](figures/)                                               | Main paper figures and supplementary recovery and coefficient plots.                                                                                              |
| Analysis scripts and notebooks                                       | Code used to calculate residual statistics, identify recurrent regions, train and evaluate the residual models, inspect possible causes, and produce the figures. |
| Manuscript source                                                    | LaTeX source and supporting files for the paper submitted to *The Open Journal of Astrophysics*.                                                                  |

## Data products

The principal data product is:

```text
data/peak_inspection_table.fits
```

This table contains the full residual-region catalogue. It is intended to support:

* investigations of missing or inaccurate atomic data;
* comparisons with alternative spectral-synthesis pipelines;
* searches for unidentified stellar absorption features;
* studies of interstellar absorption;
* identification of telluric, sky, and reduction residuals;
* prioritisation of wavelength regions for future improvements to spectral models.

The classifications should be treated as informed plausibility assessments. Users interested in an individual region should consult both the table comments and the corresponding diagnostic plot in `residual_inspection/`.

We further provide all models of **The Cannon** within `models/`.

## Citation

The paper is currently in preparation. Please use the following placeholder until the final journal citation and DOI are available:

```bibtex
@ARTICLE{Buder2026ResidualCannon,
    author        = {{Buder}, Sven and
                     {R{\'o}{\.z}{\'a}{\'n}ski}, Tomasz and
                     {Hogg}, David W.},
    title         = "{Reading Between the Lines: How Much Information Remains After Fitting a Stellar Spectrum?}",
    journal       = {The Open Journal of Astrophysics},
    year          = {2026},
    volume        = {TBD},
    number        = {TBD},
    pages         = {TBD},
    doi           = {TBD},
    eprint        = {TBD},
    archivePrefix = {arXiv},
    primaryClass  = {astro-ph.SR}
}

```
