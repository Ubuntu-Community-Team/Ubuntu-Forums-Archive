---
title: "Kernel panic-not syncing: Attempted to kill init Question?"
date: 2011-07-20
forum: Server Platforms
---

### Post by dirtrider1 on 2011-07-20
I recently installed Ubuntu server 10.04 32bit on my old HP Compaq Proliant ML330 G3 and after trying to re-install I'm getting this error while running the installation disk -

udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:06.0/host4/target4:0:0/4:0:0:0/block/sda (88
/sys/devices/pci0000:00/0000:00:06.0/host4/target4:0:0/4:0:0:0/block/sda/sda (886)
{  180.688365} Kernel panic - not syncing: Attempted to kill init!

I also get similar errors while attempting to boot off the hard drive except it allows me to type my encryption passphrase and then it shows a purple screen that says Ubuntu 10.04 exactly like the graphical boot screen then it stalls out.

I understand what the Kernel panic-not syncing: attempted to kill init message means, but I'm still trying to track down what is causing this issue? My server has 2 ide channels and I added a PCI-X to Sata card with two Sata drives connected and one Ide drive connected as the system drive with root,swap and boot partition.  My setup had the two Sata drives in a raid0 and the ide drive setup with encrypted root and swap and a boot partition.

Any help would be greatly appreciated thanks

---

