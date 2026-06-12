---
title: "Having truble opening and installing qemu"
date: 2017-03-03
forum: Virtualisation
---

### Post by andreadixon825 on 2017-03-03
Hello I just got a new computer and for some reason I'm getting this error when trying load a img file.

```
~/Downloads$ qemu -hda disk.img
No command 'qemu' found, did you mean:
 Command 'qtemu' from package 'qtemu' (universe)
 Command 'aqemu' from package 'aqemu' (universe)
qemu: command not found
```

I'm making an operating system and I use this kind of commands but its not working right.

```
qemu -hda disk.img
```

It works on one of my other computers but not my new one, dose any one knows whats I'm doing wrong?

Thanks

---

### Post by slickymaster on 2017-03-03
*Thread moved to **Virtualisation**.*

---

### Post by andreadixon825 on 2017-03-03
ok thank you

---

### Post by TheFu on 2017-03-03
> qemu: command not found

"Command not found", means the required package containing the program hasn't been installed.

The error provides a few options for packages which contain a binary with that name. Install the one you want.

**Updated:**
Tab completion on a 16.04 box, provided these options:
```
$ qemu-
qemu-img                  qemu-system-lm32          qemu-system-or32          qemu-system-tricore
qemu-io                   qemu-system-m68k          qemu-system-ppc           qemu-system-unicore32
qemu-make-debian-root     qemu-system-microblaze    qemu-system-ppc64         qemu-system-x86_64
qemu-nbd                  qemu-system-microblazeel  qemu-system-ppc64le       qemu-system-x86_64-spice
qemu-system-aarch64       qemu-system-mips          qemu-system-ppcemb        qemu-system-xtensa
qemu-system-alpha         qemu-system-mips64        qemu-system-sh4           qemu-system-xtensaeb
qemu-system-arm           qemu-system-mips64el      qemu-system-sh4eb         
qemu-system-cris          qemu-system-mipsel        qemu-system-sparc         
qemu-system-i386          qemu-system-moxie         qemu-system-sparc64       

```
Since qemu can emulate different CPUs in software, there are many choices.  If you want the best performance, use KVM on a system that has VT-x support enabled. That would limit your choices to either qemu-system-x86_64 or qemu-system-i386.  I've never run qemu emulations directly. Always used a GUI to manage them and haven't used anything but KVM since 2011-ish.  I suspect the startup for an OS would probably need more options than just the disk image file.  Perhaps some networking would be nice?

---

### Post by Doug S on 2017-03-03
As far as I know, there is not a binary called "qemu". You need to determine which architecture qemu you need and install it. Use [this page]("http://packages.ubuntu.com/search?suite=xenial&searchon=names&keywords=qemu") as a reference (I used 16.04, you use whatever version you are running). Or, work one level up from qemu as "Libvirt provides an abstraction from specific versions and hiperviors and encapsulates some workarounds and best practises". [Reference]("https://help.ubuntu.com/lts/serverguide/qemu.html").

---

### Post by andreadixon825 on 2017-03-03
ok thanks guys I got it working now, thank you very much :)

---

### Post by DuckHook on 2017-03-03
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

