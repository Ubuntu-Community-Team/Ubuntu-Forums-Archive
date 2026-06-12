---
title: "Gigabyte GA-Z97MX-Gaming 5 KVM GPU Passthrough"
date: 2015-10-12
forum: Virtualisation
---

### Post by dik232 on 2015-10-12
I want to build myself a new machine for work and play. This machine will run *buntu but in order to test / support Windows users and to play games that aren't available on Linux my plan is to run Windows in KVM. Obviously to game I'm going to need to pass a GPU through. I'm currently looking at a GTX970.

I would prefer to keep this machine as small as possible and am looking at m-ATX boards. The Gigabyte GA-Z97MX-Gaming 5 looks like it could be the mb for me but I need some advice from a hardware / kvm guru. 

One of the online resources I'm using is this [spreadsheet]("https://docs.google.com/spreadsheets/d/1LnGpTrXalwGVNy0PWJDURhyxa3sgqkGXmvNCIvIMenk/edit?pli=1#gid=0") . It contains an entry for the GA-Z97MX-Gaming 5 but it states "PCI 16x IOMMU group in motherboard includes ethernet port, so keeping internet on the host requires an alternative interface." It also says that no patches have been used.

Questions:


1. Would the ACS kernel patch fix this problem? If not then I suppose I could get a PCI or USB ethernet adapter but I'd rather not if I don't have to.


2. Is this issue caused by the fact that this is a m-ATX board. Would I be better off ditching m-ATX and going with something like the ASRock Z97 Extreme6, or is there a another m-ATX board that would work?


3. Are there any obvious mistakes in my plan?


Thanks in advance


D :)

---

### Post by KillerKelvUK on 2015-10-12
Hi D, so I believe the following are your answers...


[LIST=1]
[*]I believe so yes, ACS is the way to go.
[*]Nothing to do with m-ATX, mix of hardware vendor design and implementation.  As it happens I have an ASRock Z97 Extreme 6 and I have to use ACS patching as this mobo's separation isn't great in comparison with others.
[*]Look at whether your GTX970 has a UEFI bios on it as if it has you can use OVMF to boot the guest and avoid the whole VGA arbitration game, the tester for the mobo on the spreadsheet you linked looks like this was their setup also.  One other point around the ASRock Z97  (if you do decide to go this route) is that HDMI audio out is broken when using vd-t/IOMMU...bug somewhere whether its hardware and kernel related i don't know...never got any support in debug and way beyond me technically to investigate unassisted.
[/LIST]

Just for giggles the below is my unpatched IOMMU group separation on the ASRock...

```

### Group 0 ###
    00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
### Group 1 ###
    00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
### Group 2 ###
    00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
### Group 3 ###
    00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
### Group 4 ###
    00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
### Group 5 ###
    00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
### Group 6 ###
    00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
### Group 7 ###
    00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
### Group 8 ###
    00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
    00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
    00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
    00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
    02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
    03:00.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:01.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:03.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:05.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:07.0 PCI bridge: ASMedia Technology Inc. Device 1184
    06:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
    07:00.0 Multimedia video controller: Spin Master Ltd. Device 3038 (rev 01)
    08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
    09:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
### Group 9 ###
    00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
### Group 10 ###
    00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
    00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
    00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller

Linux blackserver 3.19.0-30-generic #33-Ubuntu SMP Mon Sep 21 20:58:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivi




```

---

### Post by dik232 on 2015-10-13
That's really helpful, thanks!

Especially the part about the GPU's UEFI bios, I'd not considered that. I imagine it'll save me a lot of time and effort. Would this have to be UEFI GOP ?

You mention that the ASRock Z97 Extreme 6 separation isn't great in comparison with others. Which others? How would I go about finding out about the group separation for different motherboards? Is it something that's possible to find in the documentation or will I have to trawl the internet in order to find out?

I am determined to get as much of this correct as possible from day one.

---

### Post by dik232 on 2015-10-15
Also....


I see you have a Xeon. Is there a reason for that? I was looking at a 4790k

---

### Post by KillerKelvUK on 2015-10-16
Yes UEFI GOP on your gfx card.

Regards my mobo and its comparison...this is just from reading posts on this forum vs orthers of users challenges with ACS briding and their stock kernels i.e. unpatched.  The spreadsheet you linked originally is the only consolidate list of passthru comparisons I've ever found.

The Xeon reference is just a stock chipset used across platforms for display and audio i think.. however my CPU is actually a 4th gen 4790s.

---

### Post by dik232 on 2015-10-17
Thanks KK, all useful information.

You clearly have more experience of this than I do (zero). If you were in the market for a motherboard what would you be looking at? Are any of them mATX?

---

### Post by KillerKelvUK on 2015-10-17
> **dik232 said:**
> Thanks KK, all useful information.

You clearly have more experience of this than I do (zero). If you were in the market for a motherboard what would you be looking at? Are any of them mATX?

Hey just keep trying and posting, best way to learn and share.

I prev ran an mATX rig but upgraded to get vt-d capability and went for the ASRock mobo.  Nothing against mATX I just needed more sata that what you can typically find on an mATX, plus needed more RAM slots.  Don't think this is an easy one to steer on as whilst the chipset specifications aka Z97 are generic the vendors application of the spec on their board creates the variances i.e. fewer SATA, USB and Mem slots...this also drives the differences in virt capabilities.  I think to manage expectations you should plan on having to patch the kernel regardless and if your eventual choice plays out differently then this is just gravy.  I'd just do a **** load of research on your chosen piece of hardware in advance to see if anyone has trodden the road you looking at...like you are doing now!

Me personally, I'd stay away from Nvidia cards for passthrough...I had a horrendous time getting it up and running and most of that was driver related.  Whilst AMD cards aren't without there issues my reading has led me to conclude that AMD users have a higher success or maybe an easier success record.

---

### Post by dik232 on 2015-10-20
You've made me see sense!

I was set on Nvidia because my laptop, running Ubuntu, has AMD GPU and I can't stand it. There's always some GPU related problem and it's never "just worked" using either the open or closed source drivers.

I've been hoping that I could eventually move away from Windows altogether so having Nvidia would be better and buying all the hardware at the same time would be more tax efficient for me.

However it's just dawned on me that making my life easier whilst trying something I've not attempted before would probably be best. Also I've a 7950 left over from an shockingly profitable mining experience. Using this would be even more tax efficient since I'll not have to pay for it!

Once I've got it working I might venture into Nvidia land, by which point the cards will be older / cheaper / on ebay and there might be some development towards making them work. I might even get drunk and try hard modding a GTX 690 into a Quadro. What could possibly go wrong?

---

### Post by KillerKelvUK on 2015-10-20
> **dik232 said:**
> You've made me see sense!

I was set on Nvidia because my laptop, running Ubuntu, has AMD GPU and I can't stand it. There's always some GPU related problem and it's never "just worked" using either the open or closed source drivers.

I've been hoping that I could eventually move away from Windows altogether so having Nvidia would be better and buying all the hardware at the same time would be more tax efficient for me.

However it's just dawned on me that making my life easier whilst trying something I've not attempted before would probably be best. Also I've a 7950 left over from an shockingly profitable mining experience. Using this would be even more tax efficient since I'll not have to pay for it!

Once I've got it working I might venture into Nvidia land, by which point the cards will be older / cheaper / on ebay and there might be some development towards making them work. I might even get drunk and try hard modding a GTX 690 into a Quadro. What could possibly go wrong?

You might find it difficult to wield a soldering iron whilst doing shots but if you do attempt to butcher your GTX whilst drunk...please please please share some pictures of your works...that will be fun for sure :-)

---

### Post by dik232 on 2015-10-21
Fail....

The 7950 I have is made by Sapphire, and apparently none of their 7950s [support UEFI]("https://www.techpowerup.com/vgabios/index.php?manufacturer=Sapphire&model=HD+7950").

Back to the drawing board for me

---

### Post by oldfred on 2015-10-21
Video cards do not care if UEFI or BIOS, motherboards must be configured for UEFI, but most new UEFI motherboards also have CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mod. Your Z97 is UEFI as all z97 boards are UEFI.

Many use nVidia as it seems to work better for gaming with Linux, although with Windows AMD has a better driver than its Linux version. But it also depends if using open source driver or proprietary driver.

             The Extreme Cases Where A NVIDIA GTX 950 Can Outperform An AMD R9 Fury On Linux OpenGL
[http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-fury&num=1](http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-fury&num=1)
NVIDIA's GeForce GTX 950 Is A $150+ Bargain For Linux Gamers
[URL="http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-linux&num=1"]http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-linux&num=1
[/URL]
 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[URL="http://ubuntuforums.org/showthread.php?t=2259210"]http://ubuntuforums.org/showthread.php?t=2259210

[/URL]
 AMD Radeon R9 290 On Ubuntu 14.04 With Catalyst Can Beat Windows 8.1
 the open-source AMD Hawaii support remains broken,
[http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1](http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1)
[http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1)  [ ]("http://ubuntuforums.org/showthread.php?t=2259210")  [ ]("http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-linux&num=1")

---

### Post by dik232 on 2015-10-21
But surely if my GPU is UEFI supported I can avoid VGA arbitration patching of the kernel, which would make my life easier.

I currently have [this 7950]("https://www.techpowerup.com/vgabios/134477/sapphire-hd7950-3072-120926-1.html") sat about and it isn't UEFI Supported whereas [this Gigabyte]("https://www.techpowerup.com/vgabios/133710/gigabyte-hd7950-3072-121218.html") card is.

Slightly confused now.

---

### Post by KillerKelvUK on 2015-10-22
I'd invite oldfred to further his views by referencing the relationships to virtualisation and vfio passthrough. His points and links are accurate but don't reference anywhere the core topic here.

My (granted limited) understanding here is that a non-UEFI GOP based gfx card cannot properly participate in VGA arbitration alongside the host IGD. As such passthrough solutions that suffer this issue break host gfx (although I understand it's somewhat still usable for some tasks). It is possible to patch this with the i915 arbitration code however this removes DRI functionally on the host desktop which again reduces host usability. 

The only way to properly avoid this problem to my understanding is to have a passthrough gfx card with a UEFI GOP and to boot the guest using OVMF, this facilitates a correct vga arbitration and both host and guest gfx work as intended.

I guess for you dik232 its the i915 patch or a new card :-(

---

### Post by oldfred on 2015-10-22
I do not use KVM, did not realize that was main issue.

There also are other threads on issues, this does say you need a UEFI card, but has a work around.
[http://ubuntuforums.org/showthread.php?t=2266916](http://ubuntuforums.org/showthread.php?t=2266916)

---

### Post by dik232 on 2015-11-05
Plan is to build the machine and put a 7950 in it. Perhaps mess with the BIOS to make it UEFI, it has two BIOSes which makes me feel safe about flashing it.

Once it works consider spending on a more modern card.

Thanks for the help, it's been very useful. I'll report back with my findings.

One question. What command do you issue to obtain unpatched IOMMU group separation?

---

### Post by KillerKelvUK on 2015-11-05
> **dik232 said:**
> 

One question. What command do you issue to obtain unpatched IOMMU group separation?

Pinched this from a rather helpful fellow, does the trick nicely!

[ATTACH]265388[/ATTACH]

---

