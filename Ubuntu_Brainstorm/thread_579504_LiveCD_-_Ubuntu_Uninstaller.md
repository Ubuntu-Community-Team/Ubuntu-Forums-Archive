---
title: "LiveCD - Ubuntu Uninstaller"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by GutsyGibbon on 2007-10-18
**The main idea**
My idea is adding an Ubuntu-uninstaller. so that windows / mac users will be able to completely remove Ubuntu and canceling it's partition from their HD.

**What is it good for?**
Many users don't have the original installation CD of their OS. so they can't use it for re-partitioning.
The uninstaller will allow them to cancel the Ubuntu partition easily.

Have a great day!:guitar:

---

### Post by smartboyathome on 2007-10-18
Ubuntu can't redistribute the windows bootloader, and you can just remove the patition for Ubuntu to uninstall it. How do you propose to replace the bootloader with windows'?

---

### Post by r3m0t on 2007-10-18
That's pretty simple. When you install, copy the windows MBR (it's only 446 bytes) into a file in the linux partition, and perhaps also in Windows. When you uninstall Ubuntu, if your filesystem is not corrupt, it can find that file and use a program such as dd to put it at the beginning of your hard drive.

Edit: but look how short the MBR code is. Do you think it can be copyrighted?

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

[http://en.wikipedia.org/wiki/Lexmark_Int'l_v._Static_Control_Components#Majority_opinion](http://en.wikipedia.org/wiki/Lexmark_Int'l_v._Static_Control_Components#Majority_opinion) (note that the simple code there was not copyrighted)l

---

### Post by GutsyGibbon on 2007-10-18
> **smartboyathome said:**
> Ubuntu can't redistribute the windows bootloader, and you can just remove the patition for Ubuntu to uninstall it. How do you propose to replace the bootloader with windows'?

I actually have no idea.
well, we have time. I belive we could think of a way and figure it out by December...
I don't really know **that** much about these things. just an idea.

---

### Post by climatewarrior on 2007-10-20
I think this is a good idea because it would make people feel safer of trying Ubuntu. I think it would also be a good idea to include a GUI grub tool for people that want to set windows as their default OS. 

The only reason i think this stuff is good its just to make people feel safer to try Ubuntu and Linux. Not to promite that people have Ubuntu as a toy in their computers.

---

### Post by Zdravko on 2007-10-20
+1.

---

