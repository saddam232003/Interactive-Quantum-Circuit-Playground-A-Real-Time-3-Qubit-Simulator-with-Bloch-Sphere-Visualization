Copy the entire text below and save it as **README.md** in your repository. It will render correctly on GitHub with proper formatting (headings, lists, bold, etc.).

---

# Interactive Quantum Circuit Playground – 3 Qubits

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey)

**A professional, real‑time quantum circuit simulator with live Bloch spheres, measurement probabilities, and a clickable gate interface – all in pure Python.**

Designed & developed by **Dr. Muhammad Saddam Khokhar** – [Quantummind.AI](https://quantummind.ai)

---

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Installation](#installation)
- [Usage](#usage)
- [Interface Guide](#interface-guide)
- [How It Works (Brief)](#how-it-works-brief)
- [Customisation](#customisation)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)
- [Author & Contact](#author--contact)

---

## Overview
This repository contains an **interactive 3‑qubit quantum circuit playground** that lets you build quantum circuits by clicking buttons and instantly observe the resulting quantum state.

- **3 live Bloch spheres** – each qubit’s state is shown as a vector on its own Bloch sphere. When a qubit becomes entangled, its Bloch vector shrinks, giving an intuitive visualisation of entanglement.
- **Measurement probability chart** – a bar graph of the probabilities for all 8 computational basis states (`|000⟩` to `|111⟩`).
- **Full gate set** – X, Y, Z, H, S, T, Rx(π/2), Ry(π/2), CNOT, CZ, and Reset.
- **Professional dark‑theme GUI** – clean, non‑overlapping layout with a dedicated control panel.

The simulation is **exact** (state‑vector evolution) and runs entirely on classical hardware – no external quantum frameworks required.

---

## Key Features
- ✅ **Real‑time interaction** – one click, instant visual update
- ✅ **Bloch spheres from reduced density matrices** – see entanglement as vector shrinkage
- ✅ **Exact 8‑dimensional state‑vector simulation** – no approximations
- ✅ **Easy‑to‑use radio button qubit selector**
- ✅ **Gate grid with clear labelling**
- ✅ **On‑screen instructions**
- ✅ **Fully reproducible, pure Python implementation**

---

## Installation

### Prerequisites
- Python 3.8 or higher
- `pip` package manager

### Clone the repository
```
git clone https://github.com/saddam232003/Variational-Quantum-Eigensolver-VQE-for-the-MaxCut-problem.git
cd Variational-Quantum-Eigensolver-VQE-for-the-MaxCut-problem
```
*(The playground script is located in the same repository; look for the file `interactive_quantum_playground.py` or the code snippet in the main directory.)*

### Install dependencies
```
pip install numpy matplotlib
```
*(SciPy is not required – only `numpy` and `matplotlib` are needed.)*

---

## Usage
Run the script directly:
```
python interactive_quantum_playground.py
```
A window will open displaying the interactive playground. No further configuration is needed.

### Quick Start
1. **Select an active qubit** using the radio buttons on the right (“Qubit 0”, “Qubit 1”, or “Qubit 2”).
2. **Click a gate button** – the Bloch sphere for that qubit rotates and the probability bars update immediately.
3. **Try a Bell state**:
   - Select **Qubit 0**, press **H** (Hadamard).
   - With **Qubit 0** still active, press **CNOT**.  
     → Both Qubit 0 and Qubit 1 Bloch vectors shrink to zero (entanglement), and the probability bars show 50% `000` and 50% `011` (or similar – check the exact labels).
4. **Reset** to `|000⟩` at any time by clicking the **Reset** button.

---

## Interface Guide
The GUI is divided into three main areas:

### 1. Bloch Sphere Panels (top left)
Three 3D spheres, one for each qubit.  
- The gold arrow shows the qubit’s reduced state.  
- If the arrow points to the surface, the qubit is in a **pure state**.  
- If the arrow shrinks toward the centre, the qubit is **entangled** with other qubits.

### 2. Probability Chart (bottom left)
A horizontal bar chart showing the probability of measuring each of the 8 computational basis states (`|000⟩` to `|111⟩`).  
- The bars update instantly after every gate.

### 3. Control Panel (right side)
- **Active Qubit selector** – three radio buttons to choose which qubit receives single‑qubit gates or acts as the **control** for two‑qubit gates.
- **Gate buttons** – a grid of all available gates:
  - **Single‑qubit**: `X`, `Y`, `Z`, `H`, `S`, `T`, `Rx(π/2)`, `Ry(π/2)`
  - **Two‑qubit**: `CNOT` and `CZ` (control = active qubit, target = next qubit modulo 3)
  - **Reset** – restores the system to `|000⟩`
- **Hints** – brief instructions at the bottom of the control panel.

---

## How It Works (Brief)
The simulator maintains the complex state vector of the 3‑qubit system (dimension 8).  
- When a gate button is clicked, the corresponding unitary matrix is constructed and applied to the state vector.
- Single‑qubit gates are extended to the full 8×8 Hilbert space using Kronecker products.
- Two‑qubit gates (CNOT, CZ) are applied by explicitly computing the 8×8 matrix elements for the chosen control‑target pair.
- After each operation, the reduced density matrix of each qubit is obtained by tracing out the other qubits, and the Bloch vector is extracted via Pauli matrix expectations.
- The measurement probabilities are simply the absolute squares of the state vector amplitudes.

All calculations are exact (no noise, no sampling) and performed in real‑time.

---

## Customisation
You can easily modify the playground to suit your needs:
- **Number of qubits**: Change the `n_qubits` parameter in the `QuantumState` constructor (be aware that the state vector size grows as 2^n).
- **Gate set**: Add new gates (e.g., arbitrary rotation angles) by extending the `apply_gate` function and adding buttons.
- **Entanglement topology**: Modify the target selection logic for CNOT/CZ (currently `(active_qubit + 1) % 3`).
- **Visual style**: The colour theme is defined in the variables `BG_MAIN`, `CYAN`, etc. – change them for a different look.

---

## Dependencies

| Package     | Version (tested) | Purpose          |
|-------------|------------------|------------------|
| `numpy`     | ≥1.21            | State‑vector arithmetic |
| `matplotlib`| ≥3.5             | GUI, 3D plotting, widgets |

No other libraries are required.

---

## Contributing
Contributions are welcome! Possible improvements:
- Add slider‑controlled rotation angles.
- Implement a circuit recording/playback feature.
- Extend to more qubits using sparse or tensor‑network representations.
- Include basic noise models.

Please open an issue or pull request on GitHub.

---

## License
This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.  
You are free to use, modify, and distribute this code for any purpose, provided you retain the original copyright notice.

---

## Author & Contact
**Dr. Muhammad Saddam Khokhar**  
Founder & Lead Researcher – [Quantummind.AI](https://quantummind.ai)  

📧 saddam_khokhar@hotmail.com  

If you use this code in your research or teaching, please cite or acknowledge the author and repository.  
For commercial or collaboration inquiries, reach out via email.

---

*Built with passion for quantum computing and clean visualisation.*
