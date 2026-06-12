---
title: "Corrupted graphics on Unity login in 12.04"
date: 2012-01-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Marcelo Ruiz on 2012-01-10
Hi everyone!
I have been having trouble trying to run 12.04 Alpha on my Toshiba Qosmio X500. I created a live pen drive and each time the dot-animated Ubuntu loading screen disappears to switch to Unity, graphics are corrupted (garbage is shown in the screen). I am able to switch to TTY1, so the system is not crashed.
I reported the bug (the link is: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/909926]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/909926")), which has been an issue since Maverick, and I was suggested to install the nVidia proprietary drivers (something that did fix the issue in the past) but it did not solve the problem. This mistake makes 12.04 unusable in my laptop.
I was wondering if any of you had the same problem and if (and how) you dealt with it.
Thanks!

---

### Post by coffeecat on 2012-01-10
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by prshah on 2012-01-10
> **Marcelo Ruiz said:**
> graphics are corrupted (garbage is shown in the screen). 

Hi, please see my old post in [http://ubuntuforums.org/showpost.php?p=7132514&postcount=2](http://ubuntuforums.org/showpost.php?p=7132514&postcount=2) (with screen photos) to check if the problem you are facing is similar. If it is, the correct thing to do is to get the correct native resolution. 

Unfortunately, I think current Ubuntu versions ignore xorg.conf, so I don't think you can fix it the way suggested in the post. 

Instead, From your corrupted screen, try using Ctrl+Alt+Numpad+ or Ctrl+Alt+Numpad- to cycle between resolutions. You may have to do this multiple times. 

A look at your /etc/log/Xorg.0.log file may yield some clues; post it here (after sanitization).

---

### Post by Marcelo Ruiz on 2012-01-11
I tried using Ctrl+Alt+Numpad+ or Ctrl+Alt+Numpad- to cycle between resolutions, but it did not work. Adding "nomodeset" to the kernel boot options allowed me to use Unity to install the nvidia-current package, but now the screen goes black and the computer freezes... :S

---

### Post by zika on 2012-01-12
> **prshah said:**
> Unfortunately, I think current Ubuntu versions ignore xorg.conf, so I don't think you can fix it the way suggested in the post.No they do not. They do not generate one but they do obey one if it exists. To make one You can exit LightDM, stop it, and do```
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
```
That helped me regain use of Gallium on my ATI card...

---

### Post by cariboo on 2012-01-12
If you're running nvidia graphics:

```
sudo nvidia-xconfig
```

works to create an /etc/X11/xorg.conf

---

### Post by Marcelo Ruiz on 2012-01-12
Hi,
Thanks for the messages. 
I erased the pendrive, reinstalled 12.04, then the nvidia drivers and I run 

```
sudo nvidia-xconfig
```

the command went fine, but I still get the black desktop after reboot and the computer freezes.
Should I also run

```

sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf

```

after running nvidia-xconfig?
Thanks!

---

### Post by effenberg0x0 on 2012-01-12
I believe this is a "how do I install NVidia drivers in any Ubuntu version" question, not properly related to PP.

If I'm right, you would probably receive much better help at the "General Help" section of this forum. However, the minute they see the words "12.04" or "PP", they send users to here. If you search that area for detailed instructions on how to deal with NVidia drivers, you'll find very complete tutorials (even I have written instructions there a couple million times, but there are more complete / better / proper tutorials).

If you search for my handle and NVidia you'll find stuff like:
[http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia](http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia)
In my threads you'll also find info on how to fix a broken lightdm setup.

Also search for +"MAFoElffen" +"nvidia" there too. He's a talented tutorial writer that has posted detailed instructions on how to fix your current issue.

Basically what you'll read in any of these tutorials is this:
**1) Switch to VT6:**
Press Ctrl+Alt+F6 and login

**2) Kill X **
sudo service lightdm stop && sleep 10
sudo killall -s KILL lightdm
sudo service gdm stop && sleep 10
sudo killall -s KILL gdm
 sudo killall -s KILL $(pidof /usr/bin/X)

**3) Purge current drivers**
sudo apt-get remove --purge nvidia* fglrx*

**4) cd to your home folder and get/chmod/run the installer**
cd
mkdir nvidia-installer
cd nvidia-installer
[B]
For 32-bit Ubuntu:[/B] wget [http://us.download.nvidia.com/XFree86/Linux-x86/290.10/NVIDIA-Linux-x86-290.10.run](http://us.download.nvidia.com/XFree86/Linux-x86/290.10/NVIDIA-Linux-x86-290.10.run)
[B]
For 64-bit Ubuntu:[/B] wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run)

chmod +x NVIDIA-Linux-x86_64-290.10.run
sudo ./ NVIDIA-Linux-x86_64-290.10.run
Answer "YES" to all questions during install.

**5) Restart lightdm**
sudo service lightdm stop
sudo service lightdm start

If the above doesn't work, what anyone will tell you (or you'll read in any thread / tutorial) is: Check for blacklisted card, lightdm settings, if nouveau is in use you might have to blacklist it /boot / purge nouveau before installing proprietary drivers, disable plymouth so you have a decent informative boot, post /etc/X11/xorg.0.log or no one can guess what's going there, etc.

---

### Post by P-I H on 2012-01-13
Both Ubuntu 11.10 and Ubuntu 12.04 will not install OK, in my test system with an Nvividia GTS250 card and a Gigabyte MA770-UD3 motherboard. I suppose it's the Noveau driver that misbehaves.

I have to set "nomodeset" to get the livecd to boot and to install the system.
To boot after the install I have to use "recovery mode" and "resume Resume to normal boot" at the presented menu. The system will now boot with a strange resulution, but works fine.
After boot I can install the Nvidia driver with Additional Drivers. I use Nvidia current.
After installation of the Nvidia driver the system works OK.

In case I do not set "nomodeset", I just get a purple screen and in case I do not boot with recovery mode, the boot ends with a corrupt login screen there nothing works and the only thing to do is to use the power switch.

---

### Post by lucazade on 2012-01-13
Nvidia 250gts doesn't work well with nouveau... screen become corrupted after some mins of use.. this bug unfortunately has never been solved.
So anytime I have to install ubuntu on this pc I unload the nouveau driver at loading and after installation I install the nvidia binary blob that works well.

---

### Post by Marcelo Ruiz on 2012-01-16
I blacklisted nouveau and still no luck.
Following directions of other post, after I installed the nvidia driver blob I run nvidia-xconfig and then deleted xorg.conf.
This is the first attempt log file (with nvidia-generated xorg.conf):

```

X.Org X Server 1.10.4
Release Date: 2011-08-19
[    78.870] X Protocol Version 11, Revision 0
[    78.870] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    78.870] Current Operating System: Linux ubuntu 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64
[    78.870] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    78.870] Build Date: 09 December 2011  11:36:47AM
[    78.870] xorg-server 2:1.10.4-1ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    78.870] Current version of pixman: 0.24.0
[    78.870] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    78.870] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    78.870] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 16 20:17:53 2012
[    78.871] (==) Using config file: "/etc/X11/xorg.conf"
[    78.871] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    78.873] (==) ServerLayout "Layout0"
[    78.873] (**) |-->Screen "Screen0" (0)
[    78.873] (**) |   |-->Monitor "Monitor0"
[    78.873] (**) |   |-->Device "Device0"
[    78.873] (**) |-->Input Device "Keyboard0"
[    78.873] (**) |-->Input Device "Mouse0"
[    78.873] (==) Automatically adding devices
[    78.873] (==) Automatically enabling devices
[    79.414] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    79.414] 	Entry deleted from font path.
[    79.414] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    79.414] 	Entry deleted from font path.
[    79.414] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    79.414] 	Entry deleted from font path.
[    79.416] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    79.416] 	Entry deleted from font path.
[    79.416] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    79.416] 	Entry deleted from font path.
[    79.417] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    79.417] 	Entry deleted from font path.
[    79.417] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    79.417] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    79.417] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    79.417] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    79.417] (WW) Disabling Keyboard0
[    79.417] (WW) Disabling Mouse0
[    79.417] (II) Loader magic: 0x7e0220
[    79.417] (II) Module ABI versions:
[    79.417] 	X.Org ANSI C Emulation: 0.4
[    79.417] 	X.Org Video Driver: 10.0
[    79.417] 	X.Org XInput driver : 12.3
[    79.417] 	X.Org Server Extension : 5.0
[    79.418] (--) PCI:*(0:1:0:0) 10de:0cb1:1179:ff50 rev 162, Mem @ 0xcc000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    79.418] (II) Open ACPI successful (/var/run/acpid.socket)
[    79.418] (II) LoadModule: "extmod"
[    79.442] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    79.459] (II) Module extmod: vendor="X.Org Foundation"
[    79.459] 	compiled for 1.10.4, module version = 1.0.0
[    79.459] 	Module class: X.Org Server Extension
[    79.459] 	ABI class: X.Org Server Extension, version 5.0
[    79.459] (II) Loading extension MIT-SCREEN-SAVER
[    79.459] (II) Loading extension XFree86-VidModeExtension
[    79.459] (II) Loading extension XFree86-DGA
[    79.459] (II) Loading extension DPMS
[    79.459] (II) Loading extension XVideo
[    79.459] (II) Loading extension XVideo-MotionCompensation
[    79.459] (II) Loading extension X-Resource
[    79.459] (II) LoadModule: "dbe"
[    79.460] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    79.492] (II) Module dbe: vendor="X.Org Foundation"
[    79.492] 	compiled for 1.10.4, module version = 1.0.0
[    79.492] 	Module class: X.Org Server Extension
[    79.492] 	ABI class: X.Org Server Extension, version 5.0
[    79.492] (II) Loading extension DOUBLE-BUFFER
[    79.492] (II) LoadModule: "glx"
[    79.493] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    94.896] (II) Module glx: vendor="NVIDIA Corporation"
[    94.913] 	compiled for 4.0.2, module version = 1.0.0
[    94.913] 	Module class: X.Org Server Extension
[    94.913] (II) NVIDIA GLX Module  290.10  Wed Nov 16 18:01:24 PST 2011
[    94.913] (II) Loading extension GLX
[    94.913] (II) LoadModule: "record"
[    94.914] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    94.915] (II) Module record: vendor="X.Org Foundation"
[    94.915] 	compiled for 1.10.4, module version = 1.13.0
[    94.915] 	Module class: X.Org Server Extension
[    94.915] 	ABI class: X.Org Server Extension, version 5.0
[    94.915] (II) Loading extension RECORD
[    94.915] (II) LoadModule: "dri"
[    94.915] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    94.926] (II) Module dri: vendor="X.Org Foundation"
[    94.926] 	compiled for 1.10.4, module version = 1.0.0
[    94.926] 	ABI class: X.Org Server Extension, version 5.0
[    94.926] (II) Loading extension XFree86-DRI
[    94.926] (II) LoadModule: "dri2"
[    94.926] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    94.927] (II) Module dri2: vendor="X.Org Foundation"
[    94.927] 	compiled for 1.10.4, module version = 1.2.0
[    94.927] 	ABI class: X.Org Server Extension, version 5.0
[    94.927] (II) Loading extension DRI2
[    94.927] (II) LoadModule: "nvidia"
[    94.927] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so

``` 

This is the second attempt log file (with no xorg.conf):

```

[    78.402] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    78.402] X Protocol Version 11, Revision 0
[    78.402] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    78.402] Current Operating System: Linux ubuntu 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64
[    78.402] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz --
[    78.402] Build Date: 09 December 2011  11:36:47AM
[    78.402] xorg-server 2:1.10.4-1ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    78.402] Current version of pixman: 0.24.0
[    78.402] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    78.402] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    78.402] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 16 20:21:52 2012
[    78.403] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    78.415] (==) No Layout section.  Using the first Screen section.
[    78.415] (==) No screen section available. Using defaults.
[    78.415] (**) |-->Screen "Default Screen Section" (0)
[    78.415] (**) |   |-->Monitor "<default monitor>"
[    78.415] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    78.415] (==) Automatically adding devices
[    78.415] (==) Automatically enabling devices
[    78.418] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    78.418] 	Entry deleted from font path.
[    78.418] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    78.418] 	Entry deleted from font path.
[    78.418] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    78.418] 	Entry deleted from font path.
[    78.420] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    78.420] 	Entry deleted from font path.
[    78.420] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    78.420] 	Entry deleted from font path.
[    78.420] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    78.420] 	Entry deleted from font path.
[    78.420] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    78.420] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    78.420] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    78.420] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    78.420] (II) Loader magic: 0x7e0220
[    78.420] (II) Module ABI versions:
[    78.420] 	X.Org ANSI C Emulation: 0.4
[    78.420] 	X.Org Video Driver: 10.0
[    78.420] 	X.Org XInput driver : 12.3
[    78.420] 	X.Org Server Extension : 5.0
[    78.422] (--) PCI:*(0:1:0:0) 10de:0cb1:1179:ff50 rev 162, Mem @ 0xcc000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    78.422] (II) Open ACPI successful (/var/run/acpid.socket)
[    78.422] (II) LoadModule: "extmod"
[    78.451] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    78.490] (II) Module extmod: vendor="X.Org Foundation"
[    78.490] 	compiled for 1.10.4, module version = 1.0.0
[    78.490] 	Module class: X.Org Server Extension
[    78.490] 	ABI class: X.Org Server Extension, version 5.0
[    78.490] (II) Loading extension MIT-SCREEN-SAVER
[    78.490] (II) Loading extension XFree86-VidModeExtension
[    78.490] (II) Loading extension XFree86-DGA
[    78.490] (II) Loading extension DPMS
[    78.490] (II) Loading extension XVideo
[    78.490] (II) Loading extension XVideo-MotionCompensation
[    78.490] (II) Loading extension X-Resource
[    78.490] (II) LoadModule: "dbe"
[    78.490] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    78.523] (II) Module dbe: vendor="X.Org Foundation"
[    78.523] 	compiled for 1.10.4, module version = 1.0.0
[    78.523] 	Module class: X.Org Server Extension
[    78.523] 	ABI class: X.Org Server Extension, version 5.0
[    78.523] (II) Loading extension DOUBLE-BUFFER
[    78.523] (II) LoadModule: "glx"
[    78.523] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    88.700] (II) Module glx: vendor="NVIDIA Corporation"
[    88.717] 	compiled for 4.0.2, module version = 1.0.0
[    88.717] 	Module class: X.Org Server Extension
[    88.717] (II) NVIDIA GLX Module  290.10  Wed Nov 16 18:01:24 PST 2011
[    88.717] (II) Loading extension GLX
[    88.717] (II) LoadModule: "record"
[    88.717] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    88.719] (II) Module record: vendor="X.Org Foundation"
[    88.719] 	compiled for 1.10.4, module version = 1.13.0
[    88.719] 	Module class: X.Org Server Extension
[    88.719] 	ABI class: X.Org Server Extension, version 5.0
[    88.719] (II) Loading extension RECORD
[    88.719] (II) LoadModule: "dri"
[    88.719] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    88.733] (II) Module dri: vendor="X.Org Foundation"
[    88.734] 	compiled for 1.10.4, module version = 1.0.0
[    88.734] 	ABI class: X.Org Server Extension, version 5.0
[    88.734] (II) Loading extension XFree86-DRI
[    88.734] (II) LoadModule: "dri2"
[    88.734] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    88.735] (II) Module dri2: vendor="X.Org Foundation"
[    88.735] 	compiled for 1.10.4, module version = 1.2.0
[    88.735] 	ABI class: X.Org Server Extension, version 5.0
[    88.735] (II) Loading extension DRI2
[    88.735] (==) Matched nvidia as autoconfigured driver 0
[    88.735] (==) Matched nouveau as autoconfigured driver 1
[    88.735] (==) Matched nv as autoconfigured driver 2
[    88.735] (==) Matched vesa as autoconfigured driver 3
[    88.735] (==) Matched fbdev as autoconfigured driver 4
[    88.735] (==) Assigned the driver to the xf86ConfigLayout
[    88.735] (II) LoadModule: "nvidia"
[    88.735] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    88.945] (II) Module nvidia: vendor="NVIDIA Corporation"
[    88.961] 	compiled for 4.0.2, module version = 1.0.0
[    88.961] 	Module class: X.Org Video Driver
[    89.013] (II) LoadModule: "nouveau"
[    89.013] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    89.058] (II) Module nouveau: vendor="X.Org Foundation"
[    89.058] 	compiled for 1.10.4, module version = 0.0.16
[    89.058] 	Module class: X.Org Video Driver
[    89.058] 	ABI class: X.Org Video Driver, version 10.0
[    89.058] (II) LoadModule: "nv"
[    89.059] (WW) Warning, couldn't open module nv
[    89.059] (II) UnloadModule: "nv"
[    89.059] (II) Unloading nv
[    89.059] (EE) Failed to load module "nv" (module does not exist, 0)
[    89.059] (II) LoadModule: "vesa"
[    89.059] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    89.060] (II) Module vesa: vendor="X.Org Foundation"
[    89.060] 	compiled for 1.10.2, module version = 2.3.0
[    89.060] 	Module class: X.Org Video Driver
[    89.060] 	ABI class: X.Org Video Driver, version 10.0
[    89.060] (II) LoadModule: "fbdev"
[    89.060] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    89.077] (II) Module fbdev: vendor="X.Org Foundation"
[    89.077] 	compiled for 1.10.0, module version = 0.4.2
[    89.077] 	ABI class: X.Org Video Driver, version 10.0
[    89.077] (II) NVIDIA dlloader X Driver  290.10  Wed Nov 16 17:41:10 PST 2011
[    89.077] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    89.095] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    89.095] (II) NOUVEAU driver for NVIDIA chipset families :
[    89.095] 	RIVA TNT        (NV04)
[    89.095] 	RIVA TNT2       (NV05)
[    89.095] 	GeForce 256     (NV10)
[    89.095] 	GeForce 2       (NV11, NV15)
[    89.095] 	GeForce 4MX     (NV17, NV18)
[    89.095] 	GeForce 3       (NV20)
[    89.095] 	GeForce 4Ti     (NV25, NV28)
[    89.095] 	GeForce FX      (NV3x)
[    89.095] 	GeForce 6       (NV4x)
[    89.095] 	GeForce 7       (G7x)
[    89.095] 	GeForce 8       (G8x)
[    89.095] 	GeForce GTX 200 (NVA0)
[    89.095] 	GeForce GTX 400 (NVC0)
[    89.095] (II) VESA: driver for VESA chipsets: vesa
[    89.095] (II) FBDEV: driver for framebuffer: fbdev
[    89.095] (++) using VT number 7

[    89.109] (II) Loading sub module "fb"
[    89.109] (II) LoadModule: "fb"
[    89.109] (II) Loading /usr/lib/xorg/modules/libfb.so
[    89.122] (II) Module fb: vendor="X.Org Foundation"
[    89.122] 	compiled for 1.10.4, module version = 1.0.0
[    89.122] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    89.122] (II) Loading sub module "wfb"
[    89.122] (II) LoadModule: "wfb"
[    89.122] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    89.148] (II) Module wfb: vendor="X.Org Foundation"
[    89.148] 	compiled for 1.10.4, module version = 1.0.0
[    89.148] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    89.148] (II) Loading sub module "ramdac"
[    89.148] (II) LoadModule: "ramdac"
[    89.148] (II) Module "ramdac" already built-in
[    89.193] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    89.193] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    89.193] (II) Loading /usr/lib/xorg/modules/libfb.so
[    89.222] (WW) Falling back to old probe method for vesa
[    89.222] (WW) Falling back to old probe method for fbdev
[    89.222] (II) Loading sub module "fbdevhw"
[    89.222] (II) LoadModule: "fbdevhw"
[    89.222] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    89.223] (II) Module fbdevhw: vendor="X.Org Foundation"
[    89.223] 	compiled for 1.10.4, module version = 0.0.2
[    89.223] 	ABI class: X.Org Video Driver, version 10.0
[    89.223] (EE) open /dev/fb0: No such file or directory
[    89.223] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    89.223] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    89.223] (==) NVIDIA(0): RGB weight 888
[    89.223] (==) NVIDIA(0): Default visual is TrueColor
[    89.223] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    89.224] (**) NVIDIA(0): Enabling 2D acceleration
[    99.306] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    99.306] (II) NVIDIA(GPU-0):     Vision stereo.
[    99.311] (II) NVIDIA(0): NVIDIA GPU GeForce GTS 360M (GT215) at PCI:1:0:0 (GPU-0)
[    99.311] (--) NVIDIA(0): Memory: 1048576 kBytes
[    99.311] (--) NVIDIA(0): VideoBIOS: 70.15.43.00.04
[    99.311] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    99.311] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    99.311] (--) NVIDIA(0): Connected display device(s) on GeForce GTS 360M at PCI:1:0:0
[    99.311] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[    99.311] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    99.311] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[   102.315] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[   102.315] (**) NVIDIA(0):     enabled on all display devices.
[   102.339] (II) NVIDIA(0): Assigned Display Device: DFP-0
[   102.339] (==) NVIDIA(0): 
[   102.339] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   102.339] (==) NVIDIA(0):     will be used as the requested mode.
[   102.339] (==) NVIDIA(0): 
[   102.339] (II) NVIDIA(0): Validated modes:
[   102.339] (II) NVIDIA(0):     "nvidia-auto-select"
[   102.339] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   103.400] (--) NVIDIA(0): DPI set to (118, 119); computed from "UseEdidDpi" X config
[   103.400] (--) NVIDIA(0):     option
[   103.400] (II) UnloadModule: "nouveau"
[   103.400] (II) Unloading nouveau
[   103.400] (II) UnloadModule: "vesa"
[   103.400] (II) Unloading vesa
[   103.400] (II) UnloadModule: "fbdev"
[   103.400] (II) Unloading fbdev
[   103.400] (II) UnloadModule: "fbdevhw"
[   103.400] (II) Unloading fbdevhw
[   103.400] (--) Depth 24 pixmap format is 32 bpp
[   103.400] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   106.418] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   108.436] (EE) NVIDIA(0): WAIT: (E, 0, 0x857d)

```

I will copy and use xorg.conf that is currently working on my system (Maverick) and post back.

---

### Post by Marcelo Ruiz on 2012-01-16
With Maverick's xorg.conf the log is as follows:

```

X.Org X Server 1.10.4
Release Date: 2011-08-19
[    54.605] X Protocol Version 11, Revision 0
[    54.605] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    54.605] Current Operating System: Linux ubuntu 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64
[    54.605] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz --
[    54.605] Build Date: 09 December 2011  11:36:47AM
[    54.605] xorg-server 2:1.10.4-1ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    54.605] Current version of pixman: 0.24.0
[    54.605] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    54.605] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    54.605] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 16 20:41:30 2012
[    54.608] (==) Using config file: "/etc/X11/xorg.conf"
[    54.608] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    54.781] (==) ServerLayout "Layout0"
[    54.781] (**) |-->Screen "Screen0" (0)
[    54.781] (**) |   |-->Monitor "Monitor0"
[    54.781] (**) |   |-->Device "Device0"
[    54.781] (**) |-->Input Device "Keyboard0"
[    54.781] (**) |-->Input Device "Mouse0"
[    54.781] (**) Option "Xinerama" "0"
[    54.781] (==) Automatically adding devices
[    54.781] (==) Automatically enabling devices
[    54.813] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    54.813] 	Entry deleted from font path.
[    54.813] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    54.813] 	Entry deleted from font path.
[    54.813] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    54.813] 	Entry deleted from font path.
[    54.836] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    54.836] 	Entry deleted from font path.
[    54.836] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    54.836] 	Entry deleted from font path.
[    54.836] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    54.836] 	Entry deleted from font path.
[    54.836] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    54.836] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    54.836] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    54.836] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    54.836] (WW) Disabling Keyboard0
[    54.836] (WW) Disabling Mouse0
[    54.836] (II) Loader magic: 0x7e0220
[    54.836] (II) Module ABI versions:
[    54.836] 	X.Org ANSI C Emulation: 0.4
[    54.836] 	X.Org Video Driver: 10.0
[    54.836] 	X.Org XInput driver : 12.3
[    54.836] 	X.Org Server Extension : 5.0
[    54.837] (--) PCI:*(0:1:0:0) 10de:0cb1:1179:ff50 rev 162, Mem @ 0xcc000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    54.837] (II) Open ACPI successful (/var/run/acpid.socket)
[    54.837] (II) "extmod" will be loaded by default.
[    54.837] (II) "dbe" will be loaded by default.
[    54.837] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    54.837] (II) "record" will be loaded by default.
[    54.837] (II) "dri" will be loaded by default.
[    54.837] (II) "dri2" will be loaded by default.
[    54.837] (II) LoadModule: "glx"
[    54.878] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    57.015] (II) Module glx: vendor="NVIDIA Corporation"
[    57.025] 	compiled for 4.0.2, module version = 1.0.0
[    57.025] 	Module class: X.Org Server Extension
[    57.025] (II) NVIDIA GLX Module  290.10  Wed Nov 16 18:01:24 PST 2011
[    57.025] (II) Loading extension GLX
[    57.025] (II) LoadModule: "extmod"
[    57.025] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    57.042] (II) Module extmod: vendor="X.Org Foundation"
[    57.042] 	compiled for 1.10.4, module version = 1.0.0
[    57.042] 	Module class: X.Org Server Extension
[    57.042] 	ABI class: X.Org Server Extension, version 5.0
[    57.042] (II) Loading extension MIT-SCREEN-SAVER
[    57.042] (II) Loading extension XFree86-VidModeExtension
[    57.042] (II) Loading extension XFree86-DGA
[    57.043] (II) Loading extension DPMS
[    57.043] (II) Loading extension XVideo
[    57.043] (II) Loading extension XVideo-MotionCompensation
[    57.043] (II) Loading extension X-Resource
[    57.043] (II) LoadModule: "dbe"
[    57.043] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    57.060] (II) Module dbe: vendor="X.Org Foundation"
[    57.060] 	compiled for 1.10.4, module version = 1.0.0
[    57.060] 	Module class: X.Org Server Extension
[    57.060] 	ABI class: X.Org Server Extension, version 5.0
[    57.060] (II) Loading extension DOUBLE-BUFFER
[    57.060] (II) LoadModule: "record"
[    57.061] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    57.062] (II) Module record: vendor="X.Org Foundation"
[    57.062] 	compiled for 1.10.4, module version = 1.13.0
[    57.062] 	Module class: X.Org Server Extension
[    57.062] 	ABI class: X.Org Server Extension, version 5.0
[    57.062] (II) Loading extension RECORD
[    57.062] (II) LoadModule: "dri"
[    57.062] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    57.075] (II) Module dri: vendor="X.Org Foundation"
[    57.075] 	compiled for 1.10.4, module version = 1.0.0
[    57.075] 	ABI class: X.Org Server Extension, version 5.0
[    57.075] (II) Loading extension XFree86-DRI
[    57.075] (II) LoadModule: "dri2"
[    57.075] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    57.077] (II) Module dri2: vendor="X.Org Foundation"
[    57.077] 	compiled for 1.10.4, module version = 1.2.0
[    57.077] 	ABI class: X.Org Server Extension, version 5.0
[    57.077] (II) Loading extension DRI2
[    57.077] (II) LoadModule: "nvidia"
[    57.077] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    57.187] (II) Module nvidia: vendor="NVIDIA Corporation"
[    57.195] 	compiled for 4.0.2, module version = 1.0.0
[    57.196] 	Module class: X.Org Video Driver
[    57.225] (II) NVIDIA dlloader X Driver  290.10  Wed Nov 16 17:41:10 PST 2011
[    57.225] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    57.231] (++) using VT number 7

[    57.240] (II) Loading sub module "fb"
[    57.240] (II) LoadModule: "fb"
[    57.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    57.253] (II) Module fb: vendor="X.Org Foundation"
[    57.253] 	compiled for 1.10.4, module version = 1.0.0
[    57.253] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    57.253] (II) Loading sub module "wfb"
[    57.253] (II) LoadModule: "wfb"
[    57.253] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    57.274] (II) Module wfb: vendor="X.Org Foundation"
[    57.274] 	compiled for 1.10.4, module version = 1.0.0
[    57.274] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    57.274] (II) Loading sub module "ramdac"
[    57.274] (II) LoadModule: "ramdac"
[    57.274] (II) Module "ramdac" already built-in
[    57.298] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    57.298] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    57.298] (II) Loading /usr/lib/xorg/modules/libfb.so
[    57.314] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    57.314] (==) NVIDIA(0): RGB weight 888
[    57.314] (==) NVIDIA(0): Default visual is TrueColor
[    57.314] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    57.314] (**) NVIDIA(0): Option "NoLogo" "True"
[    57.314] (**) NVIDIA(0): Option "RenderAccel" "on"
[    57.314] (**) NVIDIA(0): Option "TwinView" "0"
[    57.314] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    57.314] (**) NVIDIA(0): Option "UseEvents" "on"
[    57.314] (**) NVIDIA(0): Enabling RENDER acceleration
[    57.314] (**) NVIDIA(0): Enabling 2D acceleration
[    64.185] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    64.185] (II) NVIDIA(GPU-0):     Vision stereo.
[    64.188] (II) NVIDIA(0): NVIDIA GPU GeForce GTS 360M (GT215) at PCI:1:0:0 (GPU-0)
[    64.188] (--) NVIDIA(0): Memory: 1048576 kBytes
[    64.188] (--) NVIDIA(0): VideoBIOS: 70.15.43.00.04
[    64.188] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    64.188] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    64.188] (--) NVIDIA(0): Connected display device(s) on GeForce GTS 360M at PCI:1:0:0
[    64.188] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[    64.188] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    64.188] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    67.196] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
[    67.196] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    67.196] (**) NVIDIA(0):     enabled on all display devices.
[    67.219] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    67.220] (II) NVIDIA(0): Validated modes:
[    67.220] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    67.220] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    68.289] (--) NVIDIA(0): DPI set to (118, 119); computed from "UseEdidDpi" X config
[    68.289] (--) NVIDIA(0):     option
[    68.289] (--) Depth 24 pixmap format is 32 bpp
[    68.289] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    71.311] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    73.330] (EE) NVIDIA(0): WAIT: (E, 0, 0x857d)

```

After reinstalling the live CD like 20 times and following effenberg0x0's instructions to the leter (thank you very much, by the way!), I am extremely frustrated.
Any other ideas?
Thanks!

---

### Post by effenberg0x0 on 2012-01-16
> **Marcelo Ruiz said:**
> With Maverick's xorg.conf the log is as follows:
...
After reinstalling the live CD like 20 times and following effenberg0x0's instructions to the leter (thank you very much, by the way!), I am extremely frustrated.
Any other ideas?
Thanks!

Don't be, everything is gonna be fine :) But it looks like it will take a while for us to pinpoint what's going on there. Ideally, I'd like to see the output of some commands before we jump to some conclusion. I'm guessing you have some way to read/write to the machine since you're posting logs. If so, create a file with any name in your home. marcelo.sh is fine. And paste this inside it:

```
#!/bin/bash

LOG_NAME="mylog"
LOG_DATE="$(date +%d%y%m-%H:%M)"
MYLOG="${HOME}/${LOG_NAME}.${LOG_DATE}.log"

echo -e "\nMS-DOS Version 4.01\n\n"
echo -e "Log placed at ${MYLOG}\n"
cd $HOME
#service lightdm stop
#sleep 10
#killall -s KILL lightdm
#service gdm stop
#sleep 10
#killall -s KILL gdm
#killall -s KILL $(pidof /usr/bin/X)

#Grep info that Something-Berg dude requested

touch ${MYLOG}
echo -e "\n\n ## lspci ##\n" > ${MYLOG}
lspci | grep -i vga >> $MYLOG

echo -e "\n\n ## lsmod ##" >> ${MYLOG}
lsmod | grep -i nouveau >> $MYLOG
lsmod | grep -i nvidia >> $MYLOG

echo -e "\n\n ## cmdline ##" >> ${MYLOG}
cat /proc/cmdline >> $MYLOG

echo -e "\n\n ## nvidia-settings-version ##" >> ${MYLOG}
/usr/bin/nvidia-settings -version >> $MYLOG

echo -e "\n\n ## The softlink mess ##" >> ${MYLOG}
ls -la /usr/lib/libGL* >> $MYLOG
ls -la /usr/lib32/libGL* >> $MYLOG

echo -e "\n\n ## Modules ##" >> ${MYLOG}
modinfo nouveau >> $MYLOG
modinfo nvidia >> $MYLOG

```chmod it +x:
```
sudo chmod +x $HOME/marcelo.sh
```Boot into the problematic install. When you get to the black or garbled screen, switch to a VT, like VT6 for example: Press Ctrl+Alt+F6. Login, cd $HOME and run
```
sudo -s
bash $HOME/marcelo.sh

```It will create a file named mylog.161201-XX:XX.log in your home. Upload it here as an attachment, so we can study it. Sorry in advance for any typos, mistakes, horrible formatting, etc. I'm really megabusy, flying between screens here, and this forum was definitely not made to be a code editor. 

It should be clearer once we analyse all the info in the created log file.

---

### Post by Marcelo Ruiz on 2012-01-16
@effenberg0x0

Thanks for your patience and help!
I uploaded the log file (changed the extension to txt to upload it here). I hope it helps.
Let me know if you need me to do anything else.
Thanks again!

---

### Post by effenberg0x0 on 2012-01-16
Hey, two tests:

1) In /etc/X11/xorg.conf, add "Option "UseEvents" "False"
```
Section "Screen"
  Option "SomeStuff" "True"
  Option "UseEvents" "False"
  Option "OtherStuff" "Lie"
EndSection

```
2) In grub command line, use acpi=off (bad... but reported to work in some cases with this hardware, as a workaround).
```
sudo nano /etc/default/grub
```Now add acpi=off to to "GRUB_CMDLINE_LINUX_DEFAULT"
```
sudo update-grub
sudo reboot now
```EDIT:
Also, the output of 
```
lsof -n -P | grep -i nouveau
```

---

### Post by Marcelo Ruiz on 2012-01-18
Hi!

It worked with acpi=off, but this leaves my laptop extremely slow, the fan working at hight speed all the time.
Any sugestions?
Thanks!

---

### Post by Marcelo Ruiz on 2012-01-18
I found the problem. It is kernel-related. For all of you experiencing the same problem, please say this bug affects you:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/901386]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/901386")

An interesting article about this:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzk]("http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzk")

The workaround is to set the kernel option: "intel_iommu=off" though this disables Intel VT-d / I/O virtualization support.
Thanks all for your help!

---

