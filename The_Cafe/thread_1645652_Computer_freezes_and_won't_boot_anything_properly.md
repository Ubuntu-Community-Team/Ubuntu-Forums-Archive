---
title: "Computer freezes and won't boot anything properly"
date: 2010-12-14
forum: The Cafe
---

### Post by angryfirelord on 2010-12-14
Hey guys. I'm having a bit of a pickle with one PC that is being as stubborn as a mule in getting it to do anything. It's an Acer M5641 that is (or was) running Vista.

About two weeks ago, the computer started having some random freezes. At first, I though it was simply a Windows Update that was conflicting with a driver. So after some trial and error with trying to get the drivers to install without it locking up, I managed to update them. At first, that seemed to do the trick.

However, a day later, the problems returned. I tried System Restore to no avail. So I figure that Vista decided to eat itself at some point in time and thought that the registry might have been corrupted. But just to be sure it wasn't anything else, I decided to run Memtest86+ on it.

Well, after an hour and 32 minutes, Memtest froze up. The screen looked like it had all static distortion on it, kind of if it was near some interference. Running it again yielded the same freezing up with no input from the keyboard and the same static lines. The only difference was the times. Some froze at 45 minutes, others froze at 3. I tried putting the memory into different slots and testing each one at a time, but they still went with the same result.

After that, I tried booting the Ubuntu live cd. I tried all of the different boot options, but the CD would never load X. It wouldn't ever load to a prompt either. 

So, has anyone ever encountered such as issue? I don't believe it's the power supply as the processor is only an E2200 and everything is pretty much onboard, including the video. I suspect the motherboard might be failing, but at first glance I didn't see any bad capacitors. It would seem like a hardware problem, but I really don't know at this point.

---

### Post by Khakilang on 2010-12-14
I had an Acerpower too. Having the same problem as yours. Still haven't figure out what causes it. Could be RAM, hard disk, motherboard or PSU. Anyway I got 2 other IBM PCs which is running perfectly so I would not bother with Acer at the moment.

---

### Post by angryfirelord on 2010-12-16
I don't believe it's the hard drive that's causing the problem. I unplugged that from the motherboard and the power supply and it's still doing the same thing. Having two sticks go at once seems like a very unlikely event, but since I don't have any other DDR2 memory to test it with, that is still up in the air. I think at this point in time it has to be the motherboard because the system does not freeze when it is in the BIOS. I suspect that when the OS loads, it is trying to use a piece of hardware on the board and it's just not working right. The only thing I can see is that the integrated video adapter somewhere might be bad. I'll have to test it with a video card just to be sure.

For those two boxes that you mentioned, do you know the specs? I'm wondering if it's a common problem with the motherboard manufacturer or if something on the board that is the same.

---

### Post by sydbat on 2010-12-16
It is either the mother or the ps. A ps that is starting to go gives out bad / random voltage that can destroy the other hardware. If you have a known good ps, plug it into the board and see if things clear up. If not, then the mother is at the end of it's life cycle.

---

### Post by angryfirelord on 2010-12-16
> **sydbat said:**
> It is either the mother or the ps. A ps that is starting to go gives out bad / random voltage that can destroy the other hardware. If you have a known good ps, plug it into the board and see if things clear up. If not, then the mother is at the end of it's life cycle.
I got lucky, someone at work today was able to find a working power supply. Unfortunately, it didn't fix the problem as the same issues appeared. I also decided for the heck of it to flash the BIOS, which didn't do anything either. The BIOS reported good chipset voltages on the old power supply, with the 12 volt reporting between 11.968 and 12.032 volts, so it looks like it's time for a new motherboard.

It's too bad, the PC isn't that old (only two years).

---

### Post by angryfirelord on 2010-12-19
More interesting development. I tested the PSU with a multimeter on a molex connector and both the 5v and 12v rails were performing very well, at around 5.03v and 12.04v respectively. However, I decided to go into memtest one last time, but I changed the Error report mode to show BadRAM patterns. Well, 2 minutes into the test, I got 800 errors and on another round, I got 2404 errors. So it seems like there's something bad about either the RAM or the RAM slots. Unfortunately, the BIOS doesn't output the voltage of the RAM, so it's impossible to know if there was a voltage drop-off or fluctuation. 

I'll have to borrow some good DDR2 from somebody, just to confirm which one it is.

Edit: I also ran the Windows Memory Diagnostic tool and it also confirmed a problem (of course, no details were provided). So I don't think memtest is giving false positives here.

---

### Post by Spr0k3t on 2010-12-19
Could be the voltage regulator circuitry on the mainboard.  Many Acer computers I've worked on with similar issues all turned out to have good components, but the caps were starting to bulge a little around the memory or cpu area.

---

### Post by mips on 2010-12-20
Micro-Scope Diagnostic Suite is very good at identifying faulty hardware of all sorts.

With Memtest test with single dimms installed in different slots to identify the culprit.

---

### Post by angryfirelord on 2010-12-26
Well, looks like I figured out the problem. Part of it may have been my fault for not doing things in the proper order.

I took the RAM out and I blew air on the RAM slots, just to make sure there wasn't any extra dust accumulation. Then, I installed the first stick, but this time I wasn't lazy and laid the computer on a flat surface, so I made extra sure the RAM was seated correctly. Tested the first stick, same thing. Errors on memtest and Vista locked up. Tested the second stick, everything was fine. No errors, and Vista is running fine. Well, as fine as Vista can run on 1GB. :P

I got an RMA from the RAM manufacturer, so hopefully the new stick will come shortly after I ship it. Thanks for all your help though, I'll be sure to keep this in mind if I encounter the same issue again.

---

### Post by Spr0k3t on 2010-12-26
Glad to hear you got it figured out.  Make sure you test the good stick in the other slots though to eliminate any other issues.

---

