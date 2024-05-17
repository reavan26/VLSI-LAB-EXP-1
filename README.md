# VLSI-LAB-EXPERIMENTS
# AIM: 
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

# APPARATUS REQUIRED: 
Xilinx 14.7 Spartan6 FPGA

# PROCEDURE: 
```
STEP:1 Start the Xilinx navigator, Select and Name the New project.
STEP:2 Select the device family, device, package and speed.
STEP:3 Select new source in the New Project and select Verilog Module as the Source type.
STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.
STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.
STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.
```
# Logic Diagram :

# Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


# Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


# Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


# Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



# Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



# 8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



# VERILOG CODE:

# Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# Full Adder:
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
# 4 bit ripple carry adder:

```

module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# 8 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# OUTPUT:
# OR gate:
![WhatsApp Image 2024-04-21 at 13 39 05_602e02fb](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/0e72fbe9-3246-44d6-8c85-5500e0d6a0fe)
# NOT gate:
![WhatsApp Image 2024-04-21 at 13 40 29_6cca89b4](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/ee475c7b-6659-4d03-ba47-8984b688a019)
# AND gate:
![WhatsApp Image 2024-04-21 at 13 40 36_bbf2b484](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/1d6d52f3-4a7d-4c28-9cdc-e89c31ed17bc)
# NAND gate:
![WhatsApp Image 2024-04-21 at 13 40 41_7e378833](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/705ce7bc-cdd3-4ed8-baa5-eb6662e43f99)
# NOR gate:
![WhatsApp Image 2024-04-21 at 13 40 47_71a83e97](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/c4a42f93-7ca5-46b6-8a42-57c598df0422)
# XNOR gate:
![WhatsApp Image 2024-04-21 at 13 41 06_9b48dab9](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/7cf7885e-f89d-4e91-8f9d-45be348ce743)
# XOR gate:
![WhatsApp Image 2024-04-21 at 13 41 18_ad5104f0](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/5921a388-d7ce-400a-baf4-28ce4b3297ab)
# Half Adder:
![WhatsApp Image 2024-04-21 at 13 41 28_cb02aad5](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/34aa5744-64d4-4062-ace1-0891c5be073c)
# Half Subtracter:
![WhatsApp Image 2024-04-21 at 13 41 34_d03e774c](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/db8953fe-8446-4ab2-b38c-63a6062dce04)
# Full Adder:
![WhatsApp Image 2024-04-21 at 13 41 41_3337770e](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/ed94728f-61c0-4188-afa5-c2a7397ec00f)
# Full Subtracter:
![WhatsApp Image 2024-04-21 at 13 41 48_ccb70f23](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/36f91c43-1c0e-4998-a468-f881566666ec)
# 4 Bit Ripple Carry Adder:
![WhatsApp Image 2024-04-21 at 13 41 54_d7d1f7e6](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/3af5f3e3-f485-4f0e-90b3-ff25a8c1b27f)
# 8 Bit Ripple Carry Adder:
![WhatsApp Image 2024-04-21 at 13 42 02_aa1fae83](https://github.com/Afsar1276/VLSI-LAB-EXP-1/assets/161407741/fbc4ac1a-cb3f-4265-965d-1530492919a3)

# RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.
