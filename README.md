# Long-Range Metal Detector & Ground Penetrating Radar

BS Electrical Engineering final-year thesis, **Information Technology University (ITU), Lahore, Pakistan** — July 2017.

📄 **[Read the full thesis (PDF)](Metal%20Detector%20Final%20Thesis.pdf)**

## Authors

- Hamza Khalid
- Tawahaa Ahmed
- Ahsan Ejaz

**Advisor:** Dr. Tauseef Tauqeer  
**Co-Advisor:** Dr. Mahboob-ur-Rehman  
Department of Electrical Engineering, Information Technology University

## Overview

Conventional metal detectors (walk-through gates, handheld wands) work by magnetic induction and only reach from a few centimetres to about 1.5 m. This project aimed to build a low-cost, locally made system for developing countries that detects concealed metal from much further away. Two use cases were targeted:

1. **Free-space metal detection.** Spotting concealed metal, such as a suicide vest or a weapon, from a distance of several metres.
2. **Ground Penetrating Radar (GPR).** Detecting buried metal (mines, pipes, wiring) by changing the operating frequency.

The system transmits an RF signal through a highly directive horn antenna and measures how strongly it reflects back. Metal reflects much more strongly than other materials, so a calibrated amplitude threshold on the received signal separates metallic objects from non-metallic ones.

## System Design

| Component | Details |
|---|---|
| Radios | 2 × National Instruments **USRP-2901** software-defined radios (half-duplex: one TX, one RX, separated so the receiver is protected from the 20 dBm transmit power) |
| Software | **NI LabVIEW 2014**: transmitter VI (sine-wave generation) and receiver VI (FFT, peak detection, amplitude thresholding via MathScript) |
| Antennas | 2 × pyramidal **horn antennas**, designed by the team and fabricated locally |
| Antenna design tools | **MATLAB** for the horn dimension calculations (Balanis design equations) and **Ansoft HFSS** for simulation |

### Horn Antenna

- Centre frequency: **2.1 GHz**
- Built on a standard **WR430** waveguide (1.7–2.6 GHz)
- Coaxial probe feed: placed λg/4 ≈ 2.97 cm from the back wall, with a probe height of λ₀/4 ≈ 3.55 cm
- Measured on a VNA: usable bandwidth (S11 < −10 dB) of **1.9–2.4 GHz**, with S11 reaching about **−50 dB at 2.09 GHz**. This closely matched the HFSS simulation.

## Results

- **Free space:** After calibration for its environment, the system told metal (an aluminium sheet was the reference) apart from a human body, a wooden board, books and phones. Tests were run at under 2 ft, 4 ft, 10 ft and 20 ft. It also told a person wearing a mock "suicide vest" (a metal sheet inside clothing) apart from a person without one.
- **GPR:** In both dry and wet soil, buried objects (metal plate, iron spanner, transformer core) raised the reflected FFT magnitude by amounts that could be told apart.
- **Limitations:**
  - Thresholds have to be recalibrated in each new environment.
  - Fast-moving objects cause false positives through the Doppler effect.
  - A non-metal very close to the antenna (10–20 cm) can look the same as metal far away (≥10 ft).
  - Uncalibrated SDR hardware limited accuracy overall.

## Future Work

- Use calibrated SDR hardware so both the magnitude **and phase** of reflections can be measured accurately.
- Give the GPR wider-band, high-directivity antennas.
- Develop the proof of concept into a deployable product.

## Thesis Contents

1. Introduction
2. Literature Review
3. Working
4. Antenna Design (MATLAB calculations, probe feeding, HFSS design)
5. Metal Detection in Free Space (setup, LabVIEW transmitter/receiver)
6. Ground Penetrating Radar
7. Results and Analysis
8. Conclusion
9. Recommendations
10. References

## Copyright

Copyright © 2017 Hamza Khalid, Tawahaa Ahmed, Ahsan Ejaz. All rights reserved.
