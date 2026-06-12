---
title: "M68HC11 and USB Bus"
date: 2008-04-09
forum: The Cafe
---

### Post by RebounD11 on 2008-04-09
If anyone has any knowledge of electronics and can help me, I need an answer to this question:

How can I connect a M68HC11 Motorola micro-controller to the USB bus?

All I need is an idea. Thank you in advance...

---

### Post by saulgoode on 2008-04-09
I have never been able to find a software-only solution and I believe you will need to add an adapter chip. FTDI offers both [USB  to UART](http://apple.clickandbuild.com/cnb/shop/ftdichip?op=catalogue-products-null&prodCategoryID=38&title=UM232R) and [USB to parallel port](http://apple.clickandbuild.com/cnb/shop/ftdichip?op=catalogue-products-null&prodCategoryID=39&title=UM245R) modules.

---

### Post by RebounD11 on 2008-04-09
So you're saying I can't program the uC to connect directly to the USB Port... 

Since this uC has an SPI interface, maybe a MAX3420E can convert SPI to USB... the only thing is I can't seem to be able to think up an electronic schematic... 

Any suggestions, links, anything helpful?

Thanks again.

---

### Post by RebounD11 on 2008-04-09
OK thanks a lot I am starting to figure out how to connect the FT232R to the M68HC11 ... only one problem left: where do I connect the handshaking signals (RTS, CTS)?

---

### Post by saulgoode on 2008-04-09
It is theoretically possible to handle USB in software, and one would think that USB would map directly to the SPI, but I have never seen it done and at this point peripheral chips are cheap enough that doing it in hardware is quite reasonable.

You would probably be better of with the MAX chip. I was not aware that existed (I haven't used my 6811 in years, I ran across the FTDI because I wanted to add a host controller to an IPAQ). A UART might seriously limit your bandwidth (if that is a concern).

---

### Post by RebounD11 on 2008-04-09
I don't really know if bandwidth is a problem... I sort of received this project out of the blue with not too many details. And it needs to be done quickly. Luckily the project only consists in the schematic diagram and the program to load into the 6811. 

That's why I need the simplest solution, HW and SW and that's why I needed urgent help, if given enough details on the final product I can create a schematic from scratch, and since it's a Motorola uC the programing will be easy (I have more experience with Motorola/Freescale ASM language than with others, and I kind of suck at C, that's why I prefer ASM).

After looking at my options I think I'll go with the MAX variant... and see where I get with that. I have 36 hours to finish this and the simulation (lucky for me the simulation has to be done with Proteus - I'm familiar with that). 

Thanks loads again for the help. I'll post the schematic and maybe the programing here when I'm done. Maybe I'll get some extra tips for future flash-projects. :D

PS: I'll mark the thread as SOLVED once I finish.

---

