---
title: "prevent mounting of USB disk on /media"
date: 2011-01-02
forum: Server Platforms
---

### Post by risacher on 2011-01-02
I have an external USB disk that I want to map into a libvirt-based virtual machine.  Unfortunately, at boot, the physical host sees the USB disk and automounts the drive as /media/video3, which seems to muck-up the device for the VM which I intended to access that disk.

Is there some clever Ubuntu way to prevent automounting a particular filesystem on removable media?

(Both the host and VMs are running Karmic)

---

