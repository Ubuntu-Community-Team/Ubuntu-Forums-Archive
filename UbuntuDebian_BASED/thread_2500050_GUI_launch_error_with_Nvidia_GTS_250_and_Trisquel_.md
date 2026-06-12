---
title: "GUI launch error with Nvidia GTS 250 and Trisquel 11 (based on Ubuntu 22.04)"
date: 2024-08-20
forum: Ubuntu/Debian BASED
---

### Post by trisquel11-gts250 on 2024-08-20
Hi.

```
$ LANG=en lscpu | grep 'Model name'
Model name:                           AMD Athlon(tm) II X2 250 Processor
$ lspci | grep "VGA" 
02:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2)
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Trisquel
Description:    Trisquel GNU/Linux Aramo (11.0.1)
Release:    11.0.1
Codename:    aramo
```

My computer is an "old" one: its processor is an AMD Athlon II X2 250 and its graphic card is an Nvidia GTS 250 (with the screen connected through VGA). I don't use Ubuntu (as [it is not fully free/libre, see FSF about this]("https://www.gnu.org/distros/common-distros.html#Ubuntu")) but Trisquel GNU/Linux, however Trisquel is based on Ubuntu LTS and in my case (Trisquel 11) on Ubuntu 22.04, so that is why it seems legit to post here, as Trisquel is about freedom and not changes in drivers (contrary to SteamOS for example).

My problem is very simple: it starts without problem, but it never managed to load the graphic card driver. In consequence, I just have "_" on top of the screen after it loaded the rest. I can switch to an other tty (with Ctrl + Alt + Fnumber), login with text (instead of lightdm), but startx fails.

```
$ cat ~/.local/share/xorg/Xorg.0.log
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[    91.367] Current Operating System: Linux gros-pc-libre 5.15.0-118-generic #128+11.0trisquel30 SMP Thu Aug 8 14:47:40 UTC 2024 x86_64
[    91.367] Kernel command line: BOOT_IMAGE=/vmlinuz-5.15.0-118-generic root=/dev/mapper/vgtrisquel-root ro nomodeset
[    91.373] xorg-server 2:21.1.4-2ubuntu1.7~22.04.11 (For technical support please see http://www.ubuntu.com/support) 
[    91.375] Current version of pixman: 0.40.0
[    91.378]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    91.378] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    91.387] (==) Log file: "/home/libruser/.local/share/xorg/Xorg.0.log", Time: Tue Aug 20 17:09:39 2024
[    91.389] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    91.391] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    91.391] (==) No Layout section.  Using the first Screen section.
[    91.391] (==) No screen section available. Using defaults.
[    91.391] (**) |-->Screen "Default Screen Section" (0)
[    91.391] (**) |   |-->Monitor "<default monitor>"
[    91.391] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    91.391] (==) Automatically adding devices
[    91.391] (==) Automatically enabling devices
[    91.391] (==) Automatically adding GPU devices
[    91.391] (==) Automatically binding GPU devices
[    91.391] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    91.391] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    91.391]     Entry deleted from font path.
[    91.391] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    91.391]     Entry deleted from font path.
[    91.391] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    91.391]     Entry deleted from font path.
[    91.392] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    91.392]     Entry deleted from font path.
[    91.392] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    91.392]     Entry deleted from font path.
[    91.392] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    91.392] (==) ModulePath set to "/usr/lib/xorg/modules"
[    91.392] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    91.392] (II) Loader magic: 0x55db54945020
[    91.392] (II) Module ABI versions:
[    91.392]     X.Org ANSI C Emulation: 0.4
[    91.392]     X.Org Video Driver: 25.2
[    91.392]     X.Org XInput driver : 24.4
[    91.392]     X.Org Server Extension : 10.0
[    91.393] (++) using VT number 6

[    91.401] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[    91.411] (--) PCI:*(2@0:0:0) 10de:0615:1458:34cb rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    91.411] (II) LoadModule: "glx"
[    91.411] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    91.414] (II) Module glx: vendor="X.Org Foundation"
[    91.414]     compiled for 1.21.1.4, module version = 1.0.0
[    91.414]     ABI class: X.Org Server Extension, version 10.0
[    91.626] (==) Matched nouveau as autoconfigured driver 0
[    91.626] (==) Matched modesetting as autoconfigured driver 1
[    91.626] (==) Matched fbdev as autoconfigured driver 2
[    91.626] (==) Matched vesa as autoconfigured driver 3
[    91.626] (==) Assigned the driver to the xf86ConfigLayout
[    91.626] (II) LoadModule: "nouveau"
[    91.626] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    91.627] (II) Module nouveau: vendor="X.Org Foundation"
[    91.627]     compiled for 1.21.1.3, module version = 1.0.17
[    91.627]     Module class: X.Org Video Driver
[    91.627]     ABI class: X.Org Video Driver, version 25.2
[    91.627] (II) LoadModule: "modesetting"
[    91.627] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    91.628] (II) Module modesetting: vendor="X.Org Foundation"
[    91.628]     compiled for 1.21.1.4, module version = 1.21.1
[    91.628]     Module class: X.Org Video Driver
[    91.628]     ABI class: X.Org Video Driver, version 25.2
[    91.628] (II) LoadModule: "fbdev"
[    91.628] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    91.628] (II) Module fbdev: vendor="X.Org Foundation"
[    91.628]     compiled for 1.21.1.3, module version = 0.5.0
[    91.628]     Module class: X.Org Video Driver
[    91.628]     ABI class: X.Org Video Driver, version 25.2
[    91.628] (II) LoadModule: "vesa"
[    91.629] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    91.629] (II) Module vesa: vendor="X.Org Foundation"
[    91.629]     compiled for 1.21.1.3, module version = 2.5.0
[    91.629]     Module class: X.Org Video Driver
[    91.629]     ABI class: X.Org Video Driver, version 25.2
[    91.629] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[    91.629] (II) NOUVEAU driver for NVIDIA chipset families :
[    91.629]     RIVA TNT            (NV04)
[    91.629]     RIVA TNT2           (NV05)
[    91.629]     GeForce 256         (NV10)
[    91.629]     GeForce 2           (NV11, NV15)
[    91.629]     GeForce 4MX         (NV17, NV18)
[    91.629]     GeForce 3           (NV20)
[    91.630]     GeForce 4Ti         (NV25, NV28)
[    91.630]     GeForce FX          (NV3x)
[    91.630]     GeForce 6           (NV4x)
[    91.630]     GeForce 7           (G7x)
[    91.630]     GeForce 8           (G8x)
[    91.630]     GeForce 9           (G9x)
[    91.630]     GeForce GTX 2xx/3xx (GT2xx)
[    91.630]     GeForce GTX 4xx/5xx (GFxxx)
[    91.630]     GeForce GTX 6xx/7xx (GKxxx)
[    91.630]     GeForce GTX 9xx     (GMxxx)
[    91.630]     GeForce GTX 10xx    (GPxxx)
[    91.630] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    91.630] (II) FBDEV: driver for framebuffer: fbdev
[    91.631] (II) VESA: driver for VESA chipsets: vesa
[    91.631] xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)
[    91.842] (EE) [drm] Failed to open DRM device for pci:0000:02:00.0: -19
[    91.842] (EE) open /dev/dri/card0: No such file or directory
[    91.842] (WW) Falling back to old probe method for modesetting
[    91.842] (EE) open /dev/dri/card0: No such file or directory
[    91.842] (II) Loading sub module "fbdevhw"
[    91.842] (II) LoadModule: "fbdevhw"
[    91.843] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    91.843] (II) Module fbdevhw: vendor="X.Org Foundation"
[    91.843]     compiled for 1.21.1.4, module version = 0.0.2
[    91.843]     ABI class: X.Org Video Driver, version 25.2
[    91.843] (EE) Unable to find a valid framebuffer device
[    91.843] (WW) Falling back to old probe method for fbdev
[    91.843] (II) Loading sub module "fbdevhw"
[    91.843] (II) LoadModule: "fbdevhw"
[    91.843] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    91.843] (II) Module fbdevhw: vendor="X.Org Foundation"
[    91.843]     compiled for 1.21.1.4, module version = 0.0.2
[    91.843]     ABI class: X.Org Video Driver, version 25.2
[    91.844] (EE) open /dev/fb0: Permission denied
[    91.844] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    91.844] (EE) Screen 0 deleted because of no matching config section.
[    91.844] (II) UnloadModule: "modesetting"
[    91.844] (EE) Screen 0 deleted because of no matching config section.
[    91.844] (II) UnloadModule: "fbdev"
[    91.844] (II) UnloadSubModule: "fbdevhw"
[    91.844] (II) Loading sub module "vbe"
[    91.844] (II) LoadModule: "vbe"
[    91.844] (II) Loading /usr/lib/xorg/modules/libint10.so
[    91.862] (II) Module int10: vendor="X.Org Foundation"
[    91.862]     compiled for 1.21.1.4, module version = 1.0.0
[    91.862]     ABI class: X.Org Video Driver, version 25.2
[    91.862] (II) Loading sub module "int10"
[    91.862] (II) LoadModule: "int10"
[    91.863] (II) Loading /usr/lib/xorg/modules/libint10.so
[    91.863] (II) Module int10: vendor="X.Org Foundation"
[    91.863]     compiled for 1.21.1.4, module version = 1.0.0
[    91.863]     ABI class: X.Org Video Driver, version 25.2
[    91.863] (II) VESA(0): initializing int10
[    91.864] (EE) VESA(0): Cannot read int vect
[    91.864] (II) UnloadModule: "vesa"
[    91.864] (II) UnloadSubModule: "int10"
[    91.864] (II) Unloading int10
[    91.864] (II) UnloadSubModule: "int10"
[    91.864] (II) Unloading int10
[    91.864] (EE) Screen(s) found, but none have a usable configuration.
[    91.864] (EE) 
Fatal server error:
[    91.864] (EE) no screens found(EE) 
[    91.864] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    91.864] (EE) Please also check the log file at "/home/libruser/.local/share/xorg/Xorg.0.log" for additional information.
[    91.865] (EE) 
[    91.872] (EE) Server terminated with error (1). Closing log file.
```

Due to this, to use the computer with a GUI, I boot in recovery mode through GRUB. The screen, that is connected in VGA to the graphic card, is recognized! However, the maximum resolution available is 1024x768 instead of 1920x1080. Moreover, the power of my graphic card is not used, as the graphic driver is Mesa's LLVMpipe (that uses the processor).

```
$ xrandr 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       0.00* 
   800x600        0.00  
   640x480        0.00
$ glxinfo | grep Device
    Device: llvmpipe (LLVM 15.0.7, 128 bits) (0xffffffff)
$ LANG=en sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fb000000-fbffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ec00(size=128) memory:c0000-dffff
```

With Trisquel 9 (based on Ubuntu 18.04) or Trisquel 10 (Ubuntu 20.04), it worked with Mesa-Nouveau. However, a newer Linux kernel caused the problem, so I stuck on an old Linux kernel. It is a computer that I used in holidays, in 2 different weeks of the year, so the problem was not big and I was lazy to try to find a fix. In consequence, I used the old Linux kernel, but with time it was really old, so I tried to fix the problem with a fresh install of Debian stable (it was Debian 11 "Bullseye", not Debian 12 "Bookworm") and Trisquel (based on Ubuntu LTS), but the problem was still there and I don't have the old kernel working with Mesa-Nouveau anymore.

According to [Mesa about the Amber branch]("https://docs.mesa3d.org/amber.html"), the support was dropped for "the DRI driver for NV04-NV20" in Mesa 22 (and Trisquel 11 provides Mesa 23.2.1). However, according to the X's log, my Nvidia GTS 250 is not part of that. But I installed libglx-amber0 and libegl-amber0, as I may be wrong, but the same problem occurs.

As a last try to fix, I created file "/etc/modprobe.d/nvidia.conf" with the content "options nvidia_drm modeset=1". But again it does not fix the problem.

How can I fix Mesa-Nouveau for my Nvidia GTS 250 on Trisquel 11 based on Ubuntu 22.04? If needed, I am a software enginner, so I guess that I should be able to compile Mesa-Nouveau from source.

Thank you for your help.

---

### Post by deadflowr on 2024-08-20
*Thread moved to **Ubuntu/Debian BASED***

---

