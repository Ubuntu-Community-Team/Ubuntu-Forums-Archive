---
title: "[apparmor] new: Chrome crashing when USB drives inserted"
date: 2013-04-02
forum: Security
---

### Post by sambhogi on 2013-04-02
I'm using rookcifer's apparmor profiles for Chrome, with some minor tweaks. The latest update to Chrome, however, crashes on start if a USB drive is present (and crashes if already running when a USB drive is inserted) with the following message:

> apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/chrome" name="/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host5/target5:0:0/5:0:0:0/block/sr0/uevent" pid=9638 comm="Chrome_FileThre" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

I know how to fix this to make Chrome not crash, my question (which I will also post as a Chrome bug) is why Chrome should require this access at all, let alone why it should crash if it does not get this access. Speculation? 

Chrome's need for fairly intrusive system access disinclines me from using it, although I like its other security and performance advantages.

---

