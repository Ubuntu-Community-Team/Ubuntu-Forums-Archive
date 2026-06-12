---
title: "Xorg not starting."
date: 2017-03-14
forum: Ubuntu/Debian BASED
---

### Post by lgbowden on 2017-03-14
This is for Trisquel 7 Lite. Yesterday, after some updates, I was requested to restart the computer which I did. It wasn't plain sailing there seems to be issues with mdadm but I fixed those. Another reboot and there's no desktop of any form just a * in the top left of the screen and that's it. There's no keyboard response. The system is up though as it's serving the mdadm raid disk via samba as well as a test website under apache and I can login using ssh.

There's no Xorg process. There's plenty in Xorg.log.o thus
```
[ 53904.808]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[ 53904.809] X Protocol Version 11, Revision 0
[ 53904.810] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[ 53904.810] Current Operating System: Linux BACKUP 3.13.0-39-lowlatency #66+7.0trisquel2 SMP PREEMPT Wed Oct 29 14:55:34 UTC 2014 i686
[ 53904.811] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-lowlatency root=UUID=e711f6ff-6a1c-4a4c-981f-66224ef77964 ro quiet splash nomdmonddf nomdmonisw
[ 53904.811] Build Date: 12 February 2015  02:49:46PM
[ 53904.812] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[ 53904.812] Current version of pixman: 0.30.2
[ 53904.812]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[ 53904.812] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 53904.815] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 14 11:14:58 2017
[ 53904.825] (II) Loader magic: 0xb775e6c0
[ 53904.825] (II) Module ABI versions:
[ 53904.825]    X.Org ANSI C Emulation: 0.4
[ 53904.825]    X.Org Video Driver: 15.0
[ 53904.825]    X.Org XInput driver : 20.0
[ 53904.825]    X.Org Server Extension : 8.0
[ 53904.829] (--) PCI:*(0:0:1:0) 8086:7125:1028:00b4 rev 3, Mem @ 0xf8000000/67108864, 0xff000000/524288
[ 53904.831] List of video drivers:
[ 53904.831]    neomagic
[ 53904.832]    openchrome
[ 53904.832]    mach64
[ 53904.832]    mga
[ 53904.832]    vmware
[ 53904.833]    radeon
[ 53904.833]    modesetting
[ 53904.833]    sisusb
[ 53904.833]    qxl
[ 53904.834]    siliconmotion
[ 53904.834]    sis
[ 53904.834]    cirrus
[ 53904.834]    trident
[ 53904.835]    intel
[ 53904.835]    r128
[ 53904.836]    tdfx
[ 53904.836]    ati
[ 53904.837]    nouveau
[ 53904.837]    savage
[ 53904.837]    s3
[ 53904.838]    vesa
[ 53904.838]    fbdev
[ 53904.840] (II) LoadModule: "neomagic"
[ 53904.840] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[ 53904.852] (II) Module neomagic: vendor="X.Org Foundation"
[ 53904.852]    compiled for 1.15.0, module version = 1.2.8
[ 53904.852]    Module class: X.Org Video Driver
[ 53904.852]    ABI class: X.Org Video Driver, version 15.0
[ 53904.852] (II) LoadModule: "openchrome"
[ 53904.853] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[ 53904.879] (II) Module openchrome: vendor="http://openchrome.org/"
[ 53904.879]    compiled for 1.15.1, module version = 0.3.3
[ 53904.879]    Module class: X.Org Video Driver
[ 53904.879]    ABI class: X.Org Video Driver, version 15.0
[ 53904.879] (II) LoadModule: "mach64"
[ 53904.879] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[ 53904.898] (II) Module mach64: vendor="X.Org Foundation"
[ 53904.898]    compiled for 1.15.0, module version = 6.9.4
[ 53904.898]    Module class: X.Org Video Driver
[ 53904.898]    ABI class: X.Org Video Driver, version 15.0
[ 53904.898] (II) LoadModule: "mga"
[ 53904.899] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[ 53904.902] (II) Module mga: vendor="X.Org Foundation"
[ 53904.902]    compiled for 1.15.0, module version = 1.6.3
[ 53904.902]    Module class: X.Org Video Driver
[ 53904.902]    ABI class: X.Org Video Driver, version 15.0
[ 53904.904] (II) LoadModule: "vmware"
[ 53904.904] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[ 53905.422] (II) Module vmware: vendor="X.Org Foundation"
[ 53905.422]    compiled for 1.15.0, module version = 13.0.2
[ 53905.422]    Module class: X.Org Video Driver
[ 53905.422]    ABI class: X.Org Video Driver, version 15.0
[ 53905.422] (II) LoadModule: "radeon"
[ 53905.423] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 53905.499] (II) Module radeon: vendor="X.Org Foundation"
[ 53905.499]    compiled for 1.15.1, module version = 7.3.0
[ 53905.499]    Module class: X.Org Video Driver
[ 53905.499]    ABI class: X.Org Video Driver, version 15.0
[ 53905.499] (II) LoadModule: "modesetting"
[ 53905.499] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 53905.509] (II) Module modesetting: vendor="X.Org Foundation"
[ 53905.510]    compiled for 1.15.0, module version = 0.8.1
[ 53905.510]    Module class: X.Org Video Driver
[ 53905.510]    ABI class: X.Org Video Driver, version 15.0
[ 53905.510] (II) LoadModule: "sisusb"
[ 53905.510] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[ 53905.524] (II) Module sisusb: vendor="X.Org Foundation"
[ 53905.524]    compiled for 1.15.0, module version = 0.9.6
[ 53905.524]    Module class: X.Org Video Driver
[ 53905.524]    ABI class: X.Org Video Driver, version 15.0
[ 53905.524] (II) LoadModule: "qxl"
[ 53905.525] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[ 53905.537] (II) Module qxl: vendor="X.Org Foundation"
[ 53905.537]    compiled for 1.15.0, module version = 0.1.1
[ 53905.537]    Module class: X.Org Video Driver
[ 53905.537]    ABI class: X.Org Video Driver, version 15.0
[ 53905.537] (II) LoadModule: "siliconmotion"
[ 53905.537] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[ 53905.563] (II) Module siliconmotion: vendor="X.Org Foundation"
[ 53905.563]    compiled for 1.15.0, module version = 1.7.7
[ 53905.563]    Module class: X.Org Video Driver
[ 53905.563]    ABI class: X.Org Video Driver, version 15.0
[ 53905.563] (II) LoadModule: "sis"
[ 53905.564] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[ 53905.596] (II) Module sis: vendor="X.Org Foundation"
[ 53905.596]    compiled for 1.15.0, module version = 0.10.7
[ 53905.596]    Module class: X.Org Video Driver
[ 53905.596]    ABI class: X.Org Video Driver, version 15.0
[ 53905.596] (II) LoadModule: "cirrus"
[ 53905.596] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[ 53905.605] (II) Module cirrus: vendor="X.Org Foundation"
[ 53905.605]    compiled for 1.15.0, module version = 1.5.2
[ 53905.605]    Module class: X.Org Video Driver
[ 53905.605]    ABI class: X.Org Video Driver, version 15.0
[ 53905.605] (II) LoadModule: "trident"
[ 53905.606] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[ 53905.619] (II) Module trident: vendor="X.Org Foundation"
[ 53905.620]    compiled for 1.15.0, module version = 1.3.6
[ 53905.620]    Module class: X.Org Video Driver
[ 53905.620]    ABI class: X.Org Video Driver, version 15.0
[ 53905.620] (II) LoadModule: "intel"
[ 53905.621] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 53905.637] (II) Module intel: vendor="X.Org Foundation"
[ 53905.637]    compiled for 1.15.1, module version = 2.99.910
[ 53905.637]    Module class: X.Org Video Driver
[ 53905.637]    ABI class: X.Org Video Driver, version 15.0
[ 53905.637] (II) LoadModule: "r128"
[ 53905.638] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[ 53905.650] (II) Module r128: vendor="X.Org Foundation"
[ 53905.650]    compiled for 1.15.0, module version = 6.9.2
[ 53905.650]    Module class: X.Org Video Driver
[ 53905.650]    ABI class: X.Org Video Driver, version 15.0
[ 53905.651] (II) LoadModule: "tdfx"
[ 53905.651] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[ 53905.658] (II) Module tdfx: vendor="X.Org Foundation"
[ 53905.658]    compiled for 1.15.0, module version = 1.4.5
[ 53905.658]    Module class: X.Org Video Driver
[ 53905.658]    ABI class: X.Org Video Driver, version 15.0
[ 53905.658] (II) LoadModule: "ati"
[ 53905.659] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 53905.665] (II) Module ati: vendor="X.Org Foundation"
[ 53905.665]    compiled for 1.15.1, module version = 7.3.0
[ 53905.665]    Module class: X.Org Video Driver
[ 53905.665]    ABI class: X.Org Video Driver, version 15.0
[ 53905.665] (II) LoadModule: "nouveau"
[ 53905.666] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 53905.695] (II) Module nouveau: vendor="X.Org Foundation"
[ 53905.695]    compiled for 1.15.0, module version = 1.0.10
[ 53905.695]    Module class: X.Org Video Driver
[ 53905.695]    ABI class: X.Org Video Driver, version 15.0
[ 53905.695] (II) LoadModule: "savage"
[ 53905.695] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[ 53905.711] (II) Module savage: vendor="X.Org Foundation"
[ 53905.712]    compiled for 1.15.0, module version = 2.3.7
[ 53905.712]    Module class: X.Org Video Driver
[ 53905.712]    ABI class: X.Org Video Driver, version 15.0
[ 53905.712] (II) LoadModule: "s3"
[ 53905.713] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[ 53905.718] (II) Module s3: vendor="X.Org Foundation"
[ 53905.718]    compiled for 1.15.0, module version = 0.6.5
[ 53905.718]    Module class: X.Org Video Driver
[ 53905.718]    ABI class: X.Org Video Driver, version 15.0
[ 53905.718] (II) LoadModule: "vesa"
[ 53905.718] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 53905.728] (II) Module vesa: vendor="X.Org Foundation"
[ 53905.728]    compiled for 1.15.0, module version = 2.3.3
[ 53905.728]    Module class: X.Org Video Driver
[ 53905.728]    ABI class: X.Org Video Driver, version 15.0
[ 53905.728] (II) LoadModule: "fbdev"
[ 53905.729] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 53905.737] (II) Module fbdev: vendor="X.Org Foundation"
[ 53905.737]    compiled for 1.15.0, module version = 0.4.4
[ 53905.737]    Module class: X.Org Video Driver
[ 53905.737]    ABI class: X.Org Video Driver, version 15.0
[ 53905.737] (WW) Falling back to old probe method for neomagic
[ 53905.737] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 53905.737] (WW) Falling back to old probe method for sisusb
[ 53905.737] (WW) Falling back to old probe method for siliconmotion
[ 53905.737] (WW) Falling back to old probe method for sis
[ 53905.737] (WW) Falling back to old probe method for cirrus
[ 53905.738] (II) Loading sub module "cirrus_laguna"
[ 53905.738] (II) LoadModule: "cirrus_laguna"
[ 53905.739] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[ 53905.746] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[ 53905.746]    compiled for 1.15.0, module version = 1.0.0
[ 53905.746]    ABI class: X.Org Video Driver, version 15.0
[ 53905.746] (II) Loading sub module "cirrus_alpine"
[ 53905.746] (II) LoadModule: "cirrus_alpine"
[ 53905.746] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[ 53905.754] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[ 53905.754]    compiled for 1.15.0, module version = 1.0.0
[ 53905.754]    ABI class: X.Org Video Driver, version 15.0
[ 53905.754] (WW) Falling back to old probe method for trident
[ 53905.754] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[ 53905.755] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[ 53905.755] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[ 53905.755] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[ 53905.756] (WW) Falling back to old probe method for s3
[ 53905.756] (II) VESA: driver for VESA chipsets: vesa
[ 53905.756] (II) FBDEV: driver for framebuffer: fbdev
[ 53905.815] (++) Using config file: "/home/leigh/xorg.conf.new"
[ 53905.816] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 53905.848] (==) ServerLayout "X.org Configured"
[ 53905.848] (**) |-->Screen "Screen0" (0)
[ 53905.848] (**) |   |-->Monitor "Monitor0"
[ 53905.849] (**) |   |-->Device "Card0"
[ 53905.849] (**) |-->Input Device "Mouse0"
[ 53905.849] (**) |-->Input Device "Keyboard0"
[ 53905.850] (==) Automatically adding devices
[ 53905.850] (==) Automatically enabling devices
[ 53905.850] (==) Automatically adding GPU devices
[ 53905.876] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.
[ 53905.876]    Entry deleted from font path.
[ 53905.876] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 53905.876]    Entry deleted from font path.
[ 53905.876] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 53905.876]    Entry deleted from font path.
[ 53905.876] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 53905.876]    Entry deleted from font path.
[ 53905.876] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 53905.876]    Entry deleted from font path.
[ 53905.876] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 53905.877]    Entry deleted from font path.
[ 53905.877] (**) FontPath set to:
        /usr/share/fonts/X11/Type1,
        built-ins,
        /usr/share/fonts/X11/Type1,
        built-ins
[ 53905.877] (**) ModulePath set to "/usr/lib/xorg/modules"
[ 53905.877] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 53905.877] (WW) Disabling Mouse0
[ 53905.877] (WW) Disabling Keyboard0
[ 53905.878] (EE) open /dev/dri/card0: No such file or directory
[ 53905.878] (WW) Falling back to old probe method for modesetting
[ 53905.878] (EE) open /dev/dri/card0: No such file or directory
[ 53905.878] (EE)
[ 53905.879] (EE) Backtrace:
[ 53905.880] (EE) 0: Xorg (xorg_backtrace+0x4f) [0xb76d71bf]
[ 53905.882] (EE) 1: Xorg (0xb752e000+0x1acfa4) [0xb76dafa4]
[ 53905.882] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb750b40c]
[ 53905.883] (EE)
[ 53905.883] (EE) Segmentation fault at address 0x0
[ 53905.884] (EE)
Fatal server error:
[ 53905.885] (EE) Caught signal 11 (Segmentation fault). Server aborting
[ 53905.885] (EE)
[ 53905.886] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[ 53905.887] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 53905.888] (EE)
```

Why has this happened and what can I do to fix it?

---

### Post by howefield on 2017-03-14
Thread moved to the "*Ubuntu/Debian BASED*" forum and code tags added.

---

