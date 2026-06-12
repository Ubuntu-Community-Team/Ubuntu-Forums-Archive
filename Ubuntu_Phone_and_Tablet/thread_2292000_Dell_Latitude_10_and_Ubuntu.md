---
title: "Dell Latitude 10 and Ubuntu"
date: 2015-08-24
forum: Ubuntu Phone and Tablet
---

### Post by gonesolo on 2015-08-24
Hi all,

I have a Dell Latitude 10 (ST2 I think).
Its currently running Windows 8.1 (slowly as it only has 2GB RAM)

I have been considering moving it over to Linux.
It has an ATOM Processor and Intel GMA Video chipset.

I'm a bit at a loss however around Ubuntu Touch which appears to only have install guides/configuration guides for Android devices to date (and only a limited number)

Should I look at installing Ubuntu Touch on this tablet of a full copy of Ubuntu and then add the touch interface to it?

Is there a best option?
Has anyone else tried Ubuntu on a Windows tablet?

---

### Post by grahammechanical on 2015-08-24
Ubuntu Touch is now called Ubuntu Phone because it is the OS for retail Ubuntu phones and in future tablet devices. Those devices use ARM CPUs as far as I can tell. I do not think that there are OS builds for the x86 CPUs.

There used to be something called Ubuntu Desktop Next which was an ISO image of the Ubuntu phone OS that could be installed on a machine with an Intel or AMD x86 CPU. I know this to be true because I did install it myself on my desktop machine. But that ISO image has not been updated since the end of May 2015. It was a preview of what was being done in Ubuntu Phone. It is no longer being developed. It was more of a curiosity than a useful OS.

So, my advice is forget Ubuntu Phone/Touch and research Ubuntu and the Atom CPU. There may be some issues there as well.



  You will need to determine if the CPU is 32 bit or 64 bit. And if the UEFI is 32 bit or 64 bit as well.

> Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

