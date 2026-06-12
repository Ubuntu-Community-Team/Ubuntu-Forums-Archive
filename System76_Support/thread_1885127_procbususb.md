---
title: "/proc/bus/usb  ??"
date: 2011-11-22
forum: System76 Support
---

### Post by reid_rsv869 on 2011-11-22
Hi group -

Running 11.10, I want to add the following line  to /etc/fstab to resolve some possible permissions issues that prevent  my vbox clients from accessing USB devices (though I have no trouble  using USB on the host).  An explanation I read said to add this line:

none /proc/bus/usb usbfs devgid=127,devmod=664 0 0

but when rebooting the system cannot mount that, saying it can't find /proc/bus/usb.

OK...I  look, and sure enough, usb is not in the /bus directory.  Must exist  somewhere or I would be able to use them now on the host.

Any thoughts?

rsv869

---

### Post by Flyers2391 on 2011-11-22
Are you using the OSE?  That is the one from the repositories and I believe this feature is not available in that edition.

---

### Post by M1GEO on 2011-11-24
Is there a way to get /proc/bus/usb back in 11.10? The closed source drivers from FTDI rely on having /proc/bus/usb available, and I need those to get my Olimex JTAG Programmer to work.

Any advice is greatly appreciated.

Cheers.

---

### Post by jdb on 2011-11-24
> **Compu-king said:**
> Is there a way to get /proc/bus/usb back in 11.10? The closed source drivers from FTDI rely on having /proc/bus/usb available, and I need those to get my Olimex JTAG Programmer to work.

Any advice is greatly appreciated.

Cheers.

If you install the PUEL version instead of the OSE version there will be USB support.
The OSE version which is open does not support USB.
THe PUEL version is free (as in beer) but it is not open, it supports USB.

jdb

---

