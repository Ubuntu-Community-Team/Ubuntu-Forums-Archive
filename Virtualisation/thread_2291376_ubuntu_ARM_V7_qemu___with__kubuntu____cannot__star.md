---
title: "ubuntu ARM V7 qemu   with  kubuntu    cannot  start x server"
date: 2015-08-19
forum: Virtualisation
---

### Post by cez1230 on 2015-08-19
i follow the steps below  to make arm v7   ubuntu filesystem,and use qemu or tiny210 to test.
when  apt-get install  xinit xorg   xdm  xubuntu      and  startx   ,
then  i find  server-xorg  start error  .


i have  trid  in qemu  and tiny210   ,the  same problem.
any one  who knows how to start xubuntu  ,gnome  xfce4  with arm V7 ?


----------  steps below -------------

```
sudo apt-get update
sudo apt-get install qemu-user-static
sudo qemu-debootstrap --arch armhf precise ubuntu_arm  
sudo chroot ubuntu_arm  
uname -m

```


ok  now  we are  in qemu armV7   ubuntu system
vi /etc/apt/source.list      and  add apt sourcelist here
```

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) raring main
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) raring multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) raring restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) raring universe

apt-get update  
apt-get install unity
apt-get install openssh-server 
apt-get install xinit  
apt-get install xorg
apt-get install xdm
apt-get install xubuntu-desktop  

```


then  i start qemu-system-arm
```
 
root@cez-desktop:~/soft/qemu-1.2.0# qemu-system-arm -M  vexpress-a9     -kernel zImage   -append "noinitrd  root=/dev/nfs   console=tty0  nfsroot=192.168.1.113:/root/nfs/ubuntu_arm   rw   ip=192.168.1.121:192.168.1.113:192.168.1.1:255.255.255.0  init=linuxrc"   -net nic,vlan=0  -net tap,ifname=tap0,script=qemu-ifup,downscript=qemu-ifdown

```


now in qemu  arm
```

startx  

```
(after  startx  ,  error  shows  the xinit  can't   start x server  ,  and  the xorg.0.log file delow)
-----------------------------------------------------------------------------------------------


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-607-imx51 armv7l Ubuntu
Current Operating System: Linux 192.168.1.121 3.0.82 #1 SMP Fri Aug 14 18:58:28 CST 2015 armv7l
Build Date: 23 April 2010  05:19:26PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 20 03:30:24 2015
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "screen0" (0)
(**) |   |-->Monitor "monitor0"
(==) No device specified for screen "screen0".
    Using the first device section listed.
(**) |   |-->Device "device0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x13bd34
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 2

(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
Primary device is not PCI

Backtrace:
Segmentation fault at address 0x4

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

