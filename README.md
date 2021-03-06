# Mixed-signal-RISC-V-based-SoC-on-FPGA

This Repository
The material and code created during the Mixed-signal RISC-V based SoC on FPGA are housed in this repository. 
The basics of FPGA was researched and a rudimentary . In addition to the iverilog, the RISC-V CPU Core was implemeted on FPGA using xilinx vivado. 

**1. Introduction to FPGA IPs**

**2. Mixed-Signal SoC details with RISC-V core and PLL IPs**

**3. Mixed-Signal FPGA flow**
 
 ## Tools
**Icarus Verilog:**

Icarus Verilog is a Verilog simulation and synthesis tool. Icarus Verilog is an implementation of the Verilog hardware description language. It supports the 1995, 2001 and 2005 versions of the standard, portions of SystemVerilog, and some extensions.

**GTKWave:**

GTKWave is a waveform viewer.

**Xilinx Vivado:**

Vivado Design Suite is a software suite produced by Xilinx for synthesis and analysis of hardware description language designs, superseding Xilinx ISE with additional features for system on a chip development and high-level synthesis. Vivado represents a ground-up rewrite and re-thinking of the entire design flow. also provides complete SoC-strength, IP-centric and system-centric, next generation development environment. Currently, this project is done using Vivado HL Design Edition 2018.3.


## Icarus verilog Simulation
Here we have used Sandpiper-saas to convert TL-Verilog code to Verilog Format.

> sandpiper-saas -i rvmyth.tlv -o rvmyth.v --iArgs

![Screenshot (970)](https://user-images.githubusercontent.com/67407412/170999226-36df40cd-7020-4a11-b94b-c0efe8ace5ff.png)

We used Icarus verilog for simulation of RVMYTH and PLL, the waveform is viewed in GTKWave Viewer.

> iverilog rvmyth_pll_tb.v rvmyth_pll.v clk_gate.v

> ./a.out

> gtkwave rvmyth_pll.vcd

![Output_in_iverilog](https://user-images.githubusercontent.com/67407412/171000547-9feaf788-9b71-4284-953a-763c227b08a5.png)

Analog Waveform

![Analog waveform in iverilog](https://user-images.githubusercontent.com/67407412/171039379-c27465ef-8434-4b48-9455-08530c0eedaa.png)


## FPGA Implementation

### Steps

1. Add rvmyth.v, clk_gate.v, top_soc.v to the design.
2. Now generate the PLL and TLA IP's from xilinx IP catalog.
3. Add the testbench as simulation source.
4. Nowe run the behavioral simulation and verify the functionality.
5. For synthesis ,add the constraints file as contriant source.
6. Run synthesis and later go with the implementation.
7. Now check for setup and hold violations of any and later generate the bitstream and program the FPGA.

Block Diagram

![Implementation in Xilinx Vivado](https://user-images.githubusercontent.com/67407412/171003616-e7fca261-42a1-439a-9209-4576a76acbaa.jpg)

Implementation in Xilinx Vivado. Here the Main Clock having 30ns time period and the core clock is having 10ns time period.

![Screenshot (976)](https://user-images.githubusercontent.com/67407412/171004296-f074f4c9-72f9-422e-9f2e-f05bc9063eaa.png)

![Analog waveform in vivado](https://user-images.githubusercontent.com/67407412/171098237-ee21b982-5b41-4dfa-987f-2e2811f8ef1e.png)


![Screenshot (983)](https://user-images.githubusercontent.com/67407412/171048271-f5101318-bb87-4c26-9790-ccbb1dea0588.png)

Design Rules

![Design rules](https://user-images.githubusercontent.com/67407412/171039639-e689af71-b632-4900-bead-7bdd3edde386.jpg)

Design Timing Summary

![Screenshot (978)](https://user-images.githubusercontent.com/67407412/171005267-1c2378f7-5df9-4e1d-b132-627cdf737afd.png)



