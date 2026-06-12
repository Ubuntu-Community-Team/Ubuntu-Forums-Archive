---
title: "Unity faster than normal?"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-23
Unity is behaving  absolutely as if it has rocket launchers attatched to it. :) It is even quicker that the early alpha-II from quantal.

  A marked increase in performance and speed.

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.7.0-3-generic #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$

---

### Post by zika on 2012-11-23
> **ventrical said:**
> Unity is behaving  absolutely as if it has rocket launchers attatched to it. :) It is even quicker that the early alpha-II from quantal.

  A marked increase in performance and speed.

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.7.0-3-generic #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$I thought I was alone...
This message of mine looks like déjà vu to me since we had a situation like this some time ago, as I recall in QQ...
It is even faster if You turn off zoom... If You do not need it...

---

### Post by serdotlinecho on 2012-11-23
You mean this compiz plugins?

---

### Post by serdotlinecho on 2012-11-23
Yeah, even on a netbook, unity dash came up faster now. Searching in unity dash is getting better and responsive, maybe because i've turn off include online search results.

```
$ uname -r;unity --version
3.7.0-3-generic
unity 6.12.0
```

---

### Post by ventrical on 2012-11-23
> **zika said:**
> I thought I was alone...
This message of mine looks like déjà vu to me since we had a situation like this some time ago, as I recall in QQ...
It is even faster if You turn off zoom... If You do not need it...

As I mentioned above, I had the same 'speedy' response times with QQ alpha2. Thanks for your input. Also noting the 'zoom' I notice they now have these very distinct yellow/orange borders around each frame. another improvment I guess. I have all the bells and whistles enabled. However, I just booted to the daily -i386 desktop iso and  no improvement so it looks  this phenom is working only on amd64. I am going to install and see if that makes any difference.

---

### Post by NikTh on 2012-11-23
So , I guess the [new Icon of Dash]("http://www.omgubuntu.co.uk/2012/11/ubuntu-updates-software-center-update-manager-icons-in-13-04") is not only eye-candy thing , but symbolizes the speed also :)

---

### Post by zika on 2012-11-23
> **ventrical said:**
> As I mentioned above, I had the same 'speedy' response times with QQ alpha2. Thanks for your input. Also noting the 'zoom' I notice they now have these very distinct yellow/orange borders around each frame. another improvment I guess. I have all the bells and whistles enabled. However, I just booted to the daily -i386 desktop iso and  no improvement so it looks  this **phenom** is working only on amd64. I am going to install and see if that makes any difference.Just what I have... ;) (X3)...

---

### Post by ventrical on 2012-11-23
> **NikTh said:**
> So , I guess the [new Icon of Dash]("http://www.omgubuntu.co.uk/2012/11/ubuntu-updates-software-center-update-manager-icons-in-13-04") is not only eye-candy thing , but symbolizes the speed also :)


I just seen that link! Thanks. You know , this happened before with alpha 2 QQ. Unity was really snappy but, as the release day drew near it became like molases (standard) again. I have a hunch that I may have downloaded a hybrid  daily-image or somthing I did wrong. I  dunno .. sure would be nice if it remained this quick.  I am about to do a hard install and see where that goes.

  *I am assuming at this stage that the "live" daily is loading all the Unity Indexes and core in memory on some type of mini virtual disk (casper?) but then it will not when  it is hard installed.

regards

---

### Post by ventrical on 2012-11-23
Ok.. I hard installed on a;

```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```

 and it is very snappy (note this is yet another one of my machines - not as fast as the Dell 3100 and non HT ,Intel 64bit) and Unity is just jumping, initially. Haven't updated so here goes.....

---

### Post by ventrical on 2012-11-23
This is just awesome. Ubuntu testing is always a phenomenon!! The install went just great and Unity 3D works on this machine as if it had HT technology! (which it does not). This is a 7 years old HP Pavilion with a;

---

### Post by zika on 2012-11-23
Oh my... Just try it without LightDM involved, i.e with startx... Even faster and snappier... Nice!

---

### Post by ventrical on 2012-11-23
> **zika said:**
> Oh my... Just try it without LightDM involved, i.e with startx... Even faster and snappier... Nice!


 I am not familiar with this starting technique. Could you put up the commands for this?

Thanks in advance.

Regards

---

### Post by zika on 2012-11-23
> **ventrical said:**
> I am not familiar with this starting technique. Could you put up the commands for this?

Thanks in advance.

RegardsJust make:
```
:~$ cat ~/.Xsession 
exec /usr/bin/unity
```and apply```
startx
``` in any tty* after stopping LightDM or any other DM...

---

### Post by ventrical on 2012-11-23
I missed somthing here. :)

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat ~/ .Xsession
cat: /home/ventrical/: Is a directory
cat: .Xsession: No such file or directory
ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat ~/.Xsession
cat: /home/ventrical/.Xsession: No such file or directory
ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat ~/.Xsession 
cat: /home/ventrical/.Xsession: No such file or directory
ventrical@ventrical-PY028AA-ABA-A1106N:~$ exec /usr/bin/unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: cube
compiz (core) - Info: Starting plugin: cube
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: rotate
compiz (core) - Info: Starting plugin: rotate
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2012-11-23 17:12:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-23 17:12:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-23 17:12:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-23 17:12:41 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:44 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:44 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:44 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110


```

---

### Post by zika on 2012-11-24
> **ventrical said:**
> I missed somthing here. :)

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat ~/ .Xsession
cat: /home/ventrical/: Is a directory
cat: .Xsession: No such file or directory
ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat ~/.Xsession
cat: /home/ventrical/.Xsession: No such file or directory
ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat ~/.Xsession 
cat: /home/ventrical/.Xsession: No such file or directory
ventrical@ventrical-PY028AA-ABA-A1106N:~$ exec /usr/bin/unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: cube
compiz (core) - Info: Starting plugin: cube
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: rotate
compiz (core) - Info: Starting plugin: rotate
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2012-11-23 17:12:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-23 17:12:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-23 17:12:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-23 17:12:41 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:43 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:44 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:44 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110
WARN  2012-11-23 17:12:44 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window56623110


```
Just make a file that gives (when made) that output with cat...
Or```
echo "exec /usr/bin/unity" > ~/.Xsession
```

---

### Post by ventrical on 2012-11-24
Connection refused .. and I keep getting this..

```

[   455.187] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   455.187] X Protocol Version 11, Revision 0
[   455.187] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[   455.187] Current Operating System: Linux ventrical-PY028AA-ABA-A1106N 3.7.0-3-generic #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 x86_64
[   455.187] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-3-generic root=UUID=811f56e4-a72e-45f1-bbfd-606ef0f5d514 ro quiet splash vt.handoff=7
[   455.187] Build Date: 19 November 2012  10:27:57AM
[   455.188] xorg-server 2:1.13.0-0ubuntu8 (For technical support please see http://www.ubuntu.com/support) 
[   455.188] Current version of pixman: 0.26.0
[   455.188]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   455.188] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   455.188] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Nov 24 04:39:28 2012
[   455.189] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   455.189] (==) No Layout section.  Using the first Screen section.
[   455.189] (==) No screen section available. Using defaults.
[   455.189] (**) |-->Screen "Default Screen Section" (0)
[   455.189] (**) |   |-->Monitor "<default monitor>"
[   455.189] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   455.189] (==) Automatically adding devices
[   455.189] (==) Automatically enabling devices
[   455.189] (==) Automatically adding GPU devices
[   455.189] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   455.189]     Entry deleted from font path.
[   455.189] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   455.189]     Entry deleted from font path.
[   455.190] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   455.190] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   455.190] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   455.190] (II) Loader magic: 0x7fb33df29c40
[   455.190] (II) Module ABI versions:
[   455.190]     X.Org ANSI C Emulation: 0.4
[   455.190]     X.Org Video Driver: 13.0
[   455.190]     X.Org XInput driver : 18.0
[   455.190]     X.Org Server Extension : 7.0
[   455.190] (II) config/udev: Adding drm device (/dev/dri/card0)
[   455.190] setversion 1.4 failed
[   455.192] (--) PCI:*(0:0:2:0) 8086:2582:103c:2a08 rev 4, Mem @ 0xcfe80000/524288, 0xd0000000/268435456, 0xcfe40000/262144, I/O @ 0x0000b800/8
[   455.193] (II) Open ACPI successful (/var/run/acpid.socket)
[   455.193] Initializing built-in extension Generic Event Extension
[   455.193] Initializing built-in extension SHAPE
[   455.193] Initializing built-in extension MIT-SHM
[   455.194] Initializing built-in extension XInputExtension
[   455.196] Initializing built-in extension XTEST
[   455.197] Initializing built-in extension BIG-REQUESTS
[   455.198] Initializing built-in extension SYNC
[   455.200] Initializing built-in extension XKEYBOARD
[   455.201] Initializing built-in extension XC-MISC
[   455.202] Initializing built-in extension SECURITY
[   455.203] Initializing built-in extension XINERAMA
[   455.205] Initializing built-in extension XFIXES
[   455.206] Initializing built-in extension RENDER
[   455.207] Initializing built-in extension RANDR
[   455.208] Initializing built-in extension COMPOSITE
[   455.209] Initializing built-in extension DAMAGE
[   455.210] Initializing built-in extension MIT-SCREEN-SAVER
[   455.211] Initializing built-in extension DOUBLE-BUFFER
[   455.212] Initializing built-in extension RECORD
[   455.214] Initializing built-in extension DPMS
[   455.215] Initializing built-in extension X-Resource
[   455.216] Initializing built-in extension XVideo
[   455.217] Initializing built-in extension XVideo-MotionCompensation
[   455.218] Initializing built-in extension XFree86-VidModeExtension
[   455.219] Initializing built-in extension XFree86-DGA
[   455.219] Initializing built-in extension XFree86-DRI
[   455.220] Initializing built-in extension DRI2
[   455.220] (II) LoadModule: "glx"
[   455.221] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   455.221] (II) Module glx: vendor="X.Org Foundation"
[   455.221]     compiled for 1.13.0, module version = 1.0.0
[   455.221]     ABI class: X.Org Server Extension, version 7.0
[   455.221] (==) AIGLX enabled
[   455.222] Loading extension GLX
[   455.222] (==) Matched intel as autoconfigured driver 0
[   455.222] (==) Matched vesa as autoconfigured driver 1
[   455.222] (==) Matched modesetting as autoconfigured driver 2
[   455.222] (==) Matched fbdev as autoconfigured driver 3
[   455.222] (==) Assigned the driver to the xf86ConfigLayout
[   455.222] (II) LoadModule: "intel"
[   455.222] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   455.223] (II) Module intel: vendor="X.Org Foundation"
[   455.223]     compiled for 1.13.0, module version = 2.20.13
[   455.223]     Module class: X.Org Video Driver
[   455.223]     ABI class: X.Org Video Driver, version 13.0
[   455.223] (II) LoadModule: "vesa"
[   455.223] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   455.223] (II) Module vesa: vendor="X.Org Foundation"
[   455.223]     compiled for 1.12.99.902, module version = 2.3.2
[   455.223]     Module class: X.Org Video Driver
[   455.223]     ABI class: X.Org Video Driver, version 13.0
[   455.223] (II) LoadModule: "modesetting"
[   455.223] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   455.224] (II) Module modesetting: vendor="X.Org Foundation"
[   455.224]     compiled for 1.13.0, module version = 0.5.0
[   455.224]     Module class: X.Org Video Driver
[   455.224]     ABI class: X.Org Video Driver, version 13.0
[   455.224] (II) LoadModule: "fbdev"
[   455.224] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   455.224] (II) Module fbdev: vendor="X.Org Foundation"
[   455.224]     compiled for 1.12.99.902, module version = 0.4.3
[   455.224]     Module class: X.Org Video Driver
[   455.224]     ABI class: X.Org Video Driver, version 13.0
[   455.224] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[   455.225] (II) VESA: driver for VESA chipsets: vesa
[   455.225] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   455.225] (II) FBDEV: driver for framebuffer: fbdev
[   455.225] (--) using VT number 8

[   455.229] (WW) Falling back to old probe method for vesa
[   455.229] (WW) Falling back to old probe method for modesetting
[   455.229] (WW) Falling back to old probe method for fbdev
[   455.229] (II) Loading sub module "fbdevhw"
[   455.229] (II) LoadModule: "fbdevhw"
[   455.229] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   455.230] (II) Module fbdevhw: vendor="X.Org Foundation"
[   455.230]     compiled for 1.13.0, module version = 0.0.2
[   455.230]     ABI class: X.Org Video Driver, version 13.0
[   455.230] (EE) intel(0): [drm] failed to set drm interface version.
[   455.230] (EE) intel(0): Failed to become DRM master.
[   455.230] (II) UnloadModule: "intel"
[   455.230] (EE) Screen(s) found, but none have a usable configuration.
[   455.230] 
Fatal server error:
[   455.230] no screens found
[   455.230] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   455.230] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   455.230] (EE) 
[   455.244] Server terminated with error (1). Closing log file.


```

*edit* doh!!  No screens found! .. could it be that this will not work because I have a KVM switcher?

---

### Post by zika on 2012-11-25
> **ventrical said:**
> Connection refused .. and I keep getting this..

```

[   455.187] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   455.187] X Protocol Version 11, Revision 0
[   455.187] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[   455.187] Current Operating System: Linux ventrical-PY028AA-ABA-A1106N 3.7.0-3-generic #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 x86_64
[   455.187] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-3-generic root=UUID=811f56e4-a72e-45f1-bbfd-606ef0f5d514 ro quiet splash vt.handoff=7
[   455.187] Build Date: 19 November 2012  10:27:57AM
[   455.188] xorg-server 2:1.13.0-0ubuntu8 (For technical support please see http://www.ubuntu.com/support) 
[   455.188] Current version of pixman: 0.26.0
[   455.188]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   455.188] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   455.188] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Nov 24 04:39:28 2012
[   455.189] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   455.189] (==) No Layout section.  Using the first Screen section.
[   455.189] (==) No screen section available. Using defaults.
[   455.189] (**) |-->Screen "Default Screen Section" (0)
[   455.189] (**) |   |-->Monitor "<default monitor>"
[   455.189] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   455.189] (==) Automatically adding devices
[   455.189] (==) Automatically enabling devices
[   455.189] (==) Automatically adding GPU devices
[   455.189] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   455.189]     Entry deleted from font path.
[   455.189] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   455.189]     Entry deleted from font path.
[   455.190] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   455.190]     Entry deleted from font path.
[   455.190] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   455.190] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   455.190] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   455.190] (II) Loader magic: 0x7fb33df29c40
[   455.190] (II) Module ABI versions:
[   455.190]     X.Org ANSI C Emulation: 0.4
[   455.190]     X.Org Video Driver: 13.0
[   455.190]     X.Org XInput driver : 18.0
[   455.190]     X.Org Server Extension : 7.0
[   455.190] (II) config/udev: Adding drm device (/dev/dri/card0)
[   455.190] setversion 1.4 failed
[   455.192] (--) PCI:*(0:0:2:0) 8086:2582:103c:2a08 rev 4, Mem @ 0xcfe80000/524288, 0xd0000000/268435456, 0xcfe40000/262144, I/O @ 0x0000b800/8
[   455.193] (II) Open ACPI successful (/var/run/acpid.socket)
[   455.193] Initializing built-in extension Generic Event Extension
[   455.193] Initializing built-in extension SHAPE
[   455.193] Initializing built-in extension MIT-SHM
[   455.194] Initializing built-in extension XInputExtension
[   455.196] Initializing built-in extension XTEST
[   455.197] Initializing built-in extension BIG-REQUESTS
[   455.198] Initializing built-in extension SYNC
[   455.200] Initializing built-in extension XKEYBOARD
[   455.201] Initializing built-in extension XC-MISC
[   455.202] Initializing built-in extension SECURITY
[   455.203] Initializing built-in extension XINERAMA
[   455.205] Initializing built-in extension XFIXES
[   455.206] Initializing built-in extension RENDER
[   455.207] Initializing built-in extension RANDR
[   455.208] Initializing built-in extension COMPOSITE
[   455.209] Initializing built-in extension DAMAGE
[   455.210] Initializing built-in extension MIT-SCREEN-SAVER
[   455.211] Initializing built-in extension DOUBLE-BUFFER
[   455.212] Initializing built-in extension RECORD
[   455.214] Initializing built-in extension DPMS
[   455.215] Initializing built-in extension X-Resource
[   455.216] Initializing built-in extension XVideo
[   455.217] Initializing built-in extension XVideo-MotionCompensation
[   455.218] Initializing built-in extension XFree86-VidModeExtension
[   455.219] Initializing built-in extension XFree86-DGA
[   455.219] Initializing built-in extension XFree86-DRI
[   455.220] Initializing built-in extension DRI2
[   455.220] (II) LoadModule: "glx"
[   455.221] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   455.221] (II) Module glx: vendor="X.Org Foundation"
[   455.221]     compiled for 1.13.0, module version = 1.0.0
[   455.221]     ABI class: X.Org Server Extension, version 7.0
[   455.221] (==) AIGLX enabled
[   455.222] Loading extension GLX
[   455.222] (==) Matched intel as autoconfigured driver 0
[   455.222] (==) Matched vesa as autoconfigured driver 1
[   455.222] (==) Matched modesetting as autoconfigured driver 2
[   455.222] (==) Matched fbdev as autoconfigured driver 3
[   455.222] (==) Assigned the driver to the xf86ConfigLayout
[   455.222] (II) LoadModule: "intel"
[   455.222] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   455.223] (II) Module intel: vendor="X.Org Foundation"
[   455.223]     compiled for 1.13.0, module version = 2.20.13
[   455.223]     Module class: X.Org Video Driver
[   455.223]     ABI class: X.Org Video Driver, version 13.0
[   455.223] (II) LoadModule: "vesa"
[   455.223] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   455.223] (II) Module vesa: vendor="X.Org Foundation"
[   455.223]     compiled for 1.12.99.902, module version = 2.3.2
[   455.223]     Module class: X.Org Video Driver
[   455.223]     ABI class: X.Org Video Driver, version 13.0
[   455.223] (II) LoadModule: "modesetting"
[   455.223] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   455.224] (II) Module modesetting: vendor="X.Org Foundation"
[   455.224]     compiled for 1.13.0, module version = 0.5.0
[   455.224]     Module class: X.Org Video Driver
[   455.224]     ABI class: X.Org Video Driver, version 13.0
[   455.224] (II) LoadModule: "fbdev"
[   455.224] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   455.224] (II) Module fbdev: vendor="X.Org Foundation"
[   455.224]     compiled for 1.12.99.902, module version = 0.4.3
[   455.224]     Module class: X.Org Video Driver
[   455.224]     ABI class: X.Org Video Driver, version 13.0
[   455.224] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[   455.225] (II) VESA: driver for VESA chipsets: vesa
[   455.225] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   455.225] (II) FBDEV: driver for framebuffer: fbdev
[   455.225] (--) using VT number 8

[   455.229] (WW) Falling back to old probe method for vesa
[   455.229] (WW) Falling back to old probe method for modesetting
[   455.229] (WW) Falling back to old probe method for fbdev
[   455.229] (II) Loading sub module "fbdevhw"
[   455.229] (II) LoadModule: "fbdevhw"
[   455.229] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   455.230] (II) Module fbdevhw: vendor="X.Org Foundation"
[   455.230]     compiled for 1.13.0, module version = 0.0.2
[   455.230]     ABI class: X.Org Video Driver, version 13.0
[   455.230] (EE) intel(0): [drm] failed to set drm interface version.
[   455.230] (EE) intel(0): Failed to become DRM master.
[   455.230] (II) UnloadModule: "intel"
[   455.230] (EE) Screen(s) found, but none have a usable configuration.
[   455.230] 
Fatal server error:
[   455.230] no screens found
[   455.230] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   455.230] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   455.230] (EE) 
[   455.244] Server terminated with error (1). Closing log file.


```*edit* doh!!  No screens found! .. could it be that this will not work because I have a KVM switcher?
Try with /usr/bin/ck-launch-session instead if exec, but I do not think it would help...
```
echo "/usr/bin/ck-launch-session /usr/bin/unity" > ~/.Xsession
```

---

### Post by wgarcia on 2012-11-25
I've noticed also an improvement in performance in 12.10 happening with updates sometime during the last 2 weeks, but maybe it's just something related with my graphic card.

---

### Post by ventrical on 2012-11-25
> **zika said:**
> Try with /usr/bin/ck-launch-session instead if exec, but I do not think it would help...
```
echo "/usr/bin/ck-launch-session /usr/bin/unity" > ~/.Xsession
```


Yes !! Thats exactly it ! Thanks zika.  I am not sure if Unity is faster but I am impressed with the low percentage of cpu resources being used when using that method.

Thanks again.

Regards..

Ventrical

---

### Post by NikTh on 2012-11-25
> **ventrical said:**
> Yes !! Thats exactly it ! Thanks zika.  I am not sure if Unity is faster but I am impressed with the low percentage of cpu resources being used when using that method.

Is this for sure ? I mean , is lightdm eats so much ?

---

### Post by ventrical on 2012-11-25
> **NikTh said:**
> Is this for sure ? I mean , is lightdm eats so much ?


Looks like  there is no real difference according to system-monitor - a before and after.

*edit*
Actually there is a slight difference when not using lightdm. Why. I don't know. I assume it may be that lightdm is TSR and is hooked to the desktop , or, just perhaps with Unity  and not other DEs

At this point I can't really document that Unity *is* actually faster but it appears this way just from response times. I also have another 13.04 install on the same machine with same conditions so my initial post was about the daily image of that day, Friday, and how Unity jumped off the page using the live USB and then subsequently the hard install.

---

### Post by fjgaude on 2012-11-25
Why not run gtkperf? It has always done good by me.

---

### Post by ventrical on 2012-11-26
With lightdm:

GtkPerf 0.40 - Starting testing: Mon Nov 26 04:21:30 2012

GtkEntry - time:  0.10
GtkComboBox - time:  7.80
GtkComboBoxEntry - time:  2.45
GtkSpinButton - time:  0.46
GtkProgressBar - time:  1.03
GtkToggleButton - time:  4.80
GtkCheckButton - time:  0.40
GtkRadioButton - time:  0.64
GtkTextView - Add text - time:  1.90
GtkTextView - Scroll - time:  0.38
GtkDrawingArea - Lines - time:  4.49
GtkDrawingArea - Circles - time:  5.19
GtkDrawingArea - Text - time:  4.25
GtkDrawingArea - Pixbufs - time:  1.30
 --- 
Total time: 35.20
--------------------------------------------------

Without lightdm (startx)
GtkPerf 0.40 - Starting testing: Mon Nov 26 04:27:20 2012

GtkEntry - time:  0.11
GtkComboBox - time:  2.35
GtkComboBoxEntry - time:  1.68
GtkSpinButton - time:  0.20
GtkProgressBar - time:  0.11
GtkToggleButton - time:  0.23
GtkCheckButton - time:  0.15
GtkRadioButton - time:  0.27
GtkTextView - Add text - time:  1.45
GtkTextView - Scroll - time:  0.29
GtkDrawingArea - Lines - time:  4.62
GtkDrawingArea - Circles - time:  4.93
GtkDrawingArea - Text - time:  2.35
GtkDrawingArea - Pixbufs - time:  1.16
 --- 
Total time: 19.91

According to that particular test there is an increase in performance using  startx (without lighdm).. so zika is correct.

---

### Post by zika on 2012-11-26
> **ventrical said:**
> According to that particular test there is an increase in performance using  startx (without lighdm).. so zika is correct.Did You have any doubts...?
Joke aside, I know, that's why I wrote about that. I've been using this for 1.5 testing period... Of course, it has some (even serious) cons (or call them ill-effects) but, I like it...

---

### Post by jerrylamos on 2012-11-26
> **zika said:**
> Try with /usr/bin/ck-launch-session instead if exec, but I do not think it would help...
```
echo "/usr/bin/ck-launch-session /usr/bin/unity" > ~/.Xsession
```
Tried that.  Oops.

> 
startx
Loading extension GLX
xinit: connection to X server lost


right back to cli.  Can't get anywhere.

Tried to start lightdm, got login screen, tried to log in, got login screen, etc.  Won't even shut down.  Power down, power up, same login screen loop.

Looks like that partition is tanked.  Blooey.

So I booted an older partition to enter this message.

I assume the only fix I have to the .Xsession startx attempt is a re-install?

---

### Post by ventrical on 2012-11-26
> **zika said:**
> Did You have any doubts...?
Joke aside, I know, that's why I wrote about that. I've been using this for 1.5 testing period... Of course, it has some (even serious) cons (or call them ill-effects) but, I like it...

Nope .. no doubts at all :) 

Also .. yes .. there are some ill effects using  KVM switchers . After I ran those gtkperf test the screen locked and froze .. error or somthing about cannot detect xKeyboard.

---

### Post by zika on 2012-11-26
> **ventrical said:**
> Nope .. no doubts at all :) 

Also .. yes .. there are some ill effects using  KVM switchers . After I ran those gtkperf test the screen locked and froze .. error or somthing about cannot detect xKeyboard.KVM is not in my system so I can not comment on that. But, I've been honest, that is not a perfect advice, not even a solution, just an option, from a time when I've started trying GnomeShell, OpenBox, FluxBox... It was easier to pin-point troublesome places that way than run around (Li)G(ht)DM...

---

### Post by ventrical on 2012-11-26
> **zika said:**
> KVM is not in my system so I can not comment on that. But, I've been honest, that is not a perfect advice, not even a solution, just an option, from a time when I've started trying GnomeShell, OpenBox, FluxBox... It was easier to pin-point troublesome places that way than run around (Li)G(ht)DM...

  I think your advice is great advice for beta testers. Thanks for sharing that method. I am always learning new things here. It's always a phenomenon and a challenge.

Regards,

ventrical

---

### Post by MG&amp;TL on 2012-11-26
> **jerrylamos said:**
> 
I assume the only fix I have to the .Xsession startx attempt is a re-install?

Since I don't have that file on a normal install, I think it's safe to remove it and see if that fixes the problem. 

```
rm ~/.Xsession
```

---

### Post by zika on 2012-11-26
> **jerrylamos said:**
> Tried that.  Oops.



right back to cli.  Can't get anywhere.

Tried to start lightdm, got login screen, tried to log in, got login screen, etc.  Won't even shut down.  Power down, power up, same login screen loop.

Looks like that partition is tanked.  Blooey.

So I booted an older partition to enter this message.

I assume the only fix I have to the .Xsession startx attempt is a re-install?Startx with such ~/.Xsession did not tank Your partition as You state... You're just having some problem with X and it showed now... Since You've entered LightDM...
Are You sure that You did not use sudo in trying startx? If You did there is a simple remedy:
remove file ~/.Xauthority ...
> **MG&TL said:**
> Since I don't have that file on a normal  install, I think it's safe to remove it and see if that fixes the  problem. 

```
rm ~/.Xsession
```Yes, that file is not a part of vanilla install. That is why I have without any caution instruct another user to make it... In other case I would (for sure) suggest making a backup...

In my book startx is a nice lacmus(litmus)...

---

### Post by jerrylamos on 2012-11-26
> **MG&TL said:**
> Since I don't have that file on a normal install, I think it's safe to remove it and see if that fixes the problem. 

```
rm ~/.Xsession
```

Yeh, I did that.  No help, still busted.  I just zsync'd raring since updating the 3.7.0.0 to 3.7.0-3 occupies 10% more disk space even after removing linux-image, headers, apt-get clean, apt-get autoclean, apt-get autoremove.

p.s. no go on install.  Gets to the part where it is looking at the partitions and spins forever.  And ever.  Tried update/upgrade no help.

---

### Post by jerrylamos on 2012-11-26
On topic, to me, more like tolerable unity.  unity is usable, though the slowest linux to boot that I have.

I've got a Lubuntu (+Firefox +Libre) on an older laptop.  Bang! Click! Snap! Do a select I'm waiting for the window to change - oops, it did already so fast I didn't see it flick on.

On the faster laptop raring unity does run without dragging its feet too much.

"faster than normal" is my Android tablet....that is, faster at what it will do, rather a real slug to do much text input even with the factory keyboard.

---

### Post by jerrylamos on 2012-11-29
On topic, maybe Unity seems faster than it was to some people - I don't have any benchmarks to show that.  Earlier Unity I resorted to 2D or Lxde I am able to use Unity O.K. lately.

Just tried Linux Mint amd64 14 for what I do noticeably faster and less keystrokes than Unity.  No benchmarks.  Now that wasn't a desktop I'd put on a phone, I'd use Android.  And comparing 1.0 GHz Android to 1.6 GHz Unity on same size pc's the Android is way faster for what it will do - internet- I don't have a clue how to do Libre Office or manage photo galleries on an Android.

I see people have Ubuntu on a Nexus 7, or maybe on a Nook (via SD card) I'll be interested in any comparisons to their native operating system. 

I do run Unity for testing purposes.

Anyone have any desktop benchmark methods?

---

### Post by ventrical on 2012-11-29
> **jerrylamos said:**
> On topic, maybe Unity seems faster than it was to some people - I don't have any benchmarks to show that.  Earlier Unity I resorted to 2D or Lxde I am able to use Unity O.K. lately.
Just tried Linux Mint amd64 14 for what I do noticeably faster and less keystrokes than Unity. 

Anyone have any desktop benchmark methods?

  I am  beta testing Ubuntu Unity 3D desktop amd64bit kernels on the previously mentioned machines. Not beta testing Linux Mint. As previously mentioned, gtkperf (sudo apt-get install gtkperf) and run that from terminal. Switch through GRUB with different kernels and notice the difference in time  (with the different conditions)  it takes to complete that test, then you will notice performance increase across different kernels. This thread does not mention tests for Lubuntu. Xubuntu or Kubuntu.

Here's how:

```

GtkPerf 0.40 - Starting testing: Thu Nov 29 08:40:03 2012

GtkEntry - time:  0.10
GtkComboBox - time:  7.28
GtkComboBoxEntry - time:  2.34
GtkSpinButton - time:  0.48
GtkProgressBar - time:  0.94
GtkToggleButton - time:  4.35
GtkCheckButton - time:  0.43
GtkRadioButton - time:  0.67
GtkTextView - Add text - time:  2.10
GtkTextView - Scroll - time:  0.40
GtkDrawingArea - Lines - time:  5.13
GtkDrawingArea - Circles - time:  5.51
GtkDrawingArea - Text - time:  3.99
GtkDrawingArea - Pixbufs - time:  1.29
 --- 
Total time: 35.02

ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -a
Linux ventrical-PY028AA-ABA-A1106N 3.7.0-030700rc2-generic #201210220428 SMP Mon Oct 22 08:37:05 UTC 2012 i686 i686 i686 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```

```

Old Quantal Questzal Kernel, 32bit

GtkPerf 0.40 - Starting testing: Thu Nov 29 08:55:16 2012

GtkEntry - time:  0.10
GtkComboBox - time:  8.85
GtkComboBoxEntry - time:  3.41
GtkSpinButton - time:  0.64
GtkProgressBar - time:  2.09
GtkToggleButton - time:  4.75
GtkCheckButton - time:  0.75
GtkRadioButton - time:  1.35
GtkTextView - Add text - time:  2.35
GtkTextView - Scroll - time:  0.43
GtkDrawingArea - Lines - time:  4.11
GtkDrawingArea - Circles - time:  5.52
GtkDrawingArea - Text - time:  3.88
GtkDrawingArea - Pixbufs - time:  1.11
 --- 
Total time: 39.34

ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -a
Linux ventrical-PY028AA-ABA-A1106N 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```

```
with ccsm on:

ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -a
Linux ventrical-PY028AA-ABA-A1106N 3.7.0-3-generic #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 


GtkPerf 0.40 - Starting testing: Thu Nov 29 09:13:32 2012

GtkEntry - time:  0.10
GtkComboBox - time:  7.75
GtkComboBoxEntry - time:  3.47
GtkSpinButton - time:  0.97
GtkProgressBar - time:  1.55
GtkToggleButton - time:  4.59
GtkCheckButton - time:  0.37
GtkRadioButton - time:  0.59
GtkTextView - Add text - time:  1.82
GtkTextView - Scroll - time:  0.36
GtkDrawingArea - Lines - time:  4.71
GtkDrawingArea - Circles - time:  4.50
GtkDrawingArea - Text - time:  3.56
GtkDrawingArea - Pixbufs - time:  1.18
 --- 
Total time: 35.55


```

```
with ccsm off:

ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -a
Linux ventrical-PY028AA-ABA-A1106N 3.7.0-3-generic #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 


GtkPerf 0.40 - Starting testing: Thu Nov 29 09:19:10 2012

GtkEntry - time:  0.10
GtkComboBox - time:  2.65
GtkComboBoxEntry - time:  1.09
GtkSpinButton - time:  0.26
GtkProgressBar - time:  0.44
GtkToggleButton - time:  1.03
GtkCheckButton - time:  0.24
GtkRadioButton - time:  0.37
GtkTextView - Add text - time:  1.23
GtkTextView - Scroll - time:  0.28
GtkDrawingArea - Lines - time:  2.17
GtkDrawingArea - Circles - time:  3.66
GtkDrawingArea - Text - time:  2.49
GtkDrawingArea - Pixbufs - time:  0.41
 --- 
Total time: 16.44


```

```


without ccsm:

ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -a
Linux ventrical-PY028AA-ABA-A1106N 3.7.0-030700rc7-generic #201211252135 SMP Mon Nov 26 02:35:53 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 


GtkPerf 0.40 - Starting testing: Thu Nov 29 09:28:53 2012

GtkEntry - time:  0.09
GtkComboBox - time:  2.58
GtkComboBoxEntry - time:  1.13
GtkSpinButton - time:  0.25
GtkProgressBar - time:  0.43
GtkToggleButton - time:  1.01
GtkCheckButton - time:  0.24
GtkRadioButton - time:  0.37
GtkTextView - Add text - time:  1.23
GtkTextView - Scroll - time:  0.27
GtkDrawingArea - Lines - time:  2.11
GtkDrawingArea - Circles - time:  3.54
GtkDrawingArea - Text - time:  2.42
GtkDrawingArea - Pixbufs - time:  0.39
 --- 
Total time: 16.07

```

 So, as you can see , there is a gradual increase in performance, although this thread did not originally  address the newer kernels installed on hardware, but, rather  a responsive like activity  coming from the  Daliy Live Build of Friday, Nov.23/2012.

 I am just trying to report beta testing of Unity 3D Raring Ringtail as best as possibly with the tools at hand.

regards..

---

### Post by fjgaude on 2012-11-29
Interesting... I use gtkperf all the time, as updates come and go. Latest:

GtkPerf 0.40 - Starting testing: Thu Nov 29 11:02:12 2012

GtkEntry - time:  0.02
GtkComboBox - time:  0.70
GtkComboBoxEntry - time:  0.26
GtkSpinButton - time:  0.05
GtkProgressBar - time:  0.11
GtkToggleButton - time:  0.28
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.08
GtkTextView - Add text - time:  0.35
GtkTextView - Scroll - time:  0.04
GtkDrawingArea - Lines - time:  0.59
GtkDrawingArea - Circles - time:  0.52
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.09
 --- 
Total time:  3.52

frank@cutie:~$ uname -a
Linux cutie 3.7.0-4-generic #12-Ubuntu SMP Tue Nov 27 23:13:21 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

With ccsm... never tried to uninstall it. Of course with Unity 3D.

To me the fastest has been with the released version of 12.10, gtkperf 3.2. 13.04 is just a tad slower,

---

### Post by ventrical on 2012-11-29
> **fjgaude said:**
> Interesting... I use gtkperf all the time, as updates come and go. Latest:

GtkPerf 0.40 - Starting testing: Thu Nov 29 11:02:12 2012

GtkEntry - time:  0.02
GtkComboBox - time:  0.70
GtkComboBoxEntry - time:  0.26
GtkSpinButton - time:  0.05
GtkProgressBar - time:  0.11
GtkToggleButton - time:  0.28
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.08
GtkTextView - Add text - time:  0.35
GtkTextView - Scroll - time:  0.04
GtkDrawingArea - Lines - time:  0.59
GtkDrawingArea - Circles - time:  0.52
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.09
 --- 
Total time:  3.52

frank@cutie:~$ uname -a
Linux cutie 3.7.0-4-generic #12-Ubuntu SMP Tue Nov 27 23:13:21 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

With ccsm... never tried to uninstall it. Of course with Unity 3D.

To me the fastest has been with the released version of 12.10, gtkperf 3.2. 13.04 is just a tad slower,


At 3.8GHz of course it is going to be faster :)

---

### Post by konas on 2012-12-01
I hope I am not too off topic, as I use Enlightenment (Unity on my gma 500 is not usable), but I tried the method of starting E. without lightdm and I get the same result in gtkperf, i.e. around 31s. (kernel 3.7 rc6) so no effect on enlightenment.

---

### Post by ventrical on 2012-12-01
I have been looking around for  other benchmarking software. There is 'saidar' and a suite from Phoronix and others in the USC, some cost $$ and others and not spoken too highly of.  Looks like the simplest test is gtkperf. 

  I cannot definitively say whether or not this test actually validates if Unity is running faster  with the newer kernels coming down the pipe. gtkperf findings  report that they are, but I can only assume that this program is reliable based on the testimonials given.

 Firstly, I am not a Unity expert nor an  Ubuntu expert nor a Linux expert.  As mentioned above , I am just using what ever tools  that are lying around on the shop floor .. so to speak.

  Thank you for your results on E.  I have used that DE but I haven't tested it in the manner you have mentioned above. Simply ? I just don't know. So, my assumptions are documented by the output of the program gtkperf. If that then is vaild proof of a performance increase then the performance increase in not verisimilitude.

---

### Post by tekstr1der on 2012-12-11
> **ventrical said:**
> I cannot definitively say whether or not this test actually validates if Unity is running faster  with the newer kernels coming down the pipe. gtkperf findings  report that they are...

I too usually run gtkperf after a driver or kernel update. Honestly the variance is typically negligible with the kernel version changes.

I was surprised yesterday after I'd compiled the latest kernel 3.4.23 and saw gtkperf was about 10% slower. I've reverted back to the stock kernel on debian wheezy for now but will build 3.6.10 today and test

GtkPerf 0.40 - Starting testing: Tue Dec 11 12:56:18 2012

GtkEntry - time:  0.01
GtkComboBox - time:  0.56
GtkComboBoxEntry - time:  0.50
GtkSpinButton - time:  0.04
GtkProgressBar - time:  0.05
GtkToggleButton - time:  0.09
GtkCheckButton - time:  0.03
GtkRadioButton - time:  0.03
GtkTextView - Add text - time:  0.07
GtkTextView - Scroll - time:  0.11
GtkDrawingArea - Lines - time:  0.17
GtkDrawingArea - Circles - time:  0.18
GtkDrawingArea - Text - time:  0.09
GtkDrawingArea - Pixbufs - time:  0.03
 --- 
Total time:  1.96

$ uname -a
Linux humonculux 3.2.0-4-amd64 #1 SMP Debian 3.2.32-1 x86_64 GNU/Linux

$ nvidia-settings -v
nvidia-settings:  version 304.48

---

### Post by ventrical on 2012-12-11
I am basically running: Linux dale-desktop 3.7.0-030700rc8-generic #201212031649 SMP Mon Dec 3 22:00:46 UTC 2012 i686 i686 i686 GNU/Linux
on most of my installs atm. Final now installed .. ready to load.

---

### Post by ventrical on 2012-12-21
> **ventrical said:**
> With lightdm:

GtkPerf 0.40 - Starting testing: Mon Nov 26 04:21:30 2012

GtkEntry - time:  0.10
GtkComboBox - time:  7.80
GtkComboBoxEntry - time:  2.45
GtkSpinButton - time:  0.46
GtkProgressBar - time:  1.03
GtkToggleButton - time:  4.80
GtkCheckButton - time:  0.40
GtkRadioButton - time:  0.64
GtkTextView - Add text - time:  1.90
GtkTextView - Scroll - time:  0.38
GtkDrawingArea - Lines - time:  4.49
GtkDrawingArea - Circles - time:  5.19
GtkDrawingArea - Text - time:  4.25
GtkDrawingArea - Pixbufs - time:  1.30
 --- 
Total time: 35.20
--------------------------------------------------
.

The above was with driver nvidia-current.

Below is with nouveau-firmware.

GtkPerf 0.40 - Starting testing: Fri Dec 21 08:19:18 2012

GtkEntry - time:  0.08
GtkComboBox - time:  3.04
GtkComboBoxEntry - time:  1.41
GtkSpinButton - time:  0.69
GtkProgressBar - time:  1.15
GtkToggleButton - time:  1.63
GtkCheckButton - time:  0.44
GtkRadioButton - time:  0.91
GtkTextView - Add text - time:  1.46
GtkTextView - Scroll - time:  0.25
GtkDrawingArea - Lines - time:  5.35
GtkDrawingArea - Circles - time:  4.80
GtkDrawingArea - Text - time:  0.83
GtkDrawingArea - Pixbufs - time:  0.79
 --- 
Total time: 22.85

Both test cases done with lighdm and ccsm on.

According to gtkperf, nouveau renders approximately 12 second increase in performance.

Regards..

---

### Post by mc4man on 2012-12-21
> **ventrical said:**
> 

According to gtkperf, nouveau renders approximately 12 second increase in performance.

Regards..
If you're going to compare nouveau to nvidia in 2d perf then you should check & see if nvidia is using 'Adaptive Performance'
If so then set nvidia to 'Prefer Max..' first, then rerun test
(if nvidia is on level 0 at start of test in adaptive mode then generally won't upclock till the scroll test

(while I don't put much stock in gtkperf at least here nvidia in Max is about 50%  faster than nouveau. (11.13 vs. 5.81 on a fairly old 8200m laptop

---

### Post by ventrical on 2012-12-21
> **mc4man said:**
> If you're going to compare nouveau to nvidia in 2d perf then you should check & see if nvidia is using 'Adaptive Performance'
If so then set nvidia to 'Prefer Max..' first, then rerun test
(if nvidia is on level 0 at start of test in adaptive mode then generally won't upclock till the scroll test

(while I don't put much stock in gtkperf at least here nvidia in Max is about 50%  faster than nouveau. (11.13 vs. 5.81 on a fairly old 8200m laptop


Very well.. I will try/do  that. The reason I drew these compares is to attempt to document my declarations that unity is faster than normal. Also .. I do not know of any other testing tool that will adequately test Unity3D performance so then I have to assume that gtkperf results lends credence to some reasonable facsimile thereof. Simply running system monitor and taking eye_shots of compiz effects does not adequately present any hard data - and then now gtkperf is questionable? So how do we aquire an adequate , comprehensive and trustworthy  chart of Unity 3D performance?

---

### Post by ventrical on 2012-12-21
> **mc4man said:**
> If you're going to compare nouveau to nvidia in 2d perf then you should check & see if nvidia is using 'Adaptive Performance'
If so then set nvidia to 'Prefer Max..' first, then rerun test
(if nvidia is on level 0 at start of test in adaptive mode then generally won't upclock till the scroll test

(while I don't put much stock in gtkperf at least here nvidia in Max is about 50%  faster than nouveau. (11.13 vs. 5.81 on a fairly old 8200m laptop


Savings of another 7 seconds to complete that test with Max setting nvidia-current.

GtkPerf 0.40 - Starting testing: Fri Dec 21 11:52:27 2012

GtkEntry - time:  0.09
GtkComboBox - time:  3.08
GtkComboBoxEntry - time:  1.68
GtkSpinButton - time:  0.33
GtkProgressBar - time:  0.54
GtkToggleButton - time:  0.98
GtkCheckButton - time:  0.30
GtkRadioButton - time:  0.64
GtkTextView - Add text - time:  1.49
GtkTextView - Scroll - time:  0.29
GtkDrawingArea - Lines - time:  1.86
GtkDrawingArea - Circles - time:  2.63
GtkDrawingArea - Text - time:  0.54
GtkDrawingArea - Pixbufs - time:  0.21
 --- 
Total time: 14.67

---

### Post by ventrical on 2013-01-10
Here are gtkperf results with SNA initialized on Intel graphics.

GtkRadioButton - time:  0.50
GtkTextView - Add text - time:  1.07
GtkTextView - Scroll - time:  0.27
GtkDrawingArea - Lines - time:  1.51
GtkDrawingArea - Circles - time:  1.55
GtkDrawingArea - Text - time:  0.73
GtkDrawingArea - Pixbufs - time:  0.18
 --- 
Total time: 15.30

---

### Post by fjgaude on 2013-01-10
I don't see it as faster than Unity in 12.10:

GtkPerf 0.40 - Starting testing: Thu Jan 10 15:42:52 2013

GtkEntry - time:  0.02
GtkComboBox - time:  0.76
GtkComboBoxEntry - time:  0.30
GtkSpinButton - time:  0.05
GtkProgressBar - time:  0.15
GtkToggleButton - time:  0.35
GtkCheckButton - time:  0.06
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.37
GtkTextView - Scroll - time:  0.05
GtkDrawingArea - Lines - time:  0.58
GtkDrawingArea - Circles - time:  0.54
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.09
 --- 
Total time:  3.79

This is about the same I get in 12.10, 3.80 or so.

---

### Post by ventrical on 2013-01-11
Here are the non "sna"  results. Also I think that this test is unique to raring.

gtkperf with "uxa"

GtkRadioButton - time:  0.61
GtkTextView - Add text - time:  1.88
GtkTextView - Scroll - time:  0.38
GtkDrawingArea - Lines - time:  4.96
GtkDrawingArea - Circles - time:  5.35
GtkDrawingArea - Text - time:  5.97
GtkDrawingArea - Pixbufs - time:  1.70
 --- 
Total time: 37.81

---

### Post by fjgaude on 2013-01-11
> **ventrical said:**
> Here are the non "sna"  results. Also I think that this test is unique to raring.

gtkperf with "uxa"

GtkRadioButton - time:  0.61
GtkTextView - Add text - time:  1.88
GtkTextView - Scroll - time:  0.38
GtkDrawingArea - Lines - time:  4.96
GtkDrawingArea - Circles - time:  5.35
GtkDrawingArea - Text - time:  5.97
GtkDrawingArea - Pixbufs - time:  1.70
 --- 
Total time: 37.81

Gosh, you have about the same quickness as my Dell netbook, mini-10n. Unity is okay there but I don't do graphic design with such a slow box. <smile>

---

### Post by ventrical on 2013-01-11
> **fjgaude said:**
> Gosh, you have about the same quickness as my Dell netbook, mini-10n. Unity is okay there but I don't do graphic design with such a slow box. <smile>


 I must apologize for being off topic on myself. That test refers to another machine (intel graphics) running a test requested in another thread .. so I had thought I would put the results here. it is a little slower than other boxes I have but it is 64bit intel and I like to experiment with it.

[http://ubuntuforums.org/showthread.php?t=2103579](http://ubuntuforums.org/showthread.php?t=2103579)

---

### Post by gwjvan on 2013-01-11
I'm guessing the increase in speed for some people is largely driver improvements.

I'm seeing the same slowdowns with the Unity Plugin and the Dash that I have seen in the past. Dash is missing the first character(s) I type sometimes (Synapse doesn't miss anything, on the same hardware), and window movements/animations are dropping more frames than Compiz+XFCE. My GPU isn't benefiting from the driver improvements we've seen recently.
 
 
 .

---

### Post by ventrical on 2013-01-11
> **gwjvan said:**
> I'm guessing the increase in speed for some people is largely driver improvements.

I'm seeing the same slowdowns with the Unity Plugin and the Dash that I have seen in the past. Dash is missing the first character(s) I type sometimes (Synapse doesn't miss anything, on the same hardware), and window movements/animations are dropping more frames than Compiz+XFCE. My GPU isn't benefiting from the driver improvements we've seen recently.
 
 
 .

  I can agree in part but I think there is something more behind the scenes going on. I originally started this thread because I had downloaded a daily .iso back several weeks ago (I call it a phenom.iso) and I ran it on my Dell Dimension 3100 which works just naturally fast with Unity 3D and compiz.  Hmmm.. I think I am going to go and visit that machine now. I think there is a combination of depends, not just drivers. I wish I could pin it down precisely (no pun intended: :)
lol

---

### Post by ventrical on 2013-01-11
Anyone else using gtkperf ??/ Could you tell me how many 'rounds" that your default is set to?

thanks

---

### Post by ventrical on 2013-01-11
I just upgraded my Dell D 3100 to raring from Quantal. Despite a few  really buggy problems (the upgrade installed the Radiance Theme) all I had to do was choose Ambiance from Desktop settings themes and it corrected all my settings. Everything was borked after upgrade. No terminal command line and icons missing from Unity lancher. Resetting back to ambiance fixed everything .. including borked compiz settings manager.

 Now having a hard install on an overall faster system I am going to try the SNA experiment on 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)


Definitely ccsm and unity are more responsive to the naked eye just after upgrade. Overall the entire system appears more responsive.

---

### Post by fjgaude on 2013-01-11
> **ventrical said:**
> Anyone else using gtkperf ??/ Coul dyou tell me how many 'rounds" that you default is set to?

thanks

As always, 100.

---

### Post by ventrical on 2013-01-11
> **fjgaude said:**
> As always, 100.


Maybe it's time for me to get an Intel i5 or Phenom or something :) lol

---

### Post by fjgaude on 2013-01-11
> **ventrical said:**
> Maybe it's time for me to get an Intel i5 or Phenom or something :) lol

I build my own, since 1980, but of course not laptops or netbooks. <smile>

---

### Post by nuttzo31 on 2013-01-11
> **fjgaude said:**
> I build my own, since 1980, but of course not laptops or netbooks. <smile>

I also build my own it's very easy to do anyone can do it.

Huge improvements in terms of speed and stability in raring and unity , it's the first version of ubuntu that has ran smoothly for me with the nvidia 310 driver.

The latest kernel 3.8 also seems to have solved my random full lockup problem as well and raring is so stable i am using it on my main machine with virtually no bugs affecting me.

---

### Post by ventrical on 2013-01-12
Same here .. plus orphaned PCs from the recycle bin.  No money , no funny! :) I try to work frugally.

---

### Post by serdotlinecho on 2013-01-12
Love the speed with intel SNA on my netbook(well, according to gtkperf......) 
But how do i make the dash smaller or resize it on this netbook?:lolflag:

[IMG]http://i.imgur.com/hpyTD.png[/IMG]

---

### Post by gwjvan on 2013-01-12
I just tried 13.04 on a faster machine than the one in my earlier post, and I'm still seeing 12.10 performance in 13.04. I can't say for sure, but it actually looks like the Dash is even receiving/handling the characters faster in 12.10 than in 13.04...

So, 2 of the computers I've tried so far show no difference in speed with 13.04. (Though the software center appears to have sped up)

I'm guessing if I try 13.04 on my computer which has a newish Nvidia card I'll see improvement.


Also: Last summer, there was an issue with the Intel graphics driver which caused Unity to perform slowly on my laptop, and at some random point it was fixed, causing my laptop to perform better. Maybe these speed improvements are bug fixes on whatever hardware some people are using.


Edit, side note: I just set up XFCE on this other machine in 12.10 to run with Compiz--- it is beautiful. I don't understand why Unity can't run as well with Compiz with the same settings. The animations seem to not be missing any frames (XFCE+Compiz), whereas simply turning the Unity Plugin on (via Unity 3D session) seems to cause frames to drop consistently.

.

---

### Post by gwjvan on 2013-01-12
> **serdotlinecho said:**
> But how do i make the dash smaller or resize it on this netbook?
 
It looks like there is no option for that (as far as I can tell, maybe someone else knows more about it)

---

### Post by gwjvan on 2013-01-12
And I want Canonical to hit a home run with Unity-- I think they can (I think Unity is on the right track). But they need to improve the speed of the basic tools of the interface.

For example, I want to be able to hit the Dash reveal key combo (Super key, by default) plus a few characters of the application name I want, and hit enter within the matter of a split second and know that my application is being launched. There are a variety of tools on Linux that do this already, and I don't see why Unity shouldn't be able to achieve this. (This isn't an attack on Unity, but a realistic assessment: The tools need to speed up in order to not break a user's flow)


.

---

### Post by zika on 2013-01-12
> **gwjvan said:**
> It looks like there is no option for that (as far as I can tell, maybe someone else knows more about it)
LauncherIconSize in CCSM>Unity>Launcher...?

---

### Post by fjgaude on 2013-01-12
> **zika said:**
> LauncherIconSize in CCSM>Unity>Launcher...?
I can reduce the launcher ions a little with ccsm but not by much, 48 to 42, on my Poulsbo netbook., Dell mini-10n.

---

### Post by zika on 2013-01-12
> **fjgaude said:**
> I can reduce the launcher ions a little with ccsm but not by much, 48 to 42, on my Poulsbo netbook., Dell mini-10n.Do not kill the messenger...

---

### Post by mc4man on 2013-01-12
> **serdotlinecho said:**
> Love the speed with intel SNA on my netbook(well, according to gtkperf......) 
But how do i make the dash smaller or resize it on this netbook?:lolflag:

Don't believe that's user controllable any more. Over unity releases how Dash size is set has changed several times, haven't paid much attention because it's always been fine here on various.

Ex. on this 13"  laptop, 1200X800
xwininfo: Window id: 0x2800007 "unity-dash"

  Absolute upper-left X:  57
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 991
  Height: 640

---

### Post by ELD on 2013-01-12
Icon size is usually in appearance settings? At least in 12.10 it was have they removed that ability?

---

### Post by ventrical on 2013-01-12
I just slid mine down to 32 but now the right mouse click will not work on the Desktop to bring up those menu items.

---

### Post by cariboo on 2013-01-12
> **ELD said:**
> Icon size is usually in appearance settings? At least in 12.10 it was have they removed that ability?

i'm not on my raring install at the moment, but you can still resize the ***Launcher*** icons. You can't and never have been able to resize the dash icons. I haven't looked lately, but there used to be a setting to change the dash size for either a desktop system or notebook/netbook, but it only allowed you to change the size from approximately full screen to 80%.

---

### Post by nuttzo31 on 2013-01-12
> **gwjvan said:**
> I just tried 13.04 on a faster machine than the one in my earlier post, and I'm still seeing 12.10 performance in 13.04. I can't say for sure, but it actually looks like the Dash is even receiving/handling the characters faster in 12.10 than in 13.04...

So, 2 of the computers I've tried so far show no difference in speed with 13.04. (Though the software center appears to have sped up)

I'm guessing if I try 13.04 on my computer which has a newish Nvidia card I'll see improvement.


Also: Last summer, there was an issue with the Intel graphics driver which caused Unity to perform slowly on my laptop, and at some random point it was fixed, causing my laptop to perform better. Maybe these speed improvements are bug fixes on whatever hardware some people are using.


Edit, side note: I just set up XFCE on this other machine in 12.10 to run with Compiz--- it is beautiful. I don't understand why Unity can't run as well with Compiz with the same settings. The animations seem to not be missing any frames (XFCE+Compiz), whereas simply turning the Unity Plugin on (via Unity 3D session) seems to cause frames to drop consistently.

.

If your computer has an nvidia card are you using the 310.14 or later drivers, there was a significant improvement for me using these drivers than the earlier ones.

---

