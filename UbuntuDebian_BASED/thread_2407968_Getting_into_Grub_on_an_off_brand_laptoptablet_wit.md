---
title: "Getting into Grub on an off brand laptop/tablet with an Intel Atom z3735f"
date: 2018-12-11
forum: Ubuntu/Debian BASED
---

### Post by clockworkmrdr on 2018-12-11
I'm working with a "Medion Akoya MD 99782 ." It's a cheap little tablet/netbook hybrid with an Intel Atom z3735f processor and 32 bit windows 10. Based on all my research, this processor is 64 bit, but the UEFI is 32 bit, leading to problems with the boot loader. After a few days of messing around with BIOS, UEFI and so on, I finally managed to get a isorespin.sh version ([linuxium]("http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html")) of Lubuntu 18.04 installed onto a 15GB ext4 partition on the drive. I installed it via live USB. Secure boot is disabled, and after using the Ubuntu boot-repair tool Ubuntu shows up in the BIOS HDD boot order (it's in fact listed twice), but setting the priority above windows doesn't stop the laptop from booting into windows. If I press F10 when the computer first boots up I can manually select Ubuntu, but windows still boots. I've tried with and without secure boot, and I've used  ```
chroot
``` to run ```
sudo update-grub
```. That command worked as far as I could tell, though I don't have the exact output in front of me anymore. What can I try next to get grub to show up or enable Ubuntu to boot from the F10 menu?

---

### Post by howefield on 2018-12-11
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2018-12-11
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by clockworkmrdr on 2018-12-12
[http://paste.ubuntu.com/p/FMmk85DPXY](http://paste.ubuntu.com/p/FMmk85DPXY)

Thanks for taking the time!

---

### Post by oldfred on 2018-12-12
Looks like you have Windows fast start up which sets hibernation flag on. Boot into Windows & turn it off.
See line 156 & up.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Your MMC drive is small for Windows & not really large for Ubuntu. Can you use different MMC card for Ubuntu & Windows? Or is card built in?
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by clockworkmrdr on 2018-12-12
I'll give that a try later tonight; I completely forgot about that feature. I don't know whether the card can be replaced or if another can be installed; there's a micro SD slot but I need the SD to store files which were previously taking up space on the windows partition. Despite freeing up nearly 30 GB and disabling the page file on the windows partition, I couldn't shrink the partition any more than 15 GB with the windows disk utility.

---

### Post by oldfred on 2018-12-12
You generally do not want to shrink NTFS partitions too much. They need 30% free to run well. And at 10% free their is almost no room for defrag to rearrange data.

---

### Post by clockworkmrdr on 2018-12-12
Turning off fast boot didn't do it. I wonder if I used the ISO respin script correctly? All I used was the --atom option (for WiFi and audio support), as the base script adds the 32 bit grub by default. Since I already used the boot repair tool and messed around with grub using chroot, I think I should probably reinstall the ISO and see if it will boot with all the default options now that fast boot is turned off.

---

### Post by freemedia2018 on 2018-12-12
I've contacted the author of the respin script and pointed him this way. No promise that he will show, the script is from 2017 and I mostly wanted to congratulate him on writing it-- I like automated remaster scripts. 

I normally work with 32bit ones personally. I still use 32bit hardware (this machine is 64 bit) and remastering lets you do pretty much whatever you want-- if automated you can do even more.

I don't have any suggestions however, that you aren't already looking into.

---

### Post by clockworkmrdr on 2018-12-13
I've tried the isorespin script a couple of different ways now and still no dice. Seeing as how this isn't my laptop, I can't just format the entire MMC card and go solo Linux, as much as I'd like to. My next idea seems harebrained at best: if I can't do anything to get past the windows boot loader, but I CAN boot from USB, why not run a boot manager from a USB? Is that even possible? I'm looking into a boot manager called Plop to find out. Anyone here have any experience with that manager? Could I do the same with rEFInd? And what if I were to format the windows EFI partition and remake it through the Lubuntu installer? Would that lead to windows not being bootable?

---

### Post by clockworkmrdr on 2018-12-13
I figured it out. In the end it had nothing to do with grub, it was my own mistake for not setting the esp and boot flags on the EFI partition while installing. I figured that since the partition already existed, Lubuntu would use it to install Grub, but you have to do that manually.

---

