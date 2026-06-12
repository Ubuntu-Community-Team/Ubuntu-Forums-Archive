---
title: "Samsung AHCI SM951 SSD Boot"
date: 2015-09-01
forum: Ubuntu, Linux and OS Chat
---

### Post by fjgaude on 2015-09-01
Has anyone using Ubuntu been successful in booting the subject drive? If so please tell me how you did it.

Thanks you!

---

### Post by oldfred on 2015-09-01
I saw in another thread that you have an Asus motherboard.
I have just a Samsung 840 pro on a standard SATA port in an Asus z97-AR motherboard.
I had to change a lot of settings in UEFI to get it to recognize UEFI boot of flash drive and install to SSD.
Have you updated UEFI? I just updated to 2501 and it reset everything back to defaults.
Did you change to "other" for OS type?
Did you turn on boot with UEFI only.
SATA support all devices, should be default
USB support full initialization. 
I turned off fast boot for cold boot. Normal boot
Set fast boot to 3 sec for warm boot.
Turned off network boot so it would not look for that.

But you may have other settings for your S2 SSD?

---

### Post by fjgaude on 2015-09-01
Thanks for coming to assist! I've been trying to read all your advise on the linked thread.

I have an Asus Z97i Plus MB with two SSDs, one a Samsung, the other a Plextor, plus a VelociRaptor HDD running Ubuntu Unity 14.04.3 and 15.10 Beta, on several partitions. I boot normally off the Samsung 850 EVO, very quick.

I also have an ASRock Z87 in another box with booting Plextor M6e and another Plextor SSD.

I've tried many setting in the UEFI BIOS of the Asus without being able to boot from the SM951. I have huge amount of data on one of its two partitions. On the other I've tried 14.04 and 15.10 without success. I see the boot partition on the grub of my main boot drive, the 850 EVO but selecting it just gets me back to the grub menu.

I carefully record all the things you suggest and perform them in the BIOS and see what happens.

It seems as maybe another issue is the efi and UEFI situation with the later .iso Linux OSs. Will have to understand it all sooner or later. <smile>

---

### Post by oldfred on 2015-09-01
My old BIOS system was from 2006 & 2009. Later I thought I would get a new UEFI system which for PC was pretty new, but bought a small SSD. It made old system so good I could not justify new system, but followed UEFI.
I started converting all new drives in 2010 to gpt as I then thought I would soon go to UEFI. I added an efi partition and bios_grub so I could boot my old system with BIOS, but later convert to UEFI. But new system got new drives and did not use the older drives anyway.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by fjgaude on 2015-09-01
Thanks again, trying to catch up on all the understanding. Oh, my BIOS is the latest, 2605! Handles all the latest CPUs and NVMe drives.

Will print out your suggestions and go into the BIOS. Will report on results later today or tomorrow.

---

### Post by fjgaude on 2015-09-01
Well, I made sure all the items you suggested were in place... I then could see the UEFI BIOS would allow me to only boot UEFI drives and the OS didn't respond to them.

It seems that the other drives are loaded with non-UEFI software, 14.04 and 15.10, likely. I think I installed 15.10 on the SM951 as UEFI but Linux simply doesn't see it. All my other partitions have non-UEFI OSs.

All my drives are ms-dos partitions, no GPT partitions. I wonder if that is my problem? I'm not trying to install any Windows, have it set for no secure boot, boot "legacy and UEFI" drives.

Understand this is not a normal SSD issue. I have several SSD partitions that boot using ms-dos style boot loading. It's just this Samsung AHCI SM951 that will not boot. I have not found any Linux user who has booted it.

After some more study I'll see if I have to convert all my drives to GPT. What a horrible thought! <smile>

Thanks again, oldfred, for the help and discussion.

---

### Post by oldfred on 2015-09-01
You do not have to convert to gpt.
But if you want to use UEFI or use it in the future best to plan conversion as/when convenient.
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.
But Ubuntu can boot from gpt with either UEFI or BIOS if you have correct supporting partitions on gpt drive. For BIOS you need a bios_grub and for UEFI you need a ESP - efi system partition.

In CSM/BIOS mode system should work. I think one of my settings makes it UEFI only as I could only boot flash drive in UEFI mode with it set to UEFI only. It would not boot in UEFI mode with the setting that was UEFI & CSM.

---

### Post by help_me2 on 2015-09-02
Sometimes is as simple as installing Ubuntu on the SSD drive first with the other drive unplugged. Then hookup the other drive and run"sudo update-grub" on the SSD. Just a thought that has worked for me before.

---

### Post by fjgaude on 2015-09-02
Thanks, I'm learning!

---

### Post by fjgaude on 2015-09-02
Yes, and thanks... While booted to the partition I wish to be first, point to that drive in the BIOS, I use update-grub, then grub-install /dev/sdx to that drive. Works fine!

---

### Post by fjgaude on 2015-09-02
Hello, oldfred, and all!

I'm learning but still no gold with the Samsung SM951 M.2 PCIe x4 installed in an adapter as a boot drive. Okay as data storage, and super quick and fast.

I noticed the original item was format GPT, made it into ms-dos MBR. Formatted to ext4, installed 15.10 with boot loader placed on it, is seen by UEFI BIOS but will not boot. Then noticed that it is still a UEFI drive as indicated by the Asus BIOS. That means the drive's internal driver is AHCI and UEFI.

I don't understand why the drive will not boot, but will still dig into the literature to understand more.

---

### Post by oldfred on 2015-09-02
To be UEFI, it really needs to be gpt partitioned. And the first partition should be the ESP - efi system partition which is FAT32 and if you use gparted with the boot flag.
If you changed to MBR and installed in BIOS mode, you must then boot in BIOS mode with UEFI & with UEFI secure boot off, and CSM on.

I prefer to only use gpt, and have both the ESP & a bios_grub for BIOS boot on every drive. Than I can install either way without having to totally repartition drive.

---

### Post by fjgaude on 2015-09-02
I have done what you say but still no go. It was like you suggested all along and didn't work. Now it is MBR style with CSM on, allowing everything to work and show.

I think this first of its kind drive only works with Windows. Do you know of any Linux people who have it as a boot drive?

---

### Post by oldfred on 2015-09-02
Have not seen or noticed a lot of M2. drives.
Do not know if they show up special when users post Summary report from Boot-Repair, I think they may just show as a standard drive. And script does not report details on drive.

---

### Post by fjgaude on 2015-09-02
I'll just hang in there and see if something comes up... it's not a life or death situation, but of course you know that. <smile>

When the NVMe version of the drive comes out I'll give it a try, as my MB is supposed to handle such.

Thanks again for all your effort to help me.

---

### Post by mc4man on 2015-09-03
I recently had a laptop that booted from an m.2 PCIe ssd, whether it was that model can't tell now as it was returned. (though I do see I searched that model in Firefox's history around the time I had ordered the laptop a month ago or so.

---

### Post by fjgaude on 2015-09-03
I have read that the SM951 is used in many laptops and even tablets. But it is still OEM. Samsung seems to not have a built-in driver for the drive. I've given up trying various BIOS settings in both Z87 and Z97 MBs. Consider that I have a Plextor M6e PCIe 2.0 x2 that boots even in the Z87 MB of ASRock. So I have concluded that my goose is cooked. The SM951 is still a super, the best SSD for a database. So I'm a happy camper until Samsung or some other company issues something like as fast and quick but will boot in Linux.

Thanks for your post, mc4man. You are a good man! <smile>

---

### Post by mc4man on 2015-09-03
I returned that laptop because it used a desktop cpu in a laptop without any added or upgraded cooling, though for *general use* didn't see that the PCIe ssd provide any advantage. (maybe it would of if I used it more than 30 min. before packing up for an rma.
The other laptop issue with m.2 PCIe ssd's is only 1 can fit vs 2 m.2 ssd's (slot1, slot2

The next laptop I tried (and just returned) had 2 m.2 ssd's + a sata3 ssd, it's issue was some releases would boot,  some wouldn't
14.04.1 - booted
14.04.3 no boot
15.04 - booted
15.10 - no boot
fedora 22 - no boot

I'm getting very wary of a third attempt at a highly configurable laptop, maybe I should just go back to a desktop machine...

---

### Post by fjgaude on 2015-09-03
> **mc4man said:**
> I returned that laptop because it used a desktop cpu in a laptop without any added or upgraded cooling, though for *general use* didn't see that the PCIe ssd provide any advantage. (maybe it would of if I used it more than 30 min. before packing up for an rma.
The other laptop issue with m.2 PCIe ssd's is only 1 can fit vs 2 m.2 ssd's (slot1, slot2

The next laptop I tried (and just returned) had 2 m.2 ssd's + a sata3 ssd, it's issue was some releases would boot,  some wouldn't
14.04.1 - booted
14.04.3 no boot
15.04 - booted
15.10 - no boot
fedora 22 - no boot

I'm getting very wary of a third attempt at a highly configurable laptop, maybe I should just go back to a desktop machine...

Oh joy! From your testing it would seem the laptop manufacturer’s M.2 SSD driver is compatible with some versions of Ubuntu.

No joy for my earlier testing: no boot on 14.02, 14.03, and 15.10. I didn't even think to try 15.04 or 14.04.1. Will do it in the next day or so and report what the results are.

It's only the Samsung SM951 that's truly in a league by itself, like the Intel 750 NVMe drives. The Samsung XP941 is next. All the other M.2 drives are related to the SATA 6MHz bus, not much faster than 550MHz/s read speeds. The SM951 is over 2000MHz/s.0

Chat with you soon!

---

### Post by fjgaude on 2015-09-03
Well, I took time off and put 14.04.1 onto the SM851, no boot!

I'm going no further... the Linux kernel needs a kernel driver for this type of M.2 drive... it'll come but who knows when? Likely after the drive becomes a non-OEM product. <smile>

Let's stay posted as news arrives.

---

### Post by mc4man on 2015-09-03
Just for info's sake the the working m.2 PCIe ssd was from System76 which is a re-branded clevo P751ZM/P771ZM
(how they've managed to sell enough to get a backorder status now is beyond me, if one intends to use one with the keyboard they're either near the arctic circle, sitting in front of an air conditioner (maybe), using an external keyboard or very calloused hands.

Also under load, ie. multi-thread 264 encoding, the cpu's always flirted with critical, pstate seemed slow to react. 
(the 1st test encode did result in a critical > shutdown

what's somewhat interesting is that limiting pstate to 90% keep the cpu's @ 80 degrees C under full load without that much of an effect of speed, but the laptop was still hot, as in very.

also to clear up, if needed - the 2nd laptop where I tested various just had 'regular' m.2 ssd's (2 Samsung 850 EVO Series mSATA3 SSD

---

### Post by fjgaude on 2015-09-04
It would seem whenever it is stated that no driver is required it means the driver is in firmware of the drive. That why drives like Plextor M6e work with Linux and Windows. I have read that Windows has a driver for the Samsung SM591 and thus there is no built-in driver. So the mystery is solved, I think. <smile>

Thanks for the run-down on your laptops! With all the new chips and CPUs coming out it should no longer be much of a issue, Skylake type things.

---

### Post by Fraoch on 2015-09-05
I have the same two drives - a Plextor M6e that boots perfectly and an SM951 that will not boot.  I'm using an ASRock Z97 Extreme6 motherboard with two M.2 slots - a PCIe 2.0 x2 that has the Plextor and a PCIe 3.0 x4 that has the SM951.

At first I couldn't even see the SM951 in the UEFI but I could see it in the OS.  It was obviously working fine, I benchmarked it at 2.5 GB/s read, 770 MB/s write.  A UEFI update then showed the drive in the UEFI but I cannot boot from it.

Based on this thread:

[http://forums.tweaktown.com/asrock/60611-booting-sm951.html](http://forums.tweaktown.com/asrock/60611-booting-sm951.html)

I first tried setting the partition type to GPT as the thread suggested, then set my UEFI "CSM Compatibility Module" "Storage OpROM loading" to "UEFI only".  That stopped the Plextor OpROM from loading but the SM951 would not boot.

The installer saw the SM951 as "EFI system" formatted but when it tried to install to it, it popped up something along the lines of "Cannot format scsi(0,0) as vfat on partition #1".

I've since found that I may need to make a special EFI boot partition but that was old advice from the early days of UEFI.  However it's someting I might try.  Otherwise...I give up!!

The thread I posted shows this should be possible in Windows but there is no mention of Linux.  Perhaps I will ask my motherboard manufacturer, they leapt into that thread unprompted with some excellent help.

Full disclosure: I am using Linux Mint 17.2, don't hate me :-) ...however the installer is the same.

---

### Post by fjgaude on 2015-09-05
Thanks, Fraoch, for you input.

Yes, we have had much the same experience. Yes, the SM951 can be installed to boot under Windows but Windows has a driver for it, Linux does not.

The M6e has a built-in driver and that is why it works so well under Linux. Samsung, from what I read, doesn't have driver code of the SM951 and its up to the OEM to provide it.

I have completely reformatted my SM951, as you might have read earlier in this series of posts, to MBR instead of GPT but it still shows itself as UEFI. I'm waiting now to see if Linux will have a driver in its latest kernel or Samsung comes out with its NVMe version. My ASUS MB Z97 has such support. Anyway, it's not life and death, so I'm much a happy camper. <smile>

---

### Post by nullsteph on 2015-10-23
I finally got my 2 SM951's dual booting Win10 and Ubuntu 15.10....and what a pain it was.
I had to burn the ISOs to DVD's to get the installs to work without erroring out.    Disabled 'secure boot', enabled UEFI, secure erased the M2 SSDs, paired the RAM down to 16GBs, and booted from the DVD for the installs.  Had to run an external DVD drive to the laptop connected through the SATA SSD ports, and  power that with a SATA power cable from another computer...ugh!  

I tried other Ubuntu versions but only 15.10 worked.  Reducing the RAM and installing from DVDs also seemed to be key.

---

### Post by fjgaude on 2015-10-23
Gosh, this is good news... something to work here as I have 15.10 on at least two computers. Don't use Windows and I understand the ways of secure boot with it. Use UEFI most of the time, especially with 15.10. Will instead be using a USB that handles UEFI, using mkusb from .iso to ready to boot. Thanks so much for tipping me off. To boot from a SM951 should be interesting! I placed copper heat sinks on three of the chips to control the heat for longer runs.

---

### Post by fjgaude on 2015-10-24
Well, I gave it my best shot, actually about five shots, but no go. Installed as UEFI on released version of 15.10... shows in the grub menu but will not boot.

I wonder if your Windows driver for this drive might be used by Ubuntu? Can't think of anything else... I know that Samsung has no driver and it will have to be in the latest Linux kernel for this drive to boot. I'm on ASUS Z97 motherboard. I wait for something to come up that fixes this situation.

---

### Post by oldfred on 2015-10-24
This mentions OpROM?
[http://forums.tweaktown.com/asrock/60611-booting-sm951.html](http://forums.tweaktown.com/asrock/60611-booting-sm951.html)

On my Asus 97 I see settings for M2 on p2-42 2.6.7 and OpRom on p 2-52 2.8.10
Have you tried changing those settings?

---

### Post by fjgaude on 2015-10-24
> **oldfred said:**
> This mentions OpROM?
[http://forums.tweaktown.com/asrock/60611-booting-sm951.html](http://forums.tweaktown.com/asrock/60611-booting-sm951.html)

On my Asus 97 I see settings for M2 on p2-42 2.6.7 and OpRom on p 2-52 2.8.10
Have you tried changing those settings?

Well, oldfred, my Asus 97 is Z97i Plus and the manual is not as long as the one you are looking at. I have the M.2 and OpRom menu items, and have tried everything but nothing works to have the UEFI SM951 Ubuntu 15.10 boot.

I guess I forgot to state recently that my M.2 Samsung is in a PCIe x4 card, so that could make a difference. Though earlier I put the little SSD into the back of the MB's M.2 slot. Didn't boot.

Since it works with another fellow's 15.10 Linux, with Windows, I just can't say what is going on. The kernel 4.2 has to have a driver for it to work, as Samsung has none in firmware and has to use what Windows offers, which is said not to be fully optimized.

I'll keep trying and reading all the info that I come across.

Thanks to all for the encouragement.

---

### Post by fjgaude on 2015-10-26
> **nullsteph said:**
> I finally got my 2 SM951's dual booting Win10 and Ubuntu 15.10....and what a pain it was.
I had to burn the ISOs to DVD's to get the installs to work without erroring out.    Disabled 'secure boot', enabled UEFI, secure erased the M2 SSDs, paired the RAM down to 16GBs, and booted from the DVD for the installs.  Had to run an external DVD drive to the laptop connected through the SATA SSD ports, and  power that with a SATA power cable from another computer...ugh!  

I tried other Ubuntu versions but only 15.10 worked.  Reducing the RAM and installing from DVDs also seemed to be key.

My curiosity is so high! You have SM951 booting into 15.10, but have Windows in the grub menu also?

I've tried everything, and I do mean everything, and cannot get it to boot with the latest version of 15.10 but I have no Windows installed.

---

