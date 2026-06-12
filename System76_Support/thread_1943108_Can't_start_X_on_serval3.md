---
title: "Can't start X on serval3"
date: 2012-03-19
forum: System76 Support
---

### Post by Vadi on 2012-03-19
Hi,

My laptops screen has been gradually failing - by refusing to display anything on the screen, for the past several months. Typically having the screen at a lower than 90* angle at boot helped, and after this, I could tilt the screen however much I wanted. A few days ago though it's been completely refusing to show with even this trick.

I thought it was a cable issue, as one of the cables that is a dual one has broken in it's top part (from all the use I guess). I tried getting them together this way and that, but it's been failing.

So I bought an external monitor instead, hoping just plugging it in would work. Unfortunately, it's not. I do have SSH access into the laptop setup, so not all is lost. It seems that X is not being started after it's booted, my graphics card (8600gtm) is not listed in lspci, and I can't start X either with startx or Xorg -configure:

> vadi@vadi-11:~$ xrandr
Can't open display 
vadi@vadi-11:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
vadi@vadi-11:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 kworker/0:0
    5 ?        00:00:00 kworker/u:0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 migration/1
    8 ?        00:00:00 kworker/1:0
    9 ?        00:00:00 ksoftirqd/1
   10 ?        00:00:00 kworker/0:1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 kworker/u:1
   15 ?        00:00:00 sync_supers
   16 ?        00:00:00 bdi-default
   17 ?        00:00:00 kintegrityd
   18 ?        00:00:00 kblockd
   19 ?        00:00:00 ata_sff
   20 ?        00:00:00 khubd
   21 ?        00:00:00 md
   22 ?        00:00:00 kworker/1:1
   23 ?        00:00:00 khungtaskd
   24 ?        00:00:00 kswapd0
   25 ?        00:00:00 ksmd
   26 ?        00:00:00 khugepaged
   27 ?        00:00:00 fsnotify_mark
   28 ?        00:00:00 ecryptfs-kthrea
   29 ?        00:00:00 crypto
   37 ?        00:00:00 kthrotld
   39 ?        00:00:00 kworker/0:2
   45 ?        00:00:00 kworker/u:2
   46 ?        00:00:00 scsi_eh_0
   47 ?        00:00:00 scsi_eh_1
   48 ?        00:00:00 kworker/u:3
   67 ?        00:00:00 kworker/1:2
  184 ?        00:00:00 scsi_eh_2
  192 ?        00:00:00 firewire
  205 ?        00:00:00 scsi_eh_3
  208 ?        00:00:00 scsi_eh_4
  242 ?        00:00:00 kworker/u:4
  266 ?        00:00:00 v86d
  315 ?        00:00:00 jbd2/sda1-8
  316 ?        00:00:00 ext4-dio-unwrit
  336 ?        00:00:00 mountall
  371 ?        00:00:00 upstart-udev-br
  373 ?        00:00:00 udevd
  503 ?        00:00:00 udevd
  504 ?        00:00:00 cfg80211
  549 ?        00:00:00 kmemstick
  561 ?        00:00:00 r592_io
  601 ?        00:00:00 iwl4965
  613 ?        00:00:00 udevd
  618 ?        00:00:00 kpsmoused
  642 ?        00:00:00 kworker/0:3
  657 ?        00:00:00 upstart-socket-
  761 ?        00:00:00 hd-audio0
 1077 ?        00:00:00 smbd
 1082 ?        00:00:00 sshd
 1085 ?        00:00:00 rsyslogd
 1103 ?        00:00:00 smbd
 1125 ?        00:00:00 dbus-daemon
 1139 ?        00:00:00 modem-manager
 1144 ?        00:00:00 NetworkManager
 1145 ?        00:00:00 avahi-daemon
 1146 ?        00:00:00 avahi-daemon
 1178 ?        00:00:00 polkitd
 1193 tty4     00:00:00 getty
 1196 tty5     00:00:00 getty
 1214 tty2     00:00:00 getty
 1215 tty3     00:00:00 getty
 1218 tty6     00:00:00 getty
 1263 ?        00:00:00 acpid
 1270 ?        00:00:00 irqbalance
 1271 ?        00:00:00 cron
 1272 ?        00:00:00 atd
 1293 ?        00:00:00 wpa_supplicant
 1295 ?        00:00:00 postgres
 1314 ?        00:00:00 postgres
 1315 ?        00:00:00 postgres
 1316 ?        00:00:00 postgres
 1317 ?        00:00:00 postgres
 1344 ?        00:00:00 cupsd
 1393 ?        00:00:00 hddtemp
 1416 ?        00:00:00 iprt
 1418 ?        00:00:00 flush-8:0
 1419 ?        00:00:00 flush-252:0
 1420 ?        00:00:00 flush-252:1
 1447 ?        00:00:00 winbindd
 1450 ?        00:00:00 winbindd
 1464 ?        00:00:00 trytond
 1477 ?        00:00:00 bluetoothd
 1483 ?        00:00:00 l2cap
 1488 ?        00:00:00 krfcommd
 1569 ?        00:00:00 dhclient
 1623 tty1     00:00:00 getty
 1662 ?        00:00:00 sshd
 1675 ?        00:00:00 nmbd
 1710 ?        00:00:00 winbindd
 1712 ?        00:00:00 sshd
 1722 ?        00:00:00 console-kit-dae
 2052 ?        00:00:00 sshd
 2053 pts/0    00:00:00 bash
 2176 ?        00:00:00 flush-ecryptfs-
 2235 pts/0    00:00:00 ps
vadi@vadi-11:~$ start
start: missing job name
Try `start --help' for more information.
vadi@vadi-11:~$ startx
xauth:  error in locking authority file /home/vadi/.Xauthority
xauth:  error in locking authority file /home/vadi/.Xauthority


X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux vadi-11 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=5a261133-b5a0-46a2-81ff-c1af4edb821e ro quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap vt.handoff=7
Build Date: 19 October 2011  05:21:26AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 19 13:59:55 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) FBDEV(0): Specified depth (24) is greater than the fbbpp (1)
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
xauth:  error in locking authority file /home/vadi/.Xauthority
vadi@vadi-11:~$ 
vadi@vadi-11:~$ cat /var/log/Xorg.0.log
[   185.524] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   185.524] X Protocol Version 11, Revision 0
[   185.524] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   185.524] Current Operating System: Linux vadi-11 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
[   185.524] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=5a261133-b5a0-46a2-81ff-c1af4edb821e ro quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap vt.handoff=7
[   185.524] Build Date: 19 October 2011  05:21:26AM
[   185.524] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   185.525] Current version of pixman: 0.22.2
[   185.525] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   185.525] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   185.525] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 19 13:59:55 2012
[   185.526] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   185.526] (==) No Layout section.  Using the first Screen section.
[   185.526] (==) No screen section available. Using defaults.
[   185.526] (**) |-->Screen "Default Screen Section" (0)
[   185.526] (**) |   |-->Monitor "<default monitor>"
[   185.527] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   185.527] (==) Automatically adding devices
[   185.527] (==) Automatically enabling devices
[   185.527] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   185.527] 	Entry deleted from font path.
[   185.527] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   185.527] 	Entry deleted from font path.
[   185.527] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   185.527] 	Entry deleted from font path.
[   185.527] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   185.527] 	Entry deleted from font path.
[   185.527] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   185.527] 	Entry deleted from font path.
[   185.527] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   185.527] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   185.527] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   185.527] (II) Loader magic: 0x7e0220
[   185.527] (II) Module ABI versions:
[   185.527] 	X.Org ANSI C Emulation: 0.4
[   185.527] 	X.Org Video Driver: 10.0
[   185.527] 	X.Org XInput driver : 12.3
[   185.527] 	X.Org Server Extension : 5.0
[   185.530] (II) Open ACPI successful (/var/run/acpid.socket)
[   185.530] (II) LoadModule: "extmod"
[   185.534] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   185.535] (II) Module extmod: vendor="X.Org Foundation"
[   185.535] 	compiled for 1.10.4, module version = 1.0.0
[   185.535] 	Module class: X.Org Server Extension
[   185.535] 	ABI class: X.Org Server Extension, version 5.0
[   185.535] (II) Loading extension MIT-SCREEN-SAVER
[   185.535] (II) Loading extension XFree86-VidModeExtension
[   185.535] (II) Loading extension XFree86-DGA
[   185.535] (II) Loading extension DPMS
[   185.535] (II) Loading extension XVideo
[   185.535] (II) Loading extension XVideo-MotionCompensation
[   185.535] (II) Loading extension X-Resource
[   185.535] (II) LoadModule: "dbe"
[   185.536] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   185.536] (II) Module dbe: vendor="X.Org Foundation"
[   185.536] 	compiled for 1.10.4, module version = 1.0.0
[   185.536] 	Module class: X.Org Server Extension
[   185.536] 	ABI class: X.Org Server Extension, version 5.0
[   185.536] (II) Loading extension DOUBLE-BUFFER
[   185.536] (II) LoadModule: "glx"
[   185.537] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   185.537] (II) Module glx: vendor="X.Org Foundation"
[   185.537] 	compiled for 1.10.4, module version = 1.0.0
[   185.537] 	ABI class: X.Org Server Extension, version 5.0
[   185.537] (==) AIGLX enabled
[   185.537] (II) Loading extension GLX
[   185.537] (II) LoadModule: "record"
[   185.538] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   185.538] (II) Module record: vendor="X.Org Foundation"
[   185.538] 	compiled for 1.10.4, module version = 1.13.0
[   185.538] 	Module class: X.Org Server Extension
[   185.538] 	ABI class: X.Org Server Extension, version 5.0
[   185.538] (II) Loading extension RECORD
[   185.538] (II) LoadModule: "dri"
[   185.539] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   185.540] (II) Module dri: vendor="X.Org Foundation"
[   185.540] 	compiled for 1.10.4, module version = 1.0.0
[   185.540] 	ABI class: X.Org Server Extension, version 5.0
[   185.540] (II) Loading extension XFree86-DRI
[   185.540] (II) LoadModule: "dri2"
[   185.540] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   185.540] (II) Module dri2: vendor="X.Org Foundation"
[   185.540] 	compiled for 1.10.4, module version = 1.2.0
[   185.540] 	ABI class: X.Org Server Extension, version 5.0
[   185.540] (II) Loading extension DRI2
[   185.540] (==) Matched vesa as autoconfigured driver 0
[   185.540] (==) Matched fbdev as autoconfigured driver 1
[   185.540] (==) Assigned the driver to the xf86ConfigLayout
[   185.540] (II) LoadModule: "vesa"
[   185.541] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   185.541] (II) Module vesa: vendor="X.Org Foundation"
[   185.541] 	compiled for 1.10.2, module version = 2.3.0
[   185.541] 	Module class: X.Org Video Driver
[   185.541] 	ABI class: X.Org Video Driver, version 10.0
[   185.541] (II) LoadModule: "fbdev"
[   185.541] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   185.541] (II) Module fbdev: vendor="X.Org Foundation"
[   185.541] 	compiled for 1.10.0, module version = 0.4.2
[   185.541] 	ABI class: X.Org Video Driver, version 10.0
[   185.541] (II) VESA: driver for VESA chipsets: vesa
[   185.541] (II) FBDEV: driver for framebuffer: fbdev
[   185.541] (--) using VT number 8

[   185.543] (WW) Falling back to old probe method for vesa
[   185.543] (WW) Falling back to old probe method for fbdev
[   185.543] (II) Loading sub module "fbdevhw"
[   185.543] (II) LoadModule: "fbdevhw"
[   185.543] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   185.544] (II) Module fbdevhw: vendor="X.Org Foundation"
[   185.544] 	compiled for 1.10.4, module version = 0.0.2
[   185.544] 	ABI class: X.Org Video Driver, version 10.0
[   185.544] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   185.544] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   185.544] (II) FBDEV(0): using default device
[   185.544] (EE) FBDEV(0): Specified depth (24) is greater than the fbbpp (1)
[   185.544] (II) UnloadModule: "fbdev"
[   185.544] (II) Unloading fbdev
[   185.544] (II) UnloadModule: "fbdevhw"
[   185.544] (II) Unloading fbdevhw
[   185.544] (EE) Screen(s) found, but none have a usable configuration.
[   185.544] 
Fatal server error:
[   185.544] no screens found
[   185.544] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   185.544] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   185.544] 
[   185.548]  ddxSigGiveUp: Closing log
vadi@vadi-11:~$ sudo startx -- -configure
xauth:  error in locking authority file /home/vadi/.Xauthority
xauth:  error in locking authority file /home/vadi/.Xauthority


X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux vadi-11 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=5a261133-b5a0-46a2-81ff-c1af4edb821e ro quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap vt.handoff=7
Build Date: 19 October 2011  05:21:26AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 19 14:00:24 2012
List of video drivers:
	intel
	mga
	r128
	trident
	s3
	s3virge
	radeon
	tdfx
	tseng
	ark
	chips
	voodoo
	sisusb
	nouveau
	savage
	vmware
	qxl
	apm
	rendition
	i128
	cirrus
	siliconmotion
	sis
	neomagic
	mach64
	openchrome
	ati
	vmwlegacy
	fbdev
	vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
No devices to configure.  Configuration failed.
 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
xauth:  error in locking authority file /home/vadi/.Xauthority
vadi@vadi-11:~$ 


Any insight is appreciated.

---

### Post by isantop on 2012-03-22
Try running from a LiveCD of Ubuntu. I'm guessing that this is a simple configuration issue. Running from the LiveCD would confirm that.

---

