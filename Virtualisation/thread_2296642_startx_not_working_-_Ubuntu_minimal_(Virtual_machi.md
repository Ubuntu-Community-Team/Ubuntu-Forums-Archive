---
title: "startx not working - Ubuntu minimal (Virtual machine)"
date: 2015-09-27
forum: Virtualisation
---

### Post by leninberg on 2015-09-27
Hello all
I am making an installation, with ubuntu minimal iso (Ubuntu 15.04 "Vivid Vervet")
I am doing it with VMware Workstation 12, on Windows 8.1.
VM-tools installed after first reboot (after completing minimal install)
I have tried with both 32 and 64bits isos, both failed.
I am following this guide (but i3 instead of xfce, and no display manager)
[https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/](https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/)

The problem comes when I type startx, it doesn't load i3.
The first time I tried I got

xauth: file /home/tom/.Xauthority does not exist

This is my /var/log/Xorg.0.log
```
[   487.270] X.Org X Server 1.17.1
Release Date: 2015-02-10
[   487.270] X Protocol Version 11, Revision 0
[   487.270] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[   487.270] Current Operating System: Linux ubuntu 3.19.0-28-generic #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015 x86_64
[   487.270] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-28-generic root=UUID=389bad69-0e80-4f45-bc04-519888024056 ro splash quiet
[   487.271] Build Date: 11 September 2015  10:30:58AM
[   487.271] xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see http://www.ubuntu.com/support) 
[   487.271] Current version of pixman: 0.32.6
[   487.271]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   487.271] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   487.272] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 27 18:00:09 2015
[   487.398] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   487.423] (==) No Layout section.  Using the first Screen section.
[   487.423] (==) No screen section available. Using defaults.
[   487.423] (**) |-->Screen "Default Screen Section" (0)
[   487.423] (**) |   |-->Monitor "<default monitor>"
[   487.424] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   487.424] (==) Automatically adding devices
[   487.424] (==) Automatically enabling devices
[   487.424] (==) Automatically adding GPU devices
[   487.456] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   487.456]     Entry deleted from font path.
[   487.456] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   487.456]     Entry deleted from font path.
[   487.456] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   487.456]     Entry deleted from font path.
[   487.456] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[   487.456]     Entry deleted from font path.
[   487.456] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   487.456]     Entry deleted from font path.
[   487.456] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   487.456]     Entry deleted from font path.
[   487.456] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[   487.456] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   487.456] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   487.457] (II) Loader magic: 0x7f4aa54b6d80
[   487.457] (II) Module ABI versions:
[   487.457]     X.Org ANSI C Emulation: 0.4
[   487.457]     X.Org Video Driver: 19.0
[   487.457]     X.Org XInput driver : 21.0
[   487.457]     X.Org Server Extension : 9.0
[   487.459] (II) xfree86: Adding drm device (/dev/dri/card0)
[   487.478] (--) PCI:*(0:0:15:0) 15ad:0405:15ad:0405 rev 0, Mem @ 0xe8000000/134217728, 0xfe000000/8388608, I/O @ 0x00001070/16, BIOS @ 0x????????/32768
[   487.479] (II) LoadModule: "glx"
[   487.497] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   487.631] (II) Module glx: vendor="X.Org Foundation"
[   487.631]     compiled for 1.17.1, module version = 1.0.0
[   487.631]     ABI class: X.Org Server Extension, version 9.0
[   487.631] (==) AIGLX enabled
[   487.631] (==) Matched vmware as autoconfigured driver 0
[   487.631] (==) Matched vmware as autoconfigured driver 1
[   487.631] (==) Matched modesetting as autoconfigured driver 2
[   487.631] (==) Matched fbdev as autoconfigured driver 3
[   487.631] (==) Matched vesa as autoconfigured driver 4
[   487.631] (==) Assigned the driver to the xf86ConfigLayout
[   487.631] (II) LoadModule: "vmware"
[   487.632] (WW) Warning, couldn't open module vmware
[   487.632] (II) UnloadModule: "vmware"
[   487.633] (II) Unloading vmware
[   487.633] (EE) Failed to load module "vmware" (module does not exist, 0)
[   487.633] (II) LoadModule: "modesetting"
[   487.633] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   487.635] (II) Module modesetting: vendor="X.Org Foundation"
[   487.635]     compiled for 1.17.1, module version = 1.17.1
[   487.635]     Module class: X.Org Video Driver
[   487.635]     ABI class: X.Org Video Driver, version 19.0
[   487.635] (II) LoadModule: "fbdev"
[   487.636] (WW) Warning, couldn't open module fbdev
[   487.636] (II) UnloadModule: "fbdev"
[   487.636] (II) Unloading fbdev
[   487.636] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   487.636] (II) LoadModule: "vesa"
[   487.636] (WW) Warning, couldn't open module vesa
[   487.636] (II) UnloadModule: "vesa"
[   487.636] (II) Unloading vesa
[   487.636] (EE) Failed to load module "vesa" (module does not exist, 0)
[   487.636] (==) Matched vmware as autoconfigured driver 0
[   487.636] (==) Matched vmware as autoconfigured driver 1
[   487.636] (==) Matched modesetting as autoconfigured driver 2
[   487.636] (==) Matched fbdev as autoconfigured driver 3
[   487.636] (==) Matched vesa as autoconfigured driver 4
[   487.636] (==) Assigned the driver to the xf86ConfigLayout
[   487.636] (II) LoadModule: "vmware"
[   487.636] (WW) Warning, couldn't open module vmware
[   487.636] (II) UnloadModule: "vmware"
[   487.636] (II) Unloading vmware
[   487.636] (EE) Failed to load module "vmware" (module does not exist, 0)
[   487.636] (II) LoadModule: "modesetting"
[   487.636] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   487.636] (II) Module modesetting: vendor="X.Org Foundation"
[   487.636]     compiled for 1.17.1, module version = 1.17.1
[   487.637]     Module class: X.Org Video Driver
[   487.637]     ABI class: X.Org Video Driver, version 19.0
[   487.637] (II) UnloadModule: "modesetting"
[   487.637] (II) Unloading modesetting
[   487.637] (II) Failed to load module "modesetting" (already loaded, 0)
[   487.637] (II) LoadModule: "fbdev"
[   487.637] (WW) Warning, couldn't open module fbdev
[   487.637] (II) UnloadModule: "fbdev"
[   487.637] (II) Unloading fbdev
[   487.637] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   487.637] (II) LoadModule: "vesa"
[   487.637] (WW) Warning, couldn't open module vesa
[   487.637] (II) UnloadModule: "vesa"
[   487.637] (II) Unloading vesa
[   487.637] (EE) Failed to load module "vesa" (module does not exist, 0)
[   487.637] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   487.637] (++) using VT number 1


[   487.637] (--) controlling tty is VT number 1, auto-enabling KeepTty
[   487.637] (II) modeset(0): using drv /dev/dri/card0
[   487.637] (WW) Falling back to old probe method for modesetting
[   487.638] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   487.638] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[   487.638] (==) modeset(0): RGB weight 888
[   487.638] (==) modeset(0): Default visual is TrueColor
[   487.638] (II) Loading sub module "glamoregl"
[   487.638] (II) LoadModule: "glamoregl"
[   487.638] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   487.787] (II) Module glamoregl: vendor="X.Org Foundation"
[   487.787]     compiled for 1.17.1, module version = 1.0.0
[   487.787]     ABI class: X.Org ANSI C Emulation, version 0.4
[   487.787] (II) glamor: OpenGL accelerated X.org driver based.
[   488.985] (II) glamor: EGL version 1.4 (DRI2):
[   489.164] (II) modeset(0): glamor initialized
[   489.165] (II) Loading sub module "dri2"
[   489.165] (II) LoadModule: "dri2"
[   489.165] (II) Module "dri2" already built-in
[   489.166] (II) modeset(0): Output Virtual-0 has no monitor section
[   489.166] (II) modeset(0): Output Virtual-1 has no monitor section
[   489.166] (II) modeset(0): Output Virtual-2 has no monitor section
[   489.167] (II) modeset(0): Output Virtual-3 has no monitor section
[   489.167] (II) modeset(0): Output Virtual-4 has no monitor section
[   489.167] (II) modeset(0): Output Virtual-5 has no monitor section
[   489.167] (II) modeset(0): Output Virtual-6 has no monitor section
[   489.167] (II) modeset(0): Output Virtual-7 has no monitor section
[   489.168] (II) modeset(0): EDID for output Virtual-0
[   489.169] (II) modeset(0): Printing probed modes for output Virtual-0
[   489.169] (II) modeset(0): Modeline "preferred"x60.0   42.75  800 850 900 950  600 650 700 750 -hsync +vsync (45.0 kHz eP)
[   489.169] (II) modeset(0): Modeline "2560x1600"x60.0  348.50  2560 2752 3032 3504  1600 1603 1609 1658 -hsync +vsync (99.5 kHz e)
[   489.169] (II) modeset(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz e)
[   489.169] (II) modeset(0): Modeline "1856x1392"x60.0  218.25  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.3 kHz e)
[   489.169] (II) modeset(0): Modeline "1792x1344"x60.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz e)
[   489.169] (II) modeset(0): Modeline "1920x1200"x59.9  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz e)
[   489.169] (II) modeset(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[   489.169] (II) modeset(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   489.169] (II) modeset(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz e)
[   489.169] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   489.169] (II) modeset(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[   489.169] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   489.169] (II) modeset(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[   489.169] (II) modeset(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[   489.169] (II) modeset(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   489.169] (II) modeset(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz e)
[   489.169] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   489.169] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   489.169] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[   489.169] (II) modeset(0): EDID for output Virtual-1
[   489.169] (II) modeset(0): EDID for output Virtual-2
[   489.169] (II) modeset(0): EDID for output Virtual-3
[   489.169] (II) modeset(0): EDID for output Virtual-4
[   489.169] (II) modeset(0): EDID for output Virtual-5
[   489.169] (II) modeset(0): EDID for output Virtual-6
[   489.169] (II) modeset(0): EDID for output Virtual-7
[   489.169] (II) modeset(0): Output Virtual-0 connected
[   489.169] (II) modeset(0): Output Virtual-1 disconnected
[   489.169] (II) modeset(0): Output Virtual-2 disconnected
[   489.169] (II) modeset(0): Output Virtual-3 disconnected
[   489.169] (II) modeset(0): Output Virtual-4 disconnected
[   489.169] (II) modeset(0): Output Virtual-5 disconnected
[   489.169] (II) modeset(0): Output Virtual-6 disconnected
[   489.169] (II) modeset(0): Output Virtual-7 disconnected
[   489.169] (II) modeset(0): Using exact sizes for initial modes
[   489.169] (II) modeset(0): Output Virtual-0 using initial mode preferred
[   489.169] (II) modeset(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   489.169] (==) modeset(0): DPI set to (96, 96)
[   489.169] (II) Loading sub module "fb"
[   489.169] (II) LoadModule: "fb"
[   489.170] (II) Loading /usr/lib/xorg/modules/libfb.so
[   489.237] (II) Module fb: vendor="X.Org Foundation"
[   489.237]     compiled for 1.17.1, module version = 1.0.0
[   489.237]     ABI class: X.Org ANSI C Emulation, version 0.4
[   489.237] (==) Depth 24 pixmap format is 32 bpp
[   489.516] (==) modeset(0): Backing store enabled
[   489.516] (==) modeset(0): Silken mouse enabled
[   489.517] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   489.518] (==) modeset(0): DPMS enabled
[   489.518] (II) modeset(0): [DRI2] Setup complete
[   489.518] (II) modeset(0): [DRI2]   DRI driver: vmwgfx
[   489.518] (II) modeset(0): [DRI2]   VDPAU driver: vmwgfx
[   489.518] failed to add fb -22
[   489.518] (EE) 
Fatal server error:
[   489.518] (EE) AddScreen/ScreenInit failed for driver 0
[   489.518] (EE) 
[   489.518] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   489.518] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   489.518] (EE) 

```

here too [http://pastebin.com/23XSz9G6](http://pastebin.com/23XSz9G6)

I shut down the virtual machine and started the virtual machine again, typed startx and then that message (.Xauthority) is not shown, but i3 still not starting.

The log is still the same (changing only numbers and times)
In case you want to see it too [http://pastebin.com/eh7r4wxS](http://pastebin.com/eh7r4wxS)

These are all the packages installed (dpkg -l):
```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                Version                           Architecture Description
+++-===================================-=================================-============-===============================================================================
ii  accountsservice                     0.6.37-1ubuntu10.1                amd64        query and manipulate user account information
ii  adduser                             3.113+nmu3ubuntu3                 all          add and remove users and groups
ii  apparmor                            2.9.1-0ubuntu9                    amd64        User-space parser utility for AppArmor
ii  apt                                 1.0.9.7ubuntu4.1                  amd64        commandline package manager
ii  apt-transport-https                 1.0.9.7ubuntu4.1                  amd64        https download transport for APT
ii  apt-utils                           1.0.9.7ubuntu4.1                  amd64        package management related utility programs
ii  aptitude                            0.6.11-1ubuntu3                   amd64        terminal-based package manager
ii  aptitude-common                     0.6.11-1ubuntu3                   all          architecture independent files for the aptitude package manager
ii  aptitude-doc-en                     0.6.11-1ubuntu3                   all          English manual for aptitude, a terminal-based package manager
ii  base-files                          7.2ubuntu9                        amd64        Debian base system miscellaneous files
ii  base-passwd                         3.5.37                            amd64        Debian base system master password and group files
ii  bash                                4.3-11ubuntu2                     amd64        GNU Bourne Again SHell
ii  bash-completion                     1:2.1-4ubuntu1                    all          programmable completion for the bash shell
ii  bind9-host                          1:9.9.5.dfsg-9ubuntu0.3           amd64        Version of 'host' bundled with BIND 9.X
ii  biosdevname                         0.4.1-0ubuntu7.1                  amd64        apply BIOS-given names to network devices
ii  bsdmainutils                        9.0.6ubuntu1                      amd64        collection of more utilities from FreeBSD
ii  bsdutils                            1:2.25.2-4ubuntu3                 amd64        basic utilities from 4.4BSD-Lite
ii  busybox-initramfs                   1:1.22.0-9ubuntu1                 amd64        Standalone shell setup for initramfs
ii  busybox-static                      1:1.22.0-9ubuntu1                 amd64        Standalone rescue shell with tons of builtin utilities
ii  bzip2                               1.0.6-7                           amd64        high-quality block-sorting file compressor - utilities
ii  ca-certificates                     20141019ubuntu0.15.04.1           all          Common CA certificates
ii  command-not-found                   0.3ubuntu15.3                     all          Suggest installation of packages in interactive bash sessions
ii  command-not-found-data              0.3ubuntu15.3                     amd64        Set of data files for command-not-found.
ii  console-setup                       1.108ubuntu5                      all          console font and keymap setup program
ii  console-setup-linux                 1.108ubuntu5                      all          Linux specific part of console-setup
ii  coreutils                           8.23-3ubuntu1                     amd64        GNU core utilities
ii  cpio                                2.11+dfsg-4.1ubuntu1              amd64        GNU cpio -- a program to manage archives of files
ii  cpp                                 4:4.9.2-2ubuntu2                  amd64        GNU C preprocessor (cpp)
ii  cpp-4.9                             4.9.2-10ubuntu13                  amd64        GNU C preprocessor
ii  crda                                3.13-1                            amd64        wireless Central Regulatory Domain Agent
ii  cron                                3.0pl1-127ubuntu1                 amd64        process scheduling daemon
ii  dash                                0.5.7-4ubuntu1                    amd64        POSIX-compliant shell
ii  dbus                                1.8.12-1ubuntu5                   amd64        simple interprocess messaging system (daemon and utilities)
ii  dconf-gsettings-backend:amd64       0.22.0-1                          amd64        simple configuration storage system - GSettings back-end
ii  dconf-service                       0.22.0-1                          amd64        simple configuration storage system - D-Bus service
ii  debconf                             1.5.55ubuntu2                     all          Debian configuration management system
ii  debconf-i18n                        1.5.55ubuntu2                     all          full internationalization support for debconf
ii  debianutils                         4.4                               amd64        Miscellaneous utilities specific to Debian
ii  desktop-file-utils                  0.22-1ubuntu3                     amd64        Utilities for .desktop files
ii  dh-python                           1.20141111-2ubuntu1               all          Debian helper tools for packaging Python libraries and applications
ii  dictionaries-common                 1.23.17                           all          spelling dictionaries - common utilities
ii  diffutils                           1:3.3-1                           amd64        File comparison utilities
ii  discover                            2.1.2-7ubuntu1                    amd64        hardware identification system
ii  discover-data                       2.2013.01.11                      all          Data lists for Discover hardware detection system
ii  dmidecode                           2.12-3                            amd64        SMBIOS/DMI table decoder
ii  dmsetup                             2:1.02.90-2ubuntu1                amd64        Linux Kernel Device Mapper userspace library
ii  dnsutils                            1:9.9.5.dfsg-9ubuntu0.3           amd64        Clients provided with BIND
ii  dosfstools                          3.0.27-1                          amd64        utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                                1.17.25ubuntu1                    amd64        Debian package management system
ii  e2fslibs:amd64                      1.42.12-1ubuntu2                  amd64        ext2/ext3/ext4 file system libraries
ii  e2fsprogs                           1.42.12-1ubuntu2                  amd64        ext2/ext3/ext4 file system utilities
ii  ed                                  1.10-2                            amd64        classic UNIX line editor
ii  eject                               2.1.5+deb1+cvs20081104-13.1       amd64        ejects CDs and operates CD-Changers under Linux
ii  emacsen-common                      2.0.8                             all          Common facilities for all emacsen
ii  file                                1:5.20-1ubuntu2                   amd64        Determines file type using "magic" numbers
ii  findutils                           4.4.2-9build1                     amd64        utilities for finding files--find, xargs
ii  fontconfig                          2.11.1-0ubuntu6                   amd64        generic font configuration library - support binaries
ii  fontconfig-config                   2.11.1-0ubuntu6                   all          generic font configuration library - configuration
ii  fonts-dejavu-core                   2.34-1ubuntu1                     all          Vera font family derivate with additional characters
ii  friendly-recovery                   0.2.30                            all          Make recovery more user-friendly
ii  ftp                                 0.17-31                           amd64        classical file transfer client
ii  fuse                                2.9.2-4ubuntu4.15.04.1            amd64        Filesystem in Userspace
ii  gcc-4.9-base:amd64                  4.9.2-10ubuntu13                  amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-5-base:amd64                    5.1~rc1-0ubuntu1                  amd64        GCC, the GNU Compiler Collection (base package)
ii  geoip-database                      20150209-1                        all          IP lookup command line tools that use the GeoIP library (country database)
ii  gettext-base                        0.19.2-2ubuntu1                   amd64        GNU Internationalization utilities for the base system
ii  gir1.2-glib-2.0:amd64               1.42.0-2.2                        amd64        Introspection data for GLib, GObject, Gio and GModule
ii  glib-networking:amd64               2.44.0-1                          amd64        network-related giomodules for GLib
ii  glib-networking-common              2.44.0-1                          all          network-related giomodules for GLib - data files
ii  glib-networking-services            2.44.0-1                          amd64        network-related giomodules for GLib - D-Bus services
ii  gnupg                               1.4.18-7ubuntu1                   amd64        GNU privacy guard - a free PGP replacement
ii  gpgv                                1.4.18-7ubuntu1                   amd64        GNU privacy guard - signature verification tool
ii  grep                                2.20-4.1                          amd64        GNU grep, egrep and fgrep
ii  groff-base                          1.22.3-1                          amd64        GNU troff text-formatting system (base system components)
ii  grub-common                         2.02~beta2-22ubuntu1.1            amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists               0.7                               amd64        GRUB gfxpayload blacklist
ii  grub-pc                             2.02~beta2-22ubuntu1.1            amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                         2.02~beta2-22ubuntu1.1            amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                        2.02~beta2-22ubuntu1.1            amd64        GRand Unified Bootloader (common files for version 2)
ii  gsettings-desktop-schemas           3.14.1-1ubuntu2                   all          GSettings desktop-wide schemas
ii  gvfs:amd64                          1.24.1-1ubuntu1                   amd64        userspace virtual filesystem - GIO module
ii  gvfs-backends                       1.24.1-1ubuntu1                   amd64        userspace virtual filesystem - backends
ii  gvfs-common                         1.24.1-1ubuntu1                   all          userspace virtual filesystem - common data files
ii  gvfs-daemons                        1.24.1-1ubuntu1                   amd64        userspace virtual filesystem - servers
ii  gvfs-libs:amd64                     1.24.1-1ubuntu1                   amd64        userspace virtual filesystem - private libraries
ii  gzip                                1.6-4ubuntu1                      amd64        GNU compression utilities
ii  hdparm                              9.43-1ubuntu3                     amd64        tune hard disk parameters for high performance
ii  hostname                            3.15ubuntu2                       amd64        utility to set/show the host name or domain name
ii  htop                                1.0.3-1                           amd64        interactive processes viewer
ii  i3                                  4.10.4-1~~vivid1                  amd64        metapackage (i3 window manager, screen locker, menu, statusbar)
ii  i3-wm                               4.10.4-1~~vivid1                  amd64        improved dynamic tiling window manager
ii  i3lock                              2.7-1~~vivid1                     amd64        improved screen locker
ii  i3status                            2.9-2~~vivid1                     amd64        Generates a status line for dzen2, xmobar or i3bar
ii  ifupdown                            0.7.48.1ubuntu10                  amd64        high level tools to configure network interfaces
ii  info                                5.2.0.dfsg.1-6                    amd64        Standalone GNU Info documentation browser
ii  init                                1.22ubuntu11                      amd64        System-V-like init utilities - metapackage
ii  init-system-helpers                 1.22ubuntu11                      all          helper tools for all init systems
ii  initramfs-tools                     0.103ubuntu15                     all          tools for generating an initramfs
ii  initramfs-tools-bin                 0.103ubuntu15                     amd64        binaries used by initramfs-tools
ii  initscripts                         2.88dsf-53.2ubuntu12              amd64        scripts for initializing and shutting down the system
ii  insserv                             1.14.0-5ubuntu3                   amd64        boot sequence organizer using LSB init.d script dependency information
ii  install-info                        5.2.0.dfsg.1-6                    amd64        Manage installed documentation in info format
ii  installation-report                 2.56ubuntu1                       all          system installation report
ii  iproute2                            3.16.0-2ubuntu1.1                 amd64        networking and traffic control tools
ii  iptables                            1.4.21-2ubuntu2                   amd64        administration tools for packet filtering and NAT
ii  iputils-ping                        3:20121221-5ubuntu2               amd64        Tools to test the reachability of network hosts
ii  iputils-tracepath                   3:20121221-5ubuntu2               amd64        Tools to trace the network path to a remote host
ii  irqbalance                          1.0.6-3ubuntu1.1                  amd64        Daemon to balance interrupts for SMP systems
ii  isc-dhcp-client                     4.3.1-5ubuntu2.2                  amd64        DHCP client for automatically obtaining an IP address
ii  isc-dhcp-common                     4.3.1-5ubuntu2.2                  amd64        common files used by all of the isc-dhcp packages
ii  iso-codes                           3.57-1                            all          ISO language, territory, currency, script codes and their translations
ii  iw                                  3.17-1                            amd64        tool for configuring Linux wireless devices
ii  kbd                                 1.15.5-1ubuntu2                   amd64        Linux console font and keytable utilities
ii  keyboard-configuration              1.108ubuntu5                      all          system-wide keyboard preferences
ii  klibc-utils                         2.0.3-0ubuntu1                    amd64        small utilities built with klibc for early boot
ii  kmod                                18-3ubuntu1                       amd64        tools for managing Linux kernel modules
ii  krb5-locales                        1.12.1+dfsg-18                    all          Internationalization support for MIT Kerberos
ii  language-pack-en                    1:15.04+20150615                  all          translation updates for language English
ii  language-pack-en-base               1:15.04+20150615                  all          translations for language English
ii  language-pack-gnome-en              1:15.04+20150615                  all          GNOME translation updates for language English
ii  language-pack-gnome-en-base         1:15.04+20150615                  all          GNOME translations for language English
ii  language-selector-common            0.143                             all          Language selector for Ubuntu
ii  laptop-detect                       0.13.7ubuntu2                     amd64        attempt to detect a laptop
ii  less                                458-3                             amd64        pager program similar to more
ii  libaccountsservice0:amd64           0.6.37-1ubuntu10.1                amd64        query and manipulate user account information - shared libraries
ii  libacl1:amd64                       2.2.52-2                          amd64        Access control list shared library
ii  libalgorithm-c3-perl                0.09-1                            all          Perl module for merging hierarchies using the C3 algorithm
ii  libapparmor-perl                    2.9.1-0ubuntu9                    amd64        AppArmor library Perl bindings
ii  libapparmor1:amd64                  2.9.1-0ubuntu9                    amd64        changehat AppArmor library
ii  libapt-inst1.5:amd64                1.0.9.7ubuntu4.1                  amd64        deb package format runtime library
ii  libapt-pkg4.12:amd64                1.0.9.7ubuntu4.1                  amd64        package management runtime library
ii  libarchive-extract-perl             0.72-1                            all          generic archive extracting module
ii  libarchive13:amd64                  3.1.2-11                          amd64        Multi-format archive and compression library (shared library)
ii  libasn1-8-heimdal:amd64             1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - ASN.1 library
ii  libasound2:amd64                    1.0.28-1                          amd64        shared library for ALSA applications
ii  libasound2-data                     1.0.28-1                          all          Configuration files and profiles for ALSA drivers
ii  libasprintf0c2:amd64                0.19.2-2ubuntu1                   amd64        GNU library to use fprintf and friends in C++
ii  libatasmart4:amd64                  0.19-3                            amd64        ATA S.M.A.R.T. reading and parsing library
ii  libatk-bridge2.0-0:amd64            2.14.0-2ubuntu1                   amd64        AT-SPI 2 toolkit bridge - shared library
ii  libatk1.0-0:amd64                   2.14.0-1ubuntu1                   amd64        ATK accessibility toolkit
ii  libatk1.0-data                      2.14.0-1ubuntu1                   all          Common files for the ATK accessibility toolkit
ii  libatm1:amd64                       1:2.5.1-1.5                       amd64        shared library for ATM (Asynchronous Transfer Mode)
ii  libatspi2.0-0:amd64                 2.14.0-1ubuntu2                   amd64        Assistive Technology Service Provider Interface - shared library
ii  libattr1:amd64                      1:2.4.47-2                        amd64        Extended attribute shared library
ii  libaudit-common                     1:2.3.7-1ubuntu2                  all          Dynamic library for security auditing - common files
ii  libaudit1:amd64                     1:2.3.7-1ubuntu2                  amd64        Dynamic library for security auditing
ii  libavahi-client3:amd64              0.6.31-4ubuntu4                   amd64        Avahi client library
ii  libavahi-common-data:amd64          0.6.31-4ubuntu4                   amd64        Avahi common data files
ii  libavahi-common3:amd64              0.6.31-4ubuntu4                   amd64        Avahi common library
ii  libavahi-glib1:amd64                0.6.31-4ubuntu4                   amd64        Avahi GLib integration library
ii  libbind9-90                         1:9.9.5.dfsg-9ubuntu0.3           amd64        BIND9 Shared Library used by BIND
ii  libblkid1:amd64                     2.25.2-4ubuntu3                   amd64        block device id library
ii  libbluetooth3:amd64                 4.101-0ubuntu25                   amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libboost-filesystem1.55.0:amd64     1.55.0+dfsg-3ubuntu2              amd64        filesystem operations (portable paths, iteration over directories, etc) in C++
ii  libboost-iostreams1.55.0:amd64      1.55.0+dfsg-3ubuntu2              amd64        Boost.Iostreams Library
ii  libboost-system1.55.0:amd64         1.55.0+dfsg-3ubuntu2              amd64        Operating system (e.g. diagnostics support) library
ii  libbsd0:amd64                       0.7.0-2                           amd64        utility functions from BSD systems - shared library
ii  libbz2-1.0:amd64                    1.0.6-7                           amd64        high-quality block-sorting file compressor library - runtime
ii  libc-bin                            2.21-0ubuntu4                     amd64        GNU C Library: Binaries
ii  libc6:amd64                         2.21-0ubuntu4                     amd64        GNU C Library: Shared libraries
ii  libcairo-gobject2:amd64             1.14.2-1ubuntu1                   amd64        Cairo 2D vector graphics library (GObject library)
ii  libcairo2:amd64                     1.14.2-1ubuntu1                   amd64        Cairo 2D vector graphics library
ii  libcap-ng0:amd64                    0.7.4-2                           amd64        An alternate POSIX capabilities library
ii  libcap2:amd64                       1:2.24-6                          amd64        POSIX 1003.1e capabilities (library)
ii  libcap2-bin                         1:2.24-6                          amd64        POSIX 1003.1e capabilities (utilities)
ii  libcdio-cdda1                       0.83-4.2                          amd64        library to read and control digital audio CDs
ii  libcdio-paranoia1                   0.83-4.2                          amd64        library to read digital audio CDs with error correction
ii  libcdio13                           0.83-4.2                          amd64        library to read and control CD-ROM
ii  libcgi-fast-perl                    1:2.04-1                          all          CGI subclass for work with FCGI
ii  libcgi-pm-perl                      4.09-2                            all          module for Common Gateway Interface applications
ii  libck-connector0:amd64              0.4.6-5                           amd64        ConsoleKit libraries
ii  libclass-accessor-perl              0.34-1                            all          Perl module that automatically generates accessors
ii  libclass-c3-perl                    0.26-1                            all          pragma for using the C3 method resolution order
ii  libclass-c3-xs-perl                 0.13-2build1                      amd64        Perl module to accelerate Class::C3
ii  libcloog-isl4:amd64                 0.18.2-3                          amd64        Chunky Loop Generator (runtime library)
ii  libcolord2:amd64                    1.2.8-0ubuntu1                    amd64        system service to manage device colour profiles -- runtime
ii  libcomerr2:amd64                    1.42.12-1ubuntu2                  amd64        common error description library
ii  libconfuse-common                   2.7-5                             all          Common files for libConfuse
ii  libconfuse0:amd64                   2.7-5                             amd64        Library for parsing configuration files
ii  libcpan-meta-perl                   2.142690-1                        all          Perl module to access CPAN distributions metadata
ii  libcryptsetup4                      2:1.6.1-1ubuntu7                  amd64        disk encryption support - shared library
ii  libcups2:amd64                      2.0.2-1ubuntu3.2                  amd64        Common UNIX Printing System(tm) - Core library
ii  libcurl3-gnutls:amd64               7.38.0-3ubuntu2.2                 amd64        easy-to-use client-side URL transfer library (GnuTLS flavour)
ii  libcwidget3:amd64                   0.5.17-2ubuntu1                   amd64        high-level terminal interface library for C++ (runtime files)
ii  libdata-optlist-perl                0.109-1                           all          module to parse and validate simple name/value option pairs
ii  libdata-section-perl                0.200006-1                        all          module to read chunks of data from a module's DATA section
ii  libdatrie1:amd64                    0.2.8-1                           amd64        Double-array trie library
ii  libdb5.3:amd64                      5.3.28-9                          amd64        Berkeley v5.3 Database Libraries [runtime]
ii  libdbus-1-3:amd64                   1.8.12-1ubuntu5                   amd64        simple interprocess messaging system (library)
ii  libdbus-glib-1-2:amd64              0.102-1                           amd64        simple interprocess messaging system (GLib-based shared library)
ii  libdconf1:amd64                     0.22.0-1                          amd64        simple configuration storage system - runtime library
ii  libdebconfclient0:amd64             0.192ubuntu1                      amd64        Debian Configuration Management System (C-implementation library)
ii  libdevmapper1.02.1:amd64            2:1.02.90-2ubuntu1                amd64        Linux Kernel Device Mapper userspace library
ii  libdiscover2                        2.1.2-7ubuntu1                    amd64        hardware identification library
ii  libdns-export100                    1:9.9.5.dfsg-9ubuntu0.3           amd64        Exported DNS Shared Library
ii  libdns100                           1:9.9.5.dfsg-9ubuntu0.3           amd64        DNS Shared Library used by BIND
ii  libdrm-intel1:amd64                 2.4.60-2                          amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64               2.4.60-2                          amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                2.4.60-2                          amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2:amd64                       2.4.60-2                          amd64        Userspace interface to kernel DRM services -- runtime
ii  libedit2:amd64                      3.1-20140620-2                    amd64        BSD editline and history libraries
ii  libegl1-mesa:amd64                  10.5.9-2ubuntu1~vivid2            amd64        free implementation of the EGL API -- runtime
ii  libelf1:amd64                       0.160-0ubuntu3                    amd64        library to read and write ELF files
ii  libepoxy0                           1.2-1                             amd64        OpenGL function pointer management library
ii  libestr0                            0.1.9-1.1build1                   amd64        Helper functions for handling strings (lib)
ii  libev4                              1:4.15-3                          amd64        high-performance event loop library modelled after libevent
ii  libevdev2:amd64                     1.3.2+dfsg-2                      amd64        wrapper library for evdev devices
ii  libexif12:amd64                     0.6.21-2                          amd64        library to parse EXIF files
ii  libexpat1:amd64                     2.1.0-6ubuntu1.1                  amd64        XML parsing C library - runtime library
ii  libfcgi-perl                        0.77-1                            amd64        helper module for FastCGI
ii  libffi6:amd64                       3.2.1-2                           amd64        Foreign Function Interface library runtime
ii  libfm-data                          1.2.3-0ubuntu1                    all          file management support (common data)
ii  libfm-extra4                        1.2.3-0ubuntu1                    amd64        file management support (extra library)
ii  libfm-gtk-data                      1.2.3-0ubuntu1                    all          file management support (GTK+ library common data)
ii  libfm-gtk4                          1.2.3-0ubuntu1                    amd64        file management support (GTK+ 2.0 GUI library)
ii  libfm4                              1.2.3-0ubuntu1                    amd64        file management support (core library)
ii  libfontconfig1:amd64                2.11.1-0ubuntu6                   amd64        generic font configuration library - runtime
ii  libfontenc1:amd64                   1:1.1.2-1                         amd64        X11 font encoding library
ii  libfreetype6:amd64                  2.5.2-2ubuntu3.1                  amd64        FreeType 2 font engine, shared library files
ii  libfribidi0:amd64                   0.19.6-3                          amd64        Free Implementation of the Unicode BiDi algorithm
ii  libfuse2:amd64                      2.9.2-4ubuntu4.15.04.1            amd64        Filesystem in Userspace (library)
ii  libgbm1:amd64                       10.5.9-2ubuntu1~vivid2            amd64        generic buffer management API -- runtime
ii  libgcc1:amd64                       1:5.1~rc1-0ubuntu1                amd64        GCC support library
ii  libgck-1-0:amd64                    3.14.0-2build1                    amd64        Glib wrapper library for PKCS#11 - runtime
ii  libgcr-3-common                     3.14.0-2build1                    all          Library for Crypto UI related tasks - common files
ii  libgcr-base-3-1:amd64               3.14.0-2build1                    amd64        Library for Crypto related tasks
ii  libgcrypt20:amd64                   1.6.2-4ubuntu2                    amd64        LGPL Crypto library - runtime library
ii  libgd3:amd64                        2.1.0-5                           amd64        GD Graphics Library
ii  libgdbm3:amd64                      1.8.3-13.1                        amd64        GNU dbm database routines (runtime version)
ii  libgdk-pixbuf2.0-0:amd64            2.31.3-1ubuntu0.1                 amd64        GDK Pixbuf library
ii  libgdk-pixbuf2.0-common             2.31.3-1ubuntu0.1                 all          GDK Pixbuf library - data files
ii  libgeoip1:amd64                     1.6.3-2                           amd64        non-DNS IP-to-country resolver library
ii  libgif4:amd64                       4.1.6-11                          amd64        library for GIF images (library)
ii  libgirepository-1.0-1:amd64         1.42.0-2.2                        amd64        Library for handling GObject introspection data (runtime library)
ii  libgl1-mesa-dri:amd64               10.5.9-2ubuntu1~vivid2            amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64               10.5.9-2ubuntu1~vivid2            amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                 10.5.9-2ubuntu1~vivid2            amd64        free implementation of the GL API -- shared library
ii  libglib2.0-0:amd64                  2.44.1-1ubuntu1                   amd64        GLib library of C routines
ii  libglib2.0-data                     2.44.1-1ubuntu1                   all          Common files for GLib library
ii  libgmp10:amd64                      2:6.0.0+dfsg-6ubuntu1             amd64        Multiprecision arithmetic library
ii  libgnutls-deb0-28:amd64             3.3.8-3ubuntu3.1                  amd64        GNU TLS library - main runtime library
ii  libgnutls-openssl27:amd64           3.3.8-3ubuntu3.1                  amd64        GNU TLS library - OpenSSL wrapper
ii  libgpg-error0:amd64                 1.17-3ubuntu1                     amd64        library for common error values and messages in GnuPG components
ii  libgphoto2-6:amd64                  2.5.4-1.1ubuntu1                  amd64        gphoto2 digital camera library
ii  libgphoto2-port10:amd64             2.5.4-1.1ubuntu1                  amd64        gphoto2 digital camera port library
ii  libgraphite2-3:amd64                1.2.4-3ubuntu1                    amd64        Font rendering engine for Complex Scripts -- library
ii  libgssapi-krb5-2:amd64              1.12.1+dfsg-18                    amd64        MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libgssapi3-heimdal:amd64            1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - GSSAPI support library
ii  libgtk-3-0:amd64                    3.14.13-0ubuntu1                  amd64        GTK+ graphical user interface library
ii  libgtk-3-common                     3.14.13-0ubuntu1                  all          common files for the GTK+ graphical user interface library
ii  libgtk2.0-0:amd64                   2.24.27-0ubuntu1                  amd64        GTK+ graphical user interface library
ii  libgtk2.0-common                    2.24.27-0ubuntu1                  all          common files for the GTK+ graphical user interface library
ii  libgudev-1.0-0:amd64                1:219-7ubuntu6                    amd64        GObject-based wrapper library for libudev
ii  libharfbuzz0b:amd64                 0.9.37-1                          amd64        OpenType text shaping engine (shared library)
ii  libhcrypto4-heimdal:amd64           1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - crypto library
ii  libheimbase1-heimdal:amd64          1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - Base library
ii  libheimntlm0-heimdal:amd64          1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - NTLM support library
ii  libhogweed2:amd64                   2.7.1-5                           amd64        low level cryptographic library (public-key cryptos)
ii  libhx509-5-heimdal:amd64            1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - X509 support library
ii  libice6:amd64                       2:1.0.9-1                         amd64        X11 Inter-Client Exchange library
ii  libicu52:amd64                      52.1-8ubuntu0.2                   amd64        International Components for Unicode
ii  libid3tag0                          0.15.1b-11                        amd64        ID3 tag reading library from the MAD project
ii  libidn11:amd64                      1.28-1ubuntu2                     amd64        GNU Libidn library, implementation of IETF IDN specifications
ii  libimlib2                           1.4.6-2                           amd64        image loading, rendering, saving library
ii  libimobiledevice4:amd64             1.1.6+dfsg-3.1                    amd64        Library for communicating with the iPhone and iPod Touch
ii  libio-string-perl                   1.08-3                            all          Emulate IO::File interface for in-core strings
ii  libirs-export91                     1:9.9.5.dfsg-9ubuntu0.3           amd64        Exported IRS Shared Library
ii  libisc-export95                     1:9.9.5.dfsg-9ubuntu0.3           amd64        Exported ISC Shared Library
ii  libisc95                            1:9.9.5.dfsg-9ubuntu0.3           amd64        ISC Shared Library used by BIND
ii  libisccc90                          1:9.9.5.dfsg-9ubuntu0.3           amd64        Command Channel Library used by BIND
ii  libisccfg-export90                  1:9.9.5.dfsg-9ubuntu0.3           amd64        Exported ISC CFG Shared Library
ii  libisccfg90                         1:9.9.5.dfsg-9ubuntu0.3           amd64        Config File Handling Library used by BIND
ii  libisl13:amd64                      0.14-1                            amd64        manipulating sets and relations of integer points bounded by linear constraints
ii  libiw30:amd64                       30~pre9-8ubuntu1                  amd64        Wireless tools - library
ii  libjasper1:amd64                    1.900.1-debian1-2.4               amd64        JasPer JPEG-2000 runtime library
ii  libjbig0:amd64                      2.1-3.1                           amd64        JBIGkit libraries
ii  libjpeg-turbo8:amd64                1.3.0-0ubuntu2                    amd64        IJG JPEG compliant runtime library.
ii  libjpeg8:amd64                      8c-2ubuntu8                       amd64        Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjson-c2:amd64                    0.11-4ubuntu2                     amd64        JSON manipulation library - shared library
ii  libjson-glib-1.0-0:amd64            1.0.2-1                           amd64        GLib JSON manipulation library
ii  libjson-glib-1.0-common             1.0.2-1                           all          GLib JSON manipulation library (common files)
ii  libk5crypto3:amd64                  1.12.1+dfsg-18                    amd64        MIT Kerberos runtime libraries - Crypto Library
ii  libkeyutils1:amd64                  1.5.9-5ubuntu1                    amd64        Linux Key Management Utilities (library)
ii  libklibc                            2.0.3-0ubuntu1                    amd64        minimal libc subset for use with initramfs
ii  libkmod2:amd64                      18-3ubuntu1                       amd64        libkmod shared library
ii  libkrb5-26-heimdal:amd64            1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - libraries
ii  libkrb5-3:amd64                     1.12.1+dfsg-18                    amd64        MIT Kerberos runtime libraries
ii  libkrb5support0:amd64               1.12.1+dfsg-18                    amd64        MIT Kerberos runtime libraries - Support library
ii  liblcms2-2:amd64                    2.6-3ubuntu2                      amd64        Little CMS 2 color management library
ii  libldap-2.4-2:amd64                 2.4.31-1+nmu2ubuntu12.3           amd64        OpenLDAP libraries
ii  libldb1:amd64                       1:1.1.18-1                        amd64        LDAP-like embedded database - shared library
ii  libllvm3.6:amd64                    1:3.6-2ubuntu1                    amd64        Modular compiler and toolchain technologies, runtime library
ii  liblocale-gettext-perl              1.05-8build1                      amd64        module using libc functions for internationalization in Perl
ii  liblockfile-bin                     1.09-6ubuntu1                     amd64        support binaries for and cli utilities based on liblockfile
ii  liblockfile1:amd64                  1.09-6ubuntu1                     amd64        NFS-safe locking library
ii  liblog-message-perl                 0.8-1                             all          powerful and flexible message logging mechanism
ii  liblog-message-simple-perl          0.10-2                            all          simplified interface to Log::Message
ii  libltdl7:amd64                      2.4.2-1.11                        amd64        System independent dlopen wrapper for GNU libtool
ii  liblwres90                          1:9.9.5.dfsg-9ubuntu0.3           amd64        Lightweight Resolver Library used by BIND
ii  liblzma5:amd64                      5.1.1alpha+20120614-2ubuntu2      amd64        XZ-format compression library
ii  liblzo2-2:amd64                     2.08-1.2                          amd64        data compression library
ii  libmagic1:amd64                     1:5.20-1ubuntu2                   amd64        File type determination library using "magic" numbers
ii  libmenu-cache-bin                   1.0.0-1                           amd64        LXDE implementation of the freedesktop Menu's cache (libexec)
ii  libmenu-cache3:amd64                1.0.0-1                           amd64        LXDE implementation of the freedesktop Menu's cache
ii  libmirclient8:amd64                 0.12.1+15.04.20150324-0ubuntu1    amd64        Display server for Ubuntu - client library
ii  libmircommon3:amd64                 0.12.1+15.04.20150324-0ubuntu1    amd64        Display server for Ubuntu - shared library
ii  libmirprotobuf0:amd64               0.12.1+15.04.20150324-0ubuntu1    amd64        Display server for Ubuntu - RPC definitions
ii  libmodule-build-perl                0.421000-2                        all          framework for building and installing Perl modules
ii  libmodule-pluggable-perl            5.1-1                             all          module for giving  modules the ability to have plugins
ii  libmodule-signature-perl            0.73-1ubuntu0.15.04.1             all          module to manipulate CPAN SIGNATURE files
ii  libmount1:amd64                     2.25.2-4ubuntu3                   amd64        device mounting library
ii  libmpc3:amd64                       1.0.3-1                           amd64        multiple precision complex floating-point library
ii  libmpdec2:amd64                     2.4.1-1                           amd64        library for decimal floating point arithmetic (runtime library)
ii  libmpfr4:amd64                      3.1.2-3                           amd64        multiple precision floating-point computation
ii  libmro-compat-perl                  0.12-1                            all          mro::* interface compatibility for Perls < 5.9.5
ii  libmtdev1:amd64                     1.1.5-1ubuntu2                    amd64        Multitouch Protocol Translation Library - shared library
ii  libmtp-common                       1.1.8-1ubuntu2                    all          Media Transfer Protocol (MTP) common files
ii  libmtp9:amd64                       1.1.8-1ubuntu2                    amd64        Media Transfer Protocol (MTP) library
ii  libncurses5:amd64                   5.9+20140712-2ubuntu2             amd64        shared libraries for terminal handling
ii  libncursesw5:amd64                  5.9+20140712-2ubuntu2             amd64        shared libraries for terminal handling (wide character support)
ii  libnettle4:amd64                    2.7.1-5                           amd64        low level cryptographic library (symmetric and one-way cryptos)
ii  libnewt0.52:amd64                   0.52.15-3ubuntu1                  amd64        Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnfnetlink0:amd64                 1.0.1-3                           amd64        Netfilter netlink library
ii  libnih-dbus1:amd64                  1.0.3-4ubuntu27                   amd64        NIH D-Bus Bindings Library
ii  libnih1:amd64                       1.0.3-4ubuntu27                   amd64        NIH Utility Library
ii  libnl-3-200:amd64                   3.2.24-2                          amd64        library for dealing with netlink sockets
ii  libnl-genl-3-200:amd64              3.2.24-2                          amd64        library for dealing with netlink sockets - generic netlink
ii  libntdb1:amd64                      1.0-5                             amd64        New Trivial Database - shared library
ii  libnuma1:amd64                      2.0.10-1ubuntu2.1                 amd64        Libraries for controlling NUMA policy
ii  libp11-kit0:amd64                   0.20.7-1                          amd64        Library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpackage-constants-perl           0.04-1                            all          List constants defined in a package
ii  libpam-modules:amd64                1.1.8-3.1ubuntu3                  amd64        Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                  1.1.8-3.1ubuntu3                  amd64        Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                      1.1.8-3.1ubuntu3                  all          Runtime support for the PAM library
ii  libpam-systemd:amd64                219-7ubuntu6                      amd64        system and service manager - PAM module
ii  libpam0g:amd64                      1.1.8-3.1ubuntu3                  amd64        Pluggable Authentication Modules library
ii  libpango-1.0-0:amd64                1.36.8-3                          amd64        Layout and rendering of internationalized text
ii  libpangocairo-1.0-0:amd64           1.36.8-3                          amd64        Layout and rendering of internationalized text
ii  libpangoft2-1.0-0:amd64             1.36.8-3                          amd64        Layout and rendering of internationalized text
ii  libparams-util-perl                 1.07-2build1                      amd64        Perl extension for simple stand-alone param checking functions
ii  libparse-debianchangelog-perl       1.2.0-1.1                         all          parse Debian changelogs and output them in other formats
ii  libparted2:amd64                    3.2-7ubuntu1                      amd64        disk partition manipulator - shared library
ii  libpcap0.8:amd64                    1.6.2-2                           amd64        system interface for user-level packet capture
ii  libpci3:amd64                       1:3.2.1-1ubuntu10                 amd64        Linux PCI Utilities (shared library)
ii  libpciaccess0:amd64                 0.13.2-3build1                    amd64        Generic PCI access library for X
ii  libpcre3:amd64                      2:8.35-3.3ubuntu1.1               amd64        Perl 5 Compatible Regular Expression Library - runtime files
ii  libperl5.20                         5.20.2-2                          amd64        shared Perl library
ii  libpipeline1:amd64                  1.4.0-1                           amd64        pipeline manipulation library
ii  libpixman-1-0:amd64                 0.32.6-3                          amd64        pixel-manipulation library for X and cairo
ii  libplist2:amd64                     1.11-3build1                      amd64        Library for handling Apple binary and XML property lists
ii  libplymouth4:amd64                  0.9.0-0ubuntu9                    amd64        graphical boot animation and logger - shared libraries
ii  libpng12-0:amd64                    1.2.51-0ubuntu3                   amd64        PNG library - runtime
ii  libpod-latex-perl                   0.61-1                            all          module to convert Pod data to formatted LaTeX
ii  libpod-readme-perl                  0.11-1                            all          Perl module to convert POD to README file
ii  libpolkit-agent-1-0:amd64           0.105-8ubuntu3                    amd64        PolicyKit Authentication Agent API
ii  libpolkit-backend-1-0:amd64         0.105-8ubuntu3                    amd64        PolicyKit backend API
ii  libpolkit-gobject-1-0:amd64         0.105-8ubuntu3                    amd64        PolicyKit Authorization API
ii  libpopt0:amd64                      1.16-10                           amd64        lib for parsing cmdline parameters
ii  libprocps3:amd64                    1:3.3.9-1ubuntu8                  amd64        library for accessing process information from /proc
ii  libprotobuf9:amd64                  2.6.1-1                           amd64        protocol buffers C++ library
ii  libproxy1:amd64                     0.4.11-4ubuntu2                   amd64        automatic proxy configuration management library (shared)
ii  libpython-stdlib:amd64              2.7.9-1                           amd64        interactive high-level object-oriented language (default python version)
ii  libpython2.7:amd64                  2.7.9-2ubuntu3                    amd64        Shared Python runtime library (version 2.7)
ii  libpython2.7-minimal:amd64          2.7.9-2ubuntu3                    amd64        Minimal subset of the Python language (version 2.7)
ii  libpython2.7-stdlib:amd64           2.7.9-2ubuntu3                    amd64        Interactive high-level object-oriented language (standard library, version 2.7)
ii  libpython3-stdlib:amd64             3.4.3-1                           amd64        interactive high-level object-oriented language (default python3 version)
ii  libpython3.4-minimal:amd64          3.4.3-3                           amd64        Minimal subset of the Python language (version 3.4)
ii  libpython3.4-stdlib:amd64           3.4.3-3                           amd64        Interactive high-level object-oriented language (standard library, version 3.4)
ii  libreadline6:amd64                  6.3-8ubuntu1                      amd64        GNU readline and history libraries, run-time libraries
ii  libregexp-common-perl               2013031301-1                      all          module with common regular expressions
ii  librest-0.7-0:amd64                 0.7.92-3                          amd64        REST service access library
ii  libroken18-heimdal:amd64            1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - roken support library
ii  librtmp1:amd64                      2.4+20131018.git79459a2-5         amd64        toolkit for RTMP streams (shared library)
ii  libsasl2-2:amd64                    2.1.26.dfsg1-13                   amd64        Cyrus SASL - authentication abstraction library
ii  libsasl2-modules:amd64              2.1.26.dfsg1-13                   amd64        Cyrus SASL - pluggable authentication modules
ii  libsasl2-modules-db:amd64           2.1.26.dfsg1-13                   amd64        Cyrus SASL - pluggable authentication modules (DB)
ii  libsecret-1-0:amd64                 0.18-1ubuntu2                     amd64        Secret store
ii  libsecret-common                    0.18-1ubuntu2                     all          Secret store (common files)
ii  libselinux1:amd64                   2.3-2                             amd64        SELinux runtime shared libraries
ii  libsemanage-common                  2.3-1build1                       all          Common files for SELinux policy management libraries
ii  libsemanage1:amd64                  2.3-1build1                       amd64        SELinux policy management library
ii  libsepol1:amd64                     2.3-2                             amd64        SELinux library for manipulating binary security policies
ii  libsigc++-2.0-0c2a:amd64            2.4.0-1                           amd64        type-safe Signal Framework for C++ - runtime
ii  libslang2:amd64                     2.3.0-2ubuntu1                    amd64        S-Lang programming library - runtime version
ii  libsm6:amd64                        2:1.2.2-1                         amd64        X11 Session Management library
ii  libsmartcols1:amd64                 2.25.2-4ubuntu3                   amd64        smart column output alignment library
ii  libsmbclient:amd64                  2:4.1.13+dfsg-4ubuntu3            amd64        shared library for communication with SMB/CIFS servers
ii  libsoftware-license-perl            0.103010-3                        all          module providing templated software licenses
ii  libsoup-gnome2.4-1:amd64            2.49.92-1                         amd64        HTTP library implementation in C -- GNOME support library
ii  libsoup2.4-1:amd64                  2.49.92-1                         amd64        HTTP library implementation in C -- Shared library
ii  libsqlite3-0:amd64                  3.8.7.4-1ubuntu0.1                amd64        SQLite 3 shared library
ii  libss2:amd64                        1.42.12-1ubuntu2                  amd64        command-line interface parsing library
ii  libssl1.0.0:amd64                   1.0.1f-1ubuntu11.4                amd64        Secure Sockets Layer toolkit - shared libraries
ii  libstartup-notification0:amd64      0.12-4                            amd64        library for program launch feedback (shared library)
ii  libstdc++6:amd64                    4.9.2-10ubuntu13                  amd64        GNU Standard C++ Library v3
ii  libsub-exporter-perl                0.986-1                           all          sophisticated exporter for custom-built routines
ii  libsub-install-perl                 0.928-1                           all          module for installing subroutines into packages easily
ii  libsub-name-perl                    0.12-1                            amd64        module for assigning a new name to referenced sub
ii  libsystemd0:amd64                   219-7ubuntu6                      amd64        systemd utility library
ii  libtalloc2:amd64                    2.1.1-2                           amd64        hierarchical pool based memory allocator
ii  libtasn1-6:amd64                    4.2-2ubuntu1.1                    amd64        Manage ASN.1 structures (runtime)
ii  libtdb1:amd64                       1.3.4-1                           amd64        Trivial Database - shared library
ii  libterm-ui-perl                     0.42-1                            all          Term::ReadLine UI made easy
ii  libtevent0:amd64                    0.9.22-1                          amd64        talloc-based event loop library - shared library
ii  libtext-charwidth-perl              0.04-7build4                      amd64        get display widths of characters on the terminal
ii  libtext-iconv-perl                  1.7-5build3                       amd64        converts between character sets in Perl
ii  libtext-soundex-perl                3.4-1build2                       amd64        implementation of the soundex algorithm
ii  libtext-template-perl               1.46-1                            all          perl module to process text templates
ii  libtext-wrapi18n-perl               0.06-7                            all          internationalized substitute of Text::Wrap
ii  libthai-data                        0.1.21-1                          all          Data files for Thai language support library
ii  libthai0:amd64                      0.1.21-1                          amd64        Thai language support library
ii  libtiff5:amd64                      4.0.3-12.3ubuntu2                 amd64        Tag Image File Format (TIFF) library
ii  libtimedate-perl                    2.3000-2                          all          collection of modules to manipulate date/time information
ii  libtinfo5:amd64                     5.9+20140712-2ubuntu2             amd64        shared low-level terminfo library for terminal handling
ii  libudev1:amd64                      219-7ubuntu6                      amd64        libudev shared library
ii  libudisks2-0:amd64                  2.1.5-1                           amd64        GObject based library to access udisks2
ii  libusb-0.1-4:amd64                  2:0.1.12-25                       amd64        userspace USB programming library
ii  libusb-1.0-0:amd64                  2:1.0.19-1                        amd64        userspace USB programming library
ii  libusbmuxd2:amd64                   1.0.9-1                           amd64        USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libustr-1.0-1:amd64                 1.0.4-3ubuntu2                    amd64        Micro string library: shared library
ii  libutempter0                        1.1.5-4build1                     amd64        A privileged helper for utmp/wtmp updates (runtime)
ii  libuuid1:amd64                      2.25.2-4ubuntu3                   amd64        Universally Unique ID library
ii  libvpx1:amd64                       1.3.0-3ubuntu1                    amd64        VP8 and VP9 video codec (shared library)
ii  libwayland-client0:amd64            1.7.0-0ubuntu1                    amd64        wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64            1.7.0-0ubuntu1                    amd64        wayland compositor infrastructure - cursor library
ii  libwayland-server0:amd64            1.7.0-0ubuntu1                    amd64        wayland compositor infrastructure - server library
ii  libwbclient0:amd64                  2:4.1.13+dfsg-4ubuntu3            amd64        Samba winbind client library
ii  libwind0-heimdal:amd64              1.6~rc2+dfsg-9                    amd64        Heimdal Kerberos - stringprep implementation
ii  libwrap0:amd64                      7.6.q-25                          amd64        Wietse Venema's TCP wrappers library
ii  libx11-6:amd64                      2:1.6.2-2ubuntu2                  amd64        X11 client-side library
ii  libx11-data                         2:1.6.2-2ubuntu2                  all          X11 client-side library
ii  libx11-xcb1:amd64                   2:1.6.2-2ubuntu2                  amd64        Xlib/XCB interface library
ii  libxapian22                         1.2.19-1                          amd64        Search engine library
ii  libxau6:amd64                       1:1.0.8-1                         amd64        X11 authorisation library
ii  libxaw7:amd64                       2:1.0.12-2                        amd64        X11 Athena Widget library
ii  libxcb-cursor0:amd64                0.1.1-3ubuntu1                    amd64        utility libraries for X C Binding -- cursor
ii  libxcb-dpms0:amd64                  1.10-2ubuntu1                     amd64        X C Binding, dpms extension
ii  libxcb-dri2-0:amd64                 1.10-2ubuntu1                     amd64        X C Binding, dri2 extension
ii  libxcb-dri3-0:amd64                 1.10-2ubuntu1                     amd64        X C Binding, dri3 extension
ii  libxcb-glx0:amd64                   1.10-2ubuntu1                     amd64        X C Binding, glx extension
ii  libxcb-icccm4:amd64                 0.4.1-1ubuntu1                    amd64        utility libraries for X C Binding -- icccm
ii  libxcb-image0:amd64                 0.4.0-1                           amd64        utility libraries for X C Binding -- image
ii  libxcb-keysyms1:amd64               0.4.0-1                           amd64        utility libraries for X C Binding -- keysyms
ii  libxcb-present0:amd64               1.10-2ubuntu1                     amd64        X C Binding, present extension
ii  libxcb-randr0:amd64                 1.10-2ubuntu1                     amd64        X C Binding, randr extension
ii  libxcb-render-util0:amd64           0.3.9-1                           amd64        utility libraries for X C Binding -- render-util
ii  libxcb-render0:amd64                1.10-2ubuntu1                     amd64        X C Binding, render extension
ii  libxcb-shape0:amd64                 1.10-2ubuntu1                     amd64        X C Binding, shape extension
ii  libxcb-shm0:amd64                   1.10-2ubuntu1                     amd64        X C Binding, shm extension
ii  libxcb-sync1:amd64                  1.10-2ubuntu1                     amd64        X C Binding, sync extension
ii  libxcb-util0:amd64                  0.3.8-3                           amd64        utility libraries for X C Binding -- atom, aux and event
ii  libxcb-xfixes0:amd64                1.10-2ubuntu1                     amd64        X C Binding, xfixes extension
ii  libxcb-xinerama0:amd64              1.10-2ubuntu1                     amd64        X C Binding, xinerama extension
ii  libxcb-xkb1:amd64                   1.10-2ubuntu1                     amd64        X C Binding, XKEYBOARD extension
ii  libxcb1:amd64                       1.10-2ubuntu1                     amd64        X C Binding
ii  libxcomposite1:amd64                1:0.4.4-1                         amd64        X11 Composite extension library
ii  libxcursor1:amd64                   1:1.1.14-1                        amd64        X cursor management library
ii  libxdamage1:amd64                   1:1.1.4-2                         amd64        X11 damaged region extension library
ii  libxdmcp6:amd64                     1:1.1.1-1build1                   amd64        X11 Display Manager Control Protocol library
ii  libxext6:amd64                      2:1.3.3-1                         amd64        X11 miscellaneous extension library
ii  libxfixes3:amd64                    1:5.0.1-2                         amd64        X11 miscellaneous 'fixes' extension library
ii  libxfont1:amd64                     1:1.4.99.901-1ubuntu1             amd64        X11 font rasterisation library
ii  libxft2:amd64                       2.3.2-1                           amd64        FreeType-based font drawing library for X
ii  libxi6:amd64                        2:1.7.4-1                         amd64        X11 Input extension library
ii  libxinerama1:amd64                  2:1.1.3-1                         amd64        X11 Xinerama extension library
ii  libxkbcommon-x11-0:amd64            0.5.0-1~~vivid1                   amd64        library to create keymaps with the XKB X11 protocol
ii  libxkbcommon0:amd64                 0.5.0-1~~vivid1                   amd64        library interface to the XKB compiler - shared library
ii  libxkbfile1:amd64                   1:1.0.8-1                         amd64        X11 keyboard file manipulation library
ii  libxml2:amd64                       2.9.2+dfsg1-3                     amd64        GNOME XML library
ii  libxmu6:amd64                       2:1.1.2-1                         amd64        X11 miscellaneous utility library
ii  libxmuu1:amd64                      2:1.1.2-1                         amd64        X11 miscellaneous micro-utility library
ii  libxpm4:amd64                       1:3.5.11-1                        amd64        X11 pixmap library
ii  libxrandr2:amd64                    2:1.4.2-1                         amd64        X11 RandR extension library
ii  libxrender1:amd64                   1:0.9.8-1build1                   amd64        X Rendering Extension client library
ii  libxshmfence1:amd64                 1.1-4                             amd64        X shared memory fences - shared library
ii  libxss1:amd64                       1:1.2.2-1                         amd64        X11 Screen Saver extension library
ii  libxt6:amd64                        1:1.1.4-1                         amd64        X11 toolkit intrinsics library
ii  libxtables10                        1.4.21-2ubuntu2                   amd64        netfilter xtables library
ii  libxtst6:amd64                      2:1.2.2-1                         amd64        X11 Testing -- Record extension library
ii  libxv1:amd64                        2:1.0.10-1                        amd64        X11 Video extension library
ii  libxxf86dga1:amd64                  2:1.1.4-1                         amd64        X11 Direct Graphics Access extension library
ii  libxxf86vm1:amd64                   1:1.1.3-1                         amd64        X11 XFree86 video mode extension library
ii  libyajl2:amd64                      2.1.0-2                           amd64        Yet Another JSON Library
ii  linux-firmware                      1.143.3                           all          Firmware for Linux kernel drivers
ii  linux-generic                       3.19.0.28.27                      amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-28             3.19.0-28.30                      all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic     3.19.0-28.30                      amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic               3.19.0.28.27                      amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-28-generic       3.19.0-28.30                      amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic 3.19.0-28.30                      amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                 3.19.0.28.27                      amd64        Generic Linux kernel image
ii  localepurge                         0.7.3.4                           all          reclaim disk space by removing unneeded localizations
ii  locales                             2.13+git20120306-19               all          common files for locale support
ii  lockfile-progs                      0.1.17                            amd64        Programs for locking and unlocking files and mailboxes
ii  login                               1:4.1.5.1-1.1ubuntu4              amd64        system login tools
ii  logrotate                           3.8.7-1ubuntu1                    amd64        Log rotation utility
ii  lsb-base                            4.1+Debian11ubuntu8               all          Linux Standard Base 4.1 init script functionality
ii  lsb-release                         4.1+Debian11ubuntu8               all          Linux Standard Base version reporting utility
ii  lshw                                02.17-1.1ubuntu1.1                amd64        information about hardware configuration
ii  lsof                                4.86+dfsg-1ubuntu2                amd64        Utility to list open files
ii  ltrace                              0.7.3-4ubuntu7                    amd64        Tracks runtime library calls in dynamically linked programs
ii  lxmenu-data                         0.1.4-1                           all          LXDE freedesktop.org menu specification
ii  makedev                             2.3.1-93ubuntu1                   all          creates device files in /dev
ii  man-db                              2.7.0.2-5                         amd64        on-line manual pager
ii  manpages                            3.74-1ubuntu1                     all          Manual pages about using a GNU/Linux system
ii  mawk                                1.3.3-17ubuntu2                   amd64        a pattern scanning and text processing language
ii  mime-support                        3.58ubuntu1                       all          MIME files 'mime.types' & 'mailcap', and support programs
ii  mir-client-platform-mesa2:amd64     0.12.1+15.04.20150324-0ubuntu1    amd64        Display server for Ubuntu - client platform library for Mesa
ii  mlocate                             0.26-1ubuntu2                     amd64        quickly find files on the filesystem based on their name
ii  module-init-tools                   18-3ubuntu1                       all          transitional dummy package (module-init-tools to kmod)
ii  mount                               2.25.2-4ubuntu3                   amd64        Tools for mounting and manipulating filesystems
ii  mountall                            2.54ubuntu1                       amd64        filesystem mounting tool
ii  mtr-tiny                            0.85-3                            amd64        Full screen ncurses traceroute tool
ii  multiarch-support                   2.21-0ubuntu4                     amd64        Transitional package to ensure multiarch compatibility
ii  nano                                2.2.6-3                           amd64        small, friendly text editor inspired by Pico
ii  ncurses-base                        5.9+20140712-2ubuntu2             all          basic terminal type definitions
ii  ncurses-bin                         5.9+20140712-2ubuntu2             amd64        terminal-related programs and man pages
ii  ncurses-term                        5.9+20140712-2ubuntu2             all          additional terminal type definitions
ii  net-tools                           1.60-26ubuntu1                    amd64        NET-3 networking toolkit
ii  netbase                             5.3                               all          Basic TCP/IP networking system
ii  netcat-openbsd                      1.105-7ubuntu1                    amd64        TCP/IP swiss army knife
ii  ntfs-3g                             1:2014.2.15AR.3-1ubuntu0.2        amd64        read/write NTFS driver for FUSE
ii  ntpdate                             1:4.2.6.p5+dfsg-3ubuntu6          amd64        client for setting system time from NTP servers
ii  openssh-client                      1:6.7p1-5ubuntu1.3                amd64        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                      1:6.7p1-5ubuntu1.3                amd64        secure shell (SSH) server, for secure access from remote machines
ii  openssh-sftp-server                 1:6.7p1-5ubuntu1.3                amd64        secure shell (SSH) sftp server module, for SFTP access from remote machines
ii  openssl                             1.0.1f-1ubuntu11.4                amd64        Secure Sockets Layer toolkit - cryptographic utility
ii  os-prober                           1.63ubuntu1                       amd64        utility to detect other OSes on a set of drives
ii  parted                              3.2-7ubuntu1                      amd64        disk partition manipulator
ii  passwd                              1:4.1.5.1-1.1ubuntu4              amd64        change and administer password and group data
ii  pciutils                            1:3.2.1-1ubuntu10                 amd64        Linux PCI Utilities
ii  pcmanfm                             1.2.3-1.1                         amd64        extremely fast and lightweight file manager
ii  perl                                5.20.2-2                          amd64        Larry Wall's Practical Extraction and Report Language
ii  perl-base                           5.20.2-2                          amd64        minimal Perl system
ii  perl-modules                        5.20.2-2                          all          Core Perl modules
ii  plymouth                            0.9.0-0ubuntu9                    amd64        graphical boot animation and logger - main package
ii  plymouth-theme-ubuntu-text          0.9.0-0ubuntu9                    amd64        graphical boot animation and logger - ubuntu-logo theme
ii  policykit-1                         0.105-8ubuntu3                    amd64        framework for managing administrative policies and privileges
ii  popularity-contest                  1.57ubuntu1                       all          Vote for your favourite packages automatically
ii  powermgmt-base                      1.31+nmu1                         all          Common utils and configs for power management
ii  ppp                                 2.4.6-3.1ubuntu1                  amd64        Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                           2.3.19ubuntu1                     all          A text menu based utility for configuring ppp
ii  pppoeconf                           1.21ubuntu1                       all          configures PPPoE/ADSL connections
ii  procps                              1:3.3.9-1ubuntu8                  amd64        /proc file system utilities
ii  psmisc                              22.21-2build1                     amd64        utilities that use the proc file system
ii  python                              2.7.9-1                           amd64        interactive high-level object-oriented language (default version)
ii  python-apt-common                   0.9.3.11build1                    all          Python interface to libapt-pkg (locales)
ii  python-minimal                      2.7.9-1                           amd64        minimal subset of the Python language (default version)
ii  python-talloc                       2.1.1-2                           amd64        hierarchical pool based memory allocator - Python bindings
ii  python2.7                           2.7.9-2ubuntu3                    amd64        Interactive high-level object-oriented language (version 2.7)
ii  python2.7-minimal                   2.7.9-2ubuntu3                    amd64        Minimal subset of the Python language (version 2.7)
ii  python3                             3.4.3-1                           amd64        interactive high-level object-oriented language (default python3 version)
ii  python3-apt                         0.9.3.11build1                    amd64        Python 3 interface to libapt-pkg
ii  python3-chardet                     2.3.0-1                           all          universal character encoding detector for Python3
ii  python3-commandnotfound             0.3ubuntu15.3                     all          Python 3 bindings for command-not-found.
ii  python3-dbus                        1.2.0-2build2                     amd64        simple interprocess messaging system (Python 3 interface)
ii  python3-distupgrade                 1:15.04.14.1                      all          manage release upgrades
ii  python3-gdbm:amd64                  3.4.3-1                           amd64        GNU dbm database support for Python 3.x
ii  python3-gi                          3.14.0-1                          amd64        Python 3 bindings for gobject-introspection libraries
ii  python3-minimal                     3.4.3-1                           amd64        minimal subset of the Python language (default python3 version)
ii  python3-pkg-resources               12.2-1                            all          Package Discovery and Resource Access using pkg_resources
ii  python3-requests                    2.4.3-6                           all          elegant and simple HTTP library for Python3, built for human beings
ii  python3-six                         1.9.0-1                           all          Python 2 and 3 compatibility library (Python 3 interface)
ii  python3-update-manager              1:15.04.7                         all          python 3.x module for update-manager
ii  python3-urllib3                     1.9.1-3                           all          HTTP library with thread-safe connection pooling for Python3
ii  python3.4                           3.4.3-3                           amd64        Interactive high-level object-oriented language (version 3.4)
ii  python3.4-minimal                   3.4.3-3                           amd64        Minimal subset of the Python language (version 3.4)
ii  readline-common                     6.3-8ubuntu1                      all          GNU readline and history libraries, common files
ii  rename                              0.20-3                            all          Perl extension for renaming multiple files
ii  resolvconf                          1.76ubuntu1                       all          name server information handler
ii  rsync                               3.1.1-3                           amd64        fast, versatile, remote (and local) file-copying tool
ii  rsyslog                             7.4.4-1ubuntu14                   amd64        reliable system and kernel logging daemon
ii  rxvt-unicode                        9.21-1                            amd64        RXVT-like terminal emulator with Unicode support
ii  samba-libs:amd64                    2:4.1.13+dfsg-4ubuntu3            amd64        Samba core libraries
ii  sed                                 4.2.2-4ubuntu1                    amd64        The GNU sed stream editor
ii  sensible-utils                      0.0.9                             all          Utilities for sensible alternative selection
ii  sgml-base                           1.26+nmu4ubuntu1                  all          SGML infrastructure and SGML catalog file support
ii  shared-mime-info                    1.3-1                             amd64        FreeDesktop.org shared MIME database and spec
ii  ssh-import-id                       4.1-0ubuntu1                      all          securely retrieve an SSH public key and install it locally
ii  strace                              4.8-1ubuntu5                      amd64        A system call tracer
ii  suckless-tools                      40-1                              amd64        simple commands for minimalistic window managers
ii  sudo                                1.8.9p5-1ubuntu5                  amd64        Provide limited super user privileges to specific users
ii  sur5r-keyring                       2015.02.08                        all          GnuPG keys of the debian.sur5r.net archive
ii  systemd                             219-7ubuntu6                      amd64        system and service manager
ii  systemd-sysv                        219-7ubuntu6                      amd64        system and service manager - SysV links
ii  sysv-rc                             2.88dsf-53.2ubuntu12              all          System-V-like runlevel change mechanism
ii  sysvinit-utils                      2.88dsf-53.2ubuntu12              amd64        System-V-like utilities
ii  tar                                 1.27.1-2                          amd64        GNU version of the tar archiving utility
ii  tasksel                             2.88ubuntu17                      all          Tool for selecting tasks for installation on Debian systems
ii  tasksel-data                        2.88ubuntu17                      all          Official tasks used for installation of Debian systems
ii  tcpd                                7.6.q-25                          amd64        Wietse Venema's TCP wrapper utilities
ii  tcpdump                             4.6.2-4ubuntu1                    amd64        command-line network traffic analyzer
ii  telnet                              0.17-36build2                     amd64        The telnet client
ii  time                                1.7-25                            amd64        GNU time program for measuring CPU resource usage
ii  tint2                               0.11+svn20121014-3                amd64        lightweight taskbar
ii  tzdata                              2015f-0ubuntu0.15.04              all          time zone and daylight-saving time data
ii  ubuntu-keyring                      2012.05.19                        all          GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                      1.334                             amd64        Minimal core of Ubuntu
ii  ubuntu-release-upgrader-core        1:15.04.14.1                      all          manage release upgrades
ii  ubuntu-standard                     1.334                             amd64        The Ubuntu standard system
ii  ucf                                 3.0030                            all          Update Configuration File(s): preserve user changes to config files
ii  udev                                219-7ubuntu6                      amd64        /dev/ and hotplug management daemon
ii  udisks2                             2.1.5-1                           amd64        D-Bus service to access and manipulate storage devices
ii  ufw                                 0.34~rc-0ubuntu5                  all          program for managing a Netfilter firewall
ii  update-manager-core                 1:15.04.7                         all          manage release upgrades
ii  ureadahead                          0.100.0-19                        amd64        Read required files in advance
ii  usbutils                            1:007-2ubuntu1                    amd64        Linux USB utilities
ii  util-linux                          2.25.2-4ubuntu3                   amd64        Miscellaneous system utilities
ii  uuid-runtime                        2.25.2-4ubuntu3                   amd64        runtime components for the Universally Unique ID library
ii  vim-common                          2:7.4.488-3ubuntu2                amd64        Vi IMproved - Common files
ii  vim-tiny                            2:7.4.488-3ubuntu2                amd64        Vi IMproved - enhanced vi editor - compact version
ii  wamerican                           7.1-1                             all          American English dictionary words for /usr/share/dict
ii  wbritish                            7.1-1                             all          British English dictionary words for /usr/share/dict
ii  wget                                1.16.1-1ubuntu1                   amd64        retrieves files from the web
ii  whiptail                            0.52.15-3ubuntu1                  amd64        Displays user-friendly dialog boxes from shell scripts
ii  wireless-regdb                      2014.11.18-1ubuntu1~ubuntu15.04.1 all          wireless regulatory database
ii  x11-common                          1:7.7+7ubuntu4                    all          X Window System (X.Org) infrastructure
ii  x11-utils                           7.7+2build1                       amd64        X11 utilities
ii  x11-xkb-utils                       7.7+1                             amd64        X11 XKB utilities
ii  x11-xserver-utils                   7.7+2ubuntu2                      amd64        X server utilities
ii  xauth                               1:1.0.9-1ubuntu2                  amd64        X authentication utility
ii  xbitmaps                            1.1.1-2                           all          Base X bitmaps
ii  xdg-user-dirs                       0.15-2ubuntu4                     amd64        tool to manage well known user directories
ii  xfonts-base                         1:1.0.4                           all          standard fonts for X
ii  xfonts-encodings                    1:1.0.4-2                         all          Encodings for X.Org fonts
ii  xfonts-utils                        1:7.7+2                           amd64        X Window System font utility programs
ii  xinit                               1.3.4-1                           amd64        X server initialisation tool
ii  xkb-data                            2.12-1ubuntu1                     all          X Keyboard Extension (XKB) configuration data
ii  xml-core                            0.13+nmu2                         all          XML infrastructure and XML catalog file support
ii  xserver-common                      2:1.17.1-0ubuntu3.1               all          common files used by various X servers
ii  xserver-xorg                        1:7.7+7ubuntu4                    amd64        X.Org X server
ii  xserver-xorg-core                   2:1.17.1-0ubuntu3.1               amd64        Xorg X server - core server
ii  xserver-xorg-input-all              1:7.7+7ubuntu4                    amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev            1:2.9.0-1ubuntu2                  amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse            1:1.9.1-1                         amd64        X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics        1.8.1-1ubuntu1                    amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse          1:13.0.0-1ubuntu1                 amd64        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom            1:0.25.0-0ubuntu1.1               amd64        X.Org X server -- Wacom input driver
ii  xterm                               312-1ubuntu1                      amd64        X terminal emulator
ii  zlib1g:amd64                        1:1.2.8.dfsg-2ubuntu1             amd64        compression library - runtime

```

here too [http://pastebin.com/aP6WTbmW](http://pastebin.com/aP6WTbmW)

Please some help would be appreciated.
Thanks in advance.

---

### Post by QIII on 2015-09-27
*Moved to **Virtualisation***

---

### Post by steeldriver on 2015-09-27
I would think you would need at least one actual xserver-xorg-video-xxx package, no?

Perhaps xserver-xorg-video-vmware - with xserver-xorg-video-vesa as a fallback?

---

### Post by leninberg on 2015-09-27
[COLOR=#000000]xserver-xorg-video-vmware did it!

Thank you very much
PS (do you think I should install [/COLOR][COLOR=#000000]xserver-xorg-video-vesa too?)[/COLOR]

---

