---
title: "Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600"
date: 2017-12-29
forum: Ubuntu/Debian BASED
---

### Post by pedro-fox on 2017-12-29
I know this thread is already been seen a million times, however I tried a LOT of different things that people recommend but it I can't upgrade 800x600 resolution. Basically, I installed BioLinux8 and the drivers for my NVIDIA. After a LOT of approaches and problems to install the drivers, dependencies and a new kernel, this is what I end up with:

```
$ nvidia-smi
      
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 387.34                 Driver Version: 387.34                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1050    Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   40C    P0    N/A /  N/A |      0MiB /  1999MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```


and

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1c8d (rev a1)
```


and 


```
$ xrandr

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600        75.0* 
```


Help is really appreciated, I wasn't posting it if I wasn't desperate at this point.:confused:

---

### Post by slickymaster on 2017-12-29
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Bashing-om on 2017-12-29
pedro-fox; Hello;

I have never seen BioLinux8 ; but using ubuntu 16.04 as my standard and the reference:
what shows:
```

lsmod | grep nvidia
lsmod | grep nouveau
dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```

See here what is installed to control the graph'c sets . Then see where we go from here .
find the fulcrum to lever  800 x 600 resolution .

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by pedro-fox on 2017-12-30
First, thank you for helping the newbie, with this. What show in my console:

```
$ lsmod | grep nvidia
nvidia_uvm            671744  0 
nvidia_drm             45056  0 
nvidia_modeset        897024  1 nvidia_drm
nvidia              13971456  2 nvidia_modeset,nvidia_uvm
drm_kms_helper        126976  2 i915,nvidia_drm
drm                   356352  4 i915,drm_kms_helper,nvidia_drm
```

```
$  lsmod | grep nouveau
(Nothing show in my console)
```

```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-387                                          387.34-0ubuntu0~gpu14.04.2                          amd64        NVIDIA CUDA runtime library
ii  nvidia-387                                            387.34-0ubuntu0~gpu14.04.2                          amd64        NVIDIA binary driver - version 387.34
ii  nvidia-opencl-icd-387                                 387.34-0ubuntu0~gpu14.04.2                          amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2.1                                             amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       387.22-0ubuntu0~gpu14.04.1                          amd64        Tool for configuring the NVIDIA graphics driver
```

```
$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.2.3-040203-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.2.3-040203-generic/updates/dkms
Found nvidia module: nvidia_387_modeset.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Detected LTS < 14.04.5. Forcing Intel/SNA
Vendor/Device Id: 8086:591b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-387/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-387/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Single card detected
No change - nothing to do
```

Sorry, I didn't get the fulcrum part.

---

### Post by Bashing-om on 2017-12-30
pedro-fox; Humm ..

that fulcrum line was but an attempt on my part to add some levity to the situation.

nvida is in a happy state, Intel - Uh Uh ( surprise - surprise) .
we have:
> 
Is intel loaded? no
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver

when we know that the Intel hardware does exist:
> 
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)


I do not know. but I must ask if the Intel graphic's set is turned off in bios ?

If still enabled in bios ->
Maybe here we consider re-installing the Intel Xorg stack ?
What kernel are we working with ?
Post back:
```

lsb_release -a
uname -a

```

Edit: 'Nother thought !
Do we have the graphic's config file ?
what shows :
```

ls -al /etc/X11/xorg.conf 

```

[INDENT][INDENT]the hunt is on
[/INDENT][/INDENT]

---

### Post by pedro-fox on 2017-12-31
This is what is shown in my console:

```
$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

$ uname -a
Linux xxxxx-pc 4.2.3-040203-generic #201510030832 SMP Sat Oct 3 12:34:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1387 Dez 29 14:55 /etc/X11/xorg.conf
```

I've already altered the xorg.conf, including "Modes" which messed up things, but I managed to recover the original file.



I'm still trying to see if Intel graphic's set is enabled on BIOS, I can't find where it is yet. And I saw in another thread the following code to re-install Xorg files, but ultimately did anything:

```
sudo apt-get install --reinstall xserver-xorg-video-intel xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Bashing-om on 2017-12-31
pedro-fox; Yukkie .

No errors at all when the X stack was re-installed ?


what is the deal with the " 4.2.3-040203-generic" kernel ?
trusty (14.04) is on:
> 
trusty-updates (kernel): Generic Linux kernel image 
3.13.0.137.146: amd64 arm64 armhf i386 ppc


What does X now have to say about things ?
post back:
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]no Intel, just not adding up -
[/INDENT][/INDENT]

---

### Post by pedro-fox on 2018-01-02
Yes, no errors at all in the X reinstall.

```
$ cat /var/log/Xorg.0.log
[     2.769] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     2.769] X Protocol Version 11, Revision 0
[     2.769] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[     2.769] Current Operating System: Linux pedro-pc 4.2.3-040203-generic #201510030832 SMP Sat Oct 3 12:34:31 UTC 2015 x86_64
[     2.769] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.3-040203-generic root=UUID=8d71db2a-bf32-444f-96d7-ddf20c2279c5 ro quiet splash vt.handoff=7
[     2.769] Build Date: 13 October 2017  01:59:06PM
[     2.769] xorg-server 2:1.15.1-0ubuntu2.11 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     2.769] Current version of pixman: 0.30.2
[     2.769]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     2.769] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.769] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  2 21:00:12 2018
[     2.770] (==) Using config file: "/etc/X11/xorg.conf"
[     2.770] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.776] (==) ServerLayout "Layout0"
[     2.776] (**) |-->Screen "Screen0" (0)
[     2.776] (**) |   |-->Monitor "Monitor0"
[     2.777] (**) |   |-->Device "Device0"
[     2.777] (**) |-->Input Device "Keyboard0"
[     2.777] (**) |-->Input Device "Mouse0"
[     2.777] (==) Automatically adding devices
[     2.777] (==) Automatically enabling devices
[     2.777] (==) Automatically adding GPU devices
[     2.779] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.779]     Entry deleted from font path.
[     2.779] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.779]     Entry deleted from font path.
[     2.779] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.779]     Entry deleted from font path.
[     2.780] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.780]     Entry deleted from font path.
[     2.780] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.780]     Entry deleted from font path.
[     2.780] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     2.780] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.780] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     2.780] (WW) Disabling Keyboard0
[     2.780] (WW) Disabling Mouse0
[     2.780] (II) Loader magic: 0x562fdfca4d40
[     2.780] (II) Module ABI versions:
[     2.780]     X.Org ANSI C Emulation: 0.4
[     2.780]     X.Org Video Driver: 15.0
[     2.780]     X.Org XInput driver : 20.0
[     2.780]     X.Org Server Extension : 8.0
[     2.780] (II) xfree86: Adding drm device (/dev/dri/card0)
[     2.782] (--) PCI:*(0:0:2:0) 8086:591b:103c:838f rev 4, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64
[     2.782] (--) PCI: (0:1:0:0) 10de:1c8d:103c:838f rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     2.791] Initializing built-in extension Generic Event Extension
[     2.791] Initializing built-in extension SHAPE
[     2.791] Initializing built-in extension MIT-SHM
[     2.791] Initializing built-in extension XInputExtension
[     2.791] Initializing built-in extension XTEST
[     2.791] Initializing built-in extension BIG-REQUESTS
[     2.791] Initializing built-in extension SYNC
[     2.791] Initializing built-in extension XKEYBOARD
[     2.791] Initializing built-in extension XC-MISC
[     2.791] Initializing built-in extension SECURITY
[     2.791] Initializing built-in extension XINERAMA
[     2.791] Initializing built-in extension XFIXES
[     2.791] Initializing built-in extension RENDER
[     2.791] Initializing built-in extension RANDR
[     2.791] Initializing built-in extension COMPOSITE
[     2.791] Initializing built-in extension DAMAGE
[     2.791] Initializing built-in extension MIT-SCREEN-SAVER
[     2.791] Initializing built-in extension DOUBLE-BUFFER
[     2.791] Initializing built-in extension RECORD
[     2.791] Initializing built-in extension DPMS
[     2.791] Initializing built-in extension Present
[     2.791] Initializing built-in extension DRI3
[     2.791] Initializing built-in extension X-Resource
[     2.791] Initializing built-in extension XVideo
[     2.791] Initializing built-in extension XVideo-MotionCompensation
[     2.791] Initializing built-in extension SELinux
[     2.791] Initializing built-in extension XFree86-VidModeExtension
[     2.791] Initializing built-in extension XFree86-DGA
[     2.791] Initializing built-in extension XFree86-DRI
[     2.791] Initializing built-in extension DRI2
[     2.791] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     2.791] (II) "glx" will be loaded by default.
[     2.791] (WW) "xmir" is not to be loaded by default. Skipping.
[     2.791] (II) LoadModule: "glx"
[     2.792] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     2.828] (II) Module glx: vendor="NVIDIA Corporation"
[     2.828]     compiled for 4.0.2, module version = 1.0.0
[     2.828]     Module class: X.Org Server Extension
[     2.828] (II) NVIDIA GLX Module  387.34  Tue Nov 21 02:04:31 PST 2017
[     2.829] Loading extension GLX
[     2.829] (II) LoadModule: "nvidia"
[     2.829] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     2.831] (II) Module nvidia: vendor="NVIDIA Corporation"
[     2.831]     compiled for 4.0.2, module version = 1.0.0
[     2.831]     Module class: X.Org Video Driver
[     2.831] (II) NVIDIA dlloader X Driver  387.34  Tue Nov 21 01:38:22 PST 2017
[     2.831] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     2.832] (++) using VT number 7

[     2.832] (EE) No devices detected.
[     2.832] (==) Matched nvidia as autoconfigured driver 0
[     2.832] (==) Matched nouveau as autoconfigured driver 1
[     2.832] (==) Matched intel as autoconfigured driver 2
[     2.832] (==) Matched modesetting as autoconfigured driver 3
[     2.832] (==) Matched fbdev as autoconfigured driver 4
[     2.832] (==) Matched vesa as autoconfigured driver 5
[     2.832] (==) Assigned the driver to the xf86ConfigLayout
[     2.832] (II) LoadModule: "nvidia"
[     2.832] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     2.833] (II) Module nvidia: vendor="NVIDIA Corporation"
[     2.833]     compiled for 4.0.2, module version = 1.0.0
[     2.833]     Module class: X.Org Video Driver
[     2.833] (II) UnloadModule: "nvidia"
[     2.833] (II) Unloading nvidia
[     2.833] (II) Failed to load module "nvidia" (already loaded, 22063)
[     2.833] (II) LoadModule: "nouveau"
[     2.834] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     2.835] (II) Module nouveau: vendor="X.Org Foundation"
[     2.835]     compiled for 1.15.0, module version = 1.0.10
[     2.835]     Module class: X.Org Video Driver
[     2.835]     ABI class: X.Org Video Driver, version 15.0
[     2.835] (II) LoadModule: "intel"
[     2.835] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     2.837] (II) Module intel: vendor="X.Org Foundation"
[     2.837]     compiled for 1.15.1, module version = 2.99.910
[     2.837]     Module class: X.Org Video Driver
[     2.837]     ABI class: X.Org Video Driver, version 15.0
[     2.837] (II) LoadModule: "modesetting"
[     2.837] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.837] (II) Module modesetting: vendor="X.Org Foundation"
[     2.837]     compiled for 1.15.0, module version = 0.8.1
[     2.837]     Module class: X.Org Video Driver
[     2.837]     ABI class: X.Org Video Driver, version 15.0
[     2.837] (II) LoadModule: "fbdev"
[     2.837] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.838] (II) Module fbdev: vendor="X.Org Foundation"
[     2.838]     compiled for 1.15.0, module version = 0.4.4
[     2.838]     Module class: X.Org Video Driver
[     2.838]     ABI class: X.Org Video Driver, version 15.0
[     2.838] (II) LoadModule: "vesa"
[     2.838] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.838] (II) Module vesa: vendor="X.Org Foundation"
[     2.838]     compiled for 1.15.0, module version = 2.3.3
[     2.838]     Module class: X.Org Video Driver
[     2.838]     ABI class: X.Org Video Driver, version 15.0
[     2.838] (II) NVIDIA dlloader X Driver  387.34  Tue Nov 21 01:38:22 PST 2017
[     2.838] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     2.838] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[     2.838] (II) NOUVEAU driver for NVIDIA chipset families :
[     2.838]     RIVA TNT        (NV04)
[     2.838]     RIVA TNT2       (NV05)
[     2.838]     GeForce 256     (NV10)
[     2.838]     GeForce 2       (NV11, NV15)
[     2.838]     GeForce 4MX     (NV17, NV18)
[     2.838]     GeForce 3       (NV20)
[     2.838]     GeForce 4Ti     (NV25, NV28)
[     2.838]     GeForce FX      (NV3x)
[     2.838]     GeForce 6       (NV4x)
[     2.838]     GeForce 7       (G7x)
[     2.838]     GeForce 8       (G8x)
[     2.838]     GeForce GTX 200 (NVA0)
[     2.838]     GeForce GTX 400 (NVC0)
[     2.838] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     2.839] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     2.839] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     2.839] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     2.839] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.839] (II) FBDEV: driver for framebuffer: fbdev
[     2.839] (II) VESA: driver for VESA chipsets: vesa
[     2.839] (++) using VT number 7

[     2.839] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     2.839] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[     2.839] (EE) [drm] KMS not enabled
[     2.839] (EE) [drm] KMS not enabled
[     2.855] (WW) Falling back to old probe method for modesetting
[     2.855] (II) Loading sub module "fbdevhw"
[     2.855] (II) LoadModule: "fbdevhw"
[     2.855] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.856] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.856]     compiled for 1.15.1, module version = 0.0.2
[     2.856]     ABI class: X.Org Video Driver, version 15.0
[     2.856] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[     2.856] (II) FBDEV(1): using default device
[     2.856] (WW) Falling back to old probe method for vesa
[     2.856] (EE) Screen 0 deleted because of no matching config section.
[     2.856] (II) UnloadModule: "modesetting"
[     2.856] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[     2.856] (==) FBDEV(0): RGB weight 888
[     2.856] (==) FBDEV(0): Default visual is TrueColor
[     2.856] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     2.856] (II) FBDEV(0): hardware: EFI VGA (video memory: 1920kB)
[     2.856] (II) FBDEV(0): checking modes against framebuffer device...
[     2.856] (II) FBDEV(0): checking modes against monitor...
[     2.856] (--) FBDEV(0): Virtual size is 800x600 (pitch 800)
[     2.856] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[     2.856] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[     2.856] (==) FBDEV(0): DPI set to (96, 96)
[     2.856] (II) Loading sub module "fb"
[     2.856] (II) LoadModule: "fb"
[     2.856] (II) Loading /usr/lib/xorg/modules/libfb.so
[     2.857] (II) Module fb: vendor="X.Org Foundation"
[     2.857]     compiled for 1.15.1, module version = 1.0.0
[     2.857]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.857] (**) FBDEV(0): using shadow framebuffer
[     2.857] (II) Loading sub module "shadow"
[     2.857] (II) LoadModule: "shadow"
[     2.857] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     2.858] (II) Module shadow: vendor="X.Org Foundation"
[     2.858]     compiled for 1.15.1, module version = 1.1.0
[     2.858]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.858] (II) UnloadModule: "nvidia"
[     2.858] (II) Unloading nvidia
[     2.858] (II) UnloadModule: "vesa"
[     2.858] (II) Unloading vesa
[     2.858] (==) Depth 24 pixmap format is 32 bpp
[     2.858] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     2.859] (==) FBDEV(0): Backing store enabled
[     2.859] (==) FBDEV(0): DPMS enabled
[     2.859] (==) RandR enabled
[     2.862] (II) SELinux: Disabled on system
[     2.863] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[     2.868] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     2.870] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     2.870] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     2.870] (II) LoadModule: "evdev"
[     2.870] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     2.871] (II) Module evdev: vendor="X.Org Foundation"
[     2.871]     compiled for 1.15.0, module version = 2.8.2
[     2.871]     Module class: X.Org XInput Driver
[     2.871]     ABI class: X.Org XInput driver, version 20.0
[     2.871] (II) Using input driver 'evdev' for 'Power Button'
[     2.871] (**) Power Button: always reports core events
[     2.871] (**) evdev: Power Button: Device: "/dev/input/event2"
[     2.871] (--) evdev: Power Button: Vendor 0 Product 0x1
[     2.871] (--) evdev: Power Button: Found keys
[     2.871] (II) evdev: Power Button: Configuring as keyboard
[     2.871] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     2.871] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     2.871] (**) Option "xkb_rules" "evdev"
[     2.871] (**) Option "xkb_model" "pc105"
[     2.871] (**) Option "xkb_layout" "pt"
[     2.872] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[     2.873] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     2.873] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     2.873] (II) Using input driver 'evdev' for 'Power Button'
[     2.873] (**) Power Button: always reports core events
[     2.873] (**) evdev: Power Button: Device: "/dev/input/event1"
[     2.873] (--) evdev: Power Button: Vendor 0 Product 0x1
[     2.873] (--) evdev: Power Button: Found keys
[     2.873] (II) evdev: Power Button: Configuring as keyboard
[     2.873] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     2.873] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     2.873] (**) Option "xkb_rules" "evdev"
[     2.873] (**) Option "xkb_model" "pc105"
[     2.873] (**) Option "xkb_layout" "pt"
[     2.873] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     2.873] (II) No input driver specified, ignoring this device.
[     2.873] (II) This device may have been added with another device file.
[     2.873] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     2.873] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     2.873] (II) config/udev: Adding input device HP Wide Vision HD Camera (/dev/input/event5)
[     2.873] (**) HP Wide Vision HD Camera: Applying InputClass "evdev keyboard catchall"
[     2.873] (II) Using input driver 'evdev' for 'HP Wide Vision HD Camera'
[     2.873] (**) HP Wide Vision HD Camera: always reports core events
[     2.873] (**) evdev: HP Wide Vision HD Camera: Device: "/dev/input/event5"
[     2.873] (--) evdev: HP Wide Vision HD Camera: Vendor 0x4f2 Product 0xb5d6
[     2.873] (--) evdev: HP Wide Vision HD Camera: Found keys
[     2.873] (II) evdev: HP Wide Vision HD Camera: Configuring as keyboard
[     2.873] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input7/event5"
[     2.873] (II) XINPUT: Adding extended input device "HP Wide Vision HD Camera" (type: KEYBOARD, id 8)
[     2.873] (**) Option "xkb_rules" "evdev"
[     2.873] (**) Option "xkb_model" "pc105"
[     2.873] (**) Option "xkb_layout" "pt"
[     2.873] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     2.873] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     2.873] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     2.873] (**) AT Translated Set 2 keyboard: always reports core events
[     2.873] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     2.873] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     2.873] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     2.873] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     2.873] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     2.873] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[     2.873] (**) Option "xkb_rules" "evdev"
[     2.873] (**) Option "xkb_model" "pc105"
[     2.873] (**) Option "xkb_layout" "pt"
[     2.874] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[     2.874] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     2.874] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     2.874] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     2.874] (II) LoadModule: "synaptics"
[     2.874] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     2.874] (II) Module synaptics: vendor="X.Org Foundation"
[     2.874]     compiled for 1.15.0, module version = 1.7.4
[     2.874]     Module class: X.Org XInput Driver
[     2.874]     ABI class: X.Org XInput driver, version 20.0
[     2.874] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     2.874] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     2.874] (**) Option "Device" "/dev/input/event7"
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1270 - 5670 (res 44)
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1240 - 4746 (res 66)
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     2.976] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     2.976] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     3.044] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event7"
[     3.044] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[     3.044] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     3.044] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     3.044] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[     3.044] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     3.044] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     3.044] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     3.044] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     3.044] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     3.044] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     3.044] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     3.045] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event4)
[     3.045] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[     3.045] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[     3.045] (**) HP Wireless hotkeys: always reports core events
[     3.045] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event4"
[     3.045] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[     3.045] (--) evdev: HP Wireless hotkeys: Found keys
[     3.045] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[     3.045] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event4"
[     3.045] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 11)
[     3.045] (**) Option "xkb_rules" "evdev"
[     3.045] (**) Option "xkb_model" "pc105"
[     3.045] (**) Option "xkb_layout" "pt"
[     3.045] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[     3.045] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     3.045] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[     3.045] (**) HP WMI hotkeys: always reports core events
[     3.045] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event6"
[     3.045] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[     3.045] (--) evdev: HP WMI hotkeys: Found keys
[     3.045] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[     3.045] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event6"
[     3.045] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[     3.045] (**) Option "xkb_rules" "evdev"
[     3.045] (**) Option "xkb_model" "pc105"
[     3.045] (**) Option "xkb_layout" "pt"
[     3.047] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    45.304] (II) XKB: reuse xkmfile /var/lib/xkb/server-7B695F22C90D43BDE9299180E8B8470DE5C26533.xkm
[    45.316] (II) XKB: reuse xkmfile /var/lib/xkb/server-4DF6D4ADA69D52A8CA764CDA17328DCBBF40F118.xkm
[    45.318] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.322] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.325] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.326] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.327] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.329] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.329] (II) XKB: reuse xkmfile /var/lib/xkb/server-4DF6D4ADA69D52A8CA764CDA17328DCBBF40F118.xkm
[    45.331] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.333] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.336] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.338] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.339] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.341] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.342] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    45.343] (II) XKB: reuse xkmfile /var/lib/xkb/server-2BE96391A32C62A55AC181853135C2CA7F918A38.xkm
[    60.286] (II) config/udev: Adding input device HP HP OMEN Mouse X9000 (/dev/input/mouse1)
[    60.286] (II) No input driver specified, ignoring this device.
[    60.286] (II) This device may have been added with another device file.
[    60.286] (II) config/udev: Adding input device HP HP OMEN Mouse X9000 (/dev/input/event8)
[    60.286] (**) HP HP OMEN Mouse X9000: Applying InputClass "evdev pointer catchall"
[    60.286] (II) Using input driver 'evdev' for 'HP HP OMEN Mouse X9000'
[    60.286] (**) HP HP OMEN Mouse X9000: always reports core events
[    60.286] (**) evdev: HP HP OMEN Mouse X9000: Device: "/dev/input/event8"
[    60.340] (--) evdev: HP HP OMEN Mouse X9000: Vendor 0x3f0 Product 0x1141
[    60.340] (--) evdev: HP HP OMEN Mouse X9000: Found 9 mouse buttons
[    60.340] (--) evdev: HP HP OMEN Mouse X9000: Found scroll wheel(s)
[    60.340] (--) evdev: HP HP OMEN Mouse X9000: Found relative axes
[    60.340] (--) evdev: HP HP OMEN Mouse X9000: Found x and y relative axes
[    60.340] (II) evdev: HP HP OMEN Mouse X9000: Configuring as mouse
[    60.340] (II) evdev: HP HP OMEN Mouse X9000: Adding scrollwheel support
[    60.340] (**) evdev: HP HP OMEN Mouse X9000: YAxisMapping: buttons 4 and 5
[    60.340] (**) evdev: HP HP OMEN Mouse X9000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    60.340] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:03F0:1141.0001/input/input9/event8"
[    60.340] (II) XINPUT: Adding extended input device "HP HP OMEN Mouse X9000" (type: MOUSE, id 13)
[    60.340] (II) evdev: HP HP OMEN Mouse X9000: initialized for relative axes.
[    60.340] (**) HP HP OMEN Mouse X9000: (accel) keeping acceleration scheme 1
[    60.340] (**) HP HP OMEN Mouse X9000: (accel) acceleration profile 0
[    60.340] (**) HP HP OMEN Mouse X9000: (accel) acceleration factor: 2.000
[    60.340] (**) HP HP OMEN Mouse X9000: (accel) acceleration threshold: 4
```

I guess it's more complicated than I thought.. :neutral: Thanks for helping me solve this.

Maybe 4.2.3-040203-generic is 3.13.0.137.146 because I recently installed a new kernel, trying to solve this.

---

### Post by Bashing-om on 2018-01-02
pedro-fox; Hummmm ..

Do not know what is not going on here :
> 
2.856] (**) FBDEV(1): claimed PCI slot 0@0:2:0

where that slot is the Intel GPU and it is loading that FBDEV driver . WHY ? Here I would expect the i915 driver to load.

And we have:
> 
2.839] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     2.839] (WW) xf86OpenConsole: setsid failed: Operation not permitted
2.839] (EE) [drm] KMS not enabled
[     2.839] (EE) [drm] KMS not enabled


Rather than hold this thread in suspense, I go see what I can learn .. and scratch my head some more.

once we know
[INDENT][INDENT]we do
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2018-01-02
pedro-fox; Well -

Consensus is a invalid xorg.conf file.

What I propose is to boot a mainline kernel, remove the present xorg.conf file, generate a new one as defaults .

So, what is the kernel situation - are all fully installed ?
show:
```

dpkg -l | grep linux-

```

Pick a mainline fully installed kernel and see what we can do .

[INDENT][INDENT]if I know better, I would do better
[/INDENT][/INDENT]

---

### Post by pedro-fox on 2018-01-10
Hi, I decided to reinstall BioLinux, since I was lacking grasp of the problem. I made some progress in this subject.

Thanks.

---

