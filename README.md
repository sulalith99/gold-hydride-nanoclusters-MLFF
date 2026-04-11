# gold-hydride-nanoclusters-MLFF
Machine learning force field for gold hydride nanoclusters 

## Repository Structure

```
.
├── Initial-Optimized-Geometries/
├── Training/
└── Testing/
```

> ⚠️ **Note:** The trained MLFF model (`MLFF-OTC-4-Model/`) is archived on OSF: **<a href="https://osf.io/58emp/overview?view_only=8a98b807cf5742a1a25b44badea07e1a" target="_blank">OSF Repository</a>** **[OSF Repository](https://osf.io/58emp/overview?view_only=8a98b807cf5742a1a25b44badea07e1a)**

### `Initial-Optimized-Geometries/`
ADF optimization input files and optimized structures for all gold-hydride nanoclusters.

### `Training/`
All files related to the MLFF training process, organized into three subdirectories:

- **`Starting-Files-For-OTF/`** – Initial files for on-the-fly (active learning) training, including `POSCAR` files (initial geometries) and `otf_train.yaml` (FLARE++ configuration file).
- **`Starting-Files-For-OTC/`** – Initial files for offline (passive learning) training, including `offline.yaml` (FLARE++ input) and `all_otf_dft.xyz` (training databases with geometries and labels) for each training cycle.
- **`Databases/`** – Individual training databases used or generated during each training cycle.

### `Testing/`
All files related to testing procedures, organized into two subdirectories:

- **`LAMMPS-Testing/`** – Input files for MLFF-based MD simulations, including `lammps.in` (LAMMPS input script) and initial structure files.

  > ⚠️ **Note:** LAMMPS simulations require the three MLFF model files (`lmp.flare`, `L_inv_lmp.flare`, `sparse_desc_lmp.flare`) to be present in the same directory.

  Representative output files are also included:
  - `log.lammps` – MLFF-predicted energies at each timestep
  - `output.dump` – Trajectory coordinates (visualizable with [OVITO](https://www.ovito.org/))

- **`VASP-Testing/`** – DFT calculation inputs including `INCAR`, `KPOINTS`, and `POTCAR` files. To run VASP calculations on trajectory snapshots, `POSCAR` files must be extracted from the LAMMPS `output.dump` files.

---

## Reproducibility

These materials ensure full reproducibility of our results and provide a computational framework adaptable to other ligand-protected metal nanocluster systems.
