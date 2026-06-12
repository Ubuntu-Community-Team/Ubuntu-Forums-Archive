---
title: "Flashing amber light on Dell Server"
date: 2008-08-23
forum: Server Platforms
---

### Post by hmhmhm on 2008-08-23
Hi,
I run 8.04 on a Dell Poweredge 1650. A few days ago, the amber light started flasing. I read the user manual and it says:

> The amber system status indicator flashes when the system needs attention due to a problem with power supplies, fans, system temperature, or hard drives.

I opened the server and the power supply and fan LEDs are all green, i.e. seem to be working ok. When I boot the machine, it says my RAID is 'optimum' and the HD LEDs seem to indicate likewise. What could cause the amber light to flash? How can I check the temperature? I maintain the server via Webmin and there isn't any information about an error there either.
Any help would be great.
Thanks!

---

### Post by windependence on 2008-08-23
One of your power supplies is bad.

-Tim

---

### Post by hmhmhm on 2008-08-25
I replaced both power supplies today, and the amber light is still flashing. Each power supply has two LEDs and they are all green. Why do you think it is the power supply?

---

### Post by insane_alien on 2008-08-25
temperature? give it a blast of compressed air to clean out the dust.

---

### Post by lordmontie on 2008-08-25
First comfirm that all hard drives are fully funcation by going into the RAID BIOS configuration tool at boot time. Use one of the options to see info about the physical disks. If all disks display info, than they should be fine.

Then check all the system fans to make sure they are running. Open the top of the case and turn on the system. Look at all the system fans and if anyone is not spining like the others, replace it.

---

### Post by hmhmhm on 2008-09-03
Unfortunately, I'm not having any luck with this. I gave it a good blast from the compressor, checked all the fans (they are all working) and the RAID BIOS signals that all HDs are working fine (which seems to be right, because the HD LEDs indicate the same). Is there no way to find out what exactly causes the amber light to flash? And how can I find out the temperature?
Thanks for all the help so far!

---

### Post by inphektion on 2008-09-03
One prob with ubuntu on the dell... no way to upgrade esm or perc card bios... and all the nice tools and utilities dell has for windows that would exactly tell you why the amber light was flashing, don't work on ubuntu....
Maybe there is a dell boot disk you can boot from that will do a check... 
I'll look cause I could use one too.

---

### Post by windependence on 2008-09-04
> **hmhmhm said:**
> Unfortunately, I'm not having any luck with this. I gave it a good blast from the compressor, checked all the fans (they are all working) and the RAID BIOS signals that all HDs are working fine (which seems to be right, because the HD LEDs indicate the same). Is there no way to find out what exactly causes the amber light to flash? And how can I find out the temperature?
Thanks for all the help so far!
Check your RAID battery. I have ordered one for mine because I am pretty sure that is the problem.

-Tim

---

