---
title: "Pop!_OS QGeeM 3rd monitor"
date: 2023-03-31
forum: Ubuntu/Debian BASED
---

### Post by agnieszka2 on 2023-03-31
I installed DisplayLink on Pop!_os system and I use DisplayLink device  usb-c to hdmi to connect my external monitor. But the device doesn't  detect it. Could you please help?

aga@pop-os:~/Work/DisplayLink USB Graphics Software for Ubuntu5.6.1-EXE$ dkms status 
evdi/1.12.0, 6.2.0-76060200-generic, x86_64: installed 
evdi/1.12.0+dfsg: added 
system76/1.0.14~1643391291~22.04~78ede46, 6.2.0-76060200-generic, x86_64: installed 
system76/1.0.14~1643391291~22.04~78ede46, 6.2.6-76060206-generic, x86_64: installed 
system76_acpi/1.0.2~1678132042~22.04~ed01124, 6.2.0-76060200-generic, x86_64: installed (original_module exists) 
system76_acpi/1.0.2~1678132042~22.04~ed01124, 6.2.6-76060206-generic, x86_64: installed (original_module exists) 
system76-io/1.0.2~1655490480~22.04~0217576, 6.2.0-76060200-generic, x86_64: installed 
system76-io/1.0.2~1655490480~22.04~0217576, 6.2.6-76060206-generic, x86_64: installed 
aga@pop-os:~/Work/DisplayLink USB Graphics Software for Ubuntu5.6.1-EXE$ lsusb -d 17e9: 
Bus 001 Device 006: ID 17e9:6000 DisplayLink QGeeM-6901

---

