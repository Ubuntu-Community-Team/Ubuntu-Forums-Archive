---
title: "Uefi"
date: 2017-05-10
forum: Security
---

### Post by gordie692 on 2017-05-10
Hey guys me again I tried Windows 10 again but not a fan sorry guys but question with this new all in desktop Acer machine if I turned off UEFI secure in BIO and installed both Mint 18.1 and Ubuntu 16.04 would I still be secured sorry for the dumb question been doing some reading on the UEFI and there question saying your secured and your not so thought I'd ask you guys besides I like both distro can't decide which one to choose

Thanks guys

---

### Post by oldfred on 2017-05-10
You normally have to boot installers with Secure boot on, so the .signed kernels & signed versions of grub are installed.
If you have to use any proprietary drivers for video or Internet then you probably cannot use Secure Boot.
If you boot installer in UEFI with Secure Boot on you can use Boot-Repair to install signed kernels.

You also cannot use grub as boot menu with Secure Boot on. It just does not chain to Windows in Secure boot mode. You can use UEFI boot menu key like f10 or f12.

       Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 
    
       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)

---

### Post by gordie692 on 2017-05-10
Thanks I'm not going to use Windows just not a fan of W10 thats why I mentioned daul booting mint and ubuntu. So I can install mint and ubuntu with UEFI enabled 
thanks for the reply

---

### Post by oldfred on 2017-05-10
Do not know what name Mint actually uses in UEFI.

Ubuntu's UEFI entry is /EFI/ubuntu/. And I install several versions of Ubuntu and each overwrites that folder. I quickly learned to backup my ESP before every install. But with Ubuntu the only real difference has been /EFI/ubuntu/grub.cfg which is a small 3 line configfile entry to find the full grub.cfg in the install. 

Of course grub has been updated, but I have yet to have grub version conflicts booting my various old & new versions.

---

