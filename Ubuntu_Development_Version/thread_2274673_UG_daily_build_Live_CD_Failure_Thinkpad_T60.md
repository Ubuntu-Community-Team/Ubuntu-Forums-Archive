---
title: "UG daily build Live CD Failure Thinkpad T60"
date: 2015-04-21
forum: Ubuntu Development Version
---

### Post by makitso on 2015-04-21
Not sure where to go with.  I had problems with UG with 14.10, there was graphics corruption with the Intel Express 945 chipset.  So, I thought I would give the latest 32 bit 15.04 live cd a spin.  This was the latest build 219 downloaded 21/4.  

When I selected the Try option, the system hung at the ..starting ACPI event daemon.  So, I added ACPI=off to the kernel parameters and tried again.  This time it got a bit further along got to a graphics screen and then hung.  So, added nomodset to the kernel boot parameters.  This time it booted to the full UG desktop.  However, there was no mouse, either wireless or touchpad.  

Am I missing something?  Oh yes, I did do a check of the dvd and it said it was fine.

---

### Post by ventrical on 2015-04-21
I had some laptops and a Dell desktop that were obsoleted by the older family chipset members. Don't have the specs right on hand but I shelved those PC. At least with unity they will not work ...

---

### Post by ventrical on 2015-04-21
Works fine on my t61


```


ubuntu-gnome@ubuntu-gnome:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller

```

---

