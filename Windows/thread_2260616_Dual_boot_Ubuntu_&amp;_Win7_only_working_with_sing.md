---
title: "Dual boot Ubuntu &amp; Win7 only working with single OS"
date: 2015-01-13
forum: Windows
---

### Post by Black_Sirrah239 on 2015-01-13
Okay, so I decided to install Ubuntu alongside my current Windows 7 install. This is the method I used, however here is some quick information:
I have 2 drives, 1x 64GB SSD (Home of Windows) & 1x 1TB HDD (Home of everything else). What I did to install Ubuntu:
[LIST]
[*]Partition HDD into 2 parts; 32GB for Ubuntu and 900GB for other data (both NTFS at this point)
[*]Install Ubuntu 14.10 onto USB and boot into Ubuntu
[*]Run Ubuntu installer
[*]Partition HDD further; 32GB partition is split into 2GB swap and 30GB ext2
[*]Set 30GB partition as '/' and 2GB as swap
[*]Attempt install
[*]Reboot computer
[/LIST]
At this point, I was unable to boot into Ubuntu and whenever I tried Windows would start up by default (Note: Windows was working perfectly fine, no booting issues or anything). By booting back into my livedisc (or USB...), I attempted again.
[LIST]
[*]Set 30GB partition as '/', 2GB as swap
[*]Set bootloader to SSD (I didnt double check this last time)
[*]Attempt install
[/LIST]
However, now I am only able to boot into Ubuntu, even though I can see all my Windows files are still there. 

Is there something I have overlooked in my tiredness and is causing problems? Both attempts I was only able to run from 1 OS that the system decided to boot and I have not been able to find a way that offers me to choose which OS I want to boot to.

---

### Post by Black_Sirrah239 on 2015-01-13
Fixed! I managed to do so by following this [man's beautiful advice]("http://askubuntu.com/a/100246") and installing 'Grub Customizer'. After doing so, moving 'Windows 7 (loader)' to the top of the boot order, it now opens grub on boot and asks which OS to boot into. Good luck to anyone else experiencing problems similar and found their way here!

---

