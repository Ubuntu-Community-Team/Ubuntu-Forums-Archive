---
title: "I upgraded, and now I have this error..."
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by mayagrafix on 2014-03-30
14.04 works fine so far, except for screaming HD fan. Only fan related software installed before upgrade is X Sensors, which has no fan speed control options. Thanks for your attention :>)

---

### Post by bapoumba on 2014-03-30
Moved to Ubuntu +1.

---

### Post by ibjsb4 on 2014-03-30
Did ACPI get turned off?

---

### Post by mayagrafix on 2014-03-30
I checked the GRUB menu (kernel command line) and under the linux entry there is **no** reference to ACPI, after quiet splash, on or off.

here is the line from GRUB:

Fi
linux       /boot/vmlinuz-3.13.0.20-generic root=UUID41040b88-9b6d-459e-ab47-91c09e3bd0af ro quiet splash $vt_handoff
initrd       /boot/initrd.img-3.13.0.-20-generic

---

### Post by pqwoerituytrueiwoq on 2014-03-30
what motherboard?
there is a fan control package that works with lm-sensors

---

### Post by mayagrafix on 2014-03-30
> there is a fan control package that works with lm-sensors 
I have lm-sensors and the xsensors graphic front end 
============================================
___________________Board___________________
Board Vendor:   Dell Inc.
Board Version:   A00
Board Name:   0GDG8Y       
Board Asset Tag:          
___________________Bios____________________
Bios Vendor:   Dell Inc.
Bios Version:   A04
Bios Date:   11/21/2011
_________________Chassis__________________
Chassis Vendor:   Dell Inc.
Chassis Version:   00
Chassis Type:   3
Product Version:   00
_________________Product__________________
Inpiron 620s

---

### Post by pqwoerituytrueiwoq on 2014-03-30
[thinkfan](apt:thinkfan) should be able to help

---

### Post by mayagrafix on 2014-03-30
Thanks for the info. I will look into it. However, I just noticed that when I put the PC in suspend mode and then wake it up, everything is normal, both fans are operating normally. Only when I boot the system do the fans go into 100%.

---

