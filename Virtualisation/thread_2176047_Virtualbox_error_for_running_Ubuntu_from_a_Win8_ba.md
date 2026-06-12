---
title: "Virtualbox error for running Ubuntu from a Win8 base OS"
date: 2013-09-22
forum: Virtualisation
---

### Post by Ian_Scott on 2013-09-22
I just bought a forth notebook that of course has Win8 as an OS. My previous 3 notebooks run Ubuntu, Mint, and dual boot Win XP. However I am reluctant to convert this new Win8 box to Linux until I've had a good play with Win8. On previous machines, Virtualbox worked perfectly from a Win XP base to run Ubuntu etc as a dual-boot OS. In the short term, I'd like to do the same with this new notebook - this seems both appropriate and pragmatic given that I just bought it yesterday! However Virtualbox starts to run (any) new VM but then stops with an error message "VT-x features locked or unavialble in MSR". I assume there must be some "enable virtualization" switch somewhere, although I've never had to do this before. I appreciate that this form relies on expertise from people well versed in Ubuntu but this is also a Virtualbox issue used to allow me to run Ubuntu from a Win8 OS base, at least in the interim. Although I like Linux and have it running on three other notebooks, I do not want to immediately switch a new notebook Win8 OS to Ubuntu until I've had a good look at how it works (yes, good old "scientific curiousity"!). However later on I will try, but expect some hardware issues will spring up unexpectedly. So, can anyone here shed some light on possible problems that may be interfering with Virtualbox, or possible web site forums were others may be wanting to do the same. It is of course unlikely that the notebook manufacturer will advise on how to get their product to run a competing OS ;). Any suggestions welcome!

---

### Post by JKyleOKC on 2013-09-23
If you can get to the BIOS, or its equivalent if the new box uses EFI or UEFI as many if not most Win8 factory setups do, the VT-x switch should be located somewhere in its setup screens. I had to explicitly enable it in an older box in order to use 64-bit guests under a 32-bit o/s installation, and that's where it was -- with a note that it should be enabled only if absolutely necessary!

A search on EFI or hyperthreading may lead you to more detailed information...

---

### Post by Ian_Scott on 2013-09-24
Hi JKyleOKC

Thanks for your reply - much appreciated. I initially thought about a BIOS switch as another notebook (Acer5920) had this in BIOS. However it was enabled by default. I tried to disable it and Virtualbox failed so like you, this seemed like a plausible approach.

However things get a bit more mickey-mouse that that! I looked at some web-chats on hyper-visors and they indicated that Win8 uses a hypervisor continuously in the background. The thread also stated that Win8 cannot run Virtualbox and this hypervisor at the same time - it needs to be disabled! Apparently the code is

bcdedit /set hypervisorlaunchtype off

Then, the comments state the need to reboot.

After that, the get the hypervisor to work again the code is

bcdedit /set hypervisorlaunchtype off

and reboot again! Well this seems user-friendly!

Otherwise I am finding that I quite like Win8. Apparently I have read about many people not liking it - well taste is personal I guess. I might try running Ubuntu on a USB hard drive as dual boot - I had this work on another notebook not long ago. Alternatively, I have three other notebooks running Ubuntu, Mint and XP is different combinations so I don't think I'll suffer any Linux withdrawal symptoms:KS!

Thanks

---

### Post by TheFu on 2013-09-24
GUIs are extremely personal. Use whatever you like and don't let anyone else tell you differently. 

I'd heard that Win8 uses Hyper-V ... so you might be able to use that instead of VirtualBox, though I wouldn't. Microsoft hasn't been known for the friendliness towards alternate OSes and virtualization.  In the MS world, people only want to run WinXP in their hypervisor - you know, for older gaming.

---

### Post by Ian_Scott on 2013-09-24
Thanks for the advise TheFu - I tend to agree! However this BIOS thing  has been bugging me and I wondered if the posted web forum threads had been  discussing some other issue or on some other machines and so on. I  booted my notebook with the esc button pushed and a BIOS screen came up.  Surprisingly I found an entry for "virtualization enable/disable" and  so I set this to enable. (Why this wasn't the default escapes me). When I  rebooted I found that Virtualbox went perfectly - whether this disables a hypervisor or not certainly produced no obvious indications! I guess you can't  believe all that you read, even if its from an Internet forum thread ;).

---

