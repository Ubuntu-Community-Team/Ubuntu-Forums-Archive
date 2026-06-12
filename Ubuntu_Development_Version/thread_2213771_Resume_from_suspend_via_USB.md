---
title: "Resume from suspend via USB?"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by ThomasNovin on 2014-03-28
Upgraded to Trusty today and wasn't able to use my previous method of resuming from suspend by just pressing the keyboard/moving the mouse.

Previously, I have enabled the relevant USB device via /proc/acpi/wakeup but now it doesn't list any USB devices?

$ grep USB /proc/acpi/wakeup
$ 

Before I could see USB0 and USB2 there.

---

### Post by ThomasNovin on 2014-03-28
Ah, it actually does work, I just can't see USB* in /proc/acpi/wakeup.

This method still works: [http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid](http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid)

---

### Post by Cavsfan on 2014-03-28
That's odd this is what I have:

```
cavsfan@cavsfan-MS-7529:~$ grep USB /proc/acpi/wakeup
USB0      S4    *enabled   pci:0000:00:1d.0
USB1      S4    *enabled   pci:0000:00:1d.1
USB2      S4    *enabled   pci:0000:00:1d.2
USB3      S4    *enabled   pci:0000:00:1d.3
EUSB      S4    *enabled   pci:0000:00:1d.7
```

Mine wakes from suspend just like it should.

But I installed this a while back it is not beta.
```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Mar 10 10:38

```

---

