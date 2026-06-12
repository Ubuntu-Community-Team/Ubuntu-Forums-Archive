---
title: "Overclocking a Nvidia GTX 570 in Precise"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Rovanion on 2012-03-17
I'm having issues enabling overclocking and getting manual control over the fanspeeds of my Nvidia GTX 570 in Precise.

I've modified my xorg.conf to enable coolbits but the options don't appear in nvidia-settings. Here's my conf:

```

Section "Device"
    Identifier    "Device0"
    Driver         "nvidia"
    VendorName    "NVIDIA Corporation"
    Option    "NoLogo"    "True"
    Option   "Coolbits" "1"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Device0"
    DefaultDepth 24
    Option "Coolbits" "1"
EndSection

```

So I'm wondering if there have been any changes to how Xorg configuration is read in 12.04, if I'm simply editing a file that has no effect. Or if there are any other known issues.

---

### Post by Rovanion on 2012-03-18
Does anyone have any idea what the issue could be?

---

### Post by dino99 on 2012-03-18
the 2000's howto are quite outdated now. now the bios is dealing with performance and powersaving because actual graphic have builtin hardware to work with.

but you can still try to burn it, or send me it before you destroy it :)

---

### Post by TerminX on 2012-03-18
You can't overclock Fermi boards on the fly under Linux as the relevant lower level bits in the driver have never been ported from Windows.

Your only option to overclock Fermi on Linux at all is to either flash the card with a custom VBIOS with your new clocks already set, or boot using another video card and pass the modded VBIOS to the NVIDIA driver (when a card isn't used as the primary output device it's not initialized at POST, leaving such initialization up to the driver).  Neither option will let you adjust clocks after initialization, but if you've already figured out your max clocks under Windows you probably won't need to.

---

### Post by Vadi on 2012-03-24
Could you describe either of the steps in more detail?

---

