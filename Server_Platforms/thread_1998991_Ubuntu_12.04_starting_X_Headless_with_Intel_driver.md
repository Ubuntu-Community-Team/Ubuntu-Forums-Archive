---
title: "Ubuntu 12.04 starting X Headless with Intel driver"
date: 2012-06-07
forum: Server Platforms
---

### Post by Tlvenn on 2012-06-07
Hi,

I am trying to start a X server headless using the intel driver ( the server has an HD2000 intel igpu).

I need this in order to render some opengl jobs that are saved as images.

My xorg.conf:
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Default Screen"
        Option "AllowEmptyInput" "true"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "glx"
        Load  "dri2"
        Load  "extmod"
        Load  "dri"
        Load  "dbe"
        Load  "record"
EndSection

Section "Monitor"
        Identifier   "Headless"
        Option "IgnoreEDID"
        HorizSync       30.0 - 72.0
        VertRefresh     50.0 - 160.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                       # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "VideoKey"                  # <i>
        #Option     "FallbackDebug"             # [<bool>]
        #Option     "Tiling"                    # [<bool>]
        #Option     "LinearFramebuffer"         # [<bool>]
        #Option     "Shadow"                    # [<bool>]
        #Option     "SwapbuffersWait"           # [<bool>]
        #Option     "TripleBuffer"              # [<bool>]
        #Option     "XvMC"                      # [<bool>]
        #Option     "XvPreferOverlay"           # [<bool>]
        #Option     "DebugFlushBatches"         # [<bool>]
        #Option     "DebugFlushCaches"          # [<bool>]
        #Option     "DebugWait"                 # [<bool>]
        #Option     "HotPlug"                   # [<bool>]
        #Option     "RelaxedFencing"            # [<bool>]
        #Option     "BufferCache"               # [<bool>]

        Option      "NoDDC"    "true"
        Identifier  "IGPU"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
 Identifier "Default Screen"
        Device     "IGPU"
        Monitor    "Headless"
        Option "UseEDID" "FALSE"
        DefaultDepth  24
        SubSection "Display"
                Depth     24
                Modes   "800x600@60"
        EndSubSection
EndSection


```

My log:

```

X.Org X Server 1.11.3
Release Date: 2011-12-16
[341984.506] X Protocol Version 11, Revision 0
[341984.506] Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
[341984.506] Current Operating System: Linux dev.magelo.com 3.2.13-grsec-xxxx-grs-ipv6-64 #1 SMP Thu Mar 29 09:48:59 UTC 2012 x86_64
[341984.506] Kernel command line: BOOT_IMAGE=/boot/bzImage-3.2.13-xxxx-grs-ipv6-64 root=/dev/md1 ro text nomodeset
[341984.506] Build Date: 07 May 2012  11:43:21PM
[341984.506] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support)
[341984.506] Current version of pixman: 0.24.4
[341984.506]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[341984.506] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[341984.507] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  7 19:11:18 2012
[341984.507] (++) Using config file: "./xorg.conf"
[341984.507] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[341984.507] (==) ServerLayout "X.org Configured"
[341984.507] (**) |-->Screen "Default Screen" (0)
[341984.507] (**) |   |-->Monitor "Headless"
[341984.507] (**) |   |-->Device "IGPU"
[341984.507] (==) Automatically adding devices
[341984.507] (==) Automatically enabling devices
[341984.507] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[341984.507]    Entry deleted from font path.
[341984.507] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[341984.507]    Entry deleted from font path.
[341984.507] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[341984.507]    Entry deleted from font path.
[341984.508] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[341984.508]    Entry deleted from font path.
[341984.508] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[341984.508]    Entry deleted from font path.
[341984.508] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[341984.508]    Entry deleted from font path.
[341984.508] (**) FontPath set to:
        built-ins,
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[341984.508] (**) ModulePath set to "/usr/lib/xorg/modules"
[341984.508] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[341984.508] (II) Loader magic: 0x7f0598fbcb00
[341984.508] (II) Module ABI versions:
[341984.508]    X.Org ANSI C Emulation: 0.4
[341984.508]    X.Org Video Driver: 11.0
[341984.508]    X.Org XInput driver : 16.0
[341984.508]    X.Org Server Extension : 6.0
[341984.508] (--) PCI:*(0:0:2:0) 8086:0102:8086:2002 rev 9, Mem @ 0xfe000000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[341984.508] (II) Open ACPI successful (/var/run/acpid.socket)
[341984.508] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[341984.508] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[341984.508] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[341984.508] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[341984.508] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[341984.508] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[341984.508] (II) LoadModule: "glx"
[341984.509] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[341984.509] (II) Module glx: vendor="X.Org Foundation"
[341984.509]    compiled for 1.11.3, module version = 1.0.0
[341984.509]    ABI class: X.Org Server Extension, version 6.0
[341984.509] (==) AIGLX enabled
[341984.509] (II) Loading extension GLX
[341984.509] (II) LoadModule: "dri2"
[341984.509] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[341984.509] (II) Module dri2: vendor="X.Org Foundation"
[341984.509]    compiled for 1.11.3, module version = 1.2.0
[341984.509]    ABI class: X.Org Server Extension, version 6.0
[341984.509] (II) Loading extension DRI2
[341984.509] (II) LoadModule: "extmod"
[341984.509] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[341984.509] (II) Module extmod: vendor="X.Org Foundation"
[341984.509]    compiled for 1.11.3, module version = 1.0.0
[341984.509]    Module class: X.Org Server Extension
[341984.509]    ABI class: X.Org Server Extension, version 6.0
[341984.509] (II) Loading extension MIT-SCREEN-SAVER
[341984.509] (II) Loading extension XFree86-VidModeExtension
[341984.509] (II) Loading extension XFree86-DGA
[341984.509] (II) Loading extension DPMS
[341984.509] (II) Loading extension XVideo
[341984.509] (II) Loading extension XVideo-MotionCompensation
[341984.509] (II) Loading extension X-Resource
[341984.509] (II) LoadModule: "dri"
[341984.510] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[341984.510] (II) Module dri: vendor="X.Org Foundation"
[341984.510]    compiled for 1.11.3, module version = 1.0.0
[341984.510]    ABI class: X.Org Server Extension, version 6.0
[341984.510] (II) Loading extension XFree86-DRI
[341984.510] (II) LoadModule: "dbe"
[341984.510] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[341984.510] (II) Module dbe: vendor="X.Org Foundation"
[341984.510]    compiled for 1.11.3, module version = 1.0.0
[341984.510]    Module class: X.Org Server Extension
[341984.510]    ABI class: X.Org Server Extension, version 6.0
[341984.510] (II) Loading extension DOUBLE-BUFFER
[341984.510] (II) LoadModule: "record"
[341984.510] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[341984.510] (II) Module record: vendor="X.Org Foundation"
[341984.510]    compiled for 1.11.3, module version = 1.13.0
[341984.510]    Module class: X.Org Server Extension
[341984.510]    ABI class: X.Org Server Extension, version 6.0
[341984.510] (II) Loading extension RECORD
[341984.510] (II) LoadModule: "intel"
[341984.510] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[341984.510] (II) Module intel: vendor="X.Org Foundation"
[341984.511]    compiled for 1.11.3, module version = 2.19.0
[341984.511]    Module class: X.Org Video Driver
[341984.511]    ABI class: X.Org Video Driver, version 11.0
[341984.511] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
        Ivybridge Server (GT2)
[341984.511] (--) using VT number 9

[341984.513] (EE) No devices detected.
[341984.513] (==) Matched intel as autoconfigured driver 0
[341984.513] (==) Matched vesa as autoconfigured driver 1
[341984.513] (==) Matched fbdev as autoconfigured driver 2
[341984.513] (==) Assigned the driver to the xf86ConfigLayout
[341984.513] (II) LoadModule: "intel"
[341984.514] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[341984.514] (II) Module intel: vendor="X.Org Foundation"
[341984.514]    compiled for 1.11.3, module version = 2.19.0
[341984.514]    Module class: X.Org Video Driver
[341984.514]    ABI class: X.Org Video Driver, version 11.0
[341984.514] (II) UnloadModule: "intel"
[341984.514] (II) Unloading intel
[341984.514] (II) Failed to load module "intel" (already loaded, 32517)
[341984.514] (II) LoadModule: "vesa"
[341984.514] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[341984.514] (II) Module vesa: vendor="X.Org Foundation"
[341984.514]    compiled for 1.11.3, module version = 2.3.0
[341984.514]    Module class: X.Org Video Driver
[341984.514]    ABI class: X.Org Video Driver, version 11.0
[341984.514] (II) LoadModule: "fbdev"
[341984.514] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[341984.514] (II) Module fbdev: vendor="X.Org Foundation"
[341984.514]    compiled for 1.11.3, module version = 0.4.2
[341984.514]    ABI class: X.Org Video Driver, version 11.0
[341984.514] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
        Ivybridge Server (GT2)
[341984.515] (II) VESA: driver for VESA chipsets: vesa
[341984.515] (II) FBDEV: driver for framebuffer: fbdev
[341984.515] (++) using VT number 9

[341984.515] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[341984.515] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[341984.515] (WW) Falling back to old probe method for vesa
[341984.515] (WW) Falling back to old probe method for fbdev
[341984.515] (EE) No devices detected.
[341984.515]
Fatal server error:
[341984.515] no screens found
[341984.515]


```

Any hints on how I can get X running using the Intel driver without any monitor ?

Thanks in advance !

---

### Post by Tlvenn on 2012-06-09
I tried with the correct DDC option to false. With minimal xorg.conf as well with no luck....

The thing that bother me is the intel drivers seems to be loaded twice and I wonder if because of that, my options are not passed to it correctly. How can i tell X server to not try to load drivers automatically ?

Even with:
  Option "AutoAddDevices" "false"
  Option "AutoEnableDevices" "false"

The X server keep detecting the intel driver and loading it on its own.... Like the vesa driver for instance that I have now uninstalled:

[341984.513] (==) Matched intel as autoconfigured driver 0
[341984.513] (==) Matched vesa as autoconfigured driver 1
[341984.513] (==) Matched fbdev as autoconfigured driver 2

If anyone as an idea, please dont be shy, I am rather stuck and would welcome any help/idea at this point.
Thanks !

---

### Post by {CGL}ToWeR on 2012-07-15
I havent looked too closely but Ive managed to get my nvidia module loaded without a physical monitor using an EDID file.  See this thread

[http://ubuntuforums.org/showthread.php?t=1851330&page=2](http://ubuntuforums.org/showthread.php?t=1851330&page=2)

The magic two lines in /etc/X11/xorg.conf being something like the following:

     ```
Section "Device"
              ... 
              Option         "ConnectedMonitor" "DFP-1"
          Option         "CustomEDID" "DFP-1:/etc/X11/toshiba.edid"
    End Section
```

I still couldnt access DISPLAY 0 in my program but at least /var/log/Xorg0.log was happy, a screen was found and no EE's

HTH

---

