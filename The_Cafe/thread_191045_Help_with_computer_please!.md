---
title: "Help with computer please!"
date: 2006-06-07
forum: The Cafe
---

### Post by white_tiger_daniel on 2006-06-07
Hi everyone.

OK.  Basics.  I turn on my computer and it goes to my CMOS settings and alerts me that my CPU/SDRAM frequency may be wrong.  I fix it and go Exit saving changes, and my system reboots but there is no video output.

Any help? :( 

Dan

---

### Post by ericesque on 2006-06-07
have you tried clearing the CMOS just for a blank slate?

It could also be a memory issue.  I'd run memtest on each stick to double check they aren't at fault.  You can get some very weird errors from bad RAM.

---

### Post by white_tiger_daniel on 2006-06-07
How would you do that?

---

### Post by mcduck on 2006-06-07
[QUOTE=white_tiger_daniel]How would you do that?[/QUOTE]
memtest is in the Grub menu when you boot the machine. But it sounds like you're not getting even that far so no help there.

Could you tell what processor model you have, and what are settings in your BIOS (cpu multiplier & FSB)..

Also, if the settings don't stay, you may need to replace your CMOS battery

---

### Post by white_tiger_daniel on 2006-06-08
Umm 900mhz Celeron, 100/133 FSB, Multiplier 9.0x

---

### Post by mcduck on 2006-06-09
[QUOTE=white_tiger_daniel]Umm 900mhz Celeron, 100/133 FSB, Multiplier 9.0x[/QUOTE]
Then that's not the problem. FSB100 is the correct setting.. 
(I just had to check, as people with AMD CPU's often try to set FSB too high, to make their AXP1600 actuallly run at 2,6GHz)

Anyway, setting it right in BIOS should allow you to boot correctly even if CMOS battery is old.. 

If you have many RAM sticks, you could try to remove one stick, boot, and if the machine won't boot try with the other stick. This way you can check that it's not a memory problem.

And while you're at it, check that all condensators on your motherboard are OK, no brown stuff coming out of them or anything..

Also did you try clearing CMOS? usually you can do that by removing the battery from your otherboard for some time. Or there might be a jumper that clears it, check your motherboards manual.

---

