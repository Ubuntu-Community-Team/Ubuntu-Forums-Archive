---
title: "WC3 TFT crashes under Wine 1.3 + Lucid Lynx"
date: 2011-01-16
forum: Wine
---

### Post by facedown on 2011-01-16
I have 2x monitors and both have different resolutions. Here's my xorg.conf:

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD HW191D"
    HorizSync       30.0 - 80.0
    VertRefresh     49.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    Option         "NoLogo" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1440+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1280+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


And my invocation using wine -1.3.11:

> meder@meder-desktop:/media/9C4C96F94C96CD80_$ wine /media/9C4C96F94C96CD80_/Program\ Files/Warcraft\ III/war3.exe -opengl -w
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f300,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f60c,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x147d18,0x147c38): stub
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented TransmitFile
fixme:imm:ImmGetOpenStatus (0x145370): semi-stub
fixme:imm:ImmReleaseContext (0x30022, 0x145370): stub


It constantly crashes on games in Bnet after a few minutes giving this Windows-like dialog. Notes:

- I don't think the "-w" has any bearing because it opens full screen regardless, and it crashes without the "-w".

- Also, when in game it has these random flashes while I'm playing, which are semi transparent and not overly obtrusive but still annoying.

- Warcraft 3 version is legit and the latest bnet patch applied.

- I am *not* emulating a virtual desktop in winecfg. The settings are vanilla/default.

Looking for any suggestions to address this crashing issue.

---

### Post by cogadh on 2011-01-16
It looks like you are trying to run the game off of a CD/DVD and not from its install location in the .wine directory. Is there a particular reason you are doing this?

---

### Post by facedown on 2011-01-16
> **cogadh said:**
> It looks like you are trying to run the game off of a CD/DVD and not from its install location in the .wine directory. Is there a particular reason you are doing this?

Huh? It's not a cd/dvd. It's on a separate Windows partition.

---

### Post by cogadh on 2011-01-16
Well, that might explain it (the "/media" directory threw me). Normally you need to install the game within Wine, its not really designed to work with an existing Windows installation.

---

### Post by facedown on 2011-01-16
> **cogadh said:**
> Well, that might explain it (the "/media" directory threw me). Normally you need to install the game within Wine, its not really designed to work with an existing Windows installation.

My Diablo 2 runs perfectly in the same manner.

---

### Post by cogadh on 2011-01-16
Some things will, most things won't. Unfortunately, far too many applications rely on Windows registry entries in order to run properly. If an application is not installed within Wine, there are no related registry entries for it to access when it needs to and Wine cannot access the real Windows registry (allowing it to would horrendously break your Windows installation). The "best practice" for using Wine is to install applications within Wine, just as you would within Windows.

---

