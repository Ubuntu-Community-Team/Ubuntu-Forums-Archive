---
title: "re-detect a previously ejected usb key without unplug/plug"
date: 2010-09-20
forum: Server Platforms
---

### Post by bluefrog on 2010-09-20
My problem is that I am trying to force the re-detection of a usb key after it has been ejected (not physically of course... eject /dev/sdd). I was thinking of
udevadm test --force --action=add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host29/target29:0:0/29:0:0:0/block/sdd

but --force is not recognized. Do I have another way to achieve what I want to do?

all this because I have a bootable usb key with grub2. whenever I change grub.cfg (edit,save,close) before I can test the key in qemu I have to unplug/plug it so that the changes are commited to "/dev/sdd"

---

