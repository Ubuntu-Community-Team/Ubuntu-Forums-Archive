---
title: "Auto reboot after power failure"
date: 2008-07-07
forum: Server Platforms
---

### Post by John Chambers on 2008-07-07
I have a new machine that I'm setting up as a server.  It has ubuntu 8.0.4 installed.  Yesterday, during a good storm, we had a brief power failure, and when the power came back, the box was off and didn't reboot until I pushed the power button.  I was a bit disappointed, since if I'm off at some conference 1000 miles away, and the power fails back home, I won't have a 1000-mile-long finger to push the power button to get the server back online.

I contacted the folks who put the box together, and they told me how to get into the BIOS and set it to automatically power on and reboot.  But it occurs to me that there might be some linux tool that can do this.  That way, I don't have to bring the server down to munge the BIO.  

I did a bunch of googling, searching ubuntuforums.org, etc., and found a lot of things about power management, but nothing that mentioned this topic (or anything about twiddling the BIOS).  So is there a tool that controls this sort of thing?  Or should I just reboot, tweak the BIOS by hand, test it, and hope that it works?

(Actually, I do have plans to add a UPS, but that only helps for brief power outages.  Sometimes power outages last more than a few minutes, the UPS will run out of electrons, and the system will power down anyway.)

Here goes first post ...

---

### Post by koenn on 2008-07-07
> **John Chambers said:**
> 
I contacted the folks who put the box together, and they told me how to get into the BIOS and set it to automatically power on and reboot.  But it occurs to me that there might be some linux tool that can do this.  That way, I don't have to bring the server down to munge the BIO.  


I'm not sure what you're asking : how would Linux make your computer boot when the computer has had its power cut of, is off, and needs to boot again before linux even gets loaded ? 

Unless you're looking for a tool that can modify the bios while the computer is up and running. Don't know of any.

---

### Post by littlegreiger on 2008-07-07
Your best bet and as far as I know the only way to do this is by editing the bios settings. There should be a setting called "Pwr-On after PWR-Fail" or something similar in the power management options in the bios. If you set this to on it should work the way you want. I would recommend testing this before you go away just in case it doesn't work correctly.

---

### Post by GouZi on 2011-12-10
Yes, usually in the bios (in general, press "Del" when booting, to get into the Bios settings), there's a "Power Management" section. In there there's an "AC" section where you can chose:
- "Soft-Off" (Always Off after power failure).
- "Soft-On" (Always On after power failure).
- "Memory" (Depends on the state before power failure).

---

