---
title: "USB drive disappears from host whenever the guest VM starts"
date: 2014-04-27
forum: Virtualisation
---

### Post by yan4 on 2014-04-27
I have an USB harddrive plugged into my system.

When I run a virtual machine (eg. Windows 7) it captures my USB drive and it disappear from host.

I would like to know how could I have the USB drive available either for guest as well for the host at the same time. Is this possible?

Thanks!

---

### Post by SeraphTC on 2014-04-29
This isn't possible - a USB device can only be connected to one system at a time (whether both are physical or either/both are virtual).

I would leave the drive connected to the host and share it, then connect to the network share from the guest.  Alternatively, if you are using VirtualBox you can set the drive up as a shared folder in the settings of the VM (I think you can also do this in VMWare)

---

### Post by yan4 on 2014-04-30
Good idea, Seraph! Thank you!

:)

---

### Post by SeraphTC on 2014-04-30
You're welcome :)

---

