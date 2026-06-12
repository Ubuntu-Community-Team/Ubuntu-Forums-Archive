---
title: "ubuntu install drops back to grub, cant seem to fix it"
date: 2023-02-13
forum: Ubuntu/Debian BASED
---

### Post by nicktf on 2023-02-13
Hi,

I have tried to install LXDE 20.04 (via live USB) on an old hp netbook, the install gives no errors but the machine drops back to the grub prompt. I have tried to fix this manually, by configuring the grub command line, but the various choices for setting the grub 'linux' and 'initrd' all seem to fail (generally cant see the sda2 device) and result in a drop back to grub. The machine used to have windows7 and the bious supports 'legacy' non efi boot. USing either of these also fails.

Any help really appreciated from someone who knows what they are doing!!

I have attached screen shots of what grub can 'see' and a failed boot

Many thanks
nick

---

### Post by nicktf on 2023-02-13
Sorry, just to clarify its the current LXLE Focal version based on Ubuntu 20.04.4 LTS (taken from grub command 'cat (hd0,2)/etc/issue)
nick

---

### Post by coffeecat on 2023-02-13
Moved from chat to a support sub-forum - *Ubuntu/Debian Based*.

---

### Post by kc1di on 2023-02-13
Is this 32 or 64 bit machine? Give us some info on what the machine is.

---

### Post by yancek on 2023-02-13
The first image you posted shows trying to boot an efi kernel yet you say your computer is not efi capable.  Do you get the same result with a non-efi kernel?  Grub sees the kernels and initrd as they show in your image.  Windows 7 was released over 13 years ago so posting some info on the hardware as suggested should be helpful.

Are you having this problem with the installer or have you installed and now get the error when trying to boot it?

---

### Post by nicktf on 2023-02-13
A HP Stream netbook, celeron 1.6Ghz, 2GB ram, 64mmc disk

---

### Post by nicktf on 2023-02-13
The machine is efi capable. The bios is current set to use uefi and then legacy mode, secure boot is disabled
Yes, I originally tried the non efi kernel, with the legacy boot, but when this booted it complained is could not find /dev/sda2, event though it appears to be installed on that device/partition.
I have no real skill/knowledge in this area, so then explored other not generic options, based on the followed the steps from here [https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux)

The live image from usb run, and from there I installed to hard hard disk, when the restart is hit and the machine boots I'm dumped at the grub prompt.
I ran the live image again and downloaded a boot repair program which claimed to have worked!

---

### Post by nicktf on 2023-02-13
Its 64bit

---

### Post by yancek on 2023-02-14
Run boot repair and select the option to Create BootInfo Summary and post the link you get when it finishes.  That should give details about your system.

---

### Post by nicktf on 2023-02-20
Hi,

Thanks for all the input.

I have managed to work this out, although not sure why is really fixed!

 The (repeated) live install seemed to have mis-identified the hard drive, setting the grub command line with (hd0,gpt2) did not work, event though that was how it saw/reported the disk.
during one boot it dropped back to a initrd prompt and there, in the /dev dir was a mmcblk0p1 and mmcblk0p2. Using mmcblk0p2 as the kernel location for grub brought the system to life :)
Not sure why is not listed as sda1 or the like?

nick

---

