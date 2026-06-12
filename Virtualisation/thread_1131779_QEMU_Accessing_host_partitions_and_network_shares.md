---
title: "QEMU: Accessing host partitions and network shares"
date: 2009-04-21
forum: Virtualisation
---

### Post by jimhabegger on 2009-04-21
I want to access a host partition and some network shares from my VM in QEMU. I've looked through the man pages and documentation, and searched in the forums, but I'm still lost.

Is there any way to use a host partition directly as one of the QEMU hard drives? If not, then I suppose I can access it through my network, as a network share.

I've learned how to connect to my network and the Internet from my VM, but I'm confused about how to access network shares, or even what to read to learn how to access network shares.

---

### Post by jimhabegger on 2009-04-21
I'm on a laptop with no floppy drive, and my CD burner doesn't work. I do have a usb stick. Maybe I could use that to transfer files between the guest and host.

---

### Post by bodhi.zazen on 2009-04-21
I suggest you use a network share (samba).

If you like you can add it directly, just do not have the usb available to both the guest and host at the same time (unmount the usb device).

Assume the device is /dev/sdb (you will have to adapt it not) ;)

```
qemu -hda windows.qcow -hdb /dev/sdb
```

---

