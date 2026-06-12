---
title: "Running Windows 10 inside Virtualbox"
date: 2018-09-11
forum: Virtualisation
---

### Post by yakooza2 on 2018-09-11
Hi,

I have bought an [Ubuntu VPS]("https://www.routerhosting.com/buy-cheap-vps-server/linux-kvm-vps/ubuntu-vps/").
I want to run Windows 10 inside of the VPS with VirtualBox but I could not. I have asked the support and they have told me the nested VPS is disabled. I was wondering if there is any way to install Windows 10 inside this VPS?

---

### Post by TheFu on 2018-09-11
Probably not with virtualbox.  Enabling nested VPS is something they control.  You can run other Linux versions using Linux containers, but not Windows. Sorry.
Straight qemu might work, for a 32-bit Windows. Don't think it will work for 64-bit.  And without hardware VT support, it will be painfully slow.

---

### Post by Skaperen on 2018-09-13
_qemu_ was originally just an emulator when everything was 32-bit. then virtualization was added.  then 64-bit was added as just virtualization.  emulation is much slower than virtualization.  but if you can't do virtualization in your VPS, your options are to use emulation (which is purely done in software) or find a better VPS provider (i don't know why they disabled it, which might be necessary for a security or performance reason).  there are other emulators out there, some limited to just 16-bit and some for other architectures.  i do not recall any of them being 64-bit.

---

