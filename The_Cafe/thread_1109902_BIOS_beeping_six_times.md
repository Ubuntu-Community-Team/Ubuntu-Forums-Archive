---
title: "BIOS beeping six times?"
date: 2009-03-29
forum: The Cafe
---

### Post by miggols99 on 2009-03-29
My old Dell computer is being very strange. The hard drive recently failed. Now it is replaced. But now, I get it beeping at me 6 times. Nothing is on the screen, so I'm assuming it's the BIOS complaining about something.. but what is it complaining about? It's definitely not the hard drive because I unplugged it and it still beeped. I pulled out all of the USB things and it still beeped. What is wrong?

---

### Post by markp1989 on 2009-03-29
> **miggols99 said:**
> My old Dell computer is being very strange. The hard drive recently failed. Now it is replaced. But now, I get it beeping at me 6 times. Nothing is on the screen, so I'm assuming it's the BIOS complaining about something.. but what is it complaining about? It's definitely not the hard drive because I unplugged it and it still beeped. I pulled out all of the USB things and it still beeped. What is wrong?

if you know what modle moterboard you have, then you can get the manual from the manufactures website, which will normaly have a list of "Beep codes"

---

### Post by perlluver on 2009-03-29
Perhaps you may have unseated a stick of memory, or the processor might be dying.  It could be a number of different things, all depends on the how many times it beeps, and how the beeps sound.

---

### Post by Skripka on 2009-03-29
BIOS beep codes are usually not good-and what they mean is completely dependent on who makes the mainboard and who wrote the BIOS.

For example my Biostar board with American Megatrends BIOS, 6 beeps means

During POST:
Keyboard contrller BAT failed.

My mainboard docs also tell me that if I get 6 or 7 beeps during POST-that it is a fatal serious problem with my hardware-and to contact the system manufacturer...as a last ditch attempt to not write off a mainboard, try removing extra add-in cards.



Again, this is my mainboard, and BIOS though-and all manufacturers have different beep codes.  Get thee to Google, with BIOS maker and board manufacturer in hand.

or-

If you have a manual for you mainboard, it should tell you the beep codes right there.

---

### Post by Vince4Amy on 2009-03-29
Try removing all additional hardware for example any PCI cards, hard drives etc and see if the problem persists. Do this one at a time and if it stops beeping after removing a certain piece of hardware then it will give us more information as to what is broken. 

I know you've ruled this out in your case but just a little off topic here My Motherboard MSI K9 Neo V3 beeps for every USB device plugged in according to them it's "a feature"...

---

### Post by Dr Small on 2009-03-29
BIOS beeping can be any number of things, but the beeps mean specific things, so if you knew the beep code, it would be easy to solve :)

Anyhow, I'd go through all the componants and try each and every one by reseating it/reconnecting it, and powering on again. Start with the graphics card (if you have one), move to the RAM (reseat it), check that the CPU fans are running, check for dust and all sorts of stuff. If you have any unnecessary PCI cards, take them out.

---

### Post by jomiolto on 2009-03-29
Gah, I read the title as "BIOS *keeping* six times" and I had a true wtf-moment for a while; "your BIOS is keeping *six* different times? How's that even possible?!"

Personal note: must learn to read slower :P

---

### Post by Polygon on 2009-03-29
we need to know who makes the motherboard and what kind of BIOS it has.

---

### Post by miggols99 on 2009-03-29
It's a Dell Dimension 5100..and a Dell BIOS?

---

### Post by Polygon on 2009-03-29
go to this page:

[http://support.dell.com/support/edocs/systems/dim5100/en/sm/tshoot0.htm](http://support.dell.com/support/edocs/systems/dim5100/en/sm/tshoot0.htm)

scroll down or ctrl+f and search for "Beep Codes"

and look at that list. when your motherboard beeps, its in sets of three, so count how many beeps there are in each set and tell us which one in the chart fits.

---

### Post by mips on 2009-03-29
Depending on the sequence of your 6 beeps here are the possible causes:
1-1-4 ROM BIOS checksum failure
1-2-3 DMA page register read/write failure
1-3-1 through 2-4-4 Memory not being properly identified or used
3-1-2 Master DMA register failure

I would say check your memory seating and possibly swap it out with other memory as three out of the above four conditions indicate it is memory related.

If the it's not the memory then try resetting the BIOS as that is the last possible cause.

---

### Post by wolfen69 on 2009-03-29
[BIOS Beep Codes]("http://www.computerhope.com/beep.htm")

---

### Post by BuffaloX on 2009-03-29
From reading what MIPS wrote,
I'd guess it's just the CMOS battery.

---

### Post by miggols99 on 2009-03-29
It looks like it's the memory. I'm going to test it out and wait a while to see which stick (there's 2) is the problem, then replace it (I don't want a slow computer...) if I have to.

---

