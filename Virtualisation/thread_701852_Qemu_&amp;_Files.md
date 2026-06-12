---
title: "Qemu &amp; Files"
date: 2008-02-19
forum: Virtualisation
---

### Post by whytheam on 2008-02-19
I have installed qemu onto a usb with  QKB.exe. Is it possible to save or move files in and out of the virtual machine qemu is running? Or, are they stuck in the "forcefield" of the iso.

---

### Post by bodhi.zazen on 2008-02-19
IMO easiest way is to boot the machine and use a network protocol, such as scp, ftp, http, samba, nfs ...

---

### Post by whytheam on 2008-02-19
The OS I have running is only 16mb. So, in other words I can't move files around without the proper network tools?

---

### Post by bodhi.zazen on 2008-02-19
16 Mb, that is small. Still you should have some network tools on it, ftp at least, possibly ssh (for scp). What OS is it ?

The only other way would be to mount the .iso with something like deamon tools or neuro, something that would allow you to add to the iso.

---

### Post by whytheam on 2008-02-20
I guess a better question to ask is if is possible for qemu to run off files and not an image and modify said files. If not is there a way to do this. I do know a bootable USB would work, but I don't want to go that route.

---

### Post by bodhi.zazen on 2008-02-20
What do you mean by "file" and "image" ?

I get the impression you are making things harder then they really are.

---

### Post by whytheam on 2008-02-21
Ok this is what I want to do. Take the files that make the OS and boot them, without them being in an image. As in .iso or .img. And, make changes to the files while the os is running and the changes don't "revert". All this as a virtual machine. What I don't want to do is format my usb create, a grub,  install the os on to the usb, and finally, finding a bios that can boot from a usb.

---

### Post by bodhi.zazen on 2008-02-21
Ah. Create a virtual hard drive and install the OS to it.

The virtual hard drive will be a file.

You make a hard drive image :

[http://www.h7.dion.ne.jp/~qemu-win/HowToFloppyCdrom-en.html](http://www.h7.dion.ne.jp/~qemu-win/HowToFloppyCdrom-en.html)

See the section on hard drives.

Then boot the iso and format the virtual HD, then install.

You will need to learn to launch qemu from the command line or use a GUI tool.

[http://www.davereyn.co.uk/](http://www.davereyn.co.uk/)

---

