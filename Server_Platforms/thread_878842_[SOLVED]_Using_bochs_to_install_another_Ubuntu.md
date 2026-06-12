---
title: "[SOLVED] Using bochs to install another Ubuntu"
date: 2008-08-03
forum: Server Platforms
---

### Post by kihjin on 2008-08-03
I've got remote access to a server running Ubuntu 8.04. My remote access is headless. I want to install Ubuntu directly from the iso onto another partition. 

I've been playing around with bochs here on my local ubuntu machine. I've successfully been able to launch the typical boot menu, however it only works when the display_library is set to X. I can't get it to come up under term or even svga, which is what I would need to use in a headless environment.

Also, I'm unsure of how to tell bochs to use a physical drive as it's virtual drive. I don't want to install to a bochs image. Unless of course that image could then be copied via dd to the partition of my choice.

I'm going to keep playing with it. Please post if you've got some ideas or a better way to do this.

Thanks.


p.s. for svga and term display_library I get this error message:

>>PANIC<< 16 bpp graphics mode not supported

I think it's because when the Ubuntu CD boots it shows that menu. Is there some way I can bypass the menu and go directly to text mode??

[solved]

The trick is you need to use the 'cirrus' vgaromimage.

ips: 5000000
boot: cdrom
mouse: enabled=0
romimage: file=/usr/share/bochs/BIOS-bochs-latest
vgaromimage: file=/usr/share/vgabios/vgabios.cirrus.bin
display_library: svga
megs: 512
ata0-master: type=disk, path="disk.bin", mode=flat, cylinders=100, heads=100, spt=63
ata0-slave: type=cdrom, path="/media/data/iso/xubuntu-8.04-alternate-i386.iso", status=inserted
log: foo.log

This works with 'term' used in the display_library as well. You wont see a menu, but you will see a blinking cursor. You may have to hit enter, and wait a minute before you see the installer boot up.

With 'term', you'll see the boot messages but after that you wont see anything else. This is messed up big. Sigh.

---

