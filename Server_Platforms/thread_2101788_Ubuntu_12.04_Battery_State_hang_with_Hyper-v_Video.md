---
title: "Ubuntu 12.04 Battery State hang with Hyper-v Video card"
date: 2013-01-05
forum: Server Platforms
---

### Post by sentinelace on 2013-01-05
If anyone runs into this issue it gets solved by booting with ubuntu live and mounting your drive.

```
sudo mount /dev/sda2 /mnt
```

Browse to /etc/X11 

Edit the xorg.conf and set to:

```
Section "Device"
       Identifier "Configured Video Device"
       Driver    "vesa"  
EndSection

Section "Monitor"
         Identifier "Configured Monitor"
         HorizSync 31.5 - 70.0
         VertRefresh 50 - 160
 EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        DefaultDepth 24
        Subsection "Display"
             Depth 24
             Modes "1280x1024" "1024x768" 
        EndSubsection
EndSection
```

---

