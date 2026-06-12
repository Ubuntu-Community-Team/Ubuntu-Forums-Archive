---
title: "Windows 8 Certified Computers May Not Be Able To Boot Linux"
date: 2011-09-21
forum: Sudan Team
---

### Post by mhmdfoss on 2011-09-21
According to an article by [ITWorld]("http://www.itworld.com/it-managementstrategy/205255/windows-8-oem-specs-may-block-linux-booting"), **Microsoft requires that Windows 8-certified machines use UEFI** (Unified Extensible Firmware Interface) **with support for secure booting** instead of the BIOS firmware.


This  means that both the firmware and software used in the boot process must  be signed by a trusted Certificate Authority and at the moment, none of  the EFI Linux bootloaders is signed. So basically, if you buy a  computer that includes the manufacturer's keys and Microsoft's keys, you  won't be able to boot a Linux distribution.


To  get secure UEFI booting support for a Linux distribution, a non-GPL  bootloader would be required and since in the near future the kernel  itself will be a part of the bootloader, the kernel would have to be  signed too, meaning you won't be able to compile your own custom  kernels.

Matthew Garrett, a Linux developer at Red Hat says:

[INDENT]"Microsoft  requires that machines conforming to the Windows 8 logo program and  running a client version of Windows 8 ship with secure boot enabled. The  two alternatives here are for Windows to be signed with a Microsoft key  and for the public part of that key to be included with all systems, or  alternatively for each OEM to include their own key and sign the  pre-installed versions of Windows. The second approach would make it  impossible to run boxed copies of Windows on Windows logo hardware, and  also impossible to install new versions of Windows unless your OEM  provided a new signed copy. The former seems more likely.

[...]  Firstly, we'd need a non-GPL boot loader. Grub 2 is released under the  GPLv3, which explicitly requires that we provide the signing keys. Grub  is under GPLv2 which lacks the explicit requirement for keys, but it  could be argued that the requirement for the scripts used to control  compilation includes that. It's a grey area, and exploiting it would be a  pretty good show of bad faith. Secondly, in the near future the design  of the kernel will mean that the kernel itself is part of the boot loader. This means that kernels will also have to be signed. Making  it impossible for users or developers to build their own kernels is not  practical. Finally, if we self-sign, it's still necessary to get our  keys included by ever OEM."[/INDENT]

Even  if the major Linux distros find a way around this (hopefully), there  are still questions like: what will happen with small Linux  distributions or how will the users or various companies boot their own  custom kernels? But before getting there, here's the most important  question:[SIZE=4][COLOR=Red] **is this legal?**[/COLOR][/SIZE]

---

### Post by srs5694 on 2011-09-21
There's already a very lengthy discussion of this topic [here.](http://ubuntuforums.org/showthread.php?t=1847476) The bottom line right now is that it's not clear how much of a real impact this will all have -- it could be anywhere from none to disastrous (at least for typical home users). My own guess is it will have closer to no impact than a disastrous one, as I detail in my posts in the other thread.

I have yet to see an opinion on the legal questions from anybody I know is qualified to comment on it -- and without more information on how it will actually be implemented, nobody who is qualified is likely to say anything.

---

### Post by mhmdfoss on 2011-09-22
thanks a lot
i hope it is a rumor

---

