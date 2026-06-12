---
title: "Clean Install from stick fails"
date: 2012-07-25
forum: Ubuntu Studio
---

### Post by Redeen on 2012-07-25
I would like to install the latest version of Ubuntu Studio to my Dell Inspiron 1420. I am currently running 10.04 LTS Lucid Lynx and notice the recommendation is for a clean install from DVD or thumb drive. I was unable to write a DVD, so put the img file on thumbdrive and used F12 command during startup to select 'boot from thumb drive'. Apparently, it cannot find the path:

/ubnkern initrd = /ubninit

I unpacked the image to the drive - see screenshot, and there is no such directory. Not sure what to do from here. Ubuntu Studio is working fine, with one exception - WiFi croaked somewhere down the line. I was hoping a clean upgrade might help fix that problem, for which I've made a separate post. I haven't done any upgrades since everything has been working and Studio has a modified kernel - assumed any upgrades would have to be with this distro going forward, not with generic Ubuntu.

---

### Post by jejeman on 2012-07-25
How did you make live USB?
I suggest that you make it again. I recommend unetbootin for creation of live USB.

---

### Post by Redeen on 2012-07-25
Thank you. I did use unetbootin to create the thumb drive. On trying again, I paid attention to an alert "missing p7zip-full" and after installing that, was able to boot (chickened out and previewed it without installing - highly confident that will now work). 12.04 looks great, BTW!

---

### Post by Redeen on 2012-07-26
I did the clean install, everything looked great, now on boot-up, all I get is a blinking cursor. I am playing around with setup, but it's looking very bad. :(

---

### Post by 2F4U on 2012-07-26
What are your hardware specs? Some video cards such as nVidia or ATI require the nomodeset grub kernel parameter to boot up correctly. Once the proprietary drivers are installed, this is no longer needed.

---

### Post by Redeen on 2012-07-26
Thanks for the speedy reply.  Does the following help? When I boot from stick, it no longer gives the option to (re-)install - how can I enable nomodest?  

From owner's manual: 

Video Controller: Intel 965Gm Express chipset 64MB shared mem. 1 GB system memory. 
**Video Type (controller) NVIDIA GeForce 8600M GS**

Graphics Bus: PCI-E X16


Additional info: 

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

---

### Post by Redeen on 2012-07-26
NOTE: I tried editing /etc/default/grub with the addition of nomodeset, but it still does not boot from the hard drive.  What physical device is the above path on?

I notices that on (clean) install, it said three partitions would be deleted, I got it to display the partitions, but it didn't show what was being deleted - I assumed whatever was created would work, but perhaps my Dell bios is looking to start from a directory that no longer exists? This is just an uneducated guess.

---

### Post by jejeman on 2012-07-26
After changeing /etc/default/grub you need to update grub for changes to take effect.
```
sudo update-grub
```

---

### Post by Redeen on 2012-07-26
sudo update grub seemed to run succesfully. Still not popping. 
On installing, I had left the room. There was something on the screen when I returned, and I bumped the space bar. Possibly some message about the install?  I can't see how to just start over and re-install from the stick.

---

### Post by jejeman on 2012-07-26
Please, write short and clear summary of your situation and what you want to achive.
I'm lost here.

---

### Post by Redeen on 2012-07-26
Terribly sorry - that was garbled. 

**Situation:**  installed Ubuntu Studio 12.04 onto a Dell Inspiron 1420 laptop from the thumb drive. 

*Upon rebooting, the Dell logo comes up, then I get nothing but a blinking cursor.* I can get into setup or choose device to boot from, via function keys. 

Additional details possibly of relevance:

This was a clean install, so when a message appeared saying some partitions would be deleted, I assume that was OK - just mentioned this in case it's important.  Everything looked normal, but I may have missed something on the very last screen, which vanished before I could read it. 

I do not recall all of the options I selected, but it was just things like username and time zone, as you know. I noticed that although I created my own account Setup says admin password is not set. I doubt this matters. I chose "log in automatically" as well.  

**My Goal: ** *I would like to be able to boot from the hard disk. *Right now, I can only boot from the thumb drive. 

I have asked several ancillary questions as they came to mind. One obvious thought is to just try installing again, but when booting from the thumb drive, it no longer presents the option, and I'm not sure what command initiates this, or if it's even necessary - it was just an idea.  

The other question was when I am in the terminal window performing the recommended edits,  whether these edits are taking place on the hard disk, or a virtual disk that is only on the thumb drive. I assume the former, but seeing as I booted from the thumb drive, I was slightly worried that I was editing something that would not be found upon rebooting from the hard drive - I know, grasping at straws. 

I have poked around the forum, and see that the advice you gave generally works. One more note - this particular laptop was one that came from the factory with Ubuntu only, no Windows. I hope all of the above wordiness clarifies things.

---

### Post by jejeman on 2012-07-27
Yes, it clears up.
>  I chose "log in automatically" as well. Generaly, this should be avoided, but it does not have anything with your situation right now.

Boot the USB and issue this command
```
sudo parted -l
```
to see if everything is ok. Paste back the output.

As for the nomodeset parameter do like this>
boot from hdd, during the Dell screen start presing left shift quickly many times, this should make Grub appear. Then edit the kernel line for first entry (read instructions at bottom of the grub screen). When in edit mode (E) find "quiet splash" erase them and write "nomodeset".

Tell us if this works.

---

### Post by Redeen on 2012-07-27
Output you requested. Pretty sure I cannot do the 'shift' button trick, because when booting from HDD, Dell screen never appears, just blinking cursor as I mentioned. Will try it anyway. I did not delete "quiet splash" when editing the original file (just went by what I spotted elsewhere on the forum) - so I'll try that, too. 

Note: It dawned on me to check support.dell.com and do a general search.  Found something on restoring factory setup, but only if restore partition has not been wiped. Might be worth a shot if all else fails.

Model: ATA TOSHIBA MK1637GS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1393kB  15.8GB  15.8GB  primary  fat32        boot, lba

---

### Post by Redeen on 2012-07-27
Tried shift key and re-editing /etc/default/grub - no luck. Looking for restore media in case the problem is missing boot sector or something along those lines. 

p.s. - I have the original Ubuntu 7.04 disk, still shrink-wrapped!
;)

---

### Post by mastablasta on 2012-07-27
if nomodeset doesn't work could it be that you installed Grub on the wrong place.
it's a bit strange that install option is gone as you say. if oyu boto form USB a menu should come first offering try it and among others install.
 
this script could tell where and how the system is installed and also what happens on boot: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Redeen on 2012-07-27
OK I ran the script. Output attached & looks like it might shed light on the problem.

---

### Post by jejeman on 2012-07-27
> No boot loader is installed in the MBR of /dev/sda.
You have installed grub on USB (sdb) not on HDD (sda).

So you need to have USB plugged in in order to boot OS from HDD.

Do the following:
Boot from USB as you do.
Install Grub on HDD (sda) with this command
```
sudo grub-install --root-directory=/ /dev/sda
```
Shutdown PC
Unplugg usb
Start PC.

---

### Post by Redeen on 2012-07-27
Hooray, it booted! 

I suspected something like this, but have never used grub.

Many thanks for seeing this all the way through, speed of response, etc.  This upgrade was long overdue, and now I have better tools at my disposal. Doubt I could have figured this out on my own.  

Ubuntu Studio 12.04 looks spiffy - no regrets.

---

### Post by Mishrito on 2012-07-28
Yep I had to manually install GRUB on my HDD too while installing Ubuntu Studio from a Live USB. This should be looked into in the next release.

---

### Post by jejeman on 2012-07-28
User can choose during setup on wich disk grub should be installed or not?

---

### Post by Mishrito on 2012-07-28
> **jejeman said:**
> User can choose during setup on wich disk grub should be installed or not?
You can? I might have missed it during the installation then.

---

