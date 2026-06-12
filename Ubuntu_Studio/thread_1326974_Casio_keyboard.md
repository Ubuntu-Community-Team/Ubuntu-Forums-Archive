---
title: "Casio keyboard"
date: 2009-11-14
forum: Ubuntu Studio
---

### Post by Ria2505 on 2009-11-14
I am new to ubuntu and I have a Casio keyboard. I am hoping to use it with rosegarden. I hooked it up to the computer with a usb cable but the computer wont recognize it. I looked on the user manual and it said i would have to install a driver from a cd-rom. The computer wont recognize the cd-rom either. What do i do?

---

### Post by frankwakeman on 2009-11-15
Your CD will be Windows and Mac Drivers.  If your keyboard hasn't been recognised (and I was surprised to find my Korg Nanokey is) then you might be out of luck as far as goes using it with Linux.

---

### Post by sgx on 2009-11-15
> **Ria2505 said:**
> I am new to ubuntu and I have a Casio keyboard. I am hoping to use it with rosegarden. I hooked it up to the computer with a usb cable but the computer wont recognize it. I looked on the user manual and it said i would have to install a driver from a cd-rom. The computer wont recognize the cd-rom either. What do i do?
there is a command

lsusb

Type this in a terminal and press the Enter key to run it, and you'll see what usb items are seen by your linux, output will be similar to this

[you@localhost ~]$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1f28:0020
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

usbview is a gui app for the same use, but can supply the info with different info.
If it shows up, find the qjackctl how-to pages, its the gui for jackd, both are standard linux apps to connect audio devices.
Cheers

---

