# PLL-IC-Design-Using-Open-Source-PDKs
Phase-Locked Loop IC design on Open-Source Google-Skywater 130nm node

## **This repository is still under construction**

![VSD Poster](https://user-images.githubusercontent.com/65411629/127780909-65694659-8320-45c2-80d2-4019e8a330df.png)

This two day tapeout workshop on **Phase-Locked Loop (PLL) IC design using Open-Source Google-Skywater 130nm node** involved designing a simple PLL using Open-Source tools. 

The labs covered the entire IC design flow from circuit design until tapeout using Open-Source 130nm Process Design Kits (PDKs) by Google-Skywater and the latest Caravel Framework by efabless. The spice simulations were done using the [ngspice](http://ngspice.sourceforge.net/) Open-Source EDA. The Layout design and parasitic extraction were done using the [Magic](http://opencircuitdesign.com/) EDA tool.


## Contents:
1. [Introduction to PLL](#introduction-to-pll)
2. [Purpose of PLL](#purpose-of-pll)
3. Components of PLL
4. Design Flow
5. Open Source Tools Used and Setup
6. PLL Circuit Specification
7. PreLayout Simulation
8. Troubleshooting Steps
9. Layout Design
10. Parasitic Extraction
11. PostLayout Simulation 
12. TapeOut
13. References
14. Acknowledgement



## Introduction to PLL
A phase-locked loop or PLL is a control system that generates an output signal whose phase is related to its input. It basically mimics its reference signal i.e. the output signal of PLL have the same or a multiple of the reference frequency and a constant phase difference with it.

![841f1c2b94c7d86da857fe8e872f6118](https://user-images.githubusercontent.com/46085827/143921549-72e1d68f-b2f8-4d19-bba0-f536e3cd3db1.png)

## Purpose of PLL
On-Chip oscillators such as ring oscillators are combination of odd number of inverters which has a certain delay. It provides  
> output clock signal of frequency = 1/(2*n*d)


Where n is the (odd) number of inverters in the ring and d is the delay of each inverter. However such a clock signal has too much phase noise or jitter and is almost unusable for high speed synchronous digital design.

On the other hand, crystal oscillators have extemely high spectral purity i.e., low phase noise. It has a superior phase noise performance as the output has no unwanted frequency.  But the application of these are not flexible as these generate a specific set of frequencies. 

However, we would like to be able to generate a clock signal of arbitrary frequency but with a spectral purity comparable to that of a crystal oscillator. The PLL comes in this context. 

The PLL is essentially a feedback control system which dynamically adjusts the phase of the on-chip oscillator (typically a voltage controlled ring oscillator) by comparing its output with a reference signal typically the crystal oscillator.
