---
title: "Flackey USB support under 16.04"
date: 2016-10-06
forum: Virtualisation
---

### Post by surferX on 2016-10-06
I have been using KVM and Virtual Machine Manager flawlessly with 14.04, I used to be able to add and remove USB Host devices to add a memory stick to a VM. 

Since upgrading to 16.04 I can't seem to get the add and remove USB Host device to work. I tried using redirect USB instead, this only work some of the time. It may work just after a reboot or the first time the usb stick is mounted, but I can't work out the pattern of when it works and when it doesn't. I have looked in /var/log/libvirt and dmesg, and nothing obvious appears that might help.

Any ideas?

---

### Post by surferX on 2016-12-01
The only message I can see they may be related are the following:

```
[154843.819690] audit: type=1400 audit(1480620624.813:202): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5" pid=16287 comm="apparmor_parser"
[154843.832952] audit: type=1400 audit(1480620624.829:203): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5//qemu_bridge_helper" pid=16287 comm="apparmor_parser"
[154843.951190] audit: type=1400 audit(1480620624.945:204): apparmor="DENIED" operation="open" profile="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5" name="/run/udev/data/c189:1" pid=16352 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=117 ouid=0
[154843.951292] audit: type=1400 audit(1480620624.945:205): apparmor="DENIED" operation="open" profile="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5" name="/run/udev/data/c189:136" pid=16352 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=117 ouid=0
[154843.951391] audit: type=1400 audit(1480620624.945:206): apparmor="DENIED" operation="open" profile="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5" name="/run/udev/data/c189:130" pid=16352 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=117 ouid=0
[154843.951492] audit: type=1400 audit(1480620624.945:207): apparmor="DENIED" operation="open" profile="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5" name="/run/udev/data/c189:131" pid=16352 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=117 ouid=0
[154843.951592] audit: type=1400 audit(1480620624.945:208): apparmor="DENIED" operation="open" profile="libvirt-84af29fc-b999-5fa3-f3db-2c25948a60a5" name="/run/udev/data/c189:132" pid=16352 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=117 ouid=0
```

One think I have just noticed is that sometimes the using the usb redirect result in the usb device being seen by the Windows VM but it usb device is with no file system, so windows want me to put a disk in the usb device...

---

### Post by surferX on 2016-12-01
this seems to fix it

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1515791](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1515791)

---

### Post by Bucky Ball on 2016-12-01
Your code is much easier to read if you use code tags. See the link in my signature at the bottom of my post for how to use them.

---

