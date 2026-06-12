---
title: "Starling 3 and acpi at boot (10.10)"
date: 2011-03-31
forum: System76 Support
---

### Post by EvilGnome on 2011-03-31
Hello! I just installed Ubuntu 10.10 Desktop on my Starling 4. At first the install/live usb would just hang during boot, but I tried the option acpi=off and the install went ahead successfully.

First boot of the installed system just hung as well, so I booted the live usb again and added acpi=off to /etc/default/grub and /boot/grub/grub.cfg on the installed system. Then it booted ok.

Can I get acpi working properly with this? Right now the cpu frequency scaling applet says "Frequency Scaling Unsupported" and the gnome power manager battery sensor doesn't change from the lightning bolt icon, regardless of battery/ac state, and I suspect this is due to disabling acpi.

The main issue is that without any ability to control the CPU, the processor and fans are running on superspeed, which will really eat away at the battery power. 

Any guidance would be greatly appreciated!

---

### Post by EvilGnome on 2011-03-31
I thought that checking the "download updates while installing" box during installation meant that the installed system would be up to date. It wasn't. So after upgrading everything (kernel included), I tried removing the acpi=off option and all above problems were resolved.

---

### Post by isantop on 2011-03-31
Good to hear you got it fixed. Let us know if you have any other problems.

---

