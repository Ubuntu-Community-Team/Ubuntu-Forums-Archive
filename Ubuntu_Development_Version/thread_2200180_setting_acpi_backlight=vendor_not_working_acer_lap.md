---
title: "setting acpi_backlight=vendor not working acer laptop"
date: 2014-01-17
forum: Ubuntu Development Version
---

### Post by nuttzo31 on 2014-01-17
Found another minor problem in 64 bit trusty, setting the backlight to vendor in grub works flawlessly in ubuntu 12.04 but in 14.04 it doesn't work. If i also append acpi_osx=linux to grub the brightness works with the function buttons but there is no graphic in the top corner.

I know it's just a minor visual bug but i like having things like that working properly.

edit
laptop is an acer e1-571

---

### Post by Toz on 2014-01-17
There have been some significant changes in backlight management between the kernel/video drivers of 12.04 and 14.04. 

Which video card(s) does this system have? How many backlight interfaces?
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
If you have just one video card (intel) and two backlight interfaces (acpi_video0 and intel_backlight) you can try creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...to force the system to use the intel_backlight interface.


You can also try using the **acpi_osi="!Windows 2012"** kernel parameter in lieu of acpi_osi=Linux to force the loading of a different set of acpi tables. Note: if you add this parameter to /etc/default/grub, you need to escape the quotes so it needs to look like **acpi_osi=\"!Windows 2012\"**.

---

### Post by nuttzo31 on 2014-01-18
> **Toz said:**
> There have been some significant changes in backlight management between the kernel/video drivers of 12.04 and 14.04. 

Which video card(s) does this system have? How many backlight interfaces?
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
If you have just one video card (intel) and two backlight interfaces (acpi_video0 and intel_backlight) you can try creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...to force the system to use the intel_backlight interface.


You can also try using the **acpi_osi="!Windows 2012"** kernel parameter in lieu of acpi_osi=Linux to force the loading of a different set of acpi tables. Note: if you add this parameter to /etc/default/grub, you need to escape the quotes so it needs to look like **acpi_osi=\"!Windows 2012\"**.

Thanks Toz, adding the intel.conf file did the trick, Now it is working flawlessly, thanks for the help

---

