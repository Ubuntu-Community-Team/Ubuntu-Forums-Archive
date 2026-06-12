---
title: "So secure even I can't use it"
date: 2005-09-19
forum: Server Platforms
---

### Post by blackheart on 2005-09-19
I installed ubuntu 5.10 preview last night, having used the live version of the same release. I now can't get into any admin functions eg Boot, and Network Setup. It asks me for my password, and I presume this is my log-in password, which it won't accept. It comes up with [Starting Boot...] in the bottom panel, and then won't actually show the window. Should I be entering my root password, and why doesn't it always bring up the password box? Can I get rid of this protection (which is what I presume it is)? I might be a beginner to linux, but I've managed to administer a Windows PC for the last 10 years, and haven't gotten into any trouble doing that.

Any help would be greatly appreciated :D

---

### Post by blastus on 2005-09-19
Welcome to the forums!

You do not login as root in Ubuntu. Login to Ubuntu with the username and password you setup when you installed it. From there if you need root access, prefix your commands with "sudo." For example, if you want to edit the file "/etc/fstab" enter...

sudo gedit /etc/fstab

The sudo command will prompt you for a password. At this point enter your password. I believe the sudo command retains your password for 15 minutes. After that you'll have to enter in your password again IF you want to run something that requires root access.

---

### Post by sinbad782 on 2005-09-26
It's true - only in Windows are you given a single administrator account by default upon first installing and then never have to enter a password when installing random third party stuff. What is more, plenty of Windows apps break whenever you try and run them as a limited user - this even holds for many of the games that Microsoft themselves publish......

Users of *Nix, Linuxes, Mac OS X etc. all have to get used to confirming their intentions whenever they wish to make any significant changes to their systems. It may mean slightly less ease of use, but it's a hell of a lot safer.

---

