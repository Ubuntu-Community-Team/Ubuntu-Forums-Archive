---
title: "Usb en VirtualBox"
date: 2013-08-30
forum: Virtualisation
---

### Post by andresol on 2013-08-30
I appreciate your cooperation helping me enable the USB port on Ubuntu 12.04 32 bit on which I have installed VirtualBox.


Thank you.

---

### Post by CharlesA on 2013-08-30
If they are USB2 ports, you need to use the version of VirtualBox from virtualbox.org and install the extension pack. You also need to install the guest additions in the VM you want USB access from.

If you are trying to use USB3 ports, as far as I know VirtualBox does not support USB3, so they won't work.

---

### Post by Perryg on 2013-08-31
Small correction.  You do not have to install the guest additions (in the guest) to be able to use USB, but they will make your guest run smoother.
Plus you do need to be in the vboxusers group on the host to be able to use USB in the guest.

---

