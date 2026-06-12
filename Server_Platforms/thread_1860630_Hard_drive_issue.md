---
title: "Hard drive issue?"
date: 2011-10-14
forum: Server Platforms
---

### Post by jhawk1 on 2011-10-14
Hey everyone, I typically come to the forum to search for answers to any issues I may encounter.  Until now I have been able to find the answers but this current problem seems to have a few additional factors.

I was running Ubuntu server on an old desktop until my mom's company upgraded and I was able to take over theirs.  I ordered a 2 TB 6 gb/s (didn't need more than 3 gb/s but this seemed to fit every other category) Western Digital drive and was going to just do a clean install of Ubuntu 10.04 or 11.04 64-bit.  However, no matter what I do the installation stops before partitioning and says there is no drive detected and that I should select a driver.  

I tried going into BIOS/Raid controller to update the configuration but it will not allow me to make changes?  This leads me to believe that it is a problem with BIOS and not Ubuntu Server but I am hoping someone can provide advice to either issue. 

I have made sure that the drive is working.  I also reformatted it to NTFS trying to start fresh.  The server is a Dell Poweredge 2900 and they were originally running Windows Server.  I have tried a few different clean hard drives and none of them seem to be detected by the machine.  BIOS says no PD detected as well.  Any ideas what I could try next?  Maybe a BIOS firmware update? (although I have never done that before).

This is relatively uncharted territory to me and usually I would just try to troubleshoot my way through but I am out of ideas.  I have left out a few details I am sure so please let me know if there is anything else that you need to know.

Thank you so much!

---

### Post by DaveWut on 2011-10-15
Hi,

Try using your DVD / CD in another computer or for a virtual machine. Sometime I used to have the same problem and it only was because my installation media was corrupted! :/ 

Dave

---

### Post by vasile002 on 2011-10-15
Try booting from a livecd and check if the drive or controller is detected properly. You may need some drivers to load before the installation process

---

### Post by jhawk1 on 2011-10-15
Ok I booted into Ubuntu 10.04 from the CD and it still appears that no disk is detected?  It does not show under storage devices.  Also, I went into hardware drivers and it said that none were needed.  I thought drives were supposed to be plug and play?

---

### Post by jhawk1 on 2011-10-16
How would I flash BIOS/just start fresh?  Or update the firmware on the motherboard?

---

