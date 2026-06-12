---
title: "640 x 480 mode line for bonobo?"
date: 2009-05-22
forum: System76 Support
---

### Post by hiryu on 2009-05-22
Hello,

I just received my System76 Bonobo Professional yesterday. 

Unfortunately the only initially available resolution for this thing was 1920x1200. I had to manually generate a bunch of modelines so other resolutions could be available.

Has anyone managed to find a working 640x480 modeline for the bonobo professional? I need it for games such as starcraft.

For educational purposes, here's the mode lines I've successfully got working:
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Modeline       "800x600"  37.52  800 832 912 1024  600 601 604 621  -HSync +Vsync
    Modeline       "1440x900"  104.58  1440 1520 1672 1904  900 901 904 931  -HSync +Vsync
    Modeline       "1280x1024"  106.97  1280 1360 1496 1712  1024 1025 1028 1059  -HSync +Vsync
    Modeline       "1280x960"  99.36  1280 1352 1488 1696  960 961 964 993  -HSync +Vsync
    Modeline       "1152x864"  80.17  1152 1216 1336 1520  864 865 868 894  -HSync +Vsync
    Modeline       "1024x768"  63.04  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
    Modeline       "800x600"  37.52  800 832 912 1024  600 601 604 621  -HSync +Vsync
EndSection

---

