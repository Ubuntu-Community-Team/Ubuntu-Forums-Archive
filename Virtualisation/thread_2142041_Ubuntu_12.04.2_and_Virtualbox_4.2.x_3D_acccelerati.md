---
title: "Ubuntu 12.04.2 and Virtualbox 4.2.x 3D accceleration configuration"
date: 2013-05-04
forum: Virtualisation
---

### Post by Lamukra on 2013-05-04
This thread is dedicated to configuring Virtualbox v. 4.2.x with ubuntu 12.04.2

I am not interested in installation of the OS but more of the configuration and 3D acceleration specifically

UPDATE: [Workaround to get 3D acceleration on Ubuntu Guest 12.04.2]("http://ubuntuforums.org/showthread.php?t=2142041&p=12634331&viewfull=1#post12634331")

**My Environment:**

Sony Vaio VPCEB1S1E
CPU: Intel Core i5-430M
Gprahics card: Radeon HD 5650 (not switchable)

Virtualbox Version: 4.2.10 or 4.2.12 (Setups made for both)
HOST: Windows 8 Pro x64
GUEST: Ubuntu 12.04.2



_**Setup 1 (Successfull):**_

> 

Virtualbox 3D acceleration enabled

Kernel:
3.5.0-23-generic (came with linux-generic-lts-quantal - fresh install)
No Guest Additions

Result: OS works in 2d mode without problem, no special functionality (Support for shared clipboard, resolution change, etc)



_[COLOR=#808080]**Setup 2 (Unsuccessful):**[/COLOR]_

> 

Virtualbox 3D acceleration enabled

Kernel:
3.5.0-23-generic (came with linux-generic-lts-quantal - fresh install)

Extra Install:
dkms, build-essential

Original Guest Additions

Result: OS goes to black screen after login and VM is unresponsive, switching to tty before login causes black screen aswell


```
cat /var/log/Xorg.0.log | grep EE
```
```

[    12.674] Initializing built-in extension MIT-SCREEN-SAVER
[    13.163] (EE) AIGLX error: vboxvideo does not export required DRI extension
[    13.163] (EE) AIGLX: reverting to software rendering
[    13.222] (II) XINPUT: Adding extended input device "VirtualBox mouse integration" (type: TOUCHSCREEN, id 8)

```



_**Setup 3 (Successful):**_

> 

Virtualbox NO 3D acceleration enabled 

Kernel:
3.5.0-23-generic (came with linux-generic-lts-quantal - fresh install)

Extra Install:
dkms, build-essential

Original Guest Additions

Result: OS works in 2d mode without problem, special functionality works as well (Support for shared clipboard, resolution change, etc)

```
dmesg | grep drm
```
```

[   12.638978] [drm] Initialized drm 1.1.0 20060810
[   12.642268] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.642273] [drm] No driver support for vblank timestamp query.
[   12.642279] [drm] Initialized vboxvideo 1.0.0 20090303 for 0000:00:02.0 on minor 0

```

```
glxinfo | grep render
```
```

direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend

```

NOTE: Setup 3 is basically the same as Setup 2, just check box for 3D acceleration is not checked in VM settings - unchecking this checkbox can fix Setup 2(no need for reinstallation of OS)

[COLOR=#696969]**_Setup 4 (partially Successful - see Result):_**[/COLOR]


This setup requires some things to do 
I deleted all *-lts-quantal packages that came with fresh install and installed "usual" ones and reinstall xserver completely

> 

VirtualBox 3D disabled

Kernel:
3.2.0-21-generic (after whole procedure - see Instructions below)

Extra install:
dkms, build-essential

Original Guest Additions installed after all procedures 

Result: 3D does not work (to boot into system with guest addition disable 3D like in "Setup 3"), but this setup succesfully installs jockey drivers and boots into OS with no problem (with no 3D, with 3D enabled same error like in other setups with 3D), with other Setups it was not possible

NOTE: if you want to use jockey provided guest additions do not install original one and if you installed the do this and repeat jockey installation
```
sudo sh /opt/V {hit TAB to aucomplete}/uninstall.sh
```
```
sudo reboot
```

*** INSTRUCTIONS ***

When system will boot -> login -> launch temrinal and do this:

```
sudo apt-get install linux-generic
```
this will install older kernel version with all headers (3.2.0-41 - on fresh install they are 3.5.0-23)

```
sudo reboot
```

and hold SHIFT to show GRUB boot loader -> Linux Previous... -> 3.2.0-41

when system boots go to tty (host+F1) -> login -> then type

```
sudo apt-get purge linux-generic-lts-quantal linux-headers-generic-lts-quantal linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic  linux-image-generic-lts-quantal linux-image-3.5.0-23-generic

```
this will delete all -lts-quantal specific kernel and headers

now update grub
```
sudo update-grub
```
```
sudo update initramfs -u
```
```
sudo reboot
```

after reboot you will automatically go to kernel 3.2.0-41 and go to tty console again -> HOST+F1

now delete all xserver-xorg-lts-quantal specific server and completely reinstall X server

```
sudo apt-get purge xserver-xorg-lts-quantal
```
it will uninstall *-lts-quantal packages and install usual xserver-xorg

now remove that xserver-xorg aswell (just to make it clean) and graphical interface (not unity) - removing xserver-xorg will cause removal of ubuntu-dekstop
```
sudo apt-get purge xserver-xorg lightdm
```

now reboot and you should get to tty console automatically(no GUI)

now just install all things again
```
sudo apt-get install xserver-xorg ubuntu-desktop lightdm
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
```
sudo reboot
```

now you will boot back to GUI -> login

*** INSTRUCTIONS END ***




[COLOR=#808080]**Setup 5 (Unsuccessful):**[/COLOR]

> 

This is the same as "Setup 2" only difference is in Kernel and Updates
On fresh install I run all upgrades and the dist-upgrade what updated kernel version to:

Kernel:
3.5.0-28-generic

Everything else is the same as "Setup 2"



Any one who knows how to make "Setup 2" or "Setup 5" to work with 3D acceleration please leave a note

---

### Post by Lamukra on 2013-05-04
Added more Setups - Setup 4 and Setup 5

---

### Post by Lamukra on 2013-05-05
[SIZE=3]Found a Pretty decent solution aka workaround for fixing 3D acceleration in Ubuntu 12.04.2 guest.[/SIZE]

> 
Workaround to get 3D acceleration:

Install VMware Player, everything works just out of the box with VMware tools installed (and even without, just slower)!!! - Amazing



---

