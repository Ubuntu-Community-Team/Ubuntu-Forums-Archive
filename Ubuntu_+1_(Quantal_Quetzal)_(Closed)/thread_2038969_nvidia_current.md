---
title: "nvidia current"
date: 2012-08-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by flipper T on 2012-08-07
nvidia current now installable from synaptic.

have installed but crashes back to logon screen for unity 3d, gnome shell & kde. working ok for unity 2d & gnome classic.

also only have native resolution on laptop monitor.

ran the unity3d check and got:

```
jk@jk-M570RU:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro FX 1600M/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.32

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

```

so a bit lost now.

any ideas ?

---

### Post by flipper T on 2012-08-07
installed nvidia-current-updates-dev (seemed like a good idea)

now kde working but not unity 3d or gnome shell.

---

### Post by effenberg0x0 on 2012-08-07
> **flipper T said:**
> installed nvidia-current-updates-dev (seemed like a good idea)

now kde working but not unity 3d or gnome shell.

Hi Flipper T, 

I'm trying to debug the same thing for a couple hours. If possible, would you mind running the commands below? I'd like to see if your results match those of other machines with similar issues.

```
Xorg -version
compiz --version
unity --version
modinfo nvidia-current | grep "version:"
sudo grep -i "NVIDIA GLX Module" /var/log/Xorg.*.log -A 10
sudo grep -i "failed" /var/log/Xorg.*.log
cat /etc/modprobe.d/nvidia-graphics-drivers.conf | grep "alias nvidia"
ls -la /lib/modules/$(uname -r)/updates/dkms/nvidia*
ls -la /lib/modules/$(uname -r)/kernel/drivers/video/nvidia*.ko
ls -la /lib/modules/$(uname -r)/kernel/drivers/video/nvidia/*.ko
ls -la /usr/lib/*GL*
ls -la /usr/lib32/*GL*

```

Regards,
Effenberg

---

### Post by flipper T on 2012-08-07
oddly, getting new message when trying to open nvidia settings

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

i follow above advice, but nothing seems to change. going back to plain old nvidia current & will report back

---

### Post by flipper T on 2012-08-07
ok, getting same message with nvidia current.

requested output to follow

---

### Post by effenberg0x0 on 2012-08-07
HI those are just to gather info, no changewould be done to your OS. I just wanted to see the output of the commands above to avoid guessing. Anyway, my guess is:

1) You have a set of drivers / module / xserver / unity / compiz / config files that do not work together

2) You have a misleading alias to the wrong nvidia module.

Regards,
Effenberg

EDIT: Thanks, waiting for your info :)

---

### Post by flipper T on 2012-08-07
```
jk@jk-M570RU:~$ Xorg -version

X.Org X Server 1.12.99.902 (1.13.0 RC 2)
Release Date: 2012-07-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-26-generic x86_64 Ubuntu
Current Operating System: Linux jk-M570RU 3.5.0-8-generic #8-Ubuntu SMP Sat Aug 4 04:42:28 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-8-generic root=UUID=fca1b954-8a2c-4017-9532-a4c05f870f2c ro quiet splash vt.handoff=7
Build Date: 31 July 2012  03:52:23AM
xorg-server 2:1.12.99.902-0ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
jk@jk-M570RU:~$ 

```

---

### Post by flipper T on 2012-08-07
```
jk@jk-M570RU:~$ compiz --version
Compiz 0.9.8
```

---

### Post by flipper T on 2012-08-07
```
jk@jk-M570RU:~$ unity --version
unity 6.0.0

```

---

### Post by flipper T on 2012-08-07
```
jk@jk-M570RU:~$ modinfo nvidia-current | grep "version:"
version:        304.32
jk@jk-M570RU:~$ sudo grep -i "NVIDIA GLX Module" /var/log/Xorg.*.log -A 10
[sudo] password for jk: 
[    27.115] (II) NVIDIA GLX Module  304.32  Thu Aug  2 19:03:23 PDT 2012
[    27.115] Loading extension GLX
[    27.115] (II) LoadModule: "nvidia"
[    27.115] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    27.115] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.115] 	compiled for 4.0.2, module version = 1.0.0
[    27.115] 	Module class: X.Org Video Driver
[    27.118] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.118] (EE) NVIDIA:     system's kernel log for additional error messages.
[    27.118] (II) UnloadModule: "nvidia"
[    27.118] (II) Unloading nvidia
jk@jk-M570RU:~$ sudo grep -i "failed" /var/log/Xorg.*.log
[    27.118] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.118] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    27.122] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.122] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    27.187] (EE) Failed to load module "nv" (module does not exist, 0)
[    27.199] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    27.325] (EE) [drm] failed to open device
[    27.795] (II) VESA(0): VESA VBE DDC read failed
[    28.110] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
jk@jk-M570RU:~$ sudo grep -i "NVIDIA GLX Module" /var/log/Xorg.*.log -A 10
[    27.115] (II) NVIDIA GLX Module  304.32  Thu Aug  2 19:03:23 PDT 2012
[    27.115] Loading extension GLX
[    27.115] (II) LoadModule: "nvidia"
[    27.115] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    27.115] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.115] 	compiled for 4.0.2, module version = 1.0.0
[    27.115] 	Module class: X.Org Video Driver
[    27.118] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.118] (EE) NVIDIA:     system's kernel log for additional error messages.
[    27.118] (II) UnloadModule: "nvidia"
[    27.118] (II) Unloading nvidia
jk@jk-M570RU:~$ sudo grep -i "failed" /var/log/Xorg.*.log
[    27.118] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.118] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    27.122] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.122] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    27.187] (EE) Failed to load module "nv" (module does not exist, 0)
[    27.199] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    27.325] (EE) [drm] failed to open device
[    27.795] (II) VESA(0): VESA VBE DDC read failed
[    28.110] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
jk@jk-M570RU:~$ cat /etc/modprobe.d/nvidia-graphics-drivers.conf | grep "alias nvidia"
alias nvidia nvidia_current_updates
jk@jk-M570RU:~$ ls -la /lib/modules/$(uname -r)/updates/dkms/nvidia*
-rw-r--r-- 1 root root 15155648 Aug  8 00:36 /lib/modules/3.5.0-8-generic/updates/dkms/nvidia_current.ko
-rw-r--r-- 1 root root 15155648 Aug  8 00:26 /lib/modules/3.5.0-8-generic/updates/dkms/nvidia_current_updates.ko
jk@jk-M570RU:~$ ls -la /lib/modules/$(uname -r)/kernel/drivers/video/nvidia*.ko
ls: cannot access /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia*.ko: No such file or directory
jk@jk-M570RU:~$ ls -la /lib/modules/$(uname -r)/kernel/drivers/video/nvidia/*.ko-rw-r--r-- 1 root root 69080 Aug  4 06:06 /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidiafb.ko
jk@jk-M570RU:~$ ls -la /usr/lib/*GL*
ls: cannot access /usr/lib/*GL*: No such file or directory
jk@jk-M570RU:~$ ls -la /usr/lib32/*GL*
ls: cannot access /usr/lib32/*GL*: No such file or directory
jk@jk-M570RU:~$ 

```

---

### Post by effenberg0x0 on 2012-08-07
Ok, I'm still testing here but:

- You have xserver 1.12.99.902 (1.13.0 RC 2), which may be the source of the problem. All your other stuff works with 1.12.1.902 (1.12.2 RC 2).

- More importantly (this is where I'm getting at recently - see [http://ubuntuforums.org/showthread.php?t=2038500](http://ubuntuforums.org/showthread.php?t=2038500)), look at your logs here:
> [    27.115] (II) NVIDIA GLX Module  304.32  Thu Aug  2 19:03:23 PDT 2012
[    27.115] Loading extension GLX
[    27.115] (II) LoadModule: "nvidia"
[    27.115] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    27.115] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.115] 	compiled for 4.0.2, module version = 1.0.0
[    27.115] 	Module class: X.Org Video Driver
[    27.118] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    27.118] (EE) NVIDIA:     system's kernel log for additional error messages.
[    27.118] (II) UnloadModule: "nvidia"
[    27.118] (II) Unloading nvidia

This is the point. Why doesnt it find and load your proper nvidia module? In all testing I've done so far, it comes from a problem with module aliases.
Your output shows us that "nvidia" is set as an alias to nvidia-current-updates.ko in your modprobe conf files. And you do have this module at /lib/modules/3.5.0-8-generic/updates/dkms/nvidia_current_updates.ko.

My guess is that one can fix this by creating a softlink, like I did in the thread I mentioned above. The difference is that I was using NVidia's binary driver, which has a different naming convention.

What I mean is this: If you have softlinks at /lib/modules/3.5.0-8-generic/kernel/drivers/video and /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia that point to /lib/modules/3.5.0-8-generic/updates/dkms/nvidia_current_updates.ko, X will manage to load NVidia module. 

**TEST:**
```
sudo ln -s /lib/modules/3.5.0-8-generic/updates/dkms/nvidia_current_updates.ko /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia.ko
sudo ln -s /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia.ko /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia_current.ko
sudo ln -s /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia.ko /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia_current_updates.ko

sudo ln -s /lib/modules/3.5.0-8-generic/updates/dkms/nvidia_current_updates.ko /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidia.ko
sudo ln -s /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia.ko /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidia_current.ko
sudo ln -s /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia.ko /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidia_current_updates.ko

sudo reboot now
```

**UNDO CHANGES (If it fails to fix things)**
OBS: It will only remove the softlinks we created, not the modules.
```
sudo rm -rf /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia.ko
sudo rm -rf /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia_current.ko
sudo rm -rf /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia_current_updates.ko

sudo rm -rf /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidia.ko
sudo rm -rf /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidia_current.ko
sudo rm -rf /lib/modules/3.5.0-8-generic/kernel/drivers/video/nvidia/nvidia_current_updates.ko

```
Let me know the results please.

Thanks!
Effenberg

---

### Post by flipper T on 2012-08-07
hi

followed your instructions, rebooted, no change as far as i can tell.

must go now, sleepy, but will be back soon.

---

### Post by effenberg0x0 on 2012-08-07
If anyone wants to jump in, my questions right now are:

- There is a percentage of people with w non-usable set of xserver+unity+compiz+kernel+nvidia module+nvidia drivers, this is normal. But why do we now suddenly see a relevant and apparetly growing percentage of users with Xorg/Kernel log pointing out problems finding NVidia module? Where is this coming from? 

- So far, I can only guess it has something to do with the way module aliases get after the users switch between NVidia from binary installer, nvidia-current, nvidia-current-updates, nouveau, xorg-edgers, etc. 

- When that is in fact the problem, one has a couple alternatives to fix it: See As seen here: [http://ubuntuforums.org/showthread.php?t=2038500](http://ubuntuforums.org/showthread.php?t=2038500)

- NVidia binary installer seems to auto check/fix modules to some extent (blacklists nouveau, for example). But it does not fix previous nvidia* aliases. Jockey has been under changes, it could be it. Is anyone keeping up with how its nvidia python handler deals with modules aliases?

- NVidia recently added dkms support. But I can't quite understand how dkms could be a part in this problem.

Regards,
Effenberg

EDIT: Is anyone interested on joining efforts to code a NVidia diagnostic/fix shell script that consolidates all or most of the common issues and workarounds we know about it? I think it can be useful for us testers, for support people, and as a sort of specification for further developments in Jockey/handlers. It's not something hard to do and maybe we can generalize it to ATI / Intel too.

---

### Post by mc4man on 2012-08-07
While I'm not using nvidia atm normally - 
installing the current Ubuntu package - any attempt to draw anything on the screen kills X in a 3d session (unity 3d, classic with effects, gnome-shell.
So the first time from nouveau to nvidia in unity 3d, because I don't use the Desktop I can successfully login, & use compiz as long as nothing is (re)-drawn (switch viewports
As soon as anything is attempted, even just a tooltip from launcher, then xserver is killed & go back to login screen
(Feels just like if one ran a kill xserver command.

This happens with Xorg 1.13.0 RC 2, (proposed) or RC 3 (the ppa), haven't tried the Xorg source in main as that would involve more than I want to do atm, 

The most prevalent error I see is fairly generic - 
XIO:  fatal IO error 4 (Interrupted system call) on X server ":0"

---

### Post by effenberg0x0 on 2012-08-07
> **mc4man said:**
> While I'm not using nvidia atm normally - 
installing the current Ubuntu package - any attempt to draw anything on the screen kills X in a 3d session (unity 3d, classic with effects, gnome-shell.
So the first time from nouveau to nvidia in unity 3d, because I don't use the Desktop I can successfully login, & use compiz as long as nothing is (re)-drawn (switch viewports
As soon as anything is attempted, even just a tooltip from launcher, then xserver is killed & go back to login screen
(Feels just like if one ran a kill xserver command.

This happens with Xorg 1.13.0 RC 2, (proposed) or RC 3 (the ppa), haven't tried the Xorg source in main as that would involve more than I want to do atm, 

The most prevalent error I see is fairly generic - 
XIO:  fatal IO error 4 (Interrupted system call) on X server ":0"

I know this error message: AFAIK, this XIO error is never the problem. It is raised when when something tries to talk to X but X is already closed. As it happens when you have stuff in your X startup script but X dies too fast.

A suggestion: What if you login, switch to any VT, then DISPLAY=:0.0 compiz --replace, go back to VT7 and let it crash? Maybe compiz would give us some output we could use in the VT. 

Or explore compiz --debug, but you would also need the dgbsym to step it through gdb. Check [https://wiki.ubuntu.com/DebuggingCompiz](https://wiki.ubuntu.com/DebuggingCompiz). It can be a lot of fun :)

Regards,
Effenberg

---

### Post by mc4man on 2012-08-08
Doesn't really have anything to do with compiz here, it's simply nvidia-current 304.32-0ubuntu3 won't work in a 3d session with xserver 1.13 (RC2 or 3
Reverting back to the xserver-xorg that's currently in main, ( 1.12.1.902 (1.12.2 RC 2) and the nvidia driver works fine.

---

### Post by VinDSL on 2012-08-08
> **effenberg0x0 said:**
> If anyone wants to jump in, my questions right now are [...]

> **mc4man said:**
> Doesn't really have anything to do with compiz here, **[COLOR="DarkRed"]it's simply nvidia-current 304.32-0ubuntu3 won't work in a 3d session with xserver 1.13[/COLOR]**[...]
Exactly!

nvidia-current 304.3x works fine with LXDE/Openbox (on top of Ubu 12.10) but the Unity and GS DEs fail to load.

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.32-0ubuntu3
  Candidate: 304.32-0ubuntu3
  Version table:
 *** 304.32-0ubuntu3 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.32-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages

vindsl@Zuul:~$ apt-cache policy lxde
lxde:
  Installed: 0.5.0-4ubuntu3
  Candidate: 0.5.0-4ubuntu3
  Version table:
 *** 0.5.0-4ubuntu3 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/universe i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ apt-cache policy openbox
openbox:
  Installed: 3.5.0-4
  Candidate: 3.5.0-4
  Version table:
 *** 3.5.0-4 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/universe i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~
Current Date/Time: Wed Aug  8 04:07:03 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc1-generic
Unity Release: unity 6.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.32

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
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch
  Installed: 2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz

vindsl@Zuul:~$ 

```

Only problem I'm currently having is with fontconfig...

```
vindsl@Zuul:~$vindsl@Zuul:~$ apt-cache policy fontconfig
fontconfig:
  Installed: 2.10.1-0ubuntu2
  Candidate: 2.10.1-0ubuntu2
  Version table:
 *** 2.10.1-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ fc-match
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-unfonts-core.conf", line 11: Having multiple values in <test> isn't supported and may not works as expected
vindsl@Zuul:~$ 

```

This fontconfig prob seems to be universal, affecting all Linux distros, not just Debian-based ones, judging by the results on various search engines.

---

### Post by effenberg0x0 on 2012-08-08
VinDSL, mc4man

My bad, when I saw reports that people could use unity 2D but not Unity 3D I thought of Compiz. I had not paid attention to reports of no 3D also in other DEs.

Regards,
Effenberg

---

### Post by dino99 on 2012-08-08
[QUOTE=VinDSL]

This fontconfig prob seems to be universal, affecting all Linux distros, not just Debian-based ones, judging by the results on various search engines.[/QUOTE]

Have had this issue too, but as the errors comments says, its deprecated : simply rename (or delete) .fonts.conf file & .fontconfig folder, then the new paths will be used instaed :P

---

### Post by VinDSL on 2012-08-08
> **dino99 said:**
> Have had this issue too, but as the errors comments says, its deprecated : simply rename (or delete) .fonts.conf file & .fontconfig folder, then the new paths will be used instaed :P
Sweet!

I'll try that...  ;)

---

### Post by VinDSL on 2012-08-08
> **effenberg0x0 said:**
> [...] when I saw reports that people could use unity 2D but not Unity 3D I thought of Compiz. I had not paid attention to reports of no 3D also in other DEs.[...]
I have a *gut feeling* that the problem is with Gnome3, not nVidia, but I have no proof of it, at this point.

If that's the case, then I suppose it would have to be addressed upstream.

---

### Post by mc4man on 2012-08-08
> **VinDSL said:**
> I have a *gut feeling* that the problem is with Gnome3, not nVidia, but I have no proof of it, at this point.

If that's the case, then I suppose it would have to be addressed upstream.

At least here it's just an xorg/nvidia crash
(get a crash report, but due to unavailable debug symbols quite useless

So here can log in to unity & do all sorts of useless stuff like expose the launcher, open Dash, open run command, go to expo.
Just can't open a window or expose a tooltip from plank or drop down an indicator menu or have the screenshot (non interactive) flash the screen 
(by default am not using the Desktop so at login it's empty
Any of those crash/kill X
(the basic crash title would be 
Xorg crashed with SIGABRT in doFreeResource()

---

### Post by paul_in_london on 2012-08-08
> **VinDSL said:**
> Exactly!

nvidia-current 304.3x works fine with LXDE/Openbox (on top of Ubu 12.10) but the Unity and GS DEs fail to load.

...

[COLOR="Red"]**Only problem I'm currently having is with fontconfig**[/COLOR]...

Do you mean apart from the instant firefox crashes even in gnome-classic and openbox/lxde?! :lolflag:

I still don't understand why this is only happening with firefox and not other browsers. I thought today's xserver-common and xserver-xorg-core updates might have helped, but nope.

---

### Post by effenberg0x0 on 2012-08-08
> **paul_in_london said:**
> Do you mean apart from the instant firefox crashes even in gnome-classic and openbox/lxde?! :lolflag:

I still don't understand why this is only happening with firefox and not other browsers. I thought today's xserver-common and xserver-xorg-core updates might have helped, but nope.


Someone at a local Ubuntu forum here speculated that the majority of people only have Firefox and Chrome and are reporting that only Firefox is broken. In such scenario, this group proposes that our current situation is more precisely defined as "Chrome is not broken, while all other browsers are" or "Chrome is not broken". Interesting theory (a lot of Google fanboys behind it too), but I do not have other browsers apart from these two to test. And if I were to test with, say, Midori and it crashed I'd probably say "meh, inconclusive - It has always crashed".

What do you guys think?

Regards,
Effenberg

EDIT: Another theory raised just now: Chrome relates to Flash differently than other browsers. When other browsers load plugins at start, they crash - Chrome does not (people still following the "all but Chrome are broken, not only Firefox" assumption).

---

### Post by paul_in_london on 2012-08-08
> **effenberg0x0 said:**
> Someone at a local Ubuntu forum here speculated that the majority of people only have Firefox and Chrome and are reporting that only Firefox is broken. In such scenario, this group proposes that our current situation is more precisely defined as "Chrome is not broken, while all other browsers are" or "Chrome is not broken". Interesting theory (a lot of Google fanboys behind it too), but I do not have other browsers apart from these two to test. And if I were to test with, say, Midori and it crashed I'd probably say "meh, inconclusive - It has always crashed".

What do you guys think?

Regards,
Effenberg

EDIT: Another theory raised just now: Chrome relates to Flash differently than other browsers. When other browsers load plugins at start, they crash - Chrome does not (people still following the "all but Chrome are broken, not only Firefox" assumption).

Well for me, chrome/chromium/iron/midori/arora/qupzilla/opera all work. It's just firefox that's the problem since the upgrade to X Server 1.13.

I currently have:

```
paul@quantal-64:~$ X -version                                                   

X.Org X Server 1.12.99.904 (1.13.0 RC 4)
Release Date: 2012-08-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-26-generic x86_64 Ubuntu
Current Operating System: Linux quantal-64 3.6.0-030600rc1-generic #201208022056 SMP Fri Aug 3 00:57:36 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.6.0-030600rc1-generic root=UUID=c16f4cbf-43d3-45d7-b41e-a8ca3b339513 ro
Build Date: 08 August 2012  11:48:21AM
xorg-server 2:1.12.99.904-0ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
paul@quantal-64:~$
``` and

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.32-0ubuntu3
  Candidate: 304.32-0ubuntu3
  Version table:
 *** 304.32-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
     304.32-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
paul@quantal-64:~$
```

---

### Post by ventrical on 2012-08-08
I have firefox working here (Gnome Classic with Effects) but can't MOVE any windows about. All windows in fact will not move but are totally functional.

---

### Post by ventrical on 2012-08-08
Unity 3D is working fine with the exception that the horizontal tearing is back between the windows title bars and the main window  being dragged.
nvidia-current 304-32-0ubuntu3
xserver-xorg-core 2:1.12.1.902

---

### Post by paul_in_london on 2012-08-08
> **ventrical said:**
> Unity 3D is working fine with the exception that the horizontal tearing is back between the windows title bars and the main window  being dragged.
nvidia-current 304-32-0ubuntu3
xserver-xorg-core 2:1.12.1.902

Hi ventrical,

Well no version of FF works for me at the moment - even in safe mode it just throws me straight back to the login screen (exactly the same effect as soon as I try to log in to a G-S session). It's annoying because it's the browser I use most.

Tried FF in gnome-classic with and without effects (usually use no effects) and in my lubuntu install (lxde session and openbox session).

We're using the same nvidia driver, but I have:

```
paul@quantal-64:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.12.99.904-0ubuntu1
  Candidate: 2:1.12.99.904-0ubuntu1
  Version table:
 *** 2:1.12.99.904-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
     2:1.12.1.902-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
paul@quantal-64:~$
```

Are you using 32 or 64 bit? Are you having issues with any other browsers?

---

### Post by ventrical on 2012-08-08
Had a similar problem a while back where I had to downgrade xserver-xorg-core.

---

### Post by ventrical on 2012-08-08
> **paul_in_london said:**
> Hi ventrical,

Well no version of FF works for me at the moment - even in safe mode it just throws me straight back to the login screen (exactly the same effect as soon as I try to log in to a G-S session). It's annoying because it's the browser I use most.

Tried FF in gnome-classic with and without effects (usually use no effects) and in my lubuntu install (lxde session and openbox session).

We're using the same nvidia driver, but I have:

```
paul@quantal-64:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.12.99.904-0ubuntu1
  Candidate: 2:1.12.99.904-0ubuntu1
  Version table:
 *** 2:1.12.99.904-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
     2:1.12.1.902-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
paul@quantal-64:~$
```Are you using 32 or 64 bit? Are you having issues with any other browsers?

32 bit.

 I just re-enabled 'proposed' repos. Updating now. I'll get back soon enough.

---

### Post by paul_in_london on 2012-08-08
> **ventrical said:**
> Had a similar problem a while back where I had to downgrade xserver-xorg-core.

That particular xserver-xorg-core update came through today, but this problem definitely seems to be associated with X Server 1.13 somehow. Just not sure why (in my case anyway) it's restricted to FF. :confused:

---

### Post by ventrical on 2012-08-08
Wow.... unbelievable. I enabled the proposed  and now I have the same thing as you - click firefox and it goes back to login screen. I downloaded Chromium and thats is working here now. Tried to file a bug on ff. I'll have to disable settings and use Chrome.

  Everything else works (seemingly)

  Looks like a classic sideXside to me.

  I'm off to try and file a bug on ff.

---

### Post by mc4man on 2012-08-08
> **paul_in_london said:**
> That particular xserver-xorg-core update came through today, but this problem definitely seems to be associated with X Server 1.13 somehow. Just not sure why (in my case anyway) **it's restricted to FF.** :confused:

Are you saying you can run a 3d session with 1.13 & nvidia?

At least here 2 basic choices - 
1.12 > nvidia or nouveau  - 3d + FF & TB work fine
1.13 > nouveau  - 3d + FF & TB work fine, nvidia - no 3d, no FF or TB in 2d

---

### Post by ventrical on 2012-08-08
Here's what I did on this.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1034671](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1034671)

what a wicked little bug.

---

### Post by VinDSL on 2012-08-08
> **mc4man said:**
> Are you saying you can run a 3d session with 1.13 & nvidia?

At least here 2 basic choices - 
1.12 > nvidia or nouveau  - 3d + FF & TB work fine
1.13 > nouveau  - 3d + FF & TB work fine, nvidia - no 3d, no FF or TB in 2d
Heh!  We're on the same page.

Put another way, my experience has been identical to yours...  ;)

---

### Post by ventrical on 2012-08-08
Does not seem to be a firefox bug.

Something is really wrong with apport also. It is reporting that Chromium had crashed, to restart it, but I just ignored it and it is still running .

---

### Post by ventrical on 2012-08-08
> **mc4man said:**
> Are you saying you can run a 3d session with 1.13 & nvidia?

At least here 2 basic choices - 
1.12 > nvidia or nouveau  - 3d + FF & TB work fine
1.13 > nouveau  - 3d + FF & TB work fine, nvidia - no 3d, no FF or TB in 2d


Yes.. that seemes to be the temporary fix.

 Took out nvidia-current and put in nouveau-firmware.

---

### Post by ventrical on 2012-08-08
Here is the apport bug-report after I installed nouveau-firmware running in Unity 3D.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1034680](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1034680)

---

### Post by mc4man on 2012-08-08
> **ventrical said:**
> Here is the apport bug-report after I installed nouveau-firmware running in Unity 3D.

Any particular reason why you are installing that package?

If your nvidia chip supports it then vsync can be enabled in nouveau, mentioned in comment 2 that atm fermi & later don't.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131)

---

### Post by ventrical on 2012-08-08
> **mc4man said:**
> Any particular reason why you are installing that package?

If your nvidia chip supports it then vsync can be enabled in nouveau, mentioned in comment 2 that atm fermi & later don't.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131)

ya know .. atm I'm so tired I'm not sure what I'm doing :)

---

### Post by VinDSL on 2012-08-08
> **VinDSL said:**
> Only problem I'm currently having is with fontconfig...

```
vindsl@Zuul:~$vindsl@Zuul:~$ apt-cache policy fontconfig
fontconfig:
  Installed: 2.10.1-0ubuntu2
  Candidate: 2.10.1-0ubuntu2
  Version table:
 *** 2.10.1-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ fc-match
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-unfonts-core.conf", line 11: Having multiple values in <test> isn't supported and may not works as expected
vindsl@Zuul:~$ 

```

> **dino99 said:**
> Have had this issue too, but as the errors comments says, its deprecated : simply rename (or delete) .fonts.conf file & .fontconfig folder, then the new paths will be used instaed :P
Don't want to hijack this thread, but thanks, my friend!  You gave me an idea.

Took care of the "old" deprecated stuff, as you suggested PLUS I manually fixed the "new" .conf files.  

As a result, no more fontconfig errors...  :D

```
vindsl@Zuul:~$ fc-match --all
DejaVuSans.ttf: "DejaVu Sans" "Book"
DejaVuSansCondensed.ttf: "DejaVu Sans" "Condensed"
DejaVuSans-ExtraLight.ttf: "DejaVu Sans" "ExtraLight"
DejaVuSans-Bold.ttf: "DejaVu Sans" "Bold"
DejaVuSansCondensed-Bold.ttf: "DejaVu Sans" "Condensed Bold"
DejaVuSans-Oblique.ttf: "DejaVu Sans" "Oblique"
DejaVuSansCondensed-Oblique.ttf: "DejaVu Sans" "Condensed Oblique"
DejaVuSans-BoldOblique.ttf: "DejaVu Sans" "Bold Oblique"
DejaVuSansCondensed-BoldOblique.ttf: "DejaVu Sans" "Condensed Bold Oblique"
n019003l.pfb: "Nimbus Sans L" "Regular"
n019043l.pfb: "Nimbus Sans L" "Regular Condensed"
n019004l.pfb: "Nimbus Sans L" "Bold"
n019044l.pfb: "Nimbus Sans L" "Bold Condensed"
n019023l.pfb: "Nimbus Sans L" "Regular Italic"
n019063l.pfb: "Nimbus Sans L" "Regular Condensed Italic"
n019024l.pfb: "Nimbus Sans L" "Bold Italic"
n019064l.pfb: "Nimbus Sans L" "Bold Condensed Italic"
Waree.ttf: "Waree" "Book"
Waree-Bold.ttf: "Waree" "Bold"
Waree-Oblique.ttf: "Waree" "Oblique"
Waree-BoldOblique.ttf: "Waree" "BoldOblique"
Loma.ttf: "Loma" "Book"
Loma-Bold.ttf: "Loma" "Bold"
Loma-Oblique.ttf: "Loma" "Oblique"
Loma-BoldOblique.ttf: "Loma" "BoldOblique"
Garuda.ttf: "Garuda" "Book"
Garuda-Bold.ttf: "Garuda" "Bold"
Garuda-Oblique.ttf: "Garuda" "Oblique"
Garuda-BoldOblique.ttf: "Garuda" "BoldOblique"
Umpush.ttf: "Umpush" "Book"
Umpush-Light.ttf: "Umpush" "Light"
Umpush-Bold.ttf: "Umpush" "Bold"
Umpush-Oblique.ttf: "Umpush" "Oblique"
Umpush-LightOblique.ttf: "Umpush" "LightOblique"
Umpush-BoldOblique.ttf: "Umpush" "BoldOblique"
KhmerOS.ttf: "Khmer OS" "Regular"
MuktiNarrow.ttf: "Mukti Narrow" "Regular"
MuktiNarrowBold.ttf: "Mukti Narrow" "Regular"
NanumGothic.ttf: "NanumGothic" "Regular"
NanumGothicBold.ttf: "NanumGothic" "Bold"
UnDotum.ttf: "UnDotum" "Regular"
UnDotumBold.ttf: "UnDotum" "Bold"
lohit_bn.ttf: "Lohit Bengali" "Regular"
lohit_gu.ttf: "Lohit Gujarati" "Regular"
lohit_hi.ttf: "Lohit Hindi" "Regular"
lohit_pa.ttf: "Lohit Punjabi" "Regular"
lohit_ta.ttf: "Lohit Tamil" "Regular"
Meera_04.ttf: "Meera" "Regular"
FreeSans.ttf: "FreeSans" "&#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1077;&#1085;"
FreeSansBold.ttf: "FreeSans" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085;"
FreeSansOblique.ttf: "FreeSans" "&#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
FreeSansBoldOblique.ttf: "FreeSans" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085; &#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
TlwgTypo.ttf: "Tlwg Typo" "Medium"
KacstArt.ttf: "KacstArt" "Medium"
KacstBook.ttf: "KacstBook" "Medium"
KacstDecorative.ttf: "KacstDecorative" "Medium"
KacstDigital.ttf: "KacstDigital" "Medium"
KacstFarsi.ttf: "KacstFarsi" "Medium"
KacstLetter.ttf: "KacstLetter" "Medium"
KacstNaskh.ttf: "KacstNaskh" "Medium"
KacstOffice.ttf: "KacstOffice" "Medium"
KacstPen.ttf: "KacstPen" "Medium"
KacstPoster.ttf: "KacstPoster" "Medium"
KacstScreen.ttf: "KacstScreen" "Medium"
KacstTitle.ttf: "KacstTitle" "Medium"
gargi.ttf: "gargi" "Medium"
TlwgTypist.ttf: "Tlwg Typist" "Medium"
TlwgMono.ttf: "TlwgMono" "Medium"
TlwgTypewriter.ttf: "TlwgTypewriter" "Medium"
Kinnari.ttf: "Kinnari" "Medium"
ConkyWeather.otf: "ConkyWeather" "Medium"
ConkyWind.otf: "ConkyWind" "Medium"
ConkyWindN.otf: "ConkyWindN" "Medium"
ConkyWindNESW.otf: "ConkyWindNESW" "Medium"
Rekha.ttf: "Rekha" "Medium"
utkal.ttf: "ori1Uni" "Medium"
Ubuntu-M.ttf: "Ubuntu" "Medium"
c059013l.pfb: "Century Schoolbook L" "Roman"
p052003l.pfb: "URW Palladio L" "Roman"
FreeMono.ttf: "FreeMono" "&#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1077;&#1085;"
FreeSerif.ttf: "FreeSerif" "&#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1077;&#1085;"
opens___.ttf: "OpenSymbol" "Regular"
KacstOne.ttf: "KacstOne" "Regular"
Norasi.ttf: "Norasi" "Regular"
Rachana_04.ttf: "Rachana" "Regular"
fonts-japanese-gothic.ttf: "TakaoPGothic" "Regular"
TakaoPGothic.ttf: "TakaoPGothic" "Regular"
KhmerOSsys.ttf: "Khmer OS System" "Regular"
DejaVuSansMono.ttf: "DejaVu Sans Mono" "Book"
DejaVuSerif.ttf: "DejaVu Serif" "Book"
NanumMyeongjo.ttf: "NanumMyeongjo" "Regular"
Purisa.ttf: "Purisa" "Medium"
KacstQurn.ttf: "KacstQurn" "Medium"
KacstTitleL.ttf: "KacstTitleL" "Medium"
Radiof.ttf: "Radio Space" "Regular"
UbuntuTitleBold.ttf: "UbuntuTitleBold" "Bold"
UbuntuTitleRegular.ttf: "UbuntuTitleRegular" "Regular"
Ubuntu-Title.ttf: "Ubuntu-Title" "Title"
Pothana2000.ttf: "Pothana2000" "Pothana2000"
Vemana.ttf: "Vemana2000" "Pothana2000"
LiberationMono-Regular.ttf: "Liberation Mono" "Regular"
LiberationSans-Regular.ttf: "Liberation Sans" "Regular"
LiberationSerif-Regular.ttf: "Liberation Serif" "Regular"
LiberationMono-Regular.ttf: "Liberation Mono" "Regular"
LiberationSans-Regular.ttf: "Liberation Sans" "Regular"
LiberationSerif-Regular.ttf: "Liberation Serif" "Regular"
Sawasdee.ttf: "Sawasdee" "Regular"
mry_KacstQurn.ttf: "mry_KacstQurn" "Regular"
Overlock-Regular-OTF.otf: "Overlock" "Regular"
Ahem.ttf: "Ahem" "Regular"
DroidSansMono.ttf: "Droid Sans Mono" "Regular"
DroidSerif-Regular.ttf: "Droid Serif" "Regular"
DroidSansMono.ttf: "Droid Sans Mono" "Regular"
DroidSerif-Regular.ttf: "Droid Serif" "Regular"
Phetsarath_OT.ttf: "Phetsarath OT" "Regular"
UnDinaru.ttf: "UnDinaru" "Regular"
BOXES.TTF: "Some Boxes" "Regular"
BOXES.TTF: "Some Boxes" "Regular"
KR A Round.ttf: "KR A Round" "Regular"
PIZZADUDEBULLETS.ttf: "PizzaDude Bullets" "Regular"
STYLBCC_.TTF: "StyleBats" "CleanCut"
cutouts.ttf: "Cut Outs for 3D FX" "Normal"
openlogos.ttf: "OpenLogos" "Regular"
Arrows.ttf: "Arrows" "Regular"
StyleBats.ttf: "StyleBats" "CleanCut"
Kedage-n.ttf: "Kedage" "Normal"
Malige-n.ttf: "Mallige" "Normal"
cutouts.ttf: "Cut Outs for 3D FX" "Normal"
Ubuntu-C.ttf: "Ubuntu Condensed" "Regular"
Ubuntu-R.ttf: "Ubuntu" "Regular"
UbuntuMono-R.ttf: "Ubuntu Mono" "Regular"
wqy-microhei.ttc: "WenQuanYi Micro Hei" "Regular"
wqy-microhei.ttc: "WenQuanYi Micro Hei Mono" "Regular"
Saab.ttf: "Saab" "Regular"
Ubuntu-R.ttf: "Ubuntu" "Regular"
DroidSans.ttf: "Droid Sans" "Regular"
DroidSans.ttf: "Droid Sans" "Regular"
DroidNaskh-Regular.ttf: "Droid Sans" "Regular"
DroidSansEthiopic-Regular.ttf: "Droid Sans" "Regular"
DroidSansHebrew-Regular.ttf: "Droid Sans" "Regular"
DroidSansThai.ttf: "Droid Sans" "Regular"
DroidSansArmenian.ttf: "Droid Sans" "Regular"
DroidSansGeorgian.ttf: "Droid Sans" "Regular"
DroidSansJapanese.ttf: "Droid Sans" "Regular"
DroidSansJapanese.ttf: "Droid Sans" "Regular"
DroidSansFallback.ttf: "Droid Sans" "Regular"
DroidSansFallbackFull.ttf: "Droid Sans" "Regular"
c0419bt_.pfb: "Courier 10 Pitch" "Regular"
c0648bt_.pfb: "Bitstream Charter" "Regular"
UnBatang.ttf: "UnBatang" "Regular"
UnGraphic.ttf: "UnGraphic" "Regular"
UnGungseo.ttf: "UnGungseo" "Regular"
UnPilgi.ttf: "UnPilgi" "Regular"
b018012l.pfb: "URW Bookman L" "Light"
n021003l.pfb: "Nimbus Roman No9 L" "Regular"
n022003l.pfb: "Nimbus Mono L" "Regular"
MOON.TTF: "Moon Phases" "Regular"
Symbol.pfb: "Symbol" "Regular"
Moon Phases.ttf: "Moon Phases" "Regular"
d050000l.pfb: "Dingbats" "Regular"
s050000l.pfb: "Standard Symbols L" "Regular"
Symbol.pfb: "Symbol" "Regular"
DejaVuSerifCondensed.ttf: "DejaVu Serif" "Condensed"
Radiofc.ttf: "Radio Space Condensed" "Condensed"
LiberationSansNarrow-Regular.ttf: "Liberation Sans Narrow" "Regular"
LiberationSansNarrow-Regular.ttf: "Liberation Sans Narrow" "Regular"
a010013l.pfb: "URW Gothic L" "Book"
UnDinaruLight.ttf: "UnDinaru" "Light"
Ubuntu-L.ttf: "Ubuntu" "Light"
Ubuntu-L.ttf: "Ubuntu" "Light"
DroidSansHebrew-Bold.ttf: "Droid Sans" "Bold"
a010015l.pfb: "URW Gothic L" "Demi"
FreeSerifBold.ttf: "FreeSerif" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085;"
FreeMonoBold.ttf: "FreeMono" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085;"
KacstOne-Bold.ttf: "KacstOne" "Bold"
Norasi-Bold.ttf: "Norasi" "Bold"
DejaVuSansMono-Bold.ttf: "DejaVu Sans Mono" "Bold"
DejaVuSerif-Bold.ttf: "DejaVu Serif" "Bold"
Purisa-Bold.ttf: "Purisa" "Bold"
TlwgTypo-Bold.ttf: "Tlwg Typo" "Bold"
Radiofb.ttf: "Radio Space Bold" "Bold"
LiberationMono-Bold.ttf: "Liberation Mono" "Bold"
LiberationSans-Bold.ttf: "Liberation Sans" "Bold"
LiberationSerif-Bold.ttf: "Liberation Serif" "Bold"
LiberationMono-Bold.ttf: "Liberation Mono" "Bold"
LiberationSans-Bold.ttf: "Liberation Sans" "Bold"
LiberationSerif-Bold.ttf: "Liberation Serif" "Bold"
TlwgTypist-Bold.ttf: "Tlwg Typist" "Bold"
TlwgMono-Bold.ttf: "TlwgMono" "Bold"
TlwgTypewriter-Bold.ttf: "TlwgTypewriter" "Bold"
Kinnari-Bold.ttf: "Kinnari" "Bold"
Sawasdee-Bold.ttf: "Sawasdee" "Bold"
DroidSerif-Bold.ttf: "Droid Serif" "Bold"
DroidSerif-Bold.ttf: "Droid Serif" "Bold"
UnDinaruBold.ttf: "UnDinaru" "Bold"
weather.ttf: "Weather" "Regular"
weather.ttf: "Weather" "Regular"
wef_____.ttf: "Weather" "Regular"
NanumMyeongjoBold.ttf: "NanumMyeongjo" "Bold"
Kedage-b.ttf: "Kedage" "Bold"
Malige-b.ttf: "Mallige" "Bold"
Ubuntu-B.ttf: "Ubuntu" "Bold"
UbuntuMono-B.ttf: "Ubuntu Mono" "Bold"
Ubuntu-B.ttf: "Ubuntu" "Bold"
DroidSans-Bold.ttf: "Droid Sans" "Bold"
DroidSans-Bold.ttf: "Droid Sans" "Bold"
DroidNaskh-Bold.ttf: "Droid Sans" "Bold"
DroidSansEthiopic-Bold.ttf: "Droid Sans" "Bold"
c0583bt_.pfb: "Courier 10 Pitch" "Bold"
c0632bt_.pfb: "Bitstream Charter" "Bold"
UnBatangBold.ttf: "UnBatang" "Bold"
UnGraphicBold.ttf: "UnGraphic" "Bold"
UnPilgiBold.ttf: "UnPilgi" "Bold"
b018015l.pfb: "URW Bookman L" "Demi Bold"
c059016l.pfb: "Century Schoolbook L" "Bold"
n021004l.pfb: "Nimbus Roman No9 L" "Medium"
n022004l.pfb: "Nimbus Mono L" "Bold"
p052004l.pfb: "URW Palladio L" "Bold"
DejaVuSerifCondensed-Bold.ttf: "DejaVu Serif" "Condensed Bold"
LiberationSansNarrow-Bold.ttf: "Liberation Sans Narrow" "Bold"
LiberationSansNarrow-Bold.ttf: "Liberation Sans Narrow" "Bold"
Kinnari-Italic.ttf: "Kinnari" "Italic"
Ubuntu-MI.ttf: "Ubuntu" "Medium Italic"
z003034l.pfb: "URW Chancery L" "Medium Italic"
FreeSerifItalic.ttf: "FreeSerif" "&#1082;&#1091;&#1088;&#1089;&#1080;&#1074;&#1077;&#1085;"
FreeMonoOblique.ttf: "FreeMono" "&#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
Norasi-Italic.ttf: "Norasi" "Italic"
DejaVuSerif-Italic.ttf: "DejaVu Serif" "Italic"
Radiofi.ttf: "Radio Space Italic" "Italic"
LiberationMono-Italic.ttf: "Liberation Mono" "Italic"
LiberationSans-Italic.ttf: "Liberation Sans" "Italic"
LiberationSerif-Italic.ttf: "Liberation Serif" "Italic"
LiberationMono-Italic.ttf: "Liberation Mono" "Italic"
LiberationSans-Italic.ttf: "Liberation Sans" "Italic"
LiberationSerif-Italic.ttf: "Liberation Serif" "Italic"
DroidSerif-Italic.ttf: "Droid Serif" "Italic"
DroidSerif-Italic.ttf: "Droid Serif" "Italic"
Ubuntu-RI.ttf: "Ubuntu" "Italic"
UbuntuMono-RI.ttf: "Ubuntu Mono" "Italic"
Ubuntu-RI.ttf: "Ubuntu" "Italic"
c0582bt_.pfb: "Courier 10 Pitch" "Italic"
c0649bt_.pfb: "Bitstream Charter" "Italic"
b018032l.pfb: "URW Bookman L" "Light Italic"
c059033l.pfb: "Century Schoolbook L" "Italic"
n021023l.pfb: "Nimbus Roman No9 L" "Regular Italic"
p052023l.pfb: "URW Palladio L" "Italic"
DejaVuSerifCondensed-Italic.ttf: "DejaVu Serif" "Condensed Italic"
LiberationSansNarrow-Italic.ttf: "Liberation Sans Narrow" "Italic"
LiberationSansNarrow-Italic.ttf: "Liberation Sans Narrow" "Italic"
Ubuntu-LI.ttf: "Ubuntu" "Light Italic"
Ubuntu-LI.ttf: "Ubuntu" "Light Italic"
FreeSerifBoldItalic.ttf: "FreeSerif" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085; &#1082;&#1091;&#1088;&#1089;&#1080;&#1074;&#1077;&#1085;"
FreeMonoBoldOblique.ttf: "FreeMono" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085; &#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
Norasi-BoldItalic.ttf: "Norasi" "BoldItalic"
DejaVuSerif-BoldItalic.ttf: "DejaVu Serif" "Bold Italic"
Radiofbi.ttf: "Radio Space Bold Italic" "Bold Italic"
LiberationMono-BoldItalic.ttf: "Liberation Mono" "Bold Italic"
LiberationSans-BoldItalic.ttf: "Liberation Sans" "Bold Italic"
LiberationSerif-BoldItalic.ttf: "Liberation Serif" "Bold Italic"
LiberationMono-BoldItalic.ttf: "Liberation Mono" "Bold Italic"
LiberationSans-BoldItalic.ttf: "Liberation Sans" "Bold Italic"
LiberationSerif-BoldItalic.ttf: "Liberation Serif" "Bold Italic"
Kinnari-BoldItalic.ttf: "Kinnari" "BoldItalic"
DroidSerif-BoldItalic.ttf: "Droid Serif" "Bold Italic"
DroidSerif-BoldItalic.ttf: "Droid Serif" "Bold Italic"
Ubuntu-BI.ttf: "Ubuntu" "Bold Italic"
UbuntuMono-BI.ttf: "Ubuntu Mono" "Bold Italic"
Ubuntu-BI.ttf: "Ubuntu" "Bold Italic"
c0611bt_.pfb: "Courier 10 Pitch" "Bold Italic"
c0633bt_.pfb: "Bitstream Charter" "Bold Italic"
b018035l.pfb: "URW Bookman L" "Demi Bold Italic"
c059036l.pfb: "Century Schoolbook L" "Bold Italic"
n021024l.pfb: "Nimbus Roman No9 L" "Medium Italic"
p052024l.pfb: "URW Palladio L" "Bold Italic"
DejaVuSerifCondensed-BoldItalic.ttf: "DejaVu Serif" "Condensed Bold Italic"
LiberationSansNarrow-BoldItalic.ttf: "Liberation Sans Narrow" "Bold Italic"
LiberationSansNarrow-BoldItalic.ttf: "Liberation Sans Narrow" "Bold Italic"
TlwgTypo-Oblique.ttf: "Tlwg Typo" "Oblique"
TlwgTypist-Oblique.ttf: "Tlwg Typist" "Oblique"
Kinnari-Oblique.ttf: "Kinnari" "Oblique"
Norasi-Oblique.ttf: "Norasi" "Oblique"
DejaVuSansMono-Oblique.ttf: "DejaVu Sans Mono" "Oblique"
Purisa-Oblique.ttf: "Purisa" "Oblique"
TlwgMono-Oblique.ttf: "TlwgMono" "Oblique"
TlwgTypewriter-Oblique.ttf: "TlwgTypewriter" "Oblique"
Sawasdee-Oblique.ttf: "Sawasdee" "Oblique"
n022023l.pfb: "Nimbus Mono L" "Regular Oblique"
a010033l.pfb: "URW Gothic L" "Book Oblique"
a010035l.pfb: "URW Gothic L" "Demi Oblique"
Norasi-BoldOblique.ttf: "Norasi" "BoldOblique"
DejaVuSansMono-BoldOblique.ttf: "DejaVu Sans Mono" "Bold Oblique"
Purisa-BoldOblique.ttf: "Purisa" "BoldOblique"
TlwgTypo-BoldOblique.ttf: "Tlwg Typo" "BoldOblique"
TlwgTypist-BoldOblique.ttf: "Tlwg Typist" "BoldOblique"
TlwgMono-BoldOblique.ttf: "TlwgMono" "BoldOblique"
TlwgTypewriter-BoldOblique.ttf: "TlwgTypewriter" "BoldOblique"
Kinnari-BoldOblique.ttf: "Kinnari" "BoldOblique"
Sawasdee-BoldOblique.ttf: "Sawasdee" "BoldOblique"
n022024l.pfb: "Nimbus Mono L" "Bold Oblique"
vindsl@Zuul:~$ 

```

Okay, back on topic.

---

### Post by Cavsfan on 2012-08-09
> **dino99 said:**
> Have had this issue too, but as the errors comments says, its deprecated : simply rename (or delete) .fonts.conf file & .fontconfig folder, then the new paths will be used instaed :P

Glad I found this thread. I am having the same font errors and was able to rename the .fontconfig folder but, cannot find the .font.conf file
There is not one in my home directory.
I get those deprecated errors every time I get updates and this is what I have:
```
fc-match --all
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
DejaVuSans.ttf: "DejaVu Sans" "Book"
DejaVuSans-Bold.ttf: "DejaVu Sans" "Bold"
n019003l.pfb: "Nimbus Sans L" "Regular"

```Could someone point me in the right direction? Thanks!

---

### Post by ventrical on 2012-08-09
> **mc4man said:**
> Any particular reason why you are installing that package?

If your nvidia chip supports it then vsync can be enabled in nouveau, mentioned in comment 2 that atm fermi & later don't.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131)

 I downgraded to xserver 1.12 and re-installed nvidia-current. All is well.  I just wanted to emulate what paul_in_london  was experiencing.
All is well here.

---

### Post by VinDSL on 2012-08-09
> **Cavsfan said:**
> Glad I found this thread. I am having the same font errors and was able to rename the .fontconfig folder but, cannot find the .font.conf file
There is not one in my home directory.
I get those deprecated errors every time I get updates and this is what I have:
```
fc-match --all
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
DejaVuSans.ttf: "DejaVu Sans" "Book"
DejaVuSans-Bold.ttf: "DejaVu Sans" "Bold"
n019003l.pfb: "Nimbus Sans L" "Regular"

```Could someone point me in the right direction? Thanks!
This morning, I posted this:

[INDENT][http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)[/INDENT]

Might help you out, if you're comfortable hacking XML code...  ;)

---

### Post by dino99 on 2012-08-09
> **VinDSL said:**
> This morning, I posted this:

[INDENT][http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)[/INDENT]

Might help you out, if you're comfortable hacking XML code...  ;)

Like me, if you does not care about the exotic fonts, then purge them and these errors should be going away :P

note: you still can reinstall them if you need them, but the room has been cleaned after purging

---

### Post by Cavsfan on 2012-08-09
> **VinDSL said:**
> This morning, I posted this:[INDENT][http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)[/INDENT]Might help you out, if you're comfortable hacking XML code...  ;)

Thanks for that VinDSL! It definitely helped.  I wasn't comfortable hacking XML before but, I am now! :wink:
Don't know if any one noticed but, when you entered **gksu nautilus** in terminal all of these same font errors appeared.
It took a few times editing and rebooting until I got it all fixed. But, all I had to do is enter **gksu nautilus**  to find out if I had fixed it.
Then I entered **fc-match --all** to confirm and sure enough all was back to normal.

The fonts that had problems on my system were not the same fonts every one else had.
Strange but, like I say I am glad I stumbled upon this thread. Now all is normal with those strange errors.
I would get errors with **sudo apt-get upgrade** and entering "Y" to get the updates.
It would be a whole bunch of lines about fonts with the word deprecated at the end.
That was annoying and so was the output in terminal when entering **gksu nautilus**.

> **dino99 said:**
> Like me, if you do not care about the exotic fonts, then purge them and these errors should be going away :P

note: you still can reinstall them if you need them, but the room has been cleaned after purging
Thank you dino99! I didn't know what to do, so I just followed VinDSL's advice and everything is good to go now. :p

BTW, I have nvidia-current installed and am having no problems in Unity. I did in Classic with effects until I tweaked CCSM and Cairo Dock.
I really like emerald window decorator and have it installed on my other 2 Ubuntus but, have not found a place to get it for Quantal 
and I definitely do not want to break it just for emerald.

```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.32

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
``````
Xorg -version

X.Org X Server 1.12.1.902 (1.12.2 RC 2)
Release Date: 2012-05-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-23-generic x86_64 Ubuntu
Current Operating System: Linux cavsfan-MS-7529 3.5.0-8-generic #8-Ubuntu SMP Sat Aug 4 04:42:28 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz root=/dev/sda9 ro quiet splash
Build Date: 22 June 2012  03:24:25AM
xorg-server 2:1.12.1.902-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

``````
cavsfan@cavsfan-MS-7529:~$ compiz --version
Compiz 0.9.8
cavsfan@cavsfan-MS-7529:~$ unity --version
unity 6.0.0
``````
cavsfan@cavsfan-MS-7529:~$ modinfo nvidia-current | grep "version:"
version:        304.32
cavsfan@cavsfan-MS-7529:~$ sudo grep -i "NVIDIA GLX Module" /var/log/Xorg.*.log -A 10
[sudo] password for cavsfan: 
[    16.742] (II) NVIDIA GLX Module  304.32  Thu Aug  2 19:03:23 PDT 2012
[    16.742] (II) Loading extension GLX
[    16.742] (II) LoadModule: "record"
[    16.742] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.742] (II) Module record: vendor="X.Org Foundation"
[    16.742]     compiled for 1.12.1.902, module version = 1.13.0
[    16.742]     Module class: X.Org Server Extension
[    16.742]     ABI class: X.Org Server Extension, version 6.0
[    16.742] (II) Loading extension RECORD
[    16.742] (II) LoadModule: "dri"
[    16.742] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
```

Thanks for the help!

---

### Post by VinDSL on 2012-08-09
> **Cavsfan said:**
> Thanks for the help!
You're welcome...

Good job, man!  ;)

---

### Post by Harry33 on 2012-08-10
> **Cavsfan said:**
> Thanks for that VinDSL! It definitely helped.  I wasn't comfortable hacking XML before but, I am now! :wink:
Don't know if any one noticed but, when you entered **gksu nautilus** in terminal all of these same font errors appeared.
It took a few times editing and rebooting until I got it all fixed. But, all I had to do is enter **gksu nautilus**  to find out if I had fixed it.
...


Command "gksu nautilus" is not anymore supported and should be used.
If you need to use nautilus as root, you can do this instead (in terminal):
```
sudo -s
```
and then
```
nautilus

```

---

### Post by Cavsfan on 2012-08-10
> **Harry33 said:**
> Command "gksu nautilus" is not anymore supported and should be used.
If you need to use nautilus as root, you can do this instead (in terminal):
```
sudo -s
```and then
```
nautilus

```

Thank you for that info. I'll try to remember that. It did give other errors besides the font ones even after I fixed the fonts.
BTW, what happened to adding the option "open as administrator" on nautilus?
I know Lucid has it, can't remember if Precise has it or not but, I believe it does.

Also the error messages I get when updates are being installed is not about fonts, it is about shotwell something or 
other and the last word on the many errors is deprecated.
Any one else getting that?

---

### Post by Cavsfan on 2012-08-10
> **VinDSL said:**
> Good job, man!  ;)

Thanks! Man, that means a lot coming from The VinDSL! :)
I have a nice conky on the right side that used to go all the way down with the weather but, when the weather channel dumped on us I didn't try to replace it.

I also have the Crunchbang Statler one on the left side.
I struggle a bit so, I figure I'll just leave it that way. I have the weather applet in Cairo Dock any way.
Thanks!

---

### Post by Cavsfan on 2012-08-10
Here are the errors I am talking about when updates are being installed.
I guess it is more than just shotwell:

```
Unpacking replacement nautilus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for menu ...
Processing triggers for shared-mime-info ...
Processing triggers for libglib2.0-0:amd64 ...
warning: Schema 'com.canonical.notify-osd' has path '/apps/notify-osd/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.ApplicationsLens' has path '/desktop/unity/lenses/applications/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Runner' has path '/desktop/unity/runner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.FilesLens' has path '/desktop/unity/lenses/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.indicator.session' has path '/apps/indicator-session/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu.update-manager' has path '/apps/update-manager/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard' has path '/apps/onboard/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.auto-show' has path '/apps/onboard/auto-show/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.keyboard' has path '/apps/onboard/keyboard/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window' has path '/apps/onboard/window/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.landscape' has path '/apps/onboard/window/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.portrait' has path '/apps/onboard/window/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette' has path '/apps/onboard/icon-palette/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.landscape' has path '/apps/onboard/icon-palette/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.portrait' has path '/apps/onboard/icon-palette/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.universal-access' has path '/apps/onboard/universal-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.theme-settings' has path '/apps/onboard/theme-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.lockdown' has path '/apps/onboard/lockdown/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.scanner' has path '/apps/onboard/scanner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.Geoclue' has path '/apps/geoclue/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.Telepathy.Logger' has path '/apps/telepathy-logger/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.gstreamer-0.10.default-elements' has path '/desktop/gstreamer/0.10/default-elements/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.Vino' has path '/desktop/gnome/remote-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.cache' has path '/desktop/gnome/crypto/cache/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.pgp' has path '/desktop/gnome/crypto/pgp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse' has path '/apps/seahorse/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse.manager' has path '/apps/seahorse/listing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.locale' has path '/system/locale/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy' has path '/system/proxy/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.http' has path '/system/proxy/http/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.https' has path '/system/proxy/https/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.ftp' has path '/system/proxy/ftp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.socks' has path '/system/proxy/socks/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-piwigo' has path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-piwigo/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-yandex-fotki' has path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-yandex-fotki/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell' has path '/apps/shotwell/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences' has path '/apps/shotwell/preferences/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.ui' has path '/apps/shotwell/preferences/ui/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.slideshow' has path '/apps/shotwell/preferences/slideshow/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.window' has path '/apps/shotwell/preferences/window/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.files' has path '/apps/shotwell/preferences/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.crop-settings' has path '/apps/shotwell/crop-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.editing' has path '/apps/shotwell/preferences/editing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing' has path '/apps/shotwell/sharing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.facebook' has path '/apps/shotwell/sharing/facebook/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.flickr' has path '/apps/shotwell/sharing/flickr/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.picasa' has path '/apps/shotwell/sharing/picasa/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.youtube' has path '/apps/shotwell/sharing/youtube/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.dataimports' has path '/apps/shotwell/dataimports/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.video' has path '/apps/shotwell/video/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.printing' has path '/apps/shotwell/printing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.plugins' has path '/apps/shotwell/plugins/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.plugins.enable-state' has path '/apps/shotwell/plugins/enable-state/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
Processing triggers for gconf2 ...
Setting up libc-dev-bin (2.15-0ubuntu17) ...
Setting up libc6-dev:amd64 (2.15-0ubuntu17) ...
Setting up libgstreamer1.0-0:amd64 (0.11.93-2) ...
Setting up libgnome-control-center1 (1:3.4.2-0ubuntu8) ...
Setting up gnome-control-center-data (1:3.4.2-0ubuntu8) ...
Setting up gnome-control-center (1:3.4.2-0ubuntu8) ...
Setting up libnautilus-extension1a (1:3.5.5-0ubuntu3) ...
Setting up nautilus-data (1:3.5.5-0ubuntu3) ...
Setting up nautilus (1:3.5.5-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
cavsfan@cavsfan-MS-7529:~$ 

```I am fairly certain I get this every time something is updated.
Is any one else getting this or is it just me?

---

### Post by zenarcher on 2012-08-10
All I can share is what I experience with Kubuntu 12.10, running the latest daily build.  Everything is fine, unless I install the Nvidia driver.  Once I install the Nvidia driver and reboot the system.....the system comes back up until I get a few moments of the desktop, then, shuts down and takes me back to the log on screen, although I have it set up for auto log on.  I can sign in and the same thing happens again...few moments of the desktop, then black screen and back to the log on screen.

---

### Post by Cavsfan on 2012-08-10
> **zenarcher said:**
> All I can share is what I experience with Kubuntu 12.10, running the latest daily build.  Everything is fine, unless I install the Nvidia driver.  Once I install the Nvidia driver and reboot the system.....the system comes back up until I get a few moments of the desktop, then, shuts down and takes me back to the log on screen, although I have it set up for auto log on.  I can sign in and the same thing happens again...few moments of the desktop, then black screen and back to the log on screen.

Don't mean to be disrespectful or anything but, this thread is for Quantal Quetzal, the development system.

---

### Post by flipper T on 2012-08-10
Kubuntu 12.10 is still QQ.

---

### Post by mc4man on 2012-08-10
> **Cavsfan said:**
> Don't mean to be disrespectful or anything but, this thread is for Quantal Quetzal, the development system.
Love Miami, Oklahoma :)

> Kubuntu [COLOR="Red"]12.10[/COLOR]
The orig topic of this thread concerns the fact that currently nvidia drivers will not work in a 3d session with  xserver 1.13 which is in the proposed repo
They work fine with the current 1.12 version in main.

Those that have upgraded to the 1.13 & affected  can either - 
Wait it out & use a 2d session & no FF or TB till fixed
Remove the nvidia drivers & use nouveau
Downgrade their appropriate xserver packages & keep nvidia

---

### Post by Cavsfan on 2012-08-10
> **flipper T said:**
> Kubuntu 12.10 is still QQ.

I'm a dork! :???: I thought I seen something besides 12.10! D'oh! My bad!

---

### Post by zenarcher on 2012-08-10
> **Cavsfan said:**
> Don't mean to be disrespectful or anything but, this thread is for Quantal Quetzal, the development system.
Love Miami, Oklahoma :)

I don't mean to be disrespectful either, but I thought 12.10 was Quantal Quetzal.

---

### Post by Cavsfan on 2012-08-10
> **zenarcher said:**
> I don't mean to be disrespectful either, but I thought 12.10 was Wuantal Quetzal.
  

I *could* get disrespectful. I thought it was Pretzal Qretzal my own self.

---

### Post by Harry33 on 2012-08-11
> **Cavsfan said:**
> Here are the errors I am talking about when updates are being installed.
I guess it is more than just shotwell:

```

...
warning: Schema 'com.canonical.notify-osd' has path '/apps/notify-osd/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.ApplicationsLens' has path '/desktop/unity/lenses/applications/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Runner' has path '/desktop/unity/runner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.FilesLens' has path '/desktop/unity/lenses/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.indicator.session' has path '/apps/indicator-session/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
...

```I am fairly certain I get this every time something is updated.
Is any one else getting this or is it just me?

Those are only warnings, not errors. They just remind that some applications still use the old and deprecated paths in their configurations (dconf). They are to be corrected later.

---

### Post by Cavsfan on 2012-08-11
> **Harry33 said:**
> Those are only warnings, not errors. They just remind that some applications still use the old and deprecated paths in their configurations (dconf). They are to be corrected later.

Thanks very much for that explanation! Good to know.

---

