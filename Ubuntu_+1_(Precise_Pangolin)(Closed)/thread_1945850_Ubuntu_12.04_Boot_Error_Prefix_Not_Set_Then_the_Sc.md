---
title: "Ubuntu 12.04 Boot Error Prefix Not Set Then the Screen Displays Gargbage"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wgilthorpe on 2012-03-23
Has anyone experienced this problem? 
 
I downloaded the beta of 12.04 and tried to boot, both from a USB and CD.
 
When I try to boot the pc the following is displayed:
 
error prefix not set
 
Then the screen displays garbage in the form of thin white veritcal lines and all activity stops. 
 
All help will be appreciated.

---

### Post by uRock on 2012-03-23
Moved to *Ubuntu+1 (Precise Pangolin)*

---

### Post by komasoftware on 2012-03-31
same problem

seems to have to do with UEFI

im on a ASUS N53SV

---

### Post by Azyx on 2012-04-11
Same problem on Asus E45M1-M Pro, also EFI with 12.04 beta 2

---

### Post by Azyx on 2012-04-21
bump

---

### Post by kschumake83 on 2012-04-21
i have sort of the same issue i get the error message and the garbled grub screen but if i just hit enter it will boot from live cd and then i can install. i am also on a uefi bios

---

### Post by Azyx on 2012-04-21
> **kschumake83 said:**
> i have sort of the same issue i get the error message and the garbled grub screen but if i just hit enter it will boot from live cd and then i can install. i am also on a uefi bios

Now mine goes to the loader: Try Ubuntu, Check disk, Install, but my computer reboot when I select, Try Ubuntu or Check disk.

Will try with a daily build tomorrow.

---

### Post by Naugas on 2012-04-22
I experience a somewhat similar problem with my Asus u36sd-a1 (uefi bios apparently) - this "prefix not set" error flashes by when I try to boot up a live usb 64 bit build, then I get to the grub menu (Try, install, test) but whatever I select there it just freezes up after a few seconds with a blank screen.

Trying any 32 bit version it boots up just fine. I tried 11.10 and a few 12.04 daily builds (not the most current one, yet).

---

### Post by Azyx on 2012-04-23
The daily build won't even boot. If I only chose my Sandisk memory, named as UEFI Sandisk, I just come in to the UEFI/BIOS again.
Should the USB disk in Gparted be flagged 'boot, lba for a 64-bit, UEFI?

---

### Post by Naugas on 2012-04-23
uefi boot doesn't seem to work (without major reconfiguration of grub at least) on my u36sd - I had to remove the selection from the boot list, then disable uefi boot, reboot, and then select the device and boot through bios. See post at [http://ubuntuforums.org/showthread.php?p=11863942#post11863942](http://ubuntuforums.org/showthread.php?p=11863942#post11863942)

---

### Post by Azyx on 2012-04-26
I Tried 12.04 on another machine (P6NGM with a Nvidia GT520 1GB) and it boot, but the screen get 'overlapped', the left edge with a laungebar being seene near the right corner. The left edge are also more transparent but clickable, but the rigt have right colours, but did not have a clickable launcher bar.

---

