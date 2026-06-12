---
title: "How to connect to an existing network - conclusion"
date: 2015-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by jfh on 2015-08-27
I started this process several days ago with chili555 trying to help.  The problem was (and is) a lack of ethernet and network drivers on my old computer.  By going to a Belarc Advisor printout I'd made months age, I found an entry for "Marvell Yukon 88E8050 PCI-E ASF Gigabit Ethernet Controller #2".  I went (on my new computer, of course)to Marvell's website and found a Linux download for that controller, which I downloaded to a USB drive, and from the USB to the old computer.  It was a zipped file (.tar), but I managed to unzip it and opened the txt file containing the instructions for unpacking and installing the thing -paragraph after paragraph of instructions, most of which I didn't understand.  Nevertheless, it did give some entries to use in Terminal, which I entered several times without success until on one effort it seemed to unpack the thing and asked for my password - which Ubuntu failed to recognize.  I then tried to boot while pressing the shift key - no luck - it even told me at one point that GRUB (whatever that is) was not installed.  I decided to make one last effort - and this time it immediately recognized my password, but still would not install the thing. 
I had installed Ubuntu 14.04 on the computer using the option to format the hard drive.  I wonder if this had the effect of deleting any items I needed to connect to the internet?  The reason I suspect this is that, after all these problems, I tried using a Vista installation disk to install Vista and delete Ubuntu, but the Microsoft Vista installation disk soon told me that I lacked the drivers for ethernet and network.
One thing that puzzles me is that I have used Ubuntu previously before with no problems.  I used it as far back as the days when Canonical would send you free installation CDs - from South Africa!  Maybe these newer versions are so much more complicated?  Who knows?
Anyway, I have one old computer that seems destined for the recycler - I had hoped to get it running so I could give it to some local charity, but I don't know anyone I dislike enough to inflict it on them it its present state. 
Sorry to have been so long winded, but thought some might be interested in this saga.

---

### Post by yancek on 2015-08-28
> it even told me at one point that GRUB (whatever that is) was not installed

GRUB:  GRand Unified Bootloader.  Without it you won't be able to boot Ubuntu.

> I had installed Ubuntu 14.04 on the computer using the option to format  the hard drive.  I wonder if this had the effect of deleting any items I  needed to connect to the internet?

Formatting the hard drive is basically overwriting everything on it for all intents and purposes for an average user.  I never used vista so wouldn't have any idea about how it acquires drivers for network hardware.  It would seem reasonable they would include them on the installation medium.

If this is an older computer you are planning to give away, Ubuntu may not be the best system for it.  You should compare your hardware with the minimum requirements at the Ubuntu site.  Something like Lubuntu or Xubuntu might work better.

---

### Post by Bucky Ball on 2015-08-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. :)

---

