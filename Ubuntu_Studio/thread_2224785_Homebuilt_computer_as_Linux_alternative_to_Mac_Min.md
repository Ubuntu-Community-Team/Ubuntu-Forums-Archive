---
title: "Homebuilt computer as Linux alternative to Mac Mini (2012)."
date: 2014-05-18
forum: Ubuntu Studio
---

### Post by globetrotterdk on 2014-05-18
I am a Linux user with a home built computer as my main computer. I have a Mac Mini (2012) that I have been using mainly for Guitar Pro 6, Rocksmith (2014), Garageband and truefire.com guitar tutorials. I decided to get serious and try to setup my home built computer to do some of the same things as I have been using my Mac Mini for. I have plenty of internal hard disks, so I decided to start out by installing Ubuntu Studio 14.04 i386 - easier said than done. After having reinstalled Ubuntu Studio 14.04 about ten times, I was finally successful. However, at boot, the system hangs with a bunch of buffer i/o errors. I have booted into recovery mode and run fsck five times and I continue to get buffer i/o errors. This could of course  mean that something is wrong with the hard disk (4 TB), but I haven't had problems with any other system installed on that drive before. That, together with numerous crashes of the Ubuntu Studio 14.04 installer (for various reasons - including attached peripherals, trying to format the drives partitions as ext4, etc. ) begs the question as to whether my hardware is up to snuff for such a project:
> Antec Three Hundred Case
AMD Phenom II 64 X6-1100T/ 3.3GHz -9MB Black BOX AM3
Asus Sabertooth 990FX Motherboard
Plextor PX-L890SA internal SATA DVD/CD Super Multi Writer
GeForce GT220-1024MB-DDR2-VGA/DVI+HDMI-ASUS V2
Cooler Master Hyper 212 Plus CPU Cooler
Corsair Builder Series CX 600W ATX Power Supply
While I have successfully installed KXStudio 14.04 on another (2TB) hard disk, it seems to me that my experiences with Ubuntu Studio suggest that maybe I need to get a NUC, Zotac or other hardware that I can use as a dedicated device. I would prefer to use what I have, but...

The observant members that read this post  :) may notice that while I have a 64-bit AMD system, I have been trying to install the i386 version of Ubuntu Studio 14.04. I have done this because the Linux (Ubuntu) version of Guitar Pro 6 requires an i386 system (how lame is that?), and I am not over the moon about TuxGuitar.

Any ideas, comments, or advice, would be appreciated.

---

### Post by oldfred on 2014-05-18
I thought the 64 bit version of Ubuntu has the capability to run most 32 bit apps now.
I did find this:
[http://ubuntuforums.org/showthread.php?t=1999054](http://ubuntuforums.org/showthread.php?t=1999054)

You have two added issues. One is a very large 4TB drive. The other is the nVidia card.

With very large drives you have to use gpt partitioning and should then use a smaller / (root) partition of 25GB and use rest of drive for /home or data. You have to have either an efi partition for UEFI boot or bios_grub partition for BIOS boot. Your system probably does not have UEFI boot, but if thinking of a new system soon, and drive may get transfered to new system then include an efi partition at beginning of drive as it is very difficult to add an efi partition at beginning of drive when it has lots of data.

With nvidia card you have to use nomodeset to boot until you install the proprietary nVidia drivers.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by globetrotterdk on 2014-05-20
Thanks for the wealth of information, that I am at this time sifting through. With regards to the i#86 libs issue, I have been trying to do just that. There is a thread on the issue [here]("http://forum.peppermintos.com/index.php?topic=291.0"). I have been using Peppermint OS4 64-bit  (an Ubuntu derivative) to do just that. Unfortunately, with limited success. That is why I thought I would try going to the horses mouth so to speak and use a 32-bit version of Ubuntu Studio.

---

