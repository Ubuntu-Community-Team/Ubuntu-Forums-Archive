---
title: "Windows 10 keeps on wiping out my dual boot"
date: 2015-09-19
forum: Windows
---

### Post by gfe on 2015-09-19
I'm using an HP Pavilion Sleekbook 14 notebook.

I had no problems setting up a dual boot with the pre-installed Windows when I got the laptop. My first problem was when I upgraded to Windows 8.1. It wiped out my dual boot. I used EasyBSD within Windows. It would boot up to a text-only boot screen; if I hit escape, it would take me to a bootup menu (I think one that's in the computer's hardware) where I could pick Ubuntu and be directed to GRUB. That was fine even if a bit improvisational.

I recently updated to Windows 10. But now every few days (I don't know what causes it), Windows 10 destroys my dual boot. I go directly into Windows and have to use EasyBSD to re-create the boot menu.

Obviously, this is inconvenient. Any suggestions?

---

### Post by ArgentWarrior on 2015-09-20
Windows 10 is a new OS and with new software comes new bugs. You might have to wait for Microsoft to fix this.

---

### Post by Bucky Ball on 2015-09-20
*Thread moved to **Windows**.*

---

### Post by kagashe on 2015-09-20
About UEFI Boot-Loaders:
Originally when you buy Windows machine it has only one Boot-loader i.e. Windows Boot-loader.

When you install Ubuntu (or any Linux Distribution) in dual boot it installs Grub Boot-loader (which does not replace Windows Boot-Loader) and both Boot-Loaders are present. When you power on the machine the Boot-Loader on top in Boot Sequence boots.

Grub also puts a link for Windows Boot-Loader so that you can boot Windows.

If you install another Linux Distribution (to make it triple Boot) once again Grub Boot-Loader is installed with the Link of this distribution on top and links for Ubuntu and Windows.

If you open Boot Sequence you can find all the three Boot-Loaders. You can also alter the sequence by entering Set-up.
By the way Grub also puts the Link to enter Set-up.

It is possible that when Windows is updated it is altering the boot sequence to bring the Windows Boot-Loader on top (but it is not wiping Grub2). If you go to BIOS Set-up you can once again alter the sequence. Generally there is a key (e.g. F2) to enter BIOS Set-up on Boot but it may not work on fastboot.

Kamalakar

---

