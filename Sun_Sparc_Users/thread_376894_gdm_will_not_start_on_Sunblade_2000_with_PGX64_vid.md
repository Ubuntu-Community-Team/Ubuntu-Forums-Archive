---
title: "gdm will not start on Sunblade 2000 with PGX64 video card - &quot;No Screens Found&quot;"
date: 2007-03-05
forum: Sun Sparc Users
---

### Post by allen248 on 2007-03-05
Hi.  I installed ubuntu on my laptop, and I liked it so much that I decided to replace Solaris.  I have a Sunblade 2000 box in my lab with a Sun Rage XL (ATI) PGX64 video card.  But, no matter how I try to configure it, I am not able to start X-windows using GDM.

When I try to start GDM, I get the following error:

```
Fatal Server Error:
   No Screens Found

```

I've tried several different configurations in the xorg.conf file, but all of them seem to return the same error.  For example, I've tried the vesa and vga drivers without any luck.  I've tried minimal resultion on the monitor, and minimal color.  I've tried different monitors.

Here is the pertinent data from my /etc/X11/xorg.conf file:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage XL"
        Driver          "ati"
        BusID           "PCI:0:1:0"
        Option          "UseFBDev"              "true"
        Option          "ReferenceClock"        "29.500MHz"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage XL"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

Here is selected error data from the error log at /var/log/Xorg.0.log after GDM fails to start:

```
...
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 108e,8001 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:04:0: chip 1077,2200 card 0000,0000 rev 05 class 01,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  1       0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  1       0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  1       0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Addressable bus resource ranges are
        [0] -1  1       0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  1       0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Addressable bus resource ranges are
        [0] -1  1       0x00000000 - 0x7fffffff (0x80000000) MX[B]
        [1] -1  1       0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  1       0x7fffffff - 0x7fffffff (0x1) MX[B]
        [1] -1  1       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  1       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  1       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  1       0x00ffffff - 0x00ffffff (0x1) IX[B]
        [5] -1  1       0x00000000 - 0x00000000 (0x1) IX[B]
(II) Active PCI resource ranges:
        [0] -1  1       0x00100000 - 0x00100fff (0x1000) MX[B]
        [1] -1  1       0xed000300 - 0xed0003ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  1       0x00100000 - 0x00100fff (0x1000) MX[B]
        [1] -1  1       0xed000300 - 0xed0003ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  1       0x7fffffff - 0x7fffffff (0x1) MX[B]
        [1] -1  1       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  1       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  1       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  1       0x00ffffff - 0x00ffffff (0x1) IX[B]
        [5] -1  1       0x00000000 - 0x00000000 (0x1) IX[B]
(II) All system resource ranges:
        [0] -1  1       0x7fffffff - 0x7fffffff (0x1) MX[B]
        [1] -1  1       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  1       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  1       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  1       0x00100000 - 0x00100fff (0x1000) MX[B]
        [5] -1  1       0x00ffffff - 0x00ffffff (0x1) IX[B]
        [6] -1  1       0x00000000 - 0x00000000 (0x1) IX[B]
        [7] -1  1       0xed000300 - 0xed0003ff (0x100) IX[B]
(II) LoadModule: "i2c"
    ....
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 6.5.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
...
(II) ATI: ATI driver (version 6.5.8) for chipset: ati
(II) R128: Driver for ATI Rage 128 chipsets:
        ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
        ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
        ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
...
        ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
        ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
        ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
        ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
...
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Rage XL".
(EE) No devices detected.

Fatal server error:
no screens found

```

This is the output of lspci:

```
0000:00:00.0 Host bridge: Sun Microsystems Computer Corp. Schizo PCI Bus Module
0000:00:04.0 SCSI storage controller: QLogic Corp. QLA2200 64-bit Fibre Channel Adapter (rev 05)
0001:00:00.0 Host bridge: Sun Microsystems Computer Corp. Schizo PCI Bus Module
0001:00:01.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
0001:00:02.0 Multimedia controller: I.I.T.: Unknown device 0003 (rev 01)
0001:00:05.0 Bridge: Sun Microsystems Computer Corp. RIO EBUS (rev 01)
0001:00:05.1 Ethernet controller: Sun Microsystems Computer Corp. RIO GEM (rev 01)
0001:00:05.2 FireWire (IEEE 1394): Sun Microsystems Computer Corp. RIO 1394 (rev 01)
0001:00:05.3 USB Controller: Sun Microsystems Computer Corp. RIO USB (rev 01)
0001:00:06.0 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 37)
0001:00:06.1 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 37)

```

This is the output of lspci -X

```
PCI:0:0:0 Host bridge: Sun Microsystems Computer Corp. Schizo PCI Bus Module
PCI:0:4:0 SCSI storage controller: QLogic Corp. QLA2200 64-bit Fibre Channel Adapter
PCI:0:0:0 Host bridge: Sun Microsystems Computer Corp. Schizo PCI Bus Module
PCI:0:1:0 VGA compatible controller: ATI Technologies Inc Rage XL
PCI:0:2:0 Multimedia controller: I.I.T.: Unknown device 0003
PCI:0:5:0 Bridge: Sun Microsystems Computer Corp. RIO EBUS
PCI:0:5:1 Ethernet controller: Sun Microsystems Computer Corp. RIO GEM
PCI:0:5:2 FireWire (IEEE 1394): Sun Microsystems Computer Corp. RIO 1394
PCI:0:5:3 USB Controller: Sun Microsystems Computer Corp. RIO USB
PCI:0:6:0 SCSI storage controller: LSI Logic / Symbios Logic 53c875
PCI:0:6:1 SCSI storage controller: LSI Logic / Symbios Logic 53c875

```

Now this is one odd thing.  The video card is actually plugged into what is prominately labeled as PCI Slot 4 on my sunblade.  Can this make sense when my BusID is autodetected as PCI:0:1:0?  

I wonder if I don't have the right video driver available?  But, I see other posts where people have gotten the PGX64 to work by simply updating the ReferenceClock option in the Devices section of xorg.conf.  That didn't work for me.

Also, the ubuntu splash screen does display OK on startup.

Does anybody have any ideas of what I can try next to get GDM running?

Thanks.

---

### Post by allen248 on 2007-03-05
I think I might be near to the solution...

I believe the problem is with the PCI BusID

When the video card is in slot PCI 4, the bus id from lspci is 
0001:00:01.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

Technically, I think this is PCI:1:0:1:0 (which isn't allowed), and it is not PCI:0:1:0.

When I move the video card to slot labled PCI 1 66, the lspci bus id becomes
0000:00:01.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

Now this is truely PCI:0:1:0, and when I boot, I don't get an error that X could not start due to "No Screens Found", rather I get hung up on a bad X display output.

So, now I'm doing a clean re-install with the card in the PCI 1 66 slot on the SB2000.  I'll keep you posted.

---

### Post by allen248 on 2007-03-06
That did it.  If anybody has a similar problem with a SB2000, try moving the ATI video card to the very bottom PCI slot.  

The xorg.conf file shown above works now.

In a nutshell, steps to install Dapper on SB2000:

1) Burn the ISO for the sparc server CD

2) Put the video card in the very bottom PCI slot.

3) Power off the sunblade completely.  Power on the sunblade and hit stop-a as the box boots up to get the open boot 'ok' prompt before anything starts to load.

4) Type 'boot cdrom' at the 'ok' prompt

5) Install the base system, then restart and log-in

6) To install the gui, 'sudo apt-get install ubuntu-desktop'
       -pick 'ati' video when asked

7) After the ubuntu-desktop install completes, edit the configuration
      -'sudo dpkg-reconfigure xserver-xorg'
           -pick ati, go with defaults
     -'sudo nano /etc/X11/xorg.conf'
            -go to the 'Device' section and add ' option "ReferenceClock" "29.500MHz" '

8)  sudo reboot

Thats it :)

I've never used linux before because it is too too much work to administrer, but I think ubuntu is a great distro.  Thanks  all for a great product!

---

### Post by arover on 2008-07-02
Thank you a lot for your posts allen. Thanks to you my Sunblade1000 Finally works!!!!!!

---

