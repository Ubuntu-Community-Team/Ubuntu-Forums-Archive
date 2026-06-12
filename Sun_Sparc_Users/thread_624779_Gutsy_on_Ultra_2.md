---
title: "Gutsy on Ultra 2???"
date: 2007-11-27
forum: Sun Sparc Users
---

### Post by n5xmt on 2007-11-27
Has anyone succesfully upgraded to Gutsy on a Sparc Ultra 2?
I started with 6.06.1 and it installs fine, upgraded to 6.10 ok, upgraded to 7.04 ok, then upgraded to 7.10 and it hangs after loading the kernel...
is 7.10 just not going to support the ESP modules anymore even doing an upgrade?
Thanks

---

### Post by jawong on 2008-01-02
I found out that kernel 2.6.22-14-sparc-smp didn't boot on my Ultra2, After reinstalling numerous times over and over again. I tried booting into my old kernel of 2.6.20-15-sparc64-smp and that worked just fine.  I'm trying to figure out why the udev portion isn't locating the drives inorder to boot.  My next step is maybe to rebuild the kernel.

---

### Post by n5xmt on 2008-01-02
> **jawong said:**
> I found out that kernel 2.6.22-14-sparc-smp didn't boot on my Ultra2, After reinstalling numerous times over and over again. I tried booting into my old kernel of 2.6.20-15-sparc64-smp and that worked just fine.  I'm trying to figure out why the udev portion isn't locating the drives inorder to boot.  My next step is maybe to rebuild the kernel.

2 things I have found...
UBUNTU decided (for whatever reason) to REMOVE support for the ESP SCSI driver and the HME network card with Gutsy...  not a clue why, but they did...  so I ran 7.04, then downloaded FULL kernel source for the 2.6.2x (latest stable) kernel from kernel.org and compiled it BEFORE rebooting after the 7.10 dist upgrade... it actually works...
make sure along with the SUNESP SCSI driver, you also enable the SYM53C8XX, QLOGIC 1280 and QLA SCSI drivers.  for some reason, until I activated ALL of those, it would not load the SUNESP drivers...

---

### Post by jawong on 2008-01-08
I am having difficulties in getting the build to work correctly.  These are the steps I did.

1. Download 2.6.23
2. Download patch 12 for 2.6.23
3. uncompressed source patched to latest
4. copied /boot/config-2.6.20-16-sparc64-smp ./.config
5. ran make menuconfig
6. verified low level scsi drivers were set to * and not M
7. compiled and installed with dpkg
8. edited silo.conf

Rebooted..... system doesn't boot goes back to initramfs.

Perhaps I can see your config and see what I am doing wrong.

---

