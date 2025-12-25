# Chord Engine using Linear Algebra  
### A Vector-Space and Operator-Theoretic Framework for Music Generation (12-TET)

## Abstract
This project presents a mathematically grounded framework for modeling musical harmony using concepts from linear algebra. Musical notes, chords, and harmonic progressions are represented as vectors and linear operators in a finite-dimensional vector space. By encoding pitch classes as basis vectors in ℝ¹², chord construction, transposition, and harmonic variation are expressed entirely through matrix operations. Audio synthesis is treated as a final linear transformation that maps abstract musical structures into physical frequencies.

The work demonstrates how algebraic abstractions—vector spaces, linear transformations, and matrix operators—can be used to construct a complete, extensible music generation system without symbolic rules or stored musical templates.

---

## Motivation
Music theory is traditionally expressed through symbolic notation or heuristic rules. This project explores whether musical structure can instead be derived purely from algebraic principles, analogous to how physical systems are modeled using linear operators.

The motivation arose from studying:
- Basis and coordinate representations
- Linear transformations and operator composition
- Subspaces and direct sums

Central question:
Can musical harmony and progression be generated entirely through linear algebraic operations?

---

## Core Mathematical Idea
All musical computation is performed in the vector space ℝ¹², where each dimension corresponds to one pitch class in Western equal temperament.

The system is built on three principles:
1. Pitch classes as basis vectors  
2. Chords as linear operators  
3. Transposition as cyclic matrix transformations  

This separation allows musical logic to be computed independently of sound synthesis.

---

## Mathematical Formulation

### Pitch-Class Representation
Each pitch class is represented as a canonical basis vector {e₀, e₁, …, e₁₁} ⊂ ℝ¹².

A chord is represented as:
c = ∑ᵢ∈K eᵢ  
where K is the set of pitch-class indices.

---

### Transposition via Shift Operators
Transposition is implemented using a cyclic shift matrix S ∈ ℝ¹²×¹²:
S eₖ = e₍ₖ₊₁₎ mod 12

Transposing by m semitones corresponds to applying Sᵐ.  
This operator acts uniformly on notes, chords, and scales.

---

### Chord Operators
Chord qualities are encoded as linear operators constructed from powers of the shift matrix:
M_chord = ∑ₖ∈K Sᵏ

Examples:
- Major triad: I + S⁴ + S⁷  
- Minor triad: I + S³ + S⁷  
- Major seventh: I + S⁴ + S⁷ + S¹¹  

Applying the operator to a root note generates the chord:
c = M_chord e_root

This formulation avoids storing musical rules and derives harmony algebraically.

---

## Frequency Mapping and Sound Synthesis
Chord vectors represent abstract pitch identities. To generate sound, a diagonal octave transformation matrix is applied:
f = T_oct c

Frequencies follow the 12-TET equal temperament relation:
fᵢ = f₀ · 2^(i/12)

Audio is synthesized using additive sinusoidal synthesis with harmonic overtones, approximating piano-like timbre. Temporal duration is encoded mathematically using BPM-based beat scaling.

---

## System Pipeline
1. Encode pitch classes as vectors in ℝ¹²  
2. Construct chord operators using shift matrices  
3. Apply operators to generate chord vectors  
4. Map vectors to frequencies via octave transformation  
5. Synthesize audio signals  
6. Control timing using beat-duration scaling  

All harmonic structure is computed before sound generation.

---

## Implementation
- Language: Python  
- Libraries: NumPy, Pandas, sounddevice, soundfile  
- Design: Modular, operator-based, extensible  

New chord types can be added by specifying interval sets, without modifying the core algebraic framework.

---

## Demonstration
The system generates and plays complete chord progressions (including popular song progressions) using only matrix operations. Transpositions, chord qualities, and timing are handled through linear transformations.

---

## Results
- Musical harmony fully represented using linear algebra  
- Uniform operator-driven chord transposition  
- No symbolic music rules or lookup tables  
- Mathematically interpretable and extensible framework  

---

## Research Relevance
This project demonstrates:
- Abstract representation learning in structured domains  
- Operator-based system design  
- Separation of symbolic structure from physical realization  
- Applicability of linear algebra to generative systems  

Relevant research areas include:
- Structured representation learning  
- Algorithmic music generation  
- Mathematical modeling of creative systems  
- Interpretable generative pipelines  

---

## Repository Structure
├── chord_engine.py        # Core linear algebra engine  
├── synthesis.py           # Frequency mapping and synthesis  
├── examples.ipynb         # Demonstrations  
├── report.pdf             # Mathematical documentation  
└── README.md  

---

## Academic Context
Course: Applied Linear Algebra (EE 635)  
Institution: Indian Institute of Technology Bombay  
Instructor: Prof. Debasattam Pal  
Academic Year: 2024–2025  

---

## Authors
Rishi Raj Vishwakarma  
Adithi Roy Chowdhury  

---

## Future Directions
- Scale-constrained harmonic subspaces  
- Voice-leading optimization via projections  
- Graph-based harmonic transitions  
- Integration with learning-based progression models  

---

## Disclaimer
Academic and research use only.
