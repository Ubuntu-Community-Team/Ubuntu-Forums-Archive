---
title: "Error on building nvidia module"
date: 2013-01-19
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2013-01-19
With the linux-image-generic 3.8.0-0 and 3.8.0-1 the nvidia module doesn't build anymore on my system. I'm using nvidia-current-updates (304.64) and this is the output:

```
Error! Bad return status for module build on kernel: 3.8.0-1-generic (x86_64)
Consult /var/lib/dkms/nvidia-current-updates/304.64/build/make.log for more information.

```

Has somebody else this problem too? The log is complaining about lot of undefined objects. It seems this version is not compatible with the Linux kernel 3.8.

---

### Post by jpeddicord on 2013-01-19
Could you post /var/lib/dkms/nvidia-current-updates/304.64/build/make.log (or the end of it, if it's huge)? I haven't run into any problems.

---

### Post by VinDSL on 2013-01-19
> **Sworddragon said:**
> Has somebody else this problem too?
I've run across this problem, repeatedly.  The 'fix' is rather complicated, but doable.

Currently, I've got nVidia 304.64 working (and pinned in Synaptic) under Linux 3.8-rc4.

```
vindsl@Zuul:~$ apt-cache policy nvidia-current-updates
nvidia-current-updates:
  Installed: 304.64-0ubuntu1
  Candidate: 304.64-0ubuntu4
  Version table:
     304.64-0ubuntu4 0
        500 http://mirror.hmc.edu/ubuntu/ raring-proposed/restricted i386 Packages
 *** 304.64-0ubuntu1 0
        500 http://mirror.hmc.edu/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
vindsl@Zuul:~$
```

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Sat Jan 19 12:21:31 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.8.0-030800rc4-generic
Gnome Release: GNOME Shell 3.7.4.1
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

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
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.1.901+git20130104+server-1.13-branch.3a8c618a-0ubuntu0ricotz

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


I'm still getting the error you posted (above), when I do kernel upgrades, but it isn't a deal breaker, e.g. the error appears in the dialog, while the initial nVidia module is building, but it isn't fatal.


Here is the most recent post, regarding how I accomplished this:

[INDENT][http://ubuntuforums.org/showpost.php?p=12417951&postcount=39](http://ubuntuforums.org/showpost.php?p=12417951&postcount=39)[/INDENT]


Hopefully, it will make sense...  ;)

---

### Post by mc4man on 2013-01-19
If you want 304.64 then you should use the 'other' 304.64 package, in current repos it's 304.64-0ubuntu2, in proposed it's 304.64-0ubuntu4
(atm there are more nvidia- packages then one needs to see.

Screen shows the one  you'd want (with proposed not enabled
note that I could install the older one, sometimes errors sometimes doesn't..

---

### Post by VinDSL on 2013-01-19
Whoa!  I am soooo tempted to try that!

I'll swill down another mug of coffee, while mulling over the consequences.

nVidia legacy drivers are brittle on this machine, and it's a major PITA to apply the patches all over again (remembering the exact sequence required, not the patching) but it is what it is...

I've been burned so many times, with the promise of this-or-that working, just to have it blow up in my face.  I'm a little gun shy, you know?

Still, there's nothing more exciting than a broken nVidia install. LoL! :D

Continuing...

---

### Post by mc4man on 2013-01-19
In synaptic I had to go fullscreen to show full range of possible nvidia-

In add. drivers, pick your poison

---

### Post by VinDSL on 2013-01-19
w00t!  Worked!

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.64-0ubuntu4
  Candidate: 304.64-0ubuntu4
  Version table:
 *** 304.64-0ubuntu4 0
        500 http://mirror.hmc.edu/ubuntu/ raring-proposed/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.64-0ubuntu2 0
        500 http://mirror.hmc.edu/ubuntu/ raring/restricted i386 Packages
vindsl@Zuul:~$
```


Fairly clean install...


```
nVidia-304 Install Dialog

(Reading database ... 410499 files and directories currently installed.)
Removing nvidia-current-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-current-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Success
INFO:Unapplying quirk Latitude E6530
DEBUG:Removing /usr/share/X11/xorg.conf.d/10-nvidia-current-updates-latitude-e6530.conf ...
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Success
INFO:Unapplying quirk ThinkPad T420s
DEBUG:Removing /usr/share/X11/xorg.conf.d/10-nvidia-current-updates-thinkpad-t420s.conf ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-settings ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-030800rc4-generic
Selecting previously unselected package nvidia-304.
(Reading database ... 410271 files and directories currently installed.)
Unpacking nvidia-304 (from .../nvidia-304_304.64-0ubuntu4_i386.deb) ...
Selecting previously unselected package nvidia-settings-304.
Unpacking nvidia-settings-304 (from .../nvidia-settings-304_304.64-0ubuntu1_i386.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up nvidia-304 (304.64-0ubuntu4) ...
update-alternatives: using /usr/lib/nvidia-304/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-304/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-304/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-304/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-304/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-304
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-304-304.64 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-030800rc4-generic
Building for architecture i686
Building initial module for 3.8.0-030800rc4-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-030800rc4-generic/updates/dkms/

depmod..........

DKMS: install completed.
Setting up nvidia-settings-304 (304.64-0ubuntu1) ...
update-alternatives: warning: alternative /usr/lib/nvidia-settings/ld.so.conf (part of link group nvidia_settings_conf) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/nvidia_settings_conf is dangling; it will be updated with best choice
update-alternatives: using /usr/lib/nvidia-settings-304/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-030800rc4-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted

```

Got the longstanding, ubiquitous KMOD failure, but it survived a reboot.

Wasn't aware they had patched nvidia-304 for linux 3.8...

Thanks, mc4man!  ;)

---

### Post by VinDSL on 2013-01-19
> **mc4man said:**
> In synaptic I had to go fullscreen to show full range of possible nvidia-
I did a "Quick filter" using "nvidia-304" and sorted the results on the "Latest Version" field.  

That narrowed things down considerably...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-jan-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-jan-2013-1.png")[/INDENT]
   

Then, I carefully read all of the changelogs, and tossed the dice.

Coffee does that to ya... :)

**EDIT**

Hey, they fixed the 12/24 hr. bug in GS (date/time settings).

I wonder when they patched that?!?!?

---

### Post by Sworddragon on 2013-01-20
I have now decided to install nvidia-304-updates 304.64-0ubuntu2 and it works fine.

---

