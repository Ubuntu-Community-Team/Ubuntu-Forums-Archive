---
title: "BIOS allowing, do you choose UEFI or standard boot option"
date: 2018-01-20
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2018-01-20
Most of the newest motherboards I've seen are UEFI only so there is no choice, but up until just the past few years it was common for the BIOS to offer UEFI as an option only. So, if your BIOS offers the option, do you choose UEFI or just use the standard "legacy" boot option?

I had been using UEFI wherever possible but I'm sort of rethinking that choice :-k

It does seem that Windows 10 is less forgiving activation-wise of a motherboard change in UEFI mode, but if you installed using a Microsoft account that can be sorted out. I'm just not sold on UEFI actually improving anything.

---

### Post by cruzer001 on 2018-01-20
I do not have a UEFI system yet, but looking to buy one.  I have read articles where it is possible to have both uefi/legacy on the same system.  To me, this sounds good.  Maybe I,m wrong, but my thinking is this setup will not allow windows upgrade bork my partitions or other installs.

---

### Post by oldfred on 2018-01-20
Windows has its product key in UEFI, not sure it even then works if you try to reinstall in BIOS/CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

A few lightweight systems do not have CSM and are then UEFI class 3. Intel is proposing that new systems in a couple of years be UEFI only or all will be Class 3.
Windows only boots in UEFI mode from gpt partitioned drives.
And Windows only boots in BIOS mode from the 35 year old MBR(msdos) partitioning scheme. 

Both my Haswell & Skylake based systems have both UEFI and CSM. But I currently turn off UEFI secure boot mode, but we may want that sometime in the future.
I do prefer gpt partitioning and started using it on my old BIOS based system in 2010.
I do not have Windows on either of those systems, so Windows issues are not an issue.

---

### Post by kansasnoob on 2018-01-20
I think most of my frustrations are hardware related. I've recently rebuilt a lot of PC's using older Intel motherboards - mostly DG41** series - and UEFI boot is an option in BIOS which is disabled by default. Those boards are circa 2008 - 2010 so UEFI was somewhat in its early stages. In most cases the existing msdos formatted hard drives were still fine so all I did was make sure any proprietary drivers were removed and the swaps were easy as falling off a log.

In some cases though I replaced older (near-failing) hard drives with refurbed SSD's and decided I might as well go for full reinstalls since they were all still running Trusty and I chose to install in UEFI mode thinking future hardware upgrades may be easier (which may or may not be the case). Then I did a few DB43** -> DG41** motherboard swaps (because the DB43** series consumes 7 watts even switched off) and they were all already UEFI.

That's where the trouble began. Nothing insurmountable but certainly not as easy as dealing the the older msdos systems. For the most part I was able to upgrade the existing Trusty installs using 16.04.1 iso's and the ESP's sorted themselves out. But the Windows installs on the dual-boots became somewhat time consuming. I must confess however that I was surprised at just how forgiving Windows 10 is of motherboard changes compared to XP.

So, right now, I think the wise strategy is to go with the defaults wherever possible. If UEFI is an option that must be enabled don't do it. If UEFI is the default do not use CSM unless necessary. I assume though that we should always still disable Secure Boot? And there are of course dozens of hardware/manufacturer glitches that may need to be worked around.

I would add that I've built a few very low-end ASRock systems that are UEFI only and other than disabling Secure Boot things couldn't have been easier. It's really nice to have a working mouse in "BIOS" settings and they refined the fan settings to an art.

---

### Post by oldfred on 2018-01-20
Some vendors started adding UEFI to new motherboards just before Windows 8 came out 5 years ago. But it seemed many systems were only checked to work with Windows and often did not implement UEFI correctly.
And early Ubuntu/grub implementations of UEFI left a lot to be desired also.

But the time I installed my first UEFI system it was Haswell and by then most of the UEFI issues had been worked out.
But various vendors, still do not fully implement UEFI which is intended to allow multiple boot. They try to make system Windows only. So various work arounds are required.

And Ubuntu's grub only installs to drive seen as sda. 
In my testing of some other distributions of grub2, I found I could specify sdb drive with Fedora and it actually installed grub to sdb's ESP. Ubuntu's grub has some hard coded changes to standard grub to make it Ubuntu, implement Secure Boot, and only install to ESP on sda drive.

---

