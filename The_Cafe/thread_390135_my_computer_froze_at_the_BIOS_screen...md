---
title: "my computer froze at the BIOS screen.."
date: 2007-03-21
forum: The Cafe
---

### Post by billdotson on 2007-03-21
2 weeks ago my PC was acting very funny and about half of the time I turned my PC off and back on or just restarted it would freeze at the BIOS screen and would sometimes require multiple restarts to get it past it.  I RMAed my motherboard and PSU and just yesterday I got them back and put the PC together.  I have an Asus P5B Deluxe/Wi-Fi AP motherboard and my replacement PSU was an Antec TruePower Trio (3 12V rails, as opposed to the one that was faulty the TruePower 2.0 w/ 2 12V rails) It was working fine and I was glad to have my PC back.  I turned the PC off last night and this morning when I got up I turned it back on.  

The computer stayed at the BIOS screen for about a minute so I shut it down (power button) and turned it back on and it went right through the BIOS.  I thought that my old motherboard and PSU were faulty and was causing this?? When I had the old MB and PSU though it would freeze if I had left it off all night, or even just doing a simple reboot for something like an update for the OS.  I don't know if my PC has so much power that it takes it awhile to get power into the motherboard and to the other parts that it freezes upon booting after being off for long periods of time or what but I noticed a similar thing about a month ago w/ my old equipment.  

Back then, I had to take my PC to the local university to get Windows reinstalled because I had botched my install by trying a registry tweak for better RAM performance.  When I got it back it 'froze' on the BIOS screen and I just left it for about 5 minutes and then it loaded into the OS.

Should I have something to worry about or does my PC just take a while to get the amount of power it needs to run?

Before I RMAed my MB I went through and checked the compatibility of all my RAM and other stuff to check that it wasn't some other hardware causing the issue.  My CPU is running at 90 degrees F and my MB is running at 72-73 degrees F so it isn't a heat issue.

Thank you.

---

### Post by dreadlord_chris on 2007-03-21
Actually you mean POST not BIOS screen. But that's just splitting hairs....

More importantly - which part of the POST is it hanging at? This can give you a clue as to what the problem actually is. So, watch the screen and note the last thing printed before the hang.

btw - P.O.S.T.: (Power On Self Test) A series of built-in diagnostics performed by the BIOS in a PC when the computer is first started.

---

### Post by bonzodog on 2007-03-21
That actually sounds like a RAM error.

The only way to truly find out is to run a RamTest, which runs outside the kernel. 

Either that, or something is not plugged in correctly on the mobo, it could even be a bad jumper setting on the drives, causing it to lock temporarily whilst it attempts to find the master drive off the First IDE port. 

The hardware itself might not be faulty, but it could be put together incorrectly. Do you know how to configure your mobo with jumper settings correctly, and have you checked that the BIOS is set-up correctly?

---

### Post by billdotson on 2007-03-21
my RAM only goes in one way so I couldn't have put that in wrong, and the RAM I have is stated to be an officially supported RAM in the manual.  Before I replaced my MB I ran memtest86 and my RAM passed 6 out of 6 times with 0 errors, and I assume that if it passed that many times it is fine.  After I put the PC together I just booted into the BIOS and told it to reset to defaults.  I have not seen anything in the manual about using jumpers to set the motherboard up and the DVD drives I have are not both IDE, one is SATA and one is IDE so I would only have a jumper on one of them.  After I set it to defaults I changed a few things like I told the RAM frequency to not be auto and to be 800MHz and then I disabled the onboard wi-fi.  

I really do not know what is going on.  I have an Asus P5B Deluxe/Wi-Fi AP edition motherboard and Corsair 6400C4 XMS2 DDR2 800MHz RAM.  I do not know if I need to switch any jumpers around or something and I am pretty sure all the parts are in the right place.. the first time I put it together the staff at the local university computer support center helped me out.  

This is really frustrating I just want my PC to work without having to troubleshoot it every 1-2 weeks. GRR.. I am frustrated.

I don't think it froze at the POST screen, it froze at the first screen that came up, the blue Asus P5B Deluxe screen, I am pretty sure the POST comes up after that.

I have heard that sometimes this freezing can happen if a device isn't working correctly or either the BIOS can't check to see if it is working before it needs to get to boot the OS.  Some guy said that it always happens when he has his iPod hooked up to his PC when he boots it up.  The only external device I have hooked up is my Maxtor USB2.0 external HDD.  Maybe that is the issue.. although that would be annoying as Ubuntu is loaded onto the external drive.  Maybe I need to tell the BIOS something about that Maxtor drive or something??  Argh this is frustrating

---

### Post by billdotson on 2007-03-24
help

---

