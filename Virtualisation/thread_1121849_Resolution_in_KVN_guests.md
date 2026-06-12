---
title: "Resolution in KVN guests"
date: 2009-04-10
forum: Virtualisation
---

### Post by FrankT-Qc on 2009-04-10
I have a problem with this setup :

Host :    Intrepid amd64
Guest :   Jaunty Beta amd64
Machine : kvm

Jaunty wont launch if I use standard vga ( -std-vga ). It makes it up to grub, let me choose but never outputs any hint of a kernel trying to boot ... I can observe some CPU utilization as well as it's memory growing just as if it would be booting fine, just without a display...

Here's the command line :

```
kvm -name"Jaunty Beta" -M pc -smp 1 -boot c -alt-grab -no-quit -m 1024 -net nic -net user -snapshot -std-vga Image.raw
```

if you take off the -std-vga, everything's fine ...

```
kvm -name"Jaunty Beta" -M pc -smp 1 -boot c -alt-grab -no-quit -m 1024 -net nic -net user -snapshot Image.raw
```

The thing is without high resolution, it's almost unusable... Any hint for me ???

---

### Post by bodhi.zazen on 2009-04-10
I moved your post. This depends on the guest. You can also try VNC.

95 % + of the time I do not use a KVM guest as a desktop , so no X ;)

---

### Post by Tomy on 2009-06-23
I just got higher resolutions to work by using "-vga std" rather than "-std-vga".

I am using Jaunty with this kvm boot setup.

```
#!/bin/sh
kvm -no-acpi -usb -usbdevice tablet -soundhw all \
-hda /winXP/winXP3.img -vga std \
-boot c \
-m 512


```update:  Here is the info on -vga


KVM-77 Released: -std-vga deprecated, Improved disk performance
Monday, October 13, 2008 - 10:16 Haydn Solomon 

....

New vga option

Instead of having three command line switches ie -std-vga, -cirrusvga and -vmwarevga, you now provide one -vga switch which takes an argument, so that:

    * qemu -std-vga becomes qemu -vga std
    * qemu -cirrusvga becomes qemu -vga cirrus
    * qemu -vmwarevga becomes qemu -vga vmware

---

