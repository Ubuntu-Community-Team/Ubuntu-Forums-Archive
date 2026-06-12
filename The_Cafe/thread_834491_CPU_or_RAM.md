---
title: "CPU or RAM ?"
date: 2008-06-19
forum: The Cafe
---

### Post by Bölvaður on 2008-06-19
I have a bit of a problem on my hands.
My brother bought a new computer components from some websites online and put them together this morning. It gives 3 (seemingly) short beeps indicating faulty RAM stick. The fans all go round and round, and there is only a blank screen indicating no connection.

I've put the memory in both slots and still there is the 3 beeps. Having it not in gives the same results also.

I was wondering if it could be one of the following:

1. Bad RAM stick
2. Motherboard problem
3. Power supply problem
4. CPU incorrectly installed

With best regards, from my brother, to you :popcorn:

---

### Post by jualin on 2008-06-19
I had a similar problem. The way that I diagnose the problems on a computer is by testing it in different environments. For instance if you take out the RAM and the problem is the same therefore either the RAM sticks don't work or that is not the problem. Try putting the same RAM in another computer to see if they work. Also try using only one RAM stick since it is too much coincidence that both RAM Sticks don't work. Also check that the motherboard is not touching the Metal Case . Try taking out the motherboard from the metal case and trying to turn on the computer with the motherboard out of the case. 
Now for the 4th option (CPU incorrectly installed) modern computers have ways that protect you from that. The CPU will not fit correctly if you don't put it in the correct way.
Hope this helps!

---

### Post by fatality_uk on 2008-06-19
Do you have a DIMM that you could take from another PC to check. You only need 1 and none of the new RAM. Try that, if it gets past the BIOS, you know it's the chips.

---

### Post by Lord Xeb on 2008-06-19
Yes, even if you take it from a PC that is running RAM at a higher FSB speed, it will clock itself down (or is it the other way around). Just make sure the voltages are right.

---

### Post by Bölvaður on 2008-06-19
I only have 1 ram now. No access to any other (going to the store tomorrow to check if I can get it replaced) and no other computer that can handle that type of ram.

Btw my ram requires 1,8v it said. how can I know that is what my mobo is giving it?

---

### Post by gn2 on 2008-06-20
Check you've got the correct beep code for the BIOS version here: [www.bioscentral.com](www.bioscentral.com)

What motherboard is it and what RAM is it? (exact model of both)
Have you checked that you've definitely got RAM that is compatible with the motherboard?

Same applies to the CPU, is it on the list of CPU's supported by the board, and is the installed BIOS version capable of using the CPU.?
It's possible that the board will only work with a CPU listed as compatible only after a BIOS update, and to be able to do the update you will need an older CPU to get the PC running. Catch 22.

Assemble the board CPU and RAM on a desk, not in the case, to eliminate the possibility of a short circuit between the board and the case.
To start it just briefly short the power switch pins with a screwdriver, or connect the button if the wire is long enough to reach from the case.

---

### Post by Bölvaður on 2008-06-20
Intel <[DG31PR]("http://www.intel.com/products/motherboard/DG31PR/index.htm") motherboard
Q6600 processor
KVR800D2E5 which should fit the motherboard perfectly. 800 Mhz, Dimm, 240 pins.


I'm going to the store to let them check out if the ramstick is fine or not. Will try to start it up outside the box if the ram isnt the problem

---

### Post by mips on 2008-06-20
[http://www.intel.com/support/motherboards/desktop/sb/cs-010249.htm](http://www.intel.com/support/motherboards/desktop/sb/cs-010249.htm)
> 
**3 beeps** - Base 64 K memory failure

Reseat the memory. 
Make sure that the contacts on the memory and the socket are clean. 
Try removing one bank of memory modules at a time. Note: Some systems might need to have a memory module in Bank 0. 
Try using RAM chips from the same manufacturer with the same part number and speed. 
Check for a faulty memory module by trying the memory in a known good system. 
Trying known good memory in the system. 
Check the power supply and check for power fluctuations. 
Swap the motherboard.

---

### Post by Bölvaður on 2008-06-20
The problem has still not been solved.

What I have found out is:

0. When turned on normally it gives 3 beeps (indicating bad ram) and doesnt show any image or connection to the display.
1. The RAM is supported by the motherboard, and it works on other machines.
2. After being connected outside the box with minimal connections to the board, it still gives 3 beeps.
3. Without any cpu there will not be any beeps, no fans will move or any sign of life, and still no vga output to monitor.

That leaves 2 obvious options.
**Firstly** it could be that the motherboard is some how broken.
**Secondly**, 3 beeps are also the code for bad CPU even if it is not stated in any manuals or online help pages.
*Thirdly * The power supply is some how bad. Giving fluctuations or wrong hz or something remotely plausible.
*Fourthly * There actually is a god, and it doesn't like me.

Do I need anything more than the 2x2 power cables and 2x12 main power one?
The only thing I got connected are those two, the cpu with the fan is in place (connected to the 4 pins), the ram is in place and the on/off button is connected.

Any thoughts at all?

---

### Post by gn2 on 2008-06-20
Have you checked that you have got the 95w TDP "Energy Efficient" version of the Q6600?

According to the motherboard manual the board will not work with the conventional Q6600 which at 105w has a higher TDP than the design limit for the board.

This from the manual: 

```
1.4     Processor
   The board is designed to support the following processors:
   &#8226;  Intel Core 2 Quad processor in an LGA775 socket with a 1066 MHz system bus
   &#8226;  Intel Core 2 Duo processor in an LGA775 socket with a 1333 MHz, 1066 MHz, or
      800 MHz system bus
   &#8226;  Intel Pentium Dual-Core processor in an LGA775 socket with an 800 MHz
      system bus
   &#8226;  Intel Celeron processor in an LGA775 socket with an 800 MHz system bus
   Other processors may be supported in the future. [COLOR="Red"][B]This board is designed to support
   processors with a maximum wattage of 95 W. The processors listed above are only
   supported when falling within the wattage requirements of the DG31PR board[/B][/COLOR]. See
   the Intel web site listed below for the most up-to-date list of supported processors.

Source: http://download.intel.com/products/motherboard/DG31PR/tps.pdf
```

The different Quad-core CPU's are listed here: [http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Quad](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Quad)

Note: there are two different Q6600 CPU's, you need the newer one.
That's if your board will even take the newer Q6600, see below...

On Intel's site there is a compatibility warning for the Q6600 and a list of compatible board revisions.
Click on "Multiple values" at the end of the Q6600 line for a clickable link explaining how to check if your board will work with a Q6600:
[http://processormatch.intel.com/CompDB/SearchResult.aspx?Boardname=dg31pr](http://processormatch.intel.com/CompDB/SearchResult.aspx?Boardname=dg31pr)


[COLOR="White"].[/COLOR]

---

### Post by damphoud on 2008-06-20
If you do have the 95w cpu, and your still having the problem: You need to take out the mobo and see if you placed a screw connector (I'm not sure what you call them...?) in the wrong location on the chaise. If the metal piece is touching your mobo without the protection of an screw hole location, you could short out a few components, like your ram. Sorry for the bad terminology... :)


EDIT: if this is true, just send back to retailer. DOA :O

---

### Post by Zeotronic on 2008-06-20
I will toss this up there, but I must warn you, that my hardware knowledge is limited... I am aware that there is a type of ram which requires that all RAM slots be filled... I have it, but I don't know what it's called... but if this is what you have, you can get blank sticks to fill the other spots, if need be. I'm pretty sure it requires all RAM be the same type of RAM as itself. But my experience in the hardware field is limited.

---

### Post by Bölvaður on 2008-06-20
Thanks everyone, you've been very helpful.

I think **gn2** might have solved this, as I actually thought it was supported type but it wasn't. I need the 0032 version of the bios after all.
So I guess I have to take a road trip to get the people at the shop to install supported cpu and correct bios before putting mine in.

Btw what is the best way to store cpu while swapping it during the bios installing procedure?


Btw Crack Attack is a really fun game ^^
Love how much work has been done on the games in the repos

---

### Post by gn2 on 2008-06-20
Intel are pretty bad for this kind of processor/board incompatibility thing, good luck getting it all working.

Have you asked the seller what they have to say about selling you a mis-matched board and CPU?

**EDIT**: Best way to store the CPU is in the original packaging.

---

