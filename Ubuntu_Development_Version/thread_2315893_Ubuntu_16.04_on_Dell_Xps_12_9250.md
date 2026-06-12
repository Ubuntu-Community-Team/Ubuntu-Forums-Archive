---
title: "Ubuntu 16.04 on Dell Xps 12 9250"
date: 2016-03-03
forum: Ubuntu Development Version
---

### Post by stefan39 on 2016-03-03
Hi,

I have installed Ubuntu Gnome 16.04 Beta on the Dell XPS 12 9250.
In the BIOS/UEFI I disabled Intel SpeedStep, Secure Boot and enabled Legacy Option ROMS.

Surprisingly, it works very well:

[LIST]
[*]Touchscreen works.
[*]There are no problems with the 4K monitor.
[*]Keyboard with mousepad works.
[*]WLAN works.
[*]Bluetooth works.
[*]Volume Buttons work.
[*]Microphone works.
[*]Headphone port works.
[/LIST]

The USB ports have often problems with hot plugging - the workaround (sudo sh -c "echo 1 > /sys/bus/pci/rescan") doesn't always work.

My biggest problem is, that suspend and resume don't work. Has anyone an idea to solve it?

---

### Post by howefield on 2016-03-03
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by stevebeaulac on 2016-03-09
I also have the Dell XPS 12 9250, and can confirm you suspend and resume issues.

---

