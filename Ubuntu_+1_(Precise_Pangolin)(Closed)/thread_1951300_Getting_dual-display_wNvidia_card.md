---
title: "Getting dual-display w/Nvidia card"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by antar on 2012-04-02
Okay, system:

Trying Ubuntu 12.04b2, AMD64 version. I have an Nvidia GT 430 FX card.

Upon completing installation, Ubuntu only detected one monitor and refused to see the second one.

I tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=1945891#5") and seriously borked my system. Gonna need to do a fresh install.

Does anyone have any insights as to how I can actually do this right this time?

---

### Post by Triality on 2012-04-02
Usually, I just use the nvidia-settings program to activate both my monitors in twin view. This should be safe to do.

Personally, I need to also edit the /etc/X11/xorg.conf file, because my vga monitors resolution is not detected properly. This might not be the case for you. 
Editing this file can be tricky so make a backup of a working version before you do any modifications, in order to replace the broken version with the new one in recovery mode.

Here is the pasted version of the relevant part:
```

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GS"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: 1280x1024 +0+0, CRT: 1280x1024 +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Note the line: Option "metamodes" "CRT: 1280x1024 +0+0, DFP: 1280x1024 +1280+0"
This I had to modify on my own, because the CRT had the wrong resolution initially.

---

### Post by antar on 2012-04-02
> **Triality said:**
> Usually, I just use the nvidia-settings program to activate both my monitors in twin view.

Oh hey!

Didn't even realize that was installed by default.

---

