# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 3 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 3 bit counter, which simply means it can count from 0 to 7 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

3-bit “Up” Counter
![Screenshot 2023-12-30 140044](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/f31de471-176d-4fad-9a5f-eb47ce28176c)




## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![Screenshot 2023-12-30 140114](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/4373360c-12eb-44e5-8aff-bcbac566d0e0)


3-bit Count Down Counter

### Procedure

1.Create a new project in Quartus II software. 2.Name the project as uc for upcounter and dc for downcounter. 3.Create a new Verilog HDL file in the project file. 4.Name the module as dc and uc for downcounter and upcounter. 5.Within the module declare input and output variables. 6.Complete the program. 7.End the module.




### PROGRAM 

Program for flipflops  and verify its truth table in quartus using Verilog programming.

Developed by: keerthivasan M

RegisterNumber: 23014067


### UP COUNTER 
```
module uc(clk, A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

A[2]=(((A[0])&(A[1]))^A[2]);

A[1]=(A[0])^A[1];

A[0]=A[0]^1;

end

endmodule
```
### DOWN COUNTER 
```
module dc(clk,A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

A[2]=(((~A[0])&(~A[1]))^A[2]);

A[1]=(~A[0])^A[1];

A[0]=1^A[0];

end
endmodule
```




### RTL LOGIC UP COUNTER AND DOWN COUNTER  

###  UP COUNTER 

![Screenshot 2023-12-30 134513](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/2e121c90-c3af-4d3d-a506-74252b523f15)

###  DOWN COUNTER 
![Screenshot 2023-12-30 134520](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/e697b481-17c7-4fc4-90d9-960cb05839d5)



### TIMING DIGRAMS FOR COUNTER  
###  UP COUNTER 

![Screenshot 2023-12-30 134529](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/57ad141a-7891-4748-a482-9831f7eae68c)

###  DOWN COUNTER 

![Screenshot 2023-12-30 134535](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/bd6dc290-9616-44a7-acdd-352582e10389)


### TRUTH TABLE 
###  UP COUNTER 
![Screenshot 2023-12-30 134541](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/a558ef78-f59f-4317-8c98-283b5142ee92)

###  DOWN COUNTER 

![Screenshot 2023-12-30 134547](https://github.com/rdxkeerthi/Exp-7-Synchornous-counters-/assets/147473120/3895f438-32e2-442c-97ed-9358e5fc4ce1)



### RESULTS 
Thus, the flipflops are implemented using verilog.
