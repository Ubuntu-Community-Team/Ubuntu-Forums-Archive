---
title: "Advice on motherboard transplant"
date: 2014-01-22
forum: Server Platforms
---

### Post by Derek_Gentle on 2014-01-22
Hello All
 
I am in the midst of upgrading my server hardware and had a question about transplanting an OS between motherboards.
 
I am currently running Ubuntu Server 12.04 on dual Xeon E5450’s, on a Supermicro X7DWE.  I want to swap out motherboards, and replace it with a Supermicro X7DWN+ due to the increased RAM support.
Both boards are (obviously) from the same manufacturer, and both use the Intel 5400 (Seaburg) chipset.  I am also using an IBM LSI SAS3444E controller to provide additional drives.
 
Are there any potential issues that I should be aware of, or should the ‘transplant’ be as simple as moving parts from one board to the next?
 
Many thanks in advance!

---

### Post by tgalati4 on 2014-01-22
It should be plug-and-play.  Pay attention to the *dmesg* messages after the first boot.  And make a list of errors and warnings that you find.  Make sure your power supply can handle the load of additional spinners.

Run your extra RAM through memtest for several cycles to make sure it's error-free.

---

### Post by Derek_Gentle on 2014-01-22
> **tgalati4 said:**
> It should be plug-and-play.  Pay attention to the *dmesg* messages after the first boot.  And make a list of errors and warnings that you find.  Make sure your power supply can handle the load of additional spinners.

Run your extra RAM through memtest for several cycles to make sure it's error-free.

Thanks for the quick reply!

I am currently using an Antec HCG 620w without any trouble.  As I currently have 8 'spinners' running, and the only thing being changed is the motherboard, I don't think I should have any power issues.

---

### Post by ian-weisser on 2014-01-22
If udev assigns serial-number specific items (like eth ports), you may get new interfaces (wlan2, eth1, etc). Easy enough to clean out the old-motherboard-specific rules from /etc/udev/rules.d/

---

