---
title: "Anyone know how: To boot a VirtualBox VM from a flash drive?"
date: 2010-08-20
forum: Virtualisation
---

### Post by ant2ne on 2010-08-20
There has got to be some trick to boot a VritualBox VM from a flash drive. I've got puppy linux that runs from my flash drive. And it is pretty cool in that it remembers changes made in that OS. I'd like to boot it in a VM for easy access (so I don't need to insert it in a computer and reboot the computer to boot from the USB drive) and perform updates and modification to that OS.

But it doesn't look like Virtual Box offers an easy solution to this. But there has got to be a way. Any ideas?

---

### Post by ant2ne on 2010-08-20
Looks like I figured it out using this sort of process

[http://agnipulse.com/2009/07/boot-your-usb-drive-in-virtualbox/]("http://agnipulse.com/2009/07/boot-your-usb-drive-in-virtualbox/")

Except the command I used was

```
VBoxManage internalcommands createrawvmdk -filename ./puppy_flash_usb.vdi -rawdisk /dev/sdh
```(all one line)

problem now is, how do I make that USB device ALLWAYS show up as sdh? Even after reboots?

---

### Post by bodhi.zazen on 2010-08-22
Portable VirtualBox :

[http://www.vbox.me/](http://www.vbox.me/)

[http://www.pendrivelinux.com/using-a-portable-virtualbox-to-run-linux-from-usb/](http://www.pendrivelinux.com/using-a-portable-virtualbox-to-run-linux-from-usb/)

As you can see , /dev/sdh is going to vary depending on your hardware.

---

### Post by ant2ne on 2010-08-23
I'm not sure why you linked those 2 sites. Its not really what I'm talking about.

There has got to be a way to assign a /dev to a given device. Perhaps by using its uuid? I know I'm digging deep into the core of the OS, but there has to be a way.

---

### Post by C.S.Cameron on 2010-08-23
I keep an XP vdi on flash drive that boots in Vbox.
I have Vuppy, (a puppy derivative with vbox), on another flash drive.
They work together ok if a bit slowly.

---

### Post by C.S.Cameron on 2010-08-23
> **bodhi.zazen said:**
> Portable VirtualBox :

[http://www.vbox.me/](http://www.vbox.me/)

[http://www.pendrivelinux.com/using-a-portable-virtualbox-to-run-linux-from-usb/](http://www.pendrivelinux.com/using-a-portable-virtualbox-to-run-linux-from-usb/)

As you can see , /dev/sdh is going to vary depending on your hardware.

I tried a portable vbox, It kept screwing up my non portable one, use with caution.

---

