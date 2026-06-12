---
title: "Will a 2009 Sys76 Wild Dog boot to UEFI?"
date: 2020-05-23
forum: System76 Support
---

### Post by watchpocket on 2020-05-23
I have a System76 Wild Dog Performance desktop unit, version ***wilp6***, from late 2009.  I've always booted it using BIOS.  

I recently discovered in its BIOS boot menu a ***"UEFI boot: Enable/Disable"*** option, so I enabled it.  I still boot my Ubuntu-MATE 18.04 OS in BIOS mode, but I'm planning on converting the 18.04 install to boot to UEFI, and then installing -- on a separate SSD -- MATE 20.04, so that both installs will be in ***UEFI-GPT ***mode.

However, I came across this line in the Wikipedia entry on UEFI:

*"In 2008, more x86-64 systems adopted UEFI. . . .  While many of these systems still allow **booting only the  BIOS-based OSes** via the Compatibility Support Module (CSM) (thus not  appearing to the user to be UEFI-based), other systems started to allow  booting UEFI-based OSes."*   [https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

[Bold emphasis added by me.]

In the entry's next sentence, it listed some of the manufacturers that ***were*** beginning to allow booting UEFI-based systems at that time, but Intel was not one of them. I am guessing that, since there ***is*** a *"UEFI boot: Enable/Disable"* option under the "Boot" tab of my BIOS menus, that I should indeed be able to boot my OSes to UEFI, but I'd like, if it's at all possible, to be sure of that.

So my question to Sys76 support folk is this:  If I get all set up with my OSes to boot to UEFI, and create EFI partitions and so on, [I][B]am I going to be hamstrung with hardware/firmware that just won't do that?

[/B][/I]Here's some info about my system from inxi:
```
[COLOR=#0000ff]System:[/COLOR]    Kernel: 5.3.0-51-generic x86_64 [COLOR=#0000ff]bits:[/COLOR] 64 [COLOR=#0000ff]compiler:[/COLOR] gcc v: 7.5.0 [COLOR=#0000ff]Desktop:[/COLOR] MATE 1.20.1 
           [COLOR=#0000ff]Distro:[/COLOR] Ubuntu 18.04.4 LTS (Bionic Beaver)
 
[COLOR=#0000ff]Machine:[/COLOR]   [COLOR=#0000ff]Type: [/COLOR]Desktop System: System76 [COLOR=#0000ff]product:[/COLOR] Wild Dog Performance[COLOR=#0000ff] v: [/COLOR]wilp6 [COLOR=#0000ff]serial:[/COLOR] <filter> 
           [COLOR=#0000ff]Mobo: [/COLOR]Intel [COLOR=#0000ff]model:[/COLOR] DP45SG v: AAE27733-405 [COLOR=#0000ff]serial: [/COLOR]<filter>[COLOR=#0000ff] BIOS:[/COLOR] Intel v: SGP4510H.86A.0108.2009.0114.2036 
          [COLOR=#0000ff] date:[/COLOR] 01/14/2009 

[COLOR=#0000ff]CPU:       Topology: [/COLOR]Quad Core [COLOR=#0000ff]model:[/COLOR] Intel Core2 Quad Q9650 [COLOR=#0000ff]bits:[/COLOR] 64 [COLOR=#0000ff]type:[/COLOR] MCP [COLOR=#0000ff]arch:[/COLOR] Penryn [COLOR=#0000ff]rev: [/COLOR]A L2 cache: 6144 KiB 
           [COLOR=#0000ff]flags:[/COLOR] lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx [COLOR=#0000ff]bogomips:[/COLOR] 23999 
           [COLOR=#0000ff]Speed:[/COLOR] 2000 MHz [COLOR=#0000ff]min/max: [/COLOR]1998/2997 MHz [COLOR=#0000ff]Core speeds (MHz): 1: [/COLOR]2000 [COLOR=#0000ff]2:[/COLOR] 2000[COLOR=#0000ff] 3:[/COLOR] 2000 [COLOR=#0000ff]4:[/COLOR] 2000
 
[COLOR=#0000ff]Graphics:  Device-1: [/COLOR]NVIDIA GF106 [GeForce GTS 450] [COLOR=#0000ff]driver: [/COLOR]nvidia[COLOR=#0000ff] v: [/COLOR]390.132 [COLOR=#0000ff]bus ID:[/COLOR] 01:00.0 
          [COLOR=#0000ff] Display: [/COLOR]x11 [COLOR=#0000ff]server: [/COLOR]X.Org 1.20.5 [COLOR=#0000ff]driver: [/COLOR]nvidia [COLOR=#0000ff]unloaded:[/COLOR] fbdev,modesetting,nouveau,vesa 
           [COLOR=#0000ff]resolution: 1:[/COLOR] 2560x1600~60Hz [COLOR=#0000ff]2: [/COLOR]2560x1600~60Hz
```

---

### Post by watchpocket on 2020-05-26
The only way to really answer this question is to try it, so I did.  And it worked.  I installed a new 18.04 Ubuntu-MATE on a USB-connected removable SSD drive, and got it to successfully install in UEFI-GPT mode.  Now to find out if my motheboard will boot from an NVMe SSD.

---

