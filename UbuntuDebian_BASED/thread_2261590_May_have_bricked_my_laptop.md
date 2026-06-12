---
title: "May have bricked my laptop"
date: 2015-01-20
forum: Ubuntu/Debian BASED
---

### Post by dylan35 on 2015-01-20
This may or may not be the right forum but I don't think there would be any active ones for my OS (Kali Linux) and I feel this is a more general question as it could probably happen on any system, I was SU (root) in the terminal on a normal privileges account as I cannot sudo, it would tell me the account is not in the sudoers file so I would just su, do admin level commands and exit su, but this time something went horribly wrong. I went into su and executed:

aptitude update

And

aptitude install libreoffice

Normally these commands would simply update whatever it was updating and install libre office, but this time I kinda let the command run and didn't pay much attention, mid way through I noticed a lot of "removed x" where x would be a range of my programs, and majority of them were system-level programs that of course when removed broke my system, it eventually got to the point of asking to remove the Kernel and gave a warning it would totally break the OS if done, so in panic i denied removing the kernel, closed the terminal and as expected couldn't launch any programs at all, USB's, the CD drive and networking were now also broken, I rebooted to see if that would fix it and now the GUI side of my OS is broken and unbootable, commands such as fdisk no longer worked and so I rebooted into recovery mode, fdisk now worked but I realised my USB ports no longer properly detected any USB or my Samsung when plugged in. I am trying to make a Live USB of Linux Mint on another partially broken laptop (Windows 7 with no drivers) and seeing if it will boot into that from the BIOS on my Linux Laptop. Has anyone encountered this before and if so, is my laptop totally bricked and how can I fix this.

---

### Post by Impavidus on 2015-01-20
So a lot of essential programs have been uninstalled and the package manager may be in an inconsistent state. It may be possible to fix this, but the fastest solution will be reinstalling. If you keep a backup of your home directory (or even easier, if you had a separate /home partition) you can keep all your personal files and configuration.

---

### Post by oldos2er on 2015-01-20
Moved to Other OS Support and Projects. 

> This may or may not be the right forum but I don't think there would be any active ones for my OS (Kali Linux) [https://forums.kali.org/](https://forums.kali.org/)

---

