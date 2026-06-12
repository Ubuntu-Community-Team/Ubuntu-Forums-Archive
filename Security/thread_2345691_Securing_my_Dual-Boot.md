---
title: "Securing my Dual-Boot"
date: 2016-12-06
forum: Security
---

### Post by spencer2 on 2016-12-06
I partitioned my drive and installed ubuntu on dual boot a few moths ago: and its newer acer with win 10, so it took me a bit to figure out and work through bios/legacy settings to get the ubuntu to boot. Once I accomplished getting ubuntu, it still never dual booted in that it it would just go straight to ubuntu. in the past and i think its supposed to now, i would be given an option between the 2 OSes when i boot up. I'm not getting this option right now. 
I hardly ever use the windows so i don't really care that it doesn't boot, but i started thinking about whether i need to be able to update software on the windows side or not.
do i need to worry about updating my windows side?
if so, i suppose i need to figure out why i'm not getting the OS option at boot (so i can at least update windows from time-to-time)?
I've also been getting weird messages when booting up and shutting down. They usually say something about my 'dev/sda6', 'autoclean'. Is this is part of the dual-boot situation?
lastly, do i need to pay more attention to any of the articles about ubuntu laptop security (like the various virus, malware, etc type programs)?

Any information would be awesomely appreciated: thank you very much.

---

### Post by DuckHook on 2016-12-06
It is important to keep *all* OSes updated, whether Windows or Linux. That's the OS's primary and most effective defence against malware. Repairing your boot process to offer Windows as an option is a separate issue and it would be best to post a separate thread on that in the subforum *Installation & Upgrades*, but the answer to your security question is straightforward: if you have it installed, you should have it up to date.

Re: autoclean

From the *apt* man page:> Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only
removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be
maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will
prevent installed packages from being erased if it is set to off.

---

### Post by DuckHook on 2016-12-06
> **spencer2 said:**
> …do i need to pay more attention to any of the articles about ubuntu laptop security (like the various virus, malware, etc type programs)?Please see the link in my sig: *Security Basics*

---

### Post by oldfred on 2016-12-07
If new Acer with UEFI and Windows 10, you should not have Legacy/BIOS/CSM on.
May be better to have Secure boot off. If Secure boot is on, you cannot boot Windows from grub menu only from UEFI boot menu.

Are Windows partitions still on drive? Can you boot Windows from UEFI boot menu?
Many sure fast start up in Windows is off.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Every Acer we have seen, needs "trust" setting to boot Ubuntu in UEFI boot mode.
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) 

 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility

Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by spencer2 on 2016-12-10
Windows partitions are still on the drive. I assume that if I set BIOS to default that Windows will boot up. Ever since I got ubuntu running (undoing the UEFI lock in BIOS), I have 1) not gotten an option at boot to choose between the 2 OSes & 2) it only boots to Ubuntu. I'll read through the Acer links (and thank you for them); but is there a specific link that shows the setting for getting boot OS options at boot?

---

### Post by oldfred on 2016-12-10
If Windows is UEFI and you installed Ubuntu in BIOS mode, you cannot dual boot from grub menu, only UEFI boot menu. Often f10 or f12 check your manual.

UEFI & BIOS are not compatible. They write hardware configuration onto drive for system to use differently, so once you start booting in one mode you cannot change.

If both in same boot mode.
sudo update-grub

---

### Post by spencer2 on 2016-12-10
so are you saying that to switch back and forth I'll just have to change BIOS settings whenever I want to go from 1 OS to the other OS?
I know in the past I was given the option of which OS to use when I booted up. If I do have to switch through BIOS, that wouldn't surprise me as I kind of think part of the UEFI is to control some of those boot/loading functions (and I could be wrong about that). 
Sorry my questions are ridiculous and I do appreciate the help.

---

### Post by oldfred on 2016-12-10
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

