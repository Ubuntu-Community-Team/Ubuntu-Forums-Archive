---
title: "Run linux VM from a usb, w/ vm software installed on usb?"
date: 2008-03-14
forum: Virtualisation
---

### Post by joeca0304 on 2008-03-14
I'm looking to run Ubuntu or another distro off a USB drive.  However, I don't want to reboot and boot off the USB drive.  

I also cannot install vmware, qemu, virtualbox or any other virtualization software on the host machine (windows).

So, can I somehow get Vmware, Qemu, or virtualbox, or some other virtualization software installed on the usb drive to run inside windows and then either boot the vm off a live cd or a vm image on the same usb drive?

The reason I can't install the virtualization software on the host pc is that it's a work computer, and I cannot install non-aproved software.

I'm really not looking for anything robust, just a distro that I can use to play with perl on, but inside a vm, but the vm software must be installed and run off the usb.

Is this possible?

---

### Post by ruibernardo on 2008-03-14
> **joeca0304 said:**
> I'm looking to run Ubuntu or another distro off a USB drive.  However, I don't want to reboot and boot off the USB drive.  

I also cannot install vmware, qemu, virtualbox or any other virtualization software on the host machine (windows).

So, can I somehow get Vmware, Qemu, or virtualbox, or some other virtualization software installed on the usb drive to run inside windows and then either boot the vm off a live cd or a vm image on the same usb drive?

The reason I can't install the virtualization software on the host pc is that it's a work computer, and I cannot install non-aproved software.

I'm really not looking for anything robust, just a distro that I can use to play with perl on, but inside a vm, but the vm software must be installed and run off the usb.

Is this possible?

Hi joe. I don't know if that's what you are looking for: [http://erikveenstra.nl/qemupuppy/index.html](http://erikveenstra.nl/qemupuppy/index.html)

It boots off the USB, starts a QEMU with your favourite OS inside. Didn't tried it but seems what you want.

---

