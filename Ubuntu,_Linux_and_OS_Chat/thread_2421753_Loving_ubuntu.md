---
title: "Loving ubuntu"
date: 2019-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by DanPerecky on 2019-06-26
I used to have a dual-boot Windows and ubuntu pc... but I never had a chance to actually boot to the ubuntu side....

Now, ubuntu 18.04.2 is installed as a guest in the virtual box... and it's great. I have both OSs going... and I use the ubuntu vm for everything that needs to be secure... With ssh - Secure Shell, particularly sshguard... things are great.  The only problem is that it's a little slow at times... even with 16Gb of ram. 

ubuntu mate coming with three different browsers is way cool. Been having problems playing youtube on Opera... but on Brave they work fine. This is what's nice about having browser choices.

Keep up the good work.:)

---

### Post by wildmanne39 on 2019-06-26
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by Shibblet on 2019-06-26
> **DanPerecky said:**
> I used to have a dual-boot Windows and ubuntu pc... but I never had a chance to actually boot to the ubuntu side....

Now, ubuntu 18.04.2 is installed as a guest in the virtual box... and it's great. I have both OSs going... and I use the ubuntu vm for everything that needs to be secure... With ssh - Secure Shell, particularly sshguard... things are great.  The only problem is that it's a little slow at times... even with 16Gb of ram. 

ubuntu mate coming with three different browsers is way cool. Been having problems playing youtube on Opera... but on Brave they work fine. This is what's nice about having browser choices.

Keep up the good work.:)

Glad to see you are enjoying it.

If you are having problems with Ubuntu being slow, it could be that it is in a VM.  Try doing a live boot off of a USB drive, (don't install, just boot into the OS).  Then you will get a more accurate idea of how Ubuntu functions.

If you want to make a live USB stick, check out these links:
[https://www.pendrivelinux.com/]("https://www.pendrivelinux.com/")
[https://rufus.ie/]("https://rufus.ie/")

---

### Post by DanPerecky on 2019-06-26
Shibblet ... Thanks for your suggestion...
Actually something just happened in my ubuntu system... Yesterday a different VM was trying to start up... (don't ask.. something to do with the .cpp file and Windows file associations).. Today my virtual box ubuntu would not boot. It only booted up to the Busy Box.

I looked up the problem and found that there is a command that I could enter there: fsck... which I did.  fsck -f /dev/sda1.   This worked great! I'm able to boot up now...and actually it seems a lot faster then previous....  Whoever made that fsck program is a genius... probably an unsung genius as well.

---

### Post by bcschmerker on 2019-06-27
**I've run serial releases of ubuntu® in a machine** that started out as a stock everex® TC-2502 (1.6 GHz VIA® C7-D, CN700 chipset with integrated UniChrome GPU) running a Good OS LLC-distributed derivative of xubuntu&#8480; 7.10 Gutsy known as gOS 1.0.1 Painful.  This TC2502 is now a gPC in name only, as I've since upgraded all the internals:  Antec® TruePower® New™ 750 Blue™ PSU, GIGABYTE® GA-MA78GM-S2HP v2.0 planar (Advanced Micro Devices® RS780G northbridge with integrated 64-bit ATi® Radeon® HD™ GPU, SB700 southbridge) Advanced Micro Devices® Athlon 64® 3500+ (superseded an X2 5600+ that failed its memory manager; to be replaced with an Advanced Micro Devices® Athlon II® X2 220); ASUS® XONAR® Essence™ STX™ audio (modified C-Media® CMI-8788 DSP); one Western Digital® WD1600JS-55NCB1 and three Toshiba® MQ01ABD050 HDD's (four MQ01's planned); TSST Corporation SH-S182D DVD-Multi optical drive.  As of 27 June 2019 I have an [open question](https://ubuntuforums.org/showthread.php?t=2421074) in Hardware concerning GIGABYTE® GV-Series video display adapters, needed due to BIOS issues evidenced by a fail retrofitting an ASUS® EAH6850 DirectCU® VDA (Advanced Micro Devices® RV-970 Pro GPU; installation reverted - incorrect POST screens).

I've run serial LTS releases from 8.10.0-LTS Hardy; am currently on 16.04.6-LTS Xenial pending a fourth Toshiba® MQ01ABD050 to replace the WD160JS-55NDC1 on SATA 0, and some adapter hardware for a Compact Flash Type I (stand-in for a solid-state drive) as Master on the GA-MA78GM-S2HP's E-IDE port (better known as PATA nowadays) with the TSST SH-5182D optical as Slave.  I anticipate any GV-R Series VDA prior to the GV-R580XWF-8GD to have driver support in 18.04.3-LTS Bionic, but am awaiting a release from the Nouveau project on Maxwell support prior to including the GV-N96D5-4GD in consideration.

---

### Post by uRock on 2019-06-27
> **bcschmerker said:**
> **I've run serial releases of ubuntu® in a machine** that started out as a stock everex® TC-2502 (1.6 GHz VIA® C7-D, CN700 chipset with integrated UniChrome GPU) running a Good OS LLC-distributed derivative of xubuntu&#8480; 7.10 Gutsy known as gOS 1.0.1 Painful.  This TC2502 is now a gPC in name only, as I've since upgraded all the internals:  Antec® TruePower® New™ 750 Blue™ PSU, GIGABYTE® GA-MA78GM-S2HP v2.0 planar (Advanced Micro Devices® RS780G northbridge with integrated 64-bit ATi® Radeon® HD™ GPU, SB700 southbridge) Advanced Micro Devices® Athlon 64® 3500+ (superseded an X2 5600+ that failed its memory manager; to be replaced with an Advanced Micro Devices® Athlon II® X2 220); ASUS® XONAR® Essence™ STX™ audio (modified C-Media® CMI-8788 DSP); one Western Digital® WD1600JS-55NCB1 and three Toshiba® MQ01ABD050 HDD's (four MQ01's planned); TSST Corporation SH-S182D DVD-Multi optical drive.  As of 27 June 2019 I have an [open question](https://ubuntuforums.org/showthread.php?t=2421074) in Hardware concerning GIGABYTE® GV-Series video display adapters, needed due to BIOS issues evidenced by a fail retrofitting an ASUS® EAH6850 DirectCU® VDA (Advanced Micro Devices® RV-970 Pro GPU; installation reverted - incorrect POST screens).

I've run serial LTS releases from 8.10.0-LTS Hardy; am currently on 16.04.6-LTS Xenial pending a fourth Toshiba® MQ01ABD050 to replace the WD160JS-55NDC1 on SATA 0, and some adapter hardware for a Compact Flash Type I (stand-in for a solid-state drive) as Master on the GA-MA78GM-S2HP's E-IDE port (better known as PATA nowadays) with the TSST SH-5182D optical as Slave.  I anticipate any GV-R Series VDA prior to the GV-R580XWF-8GD to have driver support in 18.04.3-LTS Bionic, but am awaiting a release from the Nouveau project on Maxwell support prior to including the GV-N96D5-4GD in consideration.

Is this relative to the original post?


@DanPerecky I'm happy to hear you're enjoying Ubuntu. I've been using it for about ten years now and it definitely makes my computing more fun and productive.

---

### Post by lammert-nijhof on 2019-06-27
If you run virtual machines, if possible you could also turn the things around. You could use a minimal install of Ubuntu as Host OS in Virtualbox and both Ubuntu and Windows 10 as a Guest. In that case I would use ZFS as file system for at least the VMs. I run my VMs on a 3 level compressed ZFS storage hierarchy with 4 GB memory cache, 50 GB SSD cache and 3 striped HDDs in total 1.82 TB. That compression does not only double the effective cache sizes, but it also speeds up the disk, because it only needs half the number of disk IOs. 

If your host remains Windows you could look at the new Microsoft file system ReFS, that tries to compete with ZFS or else try compressing that NTFS directory to reduce the number of disk IOs needed for loading Ubuntu and its programs. Like you noticed performance depends for 80% on your disk speed and throughput.

---

### Post by DanPerecky on 2019-06-28
[[COLOR=#000000]lammert-nijhof[/COLOR]]("https://ubuntuforums.org/member.php?u=1949495")[COLOR=#000000]  - Thanks for your suggestions. You're right... but I don't have the time to consider such a big reconfiguration. I do see a lot of I/O in my system performance app, Maybe the ReFS will help.... some time in the future. Worth a try.[/COLOR]

---

### Post by DanPerecky on 2019-06-29
lammert-nijhof - ETA. I was trying something and found that I had to increase the size of the .vhd file.... The .vhd file is 15Gb... with the old ceiling at 20Gb. I used VBoxManage to increase it to 25Gb... I also did a apt get-upgrade.. and wow.. the response time on this Linux system is like double the speed...  I don't know why that is... but one or the other .... seemed to help a lot.

---

