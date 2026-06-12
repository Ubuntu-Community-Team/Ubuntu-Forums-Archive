---
title: "[SOLVED] Troubleshooting Defective Hardware?"
date: 2008-09-14
forum: The Cafe
---

### Post by Novega on 2008-09-14
Hey guys, I bought components today so I could build my cousins new computer for him... something is wrong but I'm not 100% sure how to troubleshoot it so I'm looking for some help.

ECS A770M-A, AM2+ Motherboard
AMD PhenomX4 9850 
2x1024 Corsair TWINX DDR2 PC6400
EVGA 9600GT Videocard
650w Cooler Master P/S

Put everything nicely into the new case, routed all the wires, double checked all connections, triple checked all connections...press power button and all the case lights and fans turn on BUT it doesn't beep (post?) and the monitor doesn't even turn on.

I thought maybe it had something to do with the RAM, switched slots...nothing. I swapped RAM from my current system (know it works for sure) ...nothing.

Maybe something is shorting it out, so I disconnected everything, sat the Motherboard on the electrostatic mat and tried to start it with only the RAM,MB, CPU and videocard connected (fewer variables)...still nothing.

Swapped Videocards with my current system..nothing

Like I said, the case lights and fans work, but the computer doesn't beep or anything. I'm thinking it's either defective Motherboard or CPU, but how do I know which?  I bought everything from Tigerdirect (Canada) and they seem to be pretty good from what people say but I've never had to return anything so I'm not sure how this will go.

What do you guys think?

---

### Post by DoctorMO on 2008-09-14
Sometimes hardware is defective and it needs to go back to the shop.

---

### Post by Icehuck on 2008-09-15
First thing I would do is remove everything from the system board. Reconnect the CPU and mount the heatsink again. Check to make sure that the heatsink is properly mounted. If your heatsink has a bracket that goes beneath the board check to see if you put it on correctly. They usually have two sides, the metal side will keep the board from posting.


To make sure its not your ram move the chips over to the next set of slots. Try to post without the video card. The machine should beep if the video card isn't plugged in.  I didn't really check what ram you had, but try posting with just one chip. Move to the next slot if it doesn't work and try the other chip as well.

---

### Post by mips on 2008-09-15
Did you connect the 6 pin PCI-E power connector to the evga 9600GT?

Best bet is to remove everything and just start with the cpu, 1x mem stick installed. Next add gfx card or swap out with a spere unit to test.

---

### Post by Novega on 2008-09-16
Well after 2 Motherboard exchanges and about $50 in wasted fuel to get back and forth from the store, I've finally got my problem fixed. :)

The problem seemed to be caused by the fact that the PhenomX4 9850 is a 125w cpu (one of only 2 AMD cpu's that have such a high requirement) ... they said not all boards can provide that much power to the CPU. Swapped the crappy ECS one for an Asus and everything worked fine.

I'm marking this one solved, learn from my mistakes and do your research :p

---

### Post by Bucky Ball on 2008-09-16
Unfortunately your research didn't lead you to the conclusion that you will waste more power and resources with a processor that requires 125W when we have the technology to reduce our impact with the same (usually better) end results (AMD and Intel both make some extremely powerful and energy efficient CPU's). The reason AMD only make 2 models of this ridiculously inefficient power guzzler is that they are being phased out (European environmental standards are slowly making this happen and eventually law).

Still, glad your computer is up and things are going to plan.
 
:)

---

