---
title: "SATA HDD using PCI card in Dell Optiplex GX1"
date: 2008-12-13
forum: Server Platforms
---

### Post by Jeztastic on 2008-12-13
Hi

I am setting up a server on a Dell Optiplex GX1 piii 450. I have a 500 GB SATA HDD, and I have attached it via a SATA - PCI Card. I would like to install straight onto this drive with no other drive attached. 

Is this possible? Any other tips? I am not going to bother with RAID at this stage.

Cheers,

Jez

---

### Post by logos34 on 2008-12-13
should work...give it a shot. If the Bios fails to recognize the drive, play with different hard disk detect settings.  

Sometimes sata pci host adapter cards can allow install but then fail to boot the system.  Hopefully that won't happen to you.

---

### Post by Jeztastic on 2008-12-13
Yup, the installer found it. :) 

I was worried cos i tried a live disk earlier, and it wasn't recognised then.

---

### Post by Jeztastic on 2008-12-13
OK, as you suggested, the PC will not boot from the SATA HDD. I've tried with SBM as well, and it doesn't recognise it... What now?

---

### Post by logos34 on 2008-12-13
hmm.  What about booting the ubuntu live cd and at the first menu selecting 'Boot from first hard disk'?

Maybe someone else knows a workaround.

---

### Post by Jeztastic on 2008-12-13
> **logos34 said:**
> hmm.  What about booting the ubuntu live cd and at the first menu selecting 'Boot from first hard disk'?


```
Boot failed: please press a key to retry 
```

:(

Whatabout grub? Will that recognise it?

---

### Post by logos34 on 2008-12-13
> **Jeztastic said:**
> ```
Boot failed: please press a key to retry 
```

:(

Whatabout grub? Will that recognise it?

if you have a floppy drive, I'd make a grub boot floppy to find out:
[http://www.google.com/url?q=https://help.ubuntu.com/community/GrubHowto/BootFloppy&sa=X&oi=revisions_result&resnum=1&ct=result&cd=1&usg=AFQjCNF7_w1B6j9Zv1hTtcwb-XLyxk8hzg](http://www.google.com/url?q=https://help.ubuntu.com/community/GrubHowto/BootFloppy&sa=X&oi=revisions_result&resnum=1&ct=result&cd=1&usg=AFQjCNF7_w1B6j9Zv1hTtcwb-XLyxk8hzg)


or a grub cd:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

---

### Post by Jeztastic on 2008-12-14
I tried super grub disk. Is that more or less the same thing? Didn't work either, although I may have been doing the wrong thing...

---

### Post by logos34 on 2008-12-14
if sgd didn't work you're probably SOL.  Then again maybe another pci sata adapter card with a different controller chipset may work.  I don't know if that's an option for you. One workaround would be to connect the drive via USB, but that means a taking a hit speed-wise (again not sure if that's an option given this is a server setup). 

sorry, fresh out of ideas...never had to deal with these cards.  all I can say is do a little googling and let us know if you find one.

---

### Post by caljohnsmith on 2008-12-14
You could check to see if the SATA drive is even being recognized by BIOS on start up by booting your Super Grub Disk, and at the first main menu press "c" to get the Grub command line; then type in the following without pressing enter:
```

grub> geometry (hd

```
And press TAB for tab-completion to see a list of your drives, starting with (hd0). Then to see the size and partitions of a drive such as (hd1), use:
```

grub> geometry (hd1)

```
If one of those (hdX) drives is your SATA drive, you can most likely boot it. But if Grub doesn't even show your SATA drive with the above commands, that could mean BIOS doesn't recognize the drive or the drive is not properly configured in your BIOS. How about giving that a shot and let us know the results.

---

### Post by Jeztastic on 2008-12-14
```
Possible disks are: fd0 hd2 cd
```

I assume that hd2 is the SATA drive, as I don't have any others connected.

Geometry of hd2 outputs;

```
drive 0x82: C/H/S = 0/1/15, the number of sectors = 2147483647, LBA
```

So it recognises the drive - how do I boot?

BTW, I have googled extensively on this already, most people seem to use workarounds with a second HDD, this isn't really an option for me.

---

### Post by caljohnsmith on 2008-12-14
Did the "geometry (hd2)" command show any partitions, or just the size of the drive as you posted? You can try booting the drive by going to the Grub command line again, and enter the following:
```
grub> rootnoverify (hd2)
grub> map (hd2) (hd0)
grub> map (hd0) (hd2)
grub> chainloader +1
grub> boot
```
And let me know exactly what happens.

---

### Post by Jeztastic on 2008-12-14
> **caljohnsmith said:**
> Did the "geometry (hd2)" command show any partitions, or just the size of the drive as you posted? 

Nope, that's everything. Will try booting now...

---

### Post by Jeztastic on 2008-12-14
> **caljohnsmith said:**
> Did the "geometry (hd2)" command show any partitions, or just the size of the drive as you posted? You can try booting the drive by going to the Grub command line again, and enter the following:

And let me know exactly what happens.

I got the following error messages;

```
grub> rootnoverify (hd2)
grub> map (hd2) (hd0)
grub> map (hd0) (hd2)
grub> chainloader +1

Error 13: Invalid or unsupported executable format

grub> boot

Error 8: Kernal must be loaded before booting


```

---

### Post by caljohnsmith on 2008-12-14
I noticed in your post #11 that Grub reports your SATA drive as having 2147483647 sectors, and since each sector is 512 bytes:
```
2147483647 * 512 = 1099511627264 bytes = 1.1 TB
```
So if your SATA drive is really 500 GB, then Grub doesn't detect it correctly, or that could mean the BIOS doesn't detect it correctly. Also, Grub should be able to see the partitions on the drive, which it couldn't. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
And for whichever is the SATA drive it lists, do:
```
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
So replace sda above if the SATA drive is a different device. Let me know how that goes.

---

### Post by Jeztastic on 2008-12-14
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001f75d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   972237734   486118836   83  Linux
/dev/sda2       972237735   976768064     2265165    5  Extended
/dev/sda5       972237798   976768064     2265133+  82  Linux swap / Solaris

```

And for whichever is the SATA drive it lists, do:

```
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda


```

Sorry, you've lost me here... am I replacing xxd with the disk identifier?

---

### Post by caljohnsmith on 2008-12-14
Since your SATA drive shows up as sda, you can just use the commands as given:
```
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
But I think at this point you most likely have a problem with how your SATA drive is set up in BIOS, because Ubuntu correctly sees the drive as 500 GB and also sees the partitions OK. Yet Grub on start up was not able to see the partitions nor detect the correct drive capacity, and on start up Grub works through the BIOS to access the drives. Can you go into your BIOS and check how you have the SATA drive configured? Some of the HDD-related settings to look for in your BIOS are "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. I would try changing any HDD-related settings you have one-by-one and see if that changes how Grub detects the HDD on start up. I would recommend writing down any settings you change so you can revert back to the original values if necessary.

Also, since Grub showed your SATA drive as (hd2) on start up and not as (hd0) or even (hd1), do you have another SATA port you can plug the drive into to see if it changes anything? That might give an important clue what is going on. Anyway, let me know how it goes.

---

