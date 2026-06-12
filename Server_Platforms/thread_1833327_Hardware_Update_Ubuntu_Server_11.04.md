---
title: "Hardware Update Ubuntu Server 11.04"
date: 2011-08-25
forum: Server Platforms
---

### Post by tfuller on 2011-08-25
Hello everyone.  I just updated my Motherboard, CPU, and RAM in my existing Ubuntu Server 11.04 64bit install.  It went surprisingly smooth and everything is working.  However, I no longer get the grub splash screen and I have this error which I believe is probably related.  17.812707 SP5100 TCO timer: mmio address 0xb8fe00 already in use

I don't believe this is adversely affecting any functions ,other than being slightly annoying.  I think it probably has something to do with the Video Card which is a Geforce 7300.

Thanks in advance for any help.

---

### Post by Wayne_V on 2011-08-26
just a couple thoughts off the top of my head:

1) does the new MB have built-in graphics and did you disable it?

2) is the a watchdog timer function in the new bios?   if so, try disabling to see if the error goes away ...

---

### Post by tfuller on 2011-08-26
Thank you very much for the reply.  

There is no onboard video on the new motherboard.

And I could not find a watchdog timer option in the bios anywhere.

Could it be that the video card is being recognized as a new card while the hardware configuration is still seeing the old profile causing a conflict?  I'm not sure if that makes sense or not.  Other than the broken splash screen the command prompt is displaying fine. 

I'm really amazed that I changed this hardware and it is working as well  as it is without any software changes.  This speaks volumes on  the versatility of linux.  That is why I hate to do a fresh install when it's working this well but I'm kind of picky about little errors like this. 

Is there a command that would rescan all the hardware and create a new profile?  Or is this all accomplished at boot?

---

