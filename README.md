Download Link: https://assignmentchef.com/product/solved-ve270-assignment-5-design-of-a-digital-clock
<br>
<ul>

 <li>To get familiarized with binary counters.</li>

 <li>To design a clock divider that slows down the frequency of a clock signal.</li>

 <li>To design a two-digit timer that counts the number of seconds from 00 to 59, and repeats.</li>

 <li>To display the two digits using the seven-segment displays on the FPGA board.</li>

 <li>. Requirement</li>

</ul>




Design a digital clock following the block diagram in Figure 1.

<strong>Figure 1.  Block Diagram of the Digital Clock </strong>

<h3>2.1 Clock Divider</h3>

The frequency of internal clock on the FPGA board that we are using is 100MHz. However, the digital clock should be triggered by a signal with 1Hz frequency. This means the on-board clock should be divided by 100,000,000 times. Design a clock divider to slow down the on-board clock signal to 1Hz.




<h3>2.2 Two Digit Timer</h3>

The digital clock counts the number of seconds with counting sequence: <strong><em> </em></strong>

00 à 01 à 02 à … à 09 à 10 à 11 à … à 59 à 00

One way to approach this task is to use two counters, one for the ten’s digit and one for the one’s digit. Thus, the counter for the one’s digit has counting sequence of:

0 à 1 à 2 à … à 9

Likewise, the incrementing of the counter for the ten’s digit is triggered by the one’s digit whenever it reaches its terminal count. The ten’s digit counter has counting sequence of: 0 à 1 à 2 à … à 5




<h3>2.3 Structure of on-board SSD</h3>

There are four common anode SSDs on the FPGA board. These four SSDs share the corresponding cathodes. In other words, the cathodes of similar segments on all four displays are connected together. The connection of the SSDs is illustrated in Figure 2. So the four displays have only one group of 7bit cathodes instead of four groups, and all SSDs get the same signals for their cathodes. There are four separate anodes, one for each display.

AN0




<strong> </strong>

<h2>Figure 2. Structure of SSDs on Nexys2 FPGA board</h2>

<strong> </strong>

Note: the four ports AN0, AN1, AN2, and AN3 on the FPGA board are not the actual anodes of the SSDs. They are the base terminals of p-type transistors. Thus providing a “0” to AN0, AN1, AN2, or AN3 will turn the corresponding SSD on. The connection is shown in Figure 3.




<strong>Figure 3.  Power connections seven segment display. </strong>

<strong> </strong>

<h3>2.4 Display of Multi-digit Number</h3>

If a 7-bit signal is provided to the cathodes and all four anodes are turned on at the same time, then the four SSDs will display the same thing. Thus, SSDs require a multiplex driving scheme. In order to display different characters on different SSDs, one anode should be turned on at a time while appropriate cathodes for the corresponding SSD shall be provided. Then the asserted anode and the appropriate 7-bit cathodes for the next SSD should be applied. If this action continues and repeats, the four SSDs will be turned on alternately displaying different characters on each SSD. If this alternate illumination is fast enough then it will appear to human eyes as if all the SSDs light up simultaneously. This driving scheme is shown as timing diagrams in Figure 4. In the figure, “digit0”, “digit1”, “digit2”, and “digit3” are the cathodes provided to each SSD when the corresponding anode is turned on. Since only two SSDs will be used in this lab, the rest two SSDs will be provided “1111111” for their cathodes when their anodes are turned on to display nothing. In order for the digits to appear bright and continuously illuminated, all four digits should be driven once every 1 to 16 ms. In other words, each anode should be turned on at a frequency in the range of 60Hz to 1KHz. This requires the clock signal in Figure 4 should be in the range of 240Hz to 4KHz. This clock signal should also be a slower output of a clock divider.




<h2>Figure 4.  Driving scheme for SSDs</h2>

<h3>3. Verilog Coding</h3>




Model the digital clock with Verilog HDL following the block diagram in Figure 1. View RTL schematic generated from your Verilog code and identify the portions corresponding to the blocks in Figure 1.




<h3>4. Simulation, Synthesis, and FPGA Implementation</h3>




Simulate your Verilog model of the digital clock. Synthesize and implement your design on the Basys3 FPGA board.




<strong>Note</strong>: the 100MHz internal clock is provided to pin “W5” on the FPGA board.

<ol start="5">

 <li></li>

</ol>