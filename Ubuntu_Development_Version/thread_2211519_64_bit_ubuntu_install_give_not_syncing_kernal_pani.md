---
title: "64 bit ubuntu install give not syncing kernal panic as it did before"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-16
There is only one drive in the PC
It was wiped by the install.

I setup a seperate / root and / home  in the installer.
The installer finishes a reboot gives this error.

So what is wrong?
Google this error seems to say the grub cant find the os.

---

### Post by sdowney717 on 2014-03-16
tried 64 bit install again and get same error, this time just letting the installer do the defaults.

I can install and run 32 bit, cant run 64 bit on this CORE2DUO board.
I can run 64 bit live usb just fine.

---

### Post by dwoodwar on 2014-03-17
I seem to have a similar issue.


Using a 64bit HP6730b laptop.

I used the Beta1 of Xubuntu fine.  but there where lots of updates to be done post install, so I tried 16 & 17 March daily xubuntu image, installation goes fine, but on reboot the machine hangs for a few seconds then I get dropped into a initramfs prompt.

Looking at /dev from this prompt does not show any disks.  Trying to manually insmod any of the drivers, seems to give an error message about the .ko file being the wrong format, even though they work from the Live Boot disk.

---

### Post by sdowney717 on 2014-03-17
To get 64 bit working, I had to install 64 bit saucy, then upgrade it to trusty.
Took a lot longer, but trusty working ok except for LAN network shares.

---

### Post by oldfred on 2014-03-17
Some older BIOS will not boot or grub will not boot from a large / partition. So if hard drive is larger, a default install creates too large of a / partition.

Often better anyway to have / at 20 or 25GB and use rest of drive for /home and small swap.

---

### Post by sdowney717 on 2014-03-17
is 200 gb too large?
drive is wd2000

---

### Post by oldfred on 2014-03-17
It can be. 
Old BIOS had a 137GB limit.

Also what setting is BIOS have hard drive, better to be AHCI or LBA (large block allocation or large), but not IDE nor RAID. If you have IDE it may emulate the old BIOS limit even with a somewhat newer BIOS.

---

### Post by sdowney717 on 2014-03-17
When I get a chance, I will look.
BUT, the motherboard is set to default settings, so people who will be installing ubuntu WILL experience this bug, 
it is pretty severe and discouraging bug to be presented with that screen on boot.
It WILL turn people off and they will say linux does not work.

It is a core 2 duo MSI 7529 intel G31 chipset MB.
Running on the IDE port, no SATA drive is in this.

---

### Post by oldfred on 2014-03-18
Are you using cable select and have the 80 conductor cable to drive with jumpers on drive set to cable select? 

Drives actually have not used IDE since hard drive went over 8GB. Back then we had to key into BIOS the CHS settings of the drive. Since then it has been LBA or large block allocation.

---

### Post by sdowney717 on 2014-03-18
> Are you using cable select and have the 80 conductor cable to drive with jumpers on drive set to cable select? 

yes

It is a wd2000 PATA drive, not SATA

First time I ever seen that Ubuntu error was with Trusty install.

Your going to get lots of people like me with default bios settings and PATA drives installing trusty like I did from scratch and I hope they dont get that screen.
Because it is an instant turn off, to someone who is not familiar with Ubuntu and makes you wonder about Linux. I know for a fact some of my family would see that and tell me linux does not work.

---

