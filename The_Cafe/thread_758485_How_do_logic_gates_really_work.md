---
title: "How do logic gates really work?"
date: 2008-04-18
forum: The Cafe
---

### Post by Kalixa on 2008-04-18
Hey guys.

I'm interested in knowing what exactly a logic gate is.

As far as I understand it, an integrated circuit consists of semiconductors on which transistors are placed. 

Now, do these transistors make up different logic gates depending on where they are placed? And based on if the transistors are on or off, the logic gates will pass different signals?

I'm a right in this, or have I totally misunderstood it.

Thanks.

---

### Post by Rhubarb on 2008-04-18
To make a logic gate you'd typically need more than one transistor to do it.
You might want to have a read through this:
[http://en.wikipedia.org/wiki/Logic_gate](http://en.wikipedia.org/wiki/Logic_gate)

---

### Post by Kalixa on 2008-04-18
I still find it difficult to understand.

Are the gates actually built up of transistors, and will these gates output a signal which the computer will base its calculations from?

---

### Post by chewearn on 2008-04-18
> **Kalixa said:**
> I still find it difficult to understand.

Are the gates actually built up of transistors, and will these gates output a signal which the computer will base its calculations from?

To put it simply:
1. Transistors are assembled into gates.
2. Gates are assembled into functional blocks, like adder, multiplier, registers, etc.
3. Functional blocks are assembled into bigger functional blocks, until finally you have the CPU itself.

---

### Post by Kalixa on 2008-04-18
> **AstalaVista said:**
> To put it simply:
1. Transistors are assembled into gates.
2. Gates are assembled into functional blocks, like adder, multiplier, registers, etc.
3. Functional blocks are assembled into bigger functional blocks, until finally you have the CPU itself.

Nice, thank you. Finally, what is a functional block?

I really appreciate your help.

---

### Post by chewearn on 2008-04-18
> **Kalixa said:**
> Nice, thank you. Finally, what is a functional block?

I really appreciate your help.

Functional block is a general term to describe a block of circuit that perform one function.

An example is *1-bit adder*:
Using a number of logic gates, you can build a circuit that has two input (P, Q), and two output (A, F).  The two input P and Q, carry the input numbers.  The output A is the result of P + Q, while R is the overflow flag.

So, the truth table for adder is:
P Q A F
--------
0 0 0 0
0 1 1 0
1 0 1 0
1 1 0 1

You can immediately see the adder can be made by two logic gates:
A = P XOR Q
F = P OR Q

---

### Post by saulgoode on 2008-04-18
> **AstalaVista said:**
> You can immediately see the adder can be made by two logic gates:
A = P XOR Q
F = P OR Q

That should be "F = P **AND** Q". 

Nice description, nonetheless.

---

### Post by Kalixa on 2008-04-18
> **AstalaVista said:**
> Functional block is a general term to describe a block of circuit that perform one function.

An example is *1-bit adder*:
Using a number of logic gates, you can build a circuit that has two input (P, Q), and two output (A, F).  The two input P and Q, carry the input numbers.  The output A is the result of P + Q, while R is the overflow flag.

So, the truth table for adder is:
P Q A F
--------
0 0 0 0
0 1 1 0
1 0 1 0
1 1 0 1

You can immediately see the adder can be made by two logic gates:
A = P XOR Q
F = P OR Q

These inputs are based on signals from the gates? And these gate signals are based on transistors which are even on or off?

Is this correct?

---

### Post by chewearn on 2008-04-18
> **saulgoode said:**
> That should be "F = P **AND** Q". 

Nice description, nonetheless.

My bad, thanks for the correction.


> **Kalixa said:**
> These inputs are based on signals from the gates? And these gate signals are based on transistors which are even on or off?

Is this correct?

Yes.

Millions of gates, or hundreds of millions of transistors for a modern CPU, all interconnected to provide the basis of the instructions set and other functions.

---

### Post by Sporkman on 2008-04-18
A "gate" is an electronic device that computes a basic boolean logic function on its inputs. Specifically, one or more signals are its inputs, and it outputs one signal as its result. The input signals are either some positive voltage ("high" or "vcc), (interpreted as "1" or "true") or ground ("low" or "gnd"), (interpreted as "0" or "false).

Some example of gates are NOT (output is false if input is true, & vice versa), AND (output is true if both inputs are true, false otherwise), OR (output is true if one of the inputs is true), etc.

As far as transistors, they have three pins - one signal input, one signal output, and one "gating" input. On one type of transistor, if the gating input is driven high, then the signal input is freely allowed through to the signal input. If the gating signal is low (i.e. gnd), then the signal input is blocked, and the transistor's output is gnd.

One way to implement a simple 2-input AND gate would be to have one input drive a transistor's signal input, and the other AND input drive the transistor's gate input. Then, the transistor will only output high (true) if both inputs are high.

---

### Post by picopir8 on 2008-04-18
Just to add a little more detail, transistors (at least in digital logic) are simply electronic controlled switches.  Each one has an input (collector), output (emitter) and a control line (base).  Applying current to the control line allows current to then pass from the input to the output.  Since a voltage (which will induce a current) must be present on both the input and control line to get an output current, a transistor  is effectively an AND gate.  An OR gate is simply two or more inputs tied to the same output.  In practice things are a little more complicated because you need to isolate inputs from outputs and ensure that the output of one gate has enough power to drive other gates (done with more transistors) but at a basic level what I said here is true.

Once you have basic building blocks to do AND/OR operations along with inverting a signal, then you can connect those together to form more complicated logic devices.

---

### Post by Kalixa on 2008-04-18
Alright. Thanks guys. I really appreciate all your answers.

---

### Post by ARhere on 2008-04-18
If you are really interrested and want to learn the basics of how computers work, the easiest way is to play with a microcontroller with assembly code.

I always suggest to start at the simplest level and work your way up, like learning how a car works starting with the engine.  The reason I suggest programming an 8-bit micro in assembly is because it is the fastest way to see how individual '1's and '0's make a computer do something.  Assembly code is known as machine language and is directly translated, or assembled,  into 8-bit instructions.

[Microchip]("http://www.microchip.com") is a semiconductor company that sells small scale and inexpensive semiconductor products like EEPROM and microcontrollers.  (*A microcontroller is like a mini computer on a single chip; complete with its own RAM and ROM*)

If you are interested, purchase [one of these kits]("http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en023805") and start programming it to blink LED's or make sounds.

Have Fun,
-AR

EDIT:  If you want to even have _more_ fun and tie electronics to Ubuntu Linux, the Linux kernel has native driver support for I2C, SPI, and RS232 (*these are serial communication protocols*) and these tools are built into most PIC microchips.  If you get the kit, it has an RS-232 serial connection and circuit built into it.  You can go into a command line in Ubuntu and use **minicom **to talk to the PIC, and you can see and play with the data directly in the assembly code.

Most engineers I know do this job because engineering is fun, so enjoy!  ;-)

---

