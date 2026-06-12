---
title: "New udev (175-0ubuntu20) in RR proposed"
date: 2013-03-13
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-03-13
We have a new udev (175-0ubuntu20) now in RR proposed repos.
That brings about important changes into udev setup:
> 
  * Drop unnecessary hardcoded libudev0 dependency from udev package.
* Drop libudev and gudev packages, built by systemd source now.


So, libudev0 is dropped and libudev1 is installed instead.
A number of packages must also be installed, built against libudev1:
- xorg-server + some drivers (evdev, ati, nouveau, intel)
- mountall
- mesa
- livm2
- initramfs-tools
- upstart
- bluez
- pulseaudio

Did someone of you already installed this setup?
I did and got immediately some issues with udev, my setup switches to busybox.
However, commanding "exit" works and all is well otherwise.

---

### Post by grahammechanical on 2013-03-13
Yes. It happened to me just now. Ran an update = restart and result = busybox. Thank you for mentioning that "exit" moves the loading of Ubuntu onwards as usual.

Up until last week every ISO image of Raring that I tried ended in Busybox. And Exit do not do much except provided a little more information.

Regards.

---

### Post by Harry33 on 2013-03-14
Here is the bug report regarding this issue:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1154813](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1154813)

The issue is that initramfs does not wait long enough for root.
This in turn causes the root UUID not to be found and eventually system dropping to busybox shell.

So, please do not upgrade intiramfs-tools before this bug is solved.

---

### Post by Harry33 on 2013-03-14
The new fix to initramfs-tools (0.103ubuntu0.7) is soon in RR-proposed.

Here:
[https://launchpad.net/ubuntu/+source/initramfs-tools/0.103ubuntu0.7](https://launchpad.net/ubuntu/+source/initramfs-tools/0.103ubuntu0.7)

---

### Post by zika on 2013-03-14
I've disabled failsafe at boot. Does new udev need failsafe?
Also, on one install I have plymouth disabled... Any problem with that and new udev?

---

### Post by serdotlinecho on 2013-03-14
[Mine]("http://ubuntuforums.org/showthread.php?t=2122068&page=5&p=12556579#post12556579")... ):P

---

### Post by zika on 2013-03-14
Making Proposed as a quarantine (sandbox) proves itself as a very good decision. Right one to get prepared for rolling distro...

---

### Post by Harry33 on 2013-03-14
> **Harry33 said:**
> The new fix to initramfs-tools (0.103ubuntu0.7) is soon in RR-proposed.

Here:
[https://launchpad.net/ubuntu/+source/initramfs-tools/0.103ubuntu0.7](https://launchpad.net/ubuntu/+source/initramfs-tools/0.103ubuntu0.7)

This relesased fix solves this issue.

---

### Post by zika on 2013-03-14
I bit the bullet, opened Proposed, went with dist-upgrade, and lived to write this after reboot...
Having several kernels and using the fact that only the first (freshest) does get updated with update-initramfs trigger, made me breathe easeier...
Of course, after first reboot, all kernels got their new incarnation...
Another day at test bay...

---

### Post by serdotlinecho on 2013-03-14
> **zika said:**
> I bit the bullet, opened Proposed, went with dist-upgrade, and lived to write this after reboot...
Having several kernels and using the fact that only the first (freshest) does get updated with update-initramfs trigger, made me breathe easeier...
Of course, after first reboot, all kernels got their new incarnation...
Another day at test bay...

@Zika, me too :D
After fresh raring install(reinstall), enable raring-proposed.  :guitar:
I only did sudo apt-get upgrade. 

```
Start-Date: 2013-03-14  17:43:42
Commandline: apt-get upgrade
Upgrade: dmsetup:i386 (1.02.74-6ubuntu1, 1.02.74-6ubuntu2), libpci3:i386 (3.1.9-6ubuntu1, 3.1.9-6ubuntu2), bluez-alsa:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), libpam0g:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), libpam-modules-bin:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), bluez-gstreamer:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), python-aptdaemon.gtk3widgets:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), libpam-modules:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), mobile-broadband-provider-info:i386 (20130121-1, 20130312-1), xserver-xorg-video-ati:i386 (7.1.0-0ubuntu1, 7.1.0-0ubuntu1b1), python3-aptdaemon:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), aptdaemon-data:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), python3-aptdaemon.pkcompat:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), libdbus-1-3:i386 (1.6.8-1ubuntu3, 1.6.8-1ubuntu4), python-aptdaemon:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), python3-software-properties:i386 (0.92.14.1, 0.92.15), libpam-runtime:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), system-config-printer-gnome:i386 (1.3.12+20130308-0ubuntu1, 1.3.12+20130308-0ubuntu1b1), bluez-cups:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), lightdm:i386 (1.4.0-0ubuntu5, 1.5.1-0ubuntu1), foomatic-db-compressed-ppds:i386 (20130308-0ubuntu1, 20130308-0ubuntu2), xserver-common:i386 (1.13.2-0ubuntu3, 1.13.3-0ubuntu1), libxatracker1:i386 (9.0.2-0ubuntu1, 9.0.2-0ubuntu1b1), gir1.2-gudev-1.0:i386 (175-0ubuntu19, 198-0ubuntu2), libpulse-mainloop-glib0:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), libpcsclite1:i386 (1.8.6-3ubuntu1, 1.8.6-3ubuntu1b1), libvlc5:i386 (2.0.5-1, 2.0.5-1build1), dbus:i386 (1.6.8-1ubuntu3, 1.6.8-1ubuntu4), udev:i386 (175-0ubuntu19, 175-0ubuntu20), liblightdm-gobject-1-0:i386 (1.4.0-0ubuntu5, 1.5.1-0ubuntu1), busybox-static:i386 (1.20.0-7ubuntu3, 1.20.0-8ubuntu1), pciutils:i386 (3.1.9-6ubuntu1, 3.1.9-6ubuntu2), pulseaudio-module-bluetooth:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), pulseaudio-module-x11:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), aptdaemon:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), system-config-printer-common:i386 (1.3.12+20130308-0ubuntu1, 1.3.12+20130308-0ubuntu1b1), libbluetooth3:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), pulseaudio-utils:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), software-properties-common:i386 (0.92.14.1, 0.92.15), libdevmapper-event1.02.1:i386 (1.02.74-6ubuntu1, 1.02.74-6ubuntu2), openprinting-ppds:i386 (20130308-0ubuntu1, 20130308-0ubuntu2), keyboard-configuration:i386 (1.70ubuntu6, 1.70ubuntu7), software-properties-gtk:i386 (0.92.14.1, 0.92.15), console-setup:i386 (1.70ubuntu6, 1.70ubuntu7), python3-aptdaemon.gtk3widgets:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), libgl1-mesa-dri:i386 (9.0.2-0ubuntu1, 9.0.2-0ubuntu1b1), vlc-data:i386 (2.0.5-1, 2.0.5-1build1), libpulsedsp:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), libopenvg1-mesa:i386 (9.0.2-0ubuntu1, 9.0.2-0ubuntu1b1), ureadahead:i386 (0.100.0-14, 0.100.0-15), busybox-initramfs:i386 (1.20.0-7ubuntu3, 1.20.0-8ubuntu1), dbus-x11:i386 (1.6.8-1ubuntu3, 1.6.8-1ubuntu4), python-cupshelpers:i386 (1.3.12+20130308-0ubuntu1, 1.3.12+20130308-0ubuntu1b1), libvlccore5:i386 (2.0.5-1, 2.0.5-1build1)
End-Date: 2013-03-14  17:46:29
```
I don't have the guts to do dist-upgrade, atm.:lolflag:

 
```
~&#10095; sudo apt-get upgrade                      
[sudo] password for serdotlinecho: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages have been kept back:
  bluez gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse
  gvfs-libs initramfs-tools initramfs-tools-bin libatasmart4
  libdevmapper1.02.1 libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-glx
  libglapi-mesa libgudev-1.0-0 liblvm2app2.2 libpulse0 mountall pulseaudio
  system-config-printer-udev udisks upstart vlc vlc-nox vlc-plugin-notify
  vlc-plugin-pulse xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-video-intel xserver-xorg-video-modesetting
  xserver-xorg-video-nouveau xserver-xorg-video-radeon
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
```

---

### Post by zika on 2013-03-14
> **serdotlinecho said:**
> @Zika, me too :D
After fresh raring install(reinstall), enable raring-proposed.  :guitar:
I only did sudo apt-get upgrade. 

```
Start-Date: 2013-03-14  17:43:42
Commandline: apt-get upgrade
Upgrade: dmsetup:i386 (1.02.74-6ubuntu1, 1.02.74-6ubuntu2), libpci3:i386 (3.1.9-6ubuntu1, 3.1.9-6ubuntu2), bluez-alsa:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), libpam0g:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), libpam-modules-bin:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), bluez-gstreamer:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), python-aptdaemon.gtk3widgets:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), libpam-modules:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), mobile-broadband-provider-info:i386 (20130121-1, 20130312-1), xserver-xorg-video-ati:i386 (7.1.0-0ubuntu1, 7.1.0-0ubuntu1b1), python3-aptdaemon:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), aptdaemon-data:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), python3-aptdaemon.pkcompat:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), libdbus-1-3:i386 (1.6.8-1ubuntu3, 1.6.8-1ubuntu4), python-aptdaemon:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), python3-software-properties:i386 (0.92.14.1, 0.92.15), libpam-runtime:i386 (1.1.3-8ubuntu1, 1.1.3-8ubuntu2), system-config-printer-gnome:i386 (1.3.12+20130308-0ubuntu1, 1.3.12+20130308-0ubuntu1b1), bluez-cups:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), lightdm:i386 (1.4.0-0ubuntu5, 1.5.1-0ubuntu1), foomatic-db-compressed-ppds:i386 (20130308-0ubuntu1, 20130308-0ubuntu2), xserver-common:i386 (1.13.2-0ubuntu3, 1.13.3-0ubuntu1), libxatracker1:i386 (9.0.2-0ubuntu1, 9.0.2-0ubuntu1b1), gir1.2-gudev-1.0:i386 (175-0ubuntu19, 198-0ubuntu2), libpulse-mainloop-glib0:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), libpcsclite1:i386 (1.8.6-3ubuntu1, 1.8.6-3ubuntu1b1), libvlc5:i386 (2.0.5-1, 2.0.5-1build1), dbus:i386 (1.6.8-1ubuntu3, 1.6.8-1ubuntu4), udev:i386 (175-0ubuntu19, 175-0ubuntu20), liblightdm-gobject-1-0:i386 (1.4.0-0ubuntu5, 1.5.1-0ubuntu1), busybox-static:i386 (1.20.0-7ubuntu3, 1.20.0-8ubuntu1), pciutils:i386 (3.1.9-6ubuntu1, 3.1.9-6ubuntu2), pulseaudio-module-bluetooth:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), pulseaudio-module-x11:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), aptdaemon:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), system-config-printer-common:i386 (1.3.12+20130308-0ubuntu1, 1.3.12+20130308-0ubuntu1b1), libbluetooth3:i386 (4.101-0ubuntu8, 4.101-0ubuntu8b1), pulseaudio-utils:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), software-properties-common:i386 (0.92.14.1, 0.92.15), libdevmapper-event1.02.1:i386 (1.02.74-6ubuntu1, 1.02.74-6ubuntu2), openprinting-ppds:i386 (20130308-0ubuntu1, 20130308-0ubuntu2), keyboard-configuration:i386 (1.70ubuntu6, 1.70ubuntu7), software-properties-gtk:i386 (0.92.14.1, 0.92.15), console-setup:i386 (1.70ubuntu6, 1.70ubuntu7), python3-aptdaemon.gtk3widgets:i386 (0.45+bzr883-0ubuntu1, 1.0-0ubuntu1), libgl1-mesa-dri:i386 (9.0.2-0ubuntu1, 9.0.2-0ubuntu1b1), vlc-data:i386 (2.0.5-1, 2.0.5-1build1), libpulsedsp:i386 (3.0-0ubuntu4, 3.0-0ubuntu4b1), libopenvg1-mesa:i386 (9.0.2-0ubuntu1, 9.0.2-0ubuntu1b1), ureadahead:i386 (0.100.0-14, 0.100.0-15), busybox-initramfs:i386 (1.20.0-7ubuntu3, 1.20.0-8ubuntu1), dbus-x11:i386 (1.6.8-1ubuntu3, 1.6.8-1ubuntu4), python-cupshelpers:i386 (1.3.12+20130308-0ubuntu1, 1.3.12+20130308-0ubuntu1b1), libvlccore5:i386 (2.0.5-1, 2.0.5-1build1)
End-Date: 2013-03-14  17:46:29
```
I don't have the guts to do dist-upgrade, atm.:lolflag:

 
```
~&#10095; sudo apt-get upgrade                      
[sudo] password for serdotlinecho: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages have been kept back:
  bluez gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse
  gvfs-libs initramfs-tools initramfs-tools-bin libatasmart4
  libdevmapper1.02.1 libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-glx
  libglapi-mesa libgudev-1.0-0 liblvm2app2.2 libpulse0 mountall pulseaudio
  system-config-printer-udev udisks upstart vlc vlc-nox vlc-plugin-notify
  vlc-plugin-pulse xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-video-intel xserver-xorg-video-modesetting
  xserver-xorg-video-nouveau xserver-xorg-video-radeon
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
```Seing new radeon made me do it. I admit...
"-s" option in apt-get helped a lot in making a decision...

---

### Post by grahammechanical on 2013-03-14
To day's updates fixes this bug on my machine.

---

### Post by dino99 on 2013-03-14
Strangely some packages have stayed with 175 number, but one have jumped to 198 (wonder if its an error)

---

### Post by VinDSL on 2013-03-14
> **grahammechanical said:**
> To day's updates fixes this bug on my machine.
Sometimes it pays to procrastinate. I held off doing any upgrades until today.  :)

Everything boots/looks/works fine here!

PPAs enabled (amongst others):
[LIST]
[*]Gnome 3
[*]Gnome 3 Staging
[*]Ricotz Testing
[*]Raring Proposed
[/LIST]

```
vindsl@Zuul:~$ apt-cache policy udev
udev:
  **[COLOR="#B22222"]Installed: 175-0ubuntu21[/COLOR]**
  Candidate: 175-0ubuntu21
  Version table:
 *** 175-0ubuntu21 0
        500 http://samaritan.ucmerced.edu/ubuntu/ raring-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     175-0ubuntu19 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
vindsl@Zuul:~$ 
```

[INDENT]**[COLOR="#A52A2A"]Gnome-Shell 3.7.91[/COLOR]**
[[IMG]http://vindsl.com/images/vindsl-desktop-14-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-14-mar-2013-1.png")[/INDENT]


[INDENT]**[COLOR="#A52A2A"]Unity 6.6.0[/COLOR]**
[[IMG]http://vindsl.com/images/vindsl-desktop-14-mar-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-14-mar-2013-2.png")[/INDENT]


```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Thu Mar 14 08:05:12 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc2-generic
Gnome Release: GNOME Shell 3.7.91
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.84

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: [http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)

Xserver Xorg Core Branch:
  Installed: 2:1.13.3-0ubuntu1

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$
```

---

### Post by Harry33 on 2013-03-15
> **dino99 said:**
> Strangely some packages have stayed with 175 number, but one have jumped to 198 (wonder if its an error)

Actually not strange at all.
Here is the explanation.
Before we used to have one source (udev) where the builds like udev and libudev0 came from. This is the v. 175.
Now, we have two different sources: udev and systemd. We use them both now.
So, udev build comes from the source udev (v. 175) and libudev1 build comes from the source systemd (v. 198).

See here:

Udev:
[https://launchpad.net/ubuntu/raring/+source/udev/175-0ubuntu21](https://launchpad.net/ubuntu/raring/+source/udev/175-0ubuntu21)

Systemd:
[https://launchpad.net/ubuntu/raring/+source/systemd/198-0ubuntu2](https://launchpad.net/ubuntu/raring/+source/systemd/198-0ubuntu2)

---

### Post by dino99 on 2013-03-15
Thanks Harry,

i might have found that myself  :mad:

---

### Post by VinDSL on 2013-03-15
And, now...

```
vindsl@Zuul:~$ apt-cache policy udev
udev:
  Installed: 175-0ubuntu23
  Candidate: 175-0ubuntu23
  Version table:
 *** 175-0ubuntu23 0
        500 http://samaritan.ucmerced.edu/ubuntu/ raring-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     175-0ubuntu19 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
vindsl@Zuul:~$ 
```


175-0ubuntu23 & counting.  :)

---

### Post by Harry33 on 2013-03-16
RR + RR-proposed + Gnome3 PPA + Gnome3 Staging PPA:
All working fine now.
So, new udev (175-0ubuntu23) and systemd (198-0ubuntu5) are good now.

---

### Post by VinDSL on 2013-03-16
> **Harry33 said:**
> RR + RR-proposed + Gnome3 PPA + Gnome3 Staging PPA:
All working fine now.
So, new udev (175-0ubuntu23) and systemd (198-0ubuntu5) are good now.
What is the verdict on Ricotz Testing PPA?

I still have it enabled, along with the PPAs you listed.

I judge it works fine here.

Have you disabled Ricotz Testing :confused:

---

### Post by Harry33 on 2013-03-17
> **VinDSL said:**
> What is the verdict on Ricotz Testing PPA?

I still have it enabled, along with the PPAs you listed.

I judge it works fine here.

Have you disabled Ricotz Testing :confused:

True, I do not use Gnome Testing PPA.
So I do not know the current state there.

---

### Post by serdotlinecho on 2013-03-17
> **grahammechanical said:**
> To day's updates fixes this bug on my machine.

I just did dist-upgrade and reboot. No more busybox.

```
~&#10095; uname -a && echo -e "\n" && apt-cache policy udev initramfs-tools | cut -d "/" -f 6
Linux raring 3.9.0-030900rc2-generic #201303102035 SMP Mon Mar 11 00:44:44 UTC 2013 i686 i686 i686 GNU/Linux


udev:
  Installed: 175-0ubuntu24
  Candidate: 175-0ubuntu24
  Version table:
 *** 175-0ubuntu24 0
main i386 Packages

initramfs-tools:
  Installed: 0.103ubuntu0.7
  Candidate: 0.103ubuntu0.7
  Version table:
 *** 0.103ubuntu0.7 0
main i386 Packages
```

---

