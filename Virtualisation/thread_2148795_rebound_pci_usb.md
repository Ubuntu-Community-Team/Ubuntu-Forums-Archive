---
title: "rebound pci usb"
date: 2013-05-26
forum: Virtualisation
---

### Post by Tibology on 2013-05-26
Hi there! :)

I can passthrough my pci usb to quemu windows and use it there, but after I shutted down the emulated windows, I want to use my usb again. 
What to do?

What was done:
echo "8086 1c2d" > /sys/bus/pci/drivers/pci-stub/new_id 
echo 0000:00:1a.0 > /sys/bus/pci/devices/0000:00:1a.0/driver/unbind
echo 0000:00:1a.0 > /sys/bus/pci/drivers/pci-stub/bind 

then running widows with quemu,

then i can unbound the pci-stub with
echo 0000:00:1a.0 > /sys/bus/pci/drivers/pci-stub/unbind
but dont know what to tell to my dear linux to use it again.

Any ideas? Thx!

---

