---
title: "URGENT!!! Partitioning hangs when using LIVE CD"
date: 2008-07-30
forum: System76 Support
---

### Post by Controls_Nut on 2008-07-30
Hi!

I'm having a bit of a problem right now, I decided to dual boot my Serval Laptop with Windows XP, because there are some Windows only programs I really need to use that aren't supported by Wine. So I decided to follow the directions as laid out in the System 76 Support pages:
 
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

I booted from the Ubuntu Live disk and have started resizing the partition, I'm guessing it's checking both partitions at this point but it keeps hanging up every 10-20 seconds. I have to keep 'waking' it by moving the mouse otherwise it just sits there and does nothing. It has 3hrs remaining, I don't want to have to sit here that whole time feeding it continual input so it doesn't hang up. ANY SUGGESTIONS!!!!!!

---

### Post by Controls_Nut on 2008-07-30
I decided to cancel the operation, and the laptop still boots okay, but it may have done something to the file system. Is there a way to check it and correct errors if it finds any?

---

### Post by justborn on 2008-07-31
it may be because of less ram speed .what is ur ram speed?

---

### Post by thomasaaron on 2008-07-31
To repair any damage done to your filesystem, you will want to run fsck *from a live cd* on your partitions. For example
```
sudo fsck dev/sda1
sudo fsck dev/sda2
```
etc...

Regarding the freezing, please tell us which computer you have. There is a freezing bug that requires some kernel parameters to be installed in your menu.lst. If this is the case, you would experience occasional stalls when booting your computer as well.

If this is not the case, give us more info on the configuration of your system: how much ram, what cpu?

---

### Post by Controls_Nut on 2008-08-01
I have the Serval Performance w/ 4GB DDR2 and the 2.5GHZ processor, recently purchased (couple of months ago), love the machine, and yes, it does hang on startup.

Okay, now I would really like to get the freeze thing fixed for the live cd, because installing windows resulted in failure. I went so far as to create an XP install disc with the correct SATA drivers, only to get past that problem and find that I have the max # of partitions allowed and Windows XP will not install. Guess I'll have to find another solution. 

OK, I stuck around my laptop for the last hour continually moving the mouse for an hour, to then move to another step which would take over 2.

Step 1: What ISO file should I download to create the Live CD? I assumed it would be the 64 bit version of 8.04.
Step 2: If I was correct in step 1, why would the partition editor pause, and require user input (mouse movement) to "unpause" it.
Question: Should it really take over 3hrs to extend sda3 from the current 102GB to 132GB?

The one praise I have for this, is, despite all my screwing around with sda3, I do not appear to have any data loss and the laptop still boots up ok (However the hangups when booting or checking disks is really annoying).

Thanks for your help.

---

### Post by thomasaaron on 2008-08-01
I think you sent me an email on this, in which I told you how to fix the freezing on while booting. This will probably also fix the freezing your having during partitioning.

If I'm wrong, and it wasn't you I sent the email to, please follow these directions to fix the freezing while booting. *THEN* try to install Windows.

1. Go into your BIOS setup menus, to the Advanced tab, and disable AHCI.

2. add clocksource=jiffies to your kernel option as follows

In a terminal, enter this command. It will pull up a text file that you will need to modify.

sudo gedit /boot/grub/menu.lst

Make your first kernel line look something like this...
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=3887ab68-7cd4-462e-9d56-8b2096f10353 clocksource=jiffies ro quiet splash

Next, find the line that looks something like this...
# defoptions=quiet splash
...and add the kerenl option to it so it looks like this...
# defoptions=quiet splash clocksource=jiffies


Save and Reboot.

---

### Post by Controls_Nut on 2008-08-01
Thank you, Thank you, Thank you, Thank you....and so on and so forth.

Although I don't know if the Live CD partitioning thing is fixed (I'm not sure how changing the installed linux grub menu will do anything when booting entirely from a CD), I did decide to try formating the 30Gigs to NTFS, and now the windows disc recognizes it! I'm currently formating to FAT32 so I can share files between systems (is this necessary?).

I did send you an email, although I haven't received one from you, so my guess is your thinking about a different individual. Next question, do I have to keep the AHCI off to stop hangups? Or now that I've edited the grub menu can I change it back?

---

### Post by thomasaaron on 2008-08-01
Not sure. I still need to test that.

---

### Post by Controls_Nut on 2008-08-01
Thanks for all your help, I think I might right my own quick tutorial for how to dual boot, now that I have successfully done it myself. You may want to mention the following things in the system76 tutorial on adding MS windows:

1) You may want to turn off AHCI in the bios before attempting the dual boot procedure.

2) If you are installing Windows to a Third or Fourth Partition, especially fourth, use Gparted on the live CD to format it to NTFS first, this helps Windows recognize the partition, and it can be reformatted to NTFS or FAT32 from the windows install disc.

3) If you are installing Windows to a third/fourth partition, the lines you add to the Grub menu (the final step) should be:

title Windows   (whatever you want, e.g. "title Windows XP")
root (hd0,#)    (# - the partition you installed windows to index starts at zero, so the fourth partition is (hd0,3)   
chainloader +1


P.S. - 
A note about #1, Windows XP install discs (including SP3 discs) do not include the drivers for SATA AHCI controllers, so the XP install disc may not find your hard drives. While turning of AHCI in the bios might fix this, I made a new XP install disc with the drivers included using nlite (nliteos.com) for which you can find tutorials. Here is where my note comes in, finding the drivers:

Go to konsole and list the pci info using lspci, somewhere in there it should list your SATA AHCI controller, for example, mine was: (for the Compal JFL92 Serval Performance Notebook)

Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)

If you have an Intel Controller, go to Intel's Website and then the download page. Here is where you may need to do a bit of searching, my controller is part of the "Mobile Intel GM965 Express Chipset" I found this by using the search function on the Intel page and typing in 82801 and looking through the search results.

Once you have found the correct chipset family, find it on the download page, for example, chipsets >> Laptop Chipsets >> Mobile Intel GM965 Express Chipset".

Select the Micrsoft OS you are going to install, and on the following page, find the Configuration Utility for pre-installing raid/SATA drivers (it may say something about hitting F6 during install in the description).

What I downloaded was a Zip archive containing bootable floppy files, including the driver files I needed to use with nlite.

Confused? 
Step Summary: 
Determine SATA AHCI controller using lspci.
Find drivers on manufacturers website (hard part).
Use with nlite to create Windows install disc (plenty of tutorials available [tutorial]("http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/")).

---

### Post by thomasaaron on 2008-08-01
Good job.

Thanks for posting your information.

---

### Post by flaflashr on 2009-04-18
Be patient!  The partitioning step does take a long time.  We just installed on an HP Pavillion dv7 with Vista using Kubuntu 8.10 AMD-64, and the partitioning step took 14 minutes, including tapping keys and moving the mouse.

Your virtue will be rewarded :P

---

