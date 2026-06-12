---
title: "How exactly do logic gates work?"
date: 2011-04-15
forum: The Cafe
---

### Post by Dustin2128 on 2011-04-15
For quite a while now, it's been annoying me that I can't seem to grasp how logic gates and boolean algebra/logic come together to form a computer. Can anyone point me to a good explanation? The main thing is that it bothers me that I can *use* a computer fairly well  but don't know how they work at the most basic of levels.

EDIT: and yes, I've looked at wikipedia.

---

### Post by giddyup306 on 2011-04-15
By using rational doors.

---

### Post by earthpigg on 2011-04-15
> **Dustin2128 said:**
> The main thing is that it bothers me that I can *use* a computer fairly well  but don't know how they work at the most basic of levels.

that just means you aren't a computer scientist. nor are most of us.

recall that when using a computer did require understanding at the basic level, only mathematicians and physicists (and that 1% that Torvalds and rms are a part of) could use them for the most part. even in 2011, computer science degrees are still very much math degrees.

what we do today is use higher level abstractions. stuff has been put in between us and the bare metal. essentially, this represents the efforts of physicists and mathematicians to make computing easier for them and accessible to us. 

not unlike people that can walk taking the time to build wheel chair ramps, except in this case it is our education and perhaps our brain that makes us differently-abled than the people taking the time to make things accessible to us.

(I've used the same metaphor to express gratitude to Steven Hawking for writing books that I can understand. His books are wheel chair ramps for my humble brain.)


I don't want to dissuade you, I just want to point out that when you have achieved the understanding you seek -- you will be part of that 1%.

---

### Post by earthpigg on 2011-04-15
I'm thinking that if I wanted to achieve that level of understanding, my first step would be to get my hands on a computer *at least* old enough to be Pre-BASIC, or an emulation thereof. Machine code, punch cards (real or emulated), or ones and zeroes - manually giving directions to CPU registers (emulated or real).

And from there, try to make it do something useful like add 2+2 or display "hello world".

Theory being that there is no better way to learn than to *do*.

---

### Post by d3v1150m471c on 2011-04-15
[http://www.youtube.com/watch?v=ee8V8leCB3U](http://www.youtube.com/watch?v=ee8V8leCB3U)

this might help. all ones and zeros 0o0o0o0o0o0o 0_o :)

---

### Post by Sporkman on 2011-04-15
Look at integer addition - for the result of adding the first bits of the summands, the resulting bit is:

r0 = a0 ^ b0 , where "^" = XOR, a 2-input logic function.

The carry bit is:

c0 = a0 & b0 , where "&" = AND, another 2-input logic function.

For the next result and carry bits, we have:

r1 = a1 ^ b1 ^ c0 , so this is a 3 input XOR function.

c1 = (a1 & b1) | (a1 & c0) | (b1 & c0) - 3 2-input AND gates feeding a 3-input OR gate

...etc. So there's how a basic computational step can be implemented with logic gates.

---

### Post by standingwave on 2011-04-15
EE here. Try this: [http://en.wikipedia.org/wiki/Finite-state_machine](http://en.wikipedia.org/wiki/Finite-state_machine)

---

### Post by NovaAesa on 2011-04-15
Memory is made from banks of Flip-Flops or latches. Those flip flops are made of (typically from my understanding) NAND gates. A NAND gate is made from transistors (in TTL and CMOS). For computation, the various banks of gates are linked together with banks of memory to perform bitwise XOR, AND, OR etc. For addition, a so called "added" is used, which is itself made from gates.

@Earthpig, you're right, computer science degrees are basically maths (and that's the way it should be IMO, I'm a computer science student). This sort of stuff is more inside the field of computer engineering.

---

### Post by 3Miro on 2011-04-15
I used NAN gates to create a one bit of memory circuit together with a read/write instruction. It was in a lab exercise in Physics for Computer Science Majors. I cannot replicate this experiment now, actually I can, but it will take me some time. There was quite a bit of math. As for the exact physics on how transistors work, I don't claim to understand it.

What I learned in that class was fun, but not really useful. If you want to learn how the computer works on low lever, look at Assembler and learn how to read simple memory dumps. I too an Assembler class and since then I have never written a single line of Assembler (I am a coder), however, what I learned in that class was invaluable in understanding how the computers work.

I don't know how much Linus Torvalds knows about NAN gates and physics of transistors, but I can guarantee you that he is an expert in assembler. On his very first machine, he used to program with hex (which is even lower than Assembler).

---

### Post by Ji Ruo on 2011-04-15
I don't know how binary computation takes place as actual circuit design etc. which I believe is what you're looking for. But for a good resource for understanding what's happening just above this level, you could try the book Inside the Machine by Jon Stokes (No Starch Press). It gives a nice simple explanation of what the computer is actually doing, and proceeds into design implementations like pipelining etc. by going through the Intel and PowerPC chip ranges from Pentium era onwards.

---

### Post by nmaster on 2011-04-15
i'm an eecs student at berkeley. logic gates aren't that hard to understand if you have some reasonable background in high school level physics and chemistry.

ee40 is the intro circuits class in which we learn about the basics of these things. if you want some information on how logic gates are built at the transistor level check out this the lecture slides labeled "Semiconductor Devices and Technology" and "Digital Integrated Circuits": [http://inst.eecs.berkeley.edu/~ee40/fa03/lecture.html]("http://inst.eecs.berkeley.edu/%7Eee40/fa03/lecture.html")
 
if you want information on how to use logic gates to (for example) build an arithmetic logic unit, take a look at cs61c. here is a link for that:[http://inst.eecs.berkeley.edu/~cs61c/resources/blocks.pdf]("http://inst.eecs.berkeley.edu/%7Ecs61c/resources/blocks.pdf") 

understanding how logic gates actually work requires some knowledge of semiconductor physics.  in my experience, computer scientists typically don't have that background.  its more in the realm of electrical engineering and physical chemistry. i would recommend that you look at the course materials for classes at berkeley and mit.  most professors make these slides and notes available online for anyone and there is a lot you learn if you are really interested. if there are any particular areas of interest, free to PM me and i can recommend some more course websites!

---

### Post by nmaster on 2011-04-15
> **3Miro said:**
> I used NAN gates to ...
i think you mean NAND...
[http://en.wikipedia.org/wiki/NAND_logic](http://en.wikipedia.org/wiki/NAND_logic)

---

### Post by fillintheblanks on 2011-04-16
a NAND gate is when 2 highs make a low

---

### Post by Mr. Picklesworth on 2011-04-16
> **Dustin2128 said:**
> For quite a while now, it's been annoying me that I can't seem to grasp how logic gates and boolean algebra/logic come together to form a computer. Can anyone point me to a good explanation? The main thing is that it bothers me that I can *use* a computer fairly well  but don't know how they work at the most basic of levels.

EDIT: and yes, I've looked at wikipedia.

Here is an absolutely wonderful book about it: [http://www1.idc.ac.il/tecs/](http://www1.idc.ac.il/tecs/)

Steps you through designing a modern computer. They cover everything from sticking together transistors to making computer games. Simulated, of course, and with a very simple architecture. They skip over some fancier details in each section for brevity, but they make it clear they're doing it.

The thing I found particularly cool when I read / did the book is its writing is focused on the &#8220;why&#8221; part with only a little bit of the &#8220;how.&#8221; It gives you the tools and lets *you* build your first XOR gate and your first ALU. It takes patience, but I thought it was a very nice and rewarding approach that I don't often get from a book.

I recommend it if you're interested :)

---

### Post by phrostbyte on 2011-04-16
Here is some logic gates wired together to do very simple addition

[http://en.wikipedia.org/wiki/File:Full_Adder.svg](http://en.wikipedia.org/wiki/File:Full_Adder.svg)

You can daisy chain these babies together to add very large numbers together. Very simple circuit building blocks can lead to very complex circuits, a truism of modern processors. 

You can look up XOR, AND, OR gates to see the different parts and what they do. Of course all logic gates are implemented using transistors - the real magic behind computers. :)

---

### Post by Paqman on 2011-04-16
> **Dustin2128 said:**
> I can't seem to grasp how logic gates and boolean algebra/logic come together to form a computer.

For me the real "aha!" moment came when an instructor demonstrated a series of flip-flops connected together in a particular configuration. Every time it clocked, one of the flip-flops at the bottom would change, and you could read across the line and interpret that as binary. In other words, it was counting. 

Once you see that these little elements can be joined together to form components with a specific function you can see that you can build up some really complex behaviour.

---

### Post by mips on 2011-04-16
> **Dustin2128 said:**
> Can anyone point me to a good explanation?

Maybe look at how transistors work and understand that first and then look at how a logic gate is built using transistors. Then trace the states as you apply a voltage. Should make a whole lot more sense

We had to learn this and build them when studying elec. eng.

The logic part after that is very easy.

---

### Post by grahammechanical on 2011-04-16
Think of logic gates as switches. They can be replicated by simple on/off switches of any kind but with electronics they are transistors. CPUs are made up of very, very small transistors arranged in certain groups that are the logic gates.

When a switch is open (off) it represents a 0. When it is closed (on) it represents a 1. Two switches open = 00. Two switches closed = 11. One switch open and one switch closed = 01 or 10 depending on which switch is the open or closed switch. And so on according to the number of switches.

Now arrange the switches in such a way that when one switch is open another is closed or a closed one becomes open. It now becomes possible to do simple mathematics. Close switch 1 AND close switch two = switch 3 closed = 2 (1+1 = 2). And stuff like that = I cannot remember how to explain it. I do remember that there are AND gates and OR gates and NOR (Not OR) gates  and NAND (Not AND) gates.

Relays and vaccum tubes (valves) were used by the British during the second world war as part of the first electronic computer. It was used to decrypt German radio signal traffic encoded by their enigma machine. And mathematicians had to be heavily involved. 

I studied this stuff decades ago for my own curiosity but I gave up when integrated circuits (ICs) came out. It became beyond my ability to understand.

Regards.

---

### Post by Chronon on 2011-04-16
> **nmaster said:**
> 
understanding how logic gates actually work requires some knowledge of semiconductor **physics**.  in my experience, computer scientists typically don't have that background.  its more in the realm of electrical engineering and physical chemistry.

Or physics perhaps?  ;)

When I took semiconductor device physics it was taught by a professor well-versed in solid-state physics.

---

### Post by Paqman on 2011-04-16
> **Chronon said:**
> Or physics perhaps?  ;)


Or witchcraft and gobbledegook. In a sane world, holes do not flow.

---

### Post by standingwave on 2011-04-16
> **Paqman said:**
> For me the real "aha!" moment came when an instructor demonstrated a series of flip-flops connected together in a particular configuration. 

That's why I included the link to finite state machines in #7. Once the student learns how a simple logic gate can be configured into a flip-flop the light-bulb generally flashes on because the circuit now has "memory," i.e. a present state and a next state dependent upon the present state plus inputs. At that point, the student can literally build anything from a counter to a counter to a traffic light controller to a computer. The difference is only scale and organization. If you can describe it in a flow chart (state diagram) then you can implement it in logic. This is a terrific little (four page) tutorial that explains the entire process: 

[http://www.cs.princeton.edu/courses/archive/spr06/cos116/FSM_Tutorial.pdf](http://www.cs.princeton.edu/courses/archive/spr06/cos116/FSM_Tutorial.pdf)

That gets you started and it's really a lot of fun because the circuit design simply flows (no pun intended) from the state diagram.

Alternatively one can simply buy an Arduino board and begin coding. :p

---

### Post by lisati on 2011-04-16
> **Paqman said:**
> In a sane world, holes do not flow.
I recall experiencing a "Huh?" moment when I first encountered something described in terms of holes and their perceived flow. It's probably one of those abstractions that's more use to some people than others.

---

### Post by Zoot7 on 2011-04-16
One would really have to understand the transistors themselves to understand the gates. The wikipedia explanation of CMOS and TTL might be the place to start.
[http://en.wikipedia.org/wiki/CMOS](http://en.wikipedia.org/wiki/CMOS)
[http://en.wikipedia.org/wiki/Transistor-transistor_logic](http://en.wikipedia.org/wiki/Transistor-transistor_logic)

Put simply, the arrays of transistors used are configured as switches. If you want to actually know how the electrons themselves behave you've got to get down to semiconductor physics.

---

### Post by standingwave on 2011-04-16
> **lisati said:**
>  It's probably one of those abstractions that's more use to some people than others.Well, if you want to get real philosophical, then [which way does electricity really flow]("http://www.eskimo.com/%7Ebillb/amateur/elecdir.html")? Or what is [electrical charge]("http://en.wikipedia.org/wiki/Electric_charge#Overview") really?

---

### Post by Paqman on 2011-04-17
> **lisati said:**
> It's probably one of those abstractions that's more use to some people than others.

For sure. All electronics and everything at a particle scale and even most electrical theory is just abstractions anyway. Like I said, witchcraft and gobbledegook.

I found that's the big mental hurdle you have to jump as a student of this stuff. I'm an engineer and we tend to be practical folks, I would imagine people with more of a physics and science background might find it a bit easier to get the right perspective maybe? I studied it in the RNZAF, and for a bunch of people who fix aeroplanes all day, giving up trying to conceptualise the processes as something _real_ instead of something abstract was a head-bender. Bottom line though is that it works, which is pretty convincing.

---

### Post by Shpongle on 2011-06-22
> **Mr. Picklesworth said:**
> Here is an absolutely wonderful book about it: [http://www1.idc.ac.il/tecs/](http://www1.idc.ac.il/tecs/)

Steps you through designing a modern computer. They cover everything from sticking together transistors to making computer games. Simulated, of course, and with a very simple architecture. They skip over some fancier details in each section for brevity, but they make it clear they're doing it.

The thing I found particularly cool when I read / did the book is its writing is focused on the “why” part with only a little bit of the “how.” It gives you the tools and lets *you* build your first XOR gate and your first ALU. It takes patience, but I thought it was a very nice and rewarding approach that I don't often get from a book.

I recommend it if you're interested :)


looks interesting , thanks for sharing

---

### Post by Bandit on 2011-06-23
> **earthpigg said:**
> I'm thinking that if I wanted to achieve that level of understanding, my first step would be to get my hands on a computer *at least* old enough to be Pre-BASIC, or an emulation thereof. Machine code, punch cards (real or emulated), or ones and zeroes - manually giving directions to CPU registers (emulated or real).

And from there, try to make it do something useful like add 2+2 or display "hello world".

Theory being that there is no better way to learn than to *do*.

I remember setting around for hours on an older Tandy to type in machine code to make a simple game only to have the power go out and have to start all back over.. /cry...  Only wished that thing had a punch card reader.

---

### Post by mips on 2011-06-24
You could also use a electronics simulator to trace the workings.

---

