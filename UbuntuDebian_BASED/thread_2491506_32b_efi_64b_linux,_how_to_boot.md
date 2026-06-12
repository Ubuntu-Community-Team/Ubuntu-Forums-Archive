---
title: "32b efi 64b linux, how to boot"
date: 2023-10-11
forum: Ubuntu/Debian BASED
---

### Post by mforum2 on 2023-10-11
Hello,


I have an old mini pc (zotac pi321) and was already successful to install linux mint a year ago.


Now I want to install a fresh verion of ubuntu (do not ask why, I messed up the current installation). I am going to use Bodhi 7 based on ubuntu 22.04 and the iso is already on the usb stick. the /efi/boot contains the file grubia32.efi and also the 64b efi files.


so far so good. during the boot process. I go into the bios and deactivate secure boot and fast boot, set efi to boot only (no legacy) and also change the boot order that usb is first.


save and exit - the boot process always brings me to the grub menus of the installed system and not to the grub entries of the usb stick!? From there I can access the grub terminal. I was following serveral online guides but apparently I always used the wrong one, because it is not working as intended.


how can I boot from the usb stick (e.g. using the grub terminal with some commands ok - but what are the correct commands?) to install a fresh version ubuntu 22.04 with bodhi?


the usb stick is hda...

---

### Post by howefield on 2023-10-11
Not Ubuntu thread, moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2023-10-11
Bodhi 7 is not an official flavor of Ubuntu.
 Moved to sub-forum.

But are you sure it is 32 bit? Manual says it supports Windows 8 which Microsoft expected UEFI boot and 64 bit.
And with only 2GB of RAM, you need a light weight flavor of Ubuntu. Do not know if Bodhi is consisted light weight or not.
And Ubuntu now is 64 bit only.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by mforum2 on 2023-10-15
Hello,

yes I am sure. The windows 8 on the system was a 32bit version. 

I was able to install efi 32bit with Mint xfce 64bit a year ago. Of course I can try xubuntu as well but...
- Bodhi provides the required efi 32bit boot file already in their default iso. 
- It is based on Ubuntu LTS. 
- Furthermore is the lightning desktop nice looking alternative and a very light solution. 

That is why I want to try Bodhi.

My problem is still that I can not boot from grub - after reading some howto's, I am able to see all grub entries (local disk and usb disk). Now I can choose boot from Bodhi but I do get an error message that grub is missing a 32bit file... I think this is the wrong way. It was working the last time, when I installed Linux over Win...

---

### Post by mforum2 on 2023-10-15
Hello,

yes I am sure. The windows 8 on the system was a 32bit version. 

I was able to install efi 32bit with Mint xfce 64bit a year ago. Of course I can try xubuntu as well but...
- Bodhi provides the required efi 32bit boot file already in their default iso. 
- It is based on Ubuntu LTS. 
- Furthermore is the lightning desktop a nice looking alternative for a light desktop. 

That is why I want to try Bodhi.

My problem is still that I can not boot from grub - after reading some howto's, I am able to see all grub entries (local disk and usb disk). Now I can choose boot from Bodhi but I do get an error message that grub is missing a 32bit grub file... I think this is the wrong way. It was working the last time without it, when I installed Linux over Win...

---

### Post by oldfred on 2023-10-15
Just because you have 32 bit Windows does not mean system is 32 bit.
Do not know Bodhi, but did you try booting with a 64 bit version?

---

### Post by qyot27 on 2023-10-16
> **oldfred said:**
> Just because you have 32 bit Windows does not mean system is 32 bit.
Do not know Bodhi, but did you try booting with a 64 bit version?
They aren't saying the system is 32-bit, they're saying the UEFI is 32-bit.  Which it is, because the 32-bit Windows that shipped on it == 32-bit UEFI, even if the CPU platform is 64-bit.  It's called mixed-mode UEFI, and it was a pain point for 64-bit Linux distros ca. 2015 (when a lot of these mini-PCs did stuff like this; the 32-bit copy of Windows was a space-saving measure for the 32GiB eMMC storage, not because of platform architecture restrictions).

[https://wiki.debian.org/UEFI#Support_for_mixed-mode_systems:_64-bit_system_with_32-bit_UEFI](https://wiki.debian.org/UEFI#Support_for_mixed-mode_systems:_64-bit_system_with_32-bit_UEFI)

I had a first-generation Quantum Byte that had that kind of mess; I ended up resorting to installing Debian (and maybe Ubuntu, eventually; I can't remember) to an external HDD and had to go through the process of injecting the *grub-efi-ia32* package (which is still there in the repos for 23.10, probably for this very reason) during either the install process or after-the-fact, and I vaguely remember that I still had to manually issue the boot commands anyway.  The Byte3 that replaced it when it died was far more sane: proper 64-bit UEFI and supported installing an SSD so you could swap over to far larger storage for the OS(es).

Can't speak for how Bodhi differs from this, though.

---

### Post by bobunderwood99 on 2023-10-16
Try installing 32-bit (i386) Debian with a lightweight DE like LXLE, LXQt, XFCE or Mate.

[https://www.debian.org/CD/http-ftp/](https://www.debian.org/CD/http-ftp/) 

[https://wiki.debian.org/DesktopEnvironment](https://wiki.debian.org/DesktopEnvironment)

---

