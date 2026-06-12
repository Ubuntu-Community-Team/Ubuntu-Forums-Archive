---
title: "Server won't boot after upgrading system"
date: 2008-05-21
forum: Server Platforms
---

### Post by Vendero on 2008-05-21
Hi everyone,

I'm new to these forums, and quite new to linux. I've poked around here and there, had some GUI-based linux distro's on my desktop, then installed Ubuntu server on a spare computer. I've made myself somewhat comfortable with the commandline and ssh, so I can log in from my university. The only drawback I could find was that openssh didn't support chrooting of users, at least not in an easy way. I came to hear that the latest version did introduce this feature however, so I fired up putty and selected 'upgrade all' (or something similar) in aptitude.

Great, let's reboot the server to make sure all services are running there new executables!

There I encountered my problem: all of a sudden my hard drive isn't detected properly anymore, or at least not as a boot device - d'oh! My system won't boot.

I could just reinstall the system, but I would really like to perserve my settings and, more importantly, I'd like to keep my SVN repositories. They contain some coding projects of which I would like to keep the revision history.

Anyway, does anyone know how I could resolve this problem? I'd like one that doesn't boil down to feeding the computer a live CD and copying all important data to a USB drive, then wipe it clean and reinstall the server.

Thanks in advance!

~Vendero

---

### Post by Antman on 2008-05-21
Please provide more details and than maybe someone can assist you:
What version of Ubuntu was originally on your machine?
What version are you trying to upgrade to?
What exact error messages are you getting when you boot the PC?
What type of hardware do you have?

---

### Post by Vendero on 2008-05-21
Ubuntu version: 7.10 server edition
I was actually just upgrading all packages which needed upgrading according to aptitude - not to 8.04 or anything. This included (amongst other things) the kernel and the openSSH daemon.

I run a Pentium III compaq, with a 13 gig internal hard disk and a 500 gig external USB 2 HD (although the comp only has USB 1)

The error messages change: "If youre running unix you need to update your system using a compaq floppy", "disk is not a valid boot disk", and, this one's new: "hard drive corrupted. Back up data on this disk and replace it to prevent data loss."

---

### Post by Vendero on 2008-05-21
Right, it seems my hard drive is corrupted. :S
The computer is now consistently outputting the last error: that I should back up my data and replace the drive. Seems this just happened to be at the same time as the updating.

Anyway, thanks for the help :)

~Vendero

---

### Post by mrtomservo on 2008-05-21
Just a stab in the dark here, but it sounds like your grub or MBR is screwy.  Sometimes that happens if you upgrade a kernel version or whatnot and something doesn't get updated properly.  If someone more knowledgeable than I has another suggest, i'd follow that one... but if all else fails perhaps reinstalling your bootloader (grub/lilo) would help, it shouldn't interfere with your existing setup.  I personally use superbootloader to reinstall grub the few times i've had to.

---

