---
title: "Dell Chromebook 11 - unable to set backlight and /sys/class/backlight/ is empty"
date: 2015-01-26
forum: Ubuntu/Debian BASED
---

### Post by fjreiu9 on 2015-01-26
I have installed Lubuntu on my Dell Chromebook 11 and everything works except for the backlight. Can't set the backlight with the brightness keys, neither with xbacklight,xdotool or any other GUI tool. 

I tried with a combination of grub options like `acpibacklight=vendor acpiosi=Linux`, `acpibacklight=legacy acpiosi=Linux`, `acpibacklight=vendor acpiosi=` and `acpibacklight=legacy acpiosi=` without success. Even more strange is that /sys/class/backlight/ is empty.

 - dmidecode - [http://pastebin.com/hBJxuVvY](http://pastebin.com/hBJxuVvY)

 - acpi (`grep -r . /proc/acpi`) - [http://paste.ubuntu.com/9880798/](http://paste.ubuntu.com/9880798/)
 
 - acpidump - [http://paste.ubuntu.com/9880816/](http://paste.ubuntu.com/9880816/)

 - results.log (`fwts`) - [http://paste.ubuntu.com/9880883/](http://paste.ubuntu.com/9880883/)

 - video (`dmesg | grep 'ACPI: Video'`) - [http://paste.ubuntu.com/9880928/](http://paste.ubuntu.com/9880928/)

 - version (`cat /proc/version`) - [http://paste.ubuntu.com/9880942/](http://paste.ubuntu.com/9880942/)

Does that give any useful information on the issue?

Given that the VGA Graphic hardware is at the addres `00:02.0` I tried to set its register values manually like this `setpci -s 00:02.0 F4.B=30` without success as the backlight stays the same. Shouldn't this work on every device given that it interfaces directly to the hardware?

---

