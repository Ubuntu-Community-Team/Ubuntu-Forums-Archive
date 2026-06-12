---
title: "General protection fault at reboot"
date: 2018-01-24
forum: Server Platforms
---

### Post by elbandido on 2018-01-24
I'm using Ubuntu Server 16.04.3 LTS on a HP Elite 8300 running a Plex server. I am fairly new to the OS. 
When rebooting the machine, it get a "general protection fault: 0000 [#1] SMP" error and the system stalls. Shutdown seems to work fine, though.

The when rebooting, the shutdown seems to go fine, but after "Reached target shutdown", I get the error:
[ATTACH=CONFIG]278311[/ATTACH]

Any suggestion or help is greatly appreciated!

---

### Post by howefield on 2018-01-24
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2018-01-24
I'm no expert in error dumps but I'd slap the Ubuntu CD in the drive, boot into it and run the memtest86 for at least an hour and see if it finds any issues with the RAM.

LHammonds

---

### Post by hschultz1960 on 2018-01-25
Hi ... for what it is worth, I am having the EXACT same problem. I am also on an HP Elite 8300 quad core system, so perhaps this is a clue.

For me the problem has not always been there, it started about 2-3 weeks ago it seems, perhaps back in December, after having worked OK for 3 months. Maybe related to an Ubuntu auto update.

I'll try dig around ...

---

### Post by elbandido on 2018-01-25
Thanks for the suggestions.
@LHammonds: I will certainly try it; although my system runs otherwise smoothly without any general protection faults.
@hschultz1960: What a coincidence! The reboot issue indeed started recently (a few weeks ago), it worked perfectly in the past. I installed Ubuntu back in September 2015.

---

### Post by jarinarenos on 2018-01-31
Same situation here. I was running on older HP hardware (HPC 6200 pro) so I thought memory might be at fault, but it tests clean.

---

### Post by ajkumaraswamy on 2018-02-02
I have the same problem with my HP Compaq 8300. Same General Protection fault at reboot. I can shutdown nonetheless. Memtest86+ gave no errors. The machine has been working well for 4 years now and this problem has arisen only in the last few weeks, specifically since Kernel 4.4.0.109. I checked and this error does not occur with previous kernels. Does this have anything to do with the recent Kernel patches against processor security vulnerabilities?

---

### Post by Dthdealer on 2018-02-14
Identical problem has just surfaced for me.

**Product:** HP Compaq Elite 8300 SFF (QV996AV)
**Processor:** Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
**Kernel:**  4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

This problem has appeared just on this one box.  The three others of the same model that I run Ubuntu 16.04 on do not appear to have this issue at the moment.  Still investigating.

EDIT: There are only two obvious differences between the three working boxes and this misbehaving one:

1) This box is using UEFI/EFI instead of BIOS+MBR
2) This box has a different model of HDD

I'm going to try nuking the install, disabling UEFI and reinstalling.

---

### Post by Dthdealer on 2018-02-15
I've completed my test: reinstalling with a BIOS+MBR style install (instead of an efi one) seems to have fixed the problem.

---

### Post by LHammonds on 2018-02-15
So, HP+UEFI+Ubuntu = Bad.  Got it.

Thanks for coming back to post your findings.

**EDIT:** Found a [page about Ubuntu + UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by QIII on 2018-02-15
Unfortunately, HP's UEFI implementation is not standards compliant.  It still looks specifically for a signed Windows Boot Manager.

---

### Post by hurratheburra on 2018-03-04
Same computer, same reboot problem, Ubuntu 16.04.3 LTS. Shutdown working fine.
Above answers were a dead end. Even tried updating the BIOS. This post helped med solve the issue: [https://askubuntu.com/questions/999952/general-protection-fault-at-reboot](https://askubuntu.com/questions/999952/general-protection-fault-at-reboot)
Ended up with a kernel downgrade to linux-image-4.4.0-87-generic and still using UEFI boot. Note that you can try out different kernels by selecting which of the installed ones to boot in grub (ESC at boot on HP 8300-> enter -> advanced...)

---

### Post by elbandido on 2018-04-12
[COLOR=#111111][FONT=Ubuntu]I just upgraded to kernel version **4.4.0-119** and the problem seems to be solved. Reboot on my system is working fine again.[/FONT][/COLOR]

---

### Post by ajkumaraswamy on 2018-05-02
Can confirm, system reboots without any problems since kernel version 4.4.0-119.

---

