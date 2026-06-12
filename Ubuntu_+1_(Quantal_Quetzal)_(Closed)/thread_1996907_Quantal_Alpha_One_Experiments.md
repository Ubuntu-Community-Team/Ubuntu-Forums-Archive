---
title: "Quantal Alpha One Experiments"
date: 2012-06-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-06-04
Quantal Alpha One images are now live and being tested. I would encourage those interested to help test (I posted a [writeup]("http://www.theorangenotebook.com/2012/05/adopt-iso-quantal-style.html") with more details, but for old hats like yourselves, you know the drill :-) ).

In addition, more experiments and news on the future images being offered and use of the -proposed repository. I'd like to point these announcements out as they I believe are applicable here.

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-June/000960.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-June/000960.html)
[https://lists.ubuntu.com/archives/ubuntu-qa/2012-June/002160.html](https://lists.ubuntu.com/archives/ubuntu-qa/2012-June/002160.html)

P.S. I trust everyone is ready for another great testing cycle, I'm excited so many folks are talking about the dev release so early in the cycle. It's great.

---

### Post by ventrical on 2012-06-04
I think a lot of us want to get our hands on Wayland and take it for a ride ! as soon as we can :) lol

---

### Post by sammiev on 2012-06-04
Tried to install June 4 every which way today. It will not install. Tried USB, DVD all to HD.

---

### Post by VinDSL on 2012-06-04
> **ventrical said:**
> I think a lot of us want to get our hands on Wayland and take it for a ride [...]
I want breakage. No, no, no!  I n-e-e-d breakage!

I'm so bored, I was thinking about making my own distro:


[INDENT][SIZE="+1"]  [COLOR="DarkOrange"]**Vinbuntu**[/COLOR]  [COLOR="Gray"]"linux for pyschos"[/SIZE][/COLOR][/INDENT]


Heh!  Let the games begin...  LoL!  :D


**EDIT**


This is a good sign!  Started synch @ 357


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-4-jun-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-jun-2012-2.png")[/INDENT]


Sounds familiar!  Where have I heard [that number]("https://duckduckgo.com/?q=357") before?!?!?!?  ;)

---

### Post by ventrical on 2012-06-04
> **VinDSL said:**
> I want breakage. No, no, no!  I n-e-e-d breakage!

I'm so bored, I was thinking about making my own distro:

[INDENT][SIZE=+1]  [COLOR=DarkOrange]**Vinbuntu**[/COLOR]  [COLOR=Gray]"linux for pyschos"[/COLOR][/SIZE][/INDENT]
Heh!  Let the games begin...  LoL!  :D

I hear ya Vin ! :) heheaheaheaheh  Somthing to warm up those processors. lol I mean I need to see smoke once in a  while :)

---

### Post by VinDSL on 2012-06-04
That's what I'm talking about!!!

Okay, I'm in....

Took about 10 minutes to boot (no joke) off a $#@! Walmart USB thumb drive.

The Congo Drums about knocked me off my Captain's Chair - man, that thing was loud!

First thing I noticed, on the desktop, was all sorts of weird drivers are installed, but not active... a Mac driver comes to mind.  Hello!?!?!

Anyway, this feels like a breath of fresh air!  Liberated, at last, from boredom.

Okay, I'm gonna muck around before attempting an install.

Looks like I got some work to do...    LoL!  :D

```
ubuntu@ubuntu:~$ echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL 12.5.22 (vindsl.com) ~
Current Date/Time: Tue Jun  5 00:18:16 UTC 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.4.0-3-generic
Unity Release: unity 5.12.0

nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 8.0.2

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

Package `mesa-utils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Xserver Xorg Core Branch
  Installed: 2:1.11.4-0ubuntu11

ubuntu@ubuntu:~$ 
```

---

### Post by VinDSL on 2012-06-04
That's better...

```
ubuntu@ubuntu:~$ echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL 12.5.22 (vindsl.com) ~
Current Date/Time: Mon Jun  4 19:52:35 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.4.0-3-generic
Unity Release: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.53

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
  Installed: 2:1.11.4-0ubuntu11

ubuntu@ubuntu:~$
```


One thing:  I don't know why they enabled SmoothScroll by default in Firefox, but it makes Fx hideously slow, and unresponsive... especially on Ubuntu Forums.

Maybe they should revisit that decision.  ;)

---

### Post by VinDSL on 2012-06-04
Whoops!  Speaking of Fx...

```

[power]: gnome-settings-daemon crashed with SIGSEGV in gnome_rr_screen_get_dpms_mode()
```

Firefox crashed on startup.

Submitted report in Launchpad.

---

### Post by mc4man on 2012-06-04
> why they enabled SmoothScroll by default in Firefox, but it makes Fx hideously slow, and unresponsive... especially on Ubuntu Forums.
Was surprised to see that today even though I do enable here, it generally works well in FF, nautilus, gedit, ect.. However  does use a fair amount of cpu, (x & compiz), & tends to break down every once in a while for no apparent reason.

---

### Post by kansasnoob on 2012-06-07
> **guitara said:**
> Quantal Alpha One images are now live and being tested. I would encourage those interested to help test (I posted a [writeup]("http://www.theorangenotebook.com/2012/05/adopt-iso-quantal-style.html") with more details, but for old hats like yourselves, you know the drill :-) ).

In addition, more experiments and news on the future images being offered and use of the -proposed repository. I'd like to point these announcements out as they I believe are applicable here.

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-June/000960.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-June/000960.html)
[https://lists.ubuntu.com/archives/ubuntu-qa/2012-June/002160.html](https://lists.ubuntu.com/archives/ubuntu-qa/2012-June/002160.html)

P.S. I trust everyone is ready for another great testing cycle, I'm excited so many folks are talking about the dev release so early in the cycle. It's great.

We need a new recruitment effort for iso/upgrade testing!

I'm running out of gas both physically and mentally ;)

Henrik recruited me this way:

[http://ubuntuforums.org/showthread.php?t=335481&highlight=henrik+ubuntu+iso+testing](http://ubuntuforums.org/showthread.php?t=335481&highlight=henrik+ubuntu+iso+testing)

The way the forums have changed maybe a recruitment effort needs to be stickied in several sub-forums, maybe a good topic to gather feedback from all forum mods :)

---

### Post by kansasnoob on 2012-06-07
BTW why no Xubuntu images?

The best way to kill FUD is with an official statement ;)

---

### Post by balloons on 2012-06-07
> **kansasnoob said:**
> BTW why no Xubuntu images?

The best way to kill FUD is with an official statement ;)

:-) No conspiracy, the xubuntu team (like a couple other flavors) decided to skip alpha one and continue focusing on development. I expect we'll see everyone shipping an alpha 2 image.

---

### Post by quids on 2012-06-08
Well it just puzzled me were CDs were being mounted since the VBoxGuest additions wouldn't auto run.

Turns out it was mounted in /run/media/myusername/VBox... instead of being under /media

Now thats sorted its time to go breaking something :)

---

### Post by jerrylamos on 2012-06-08
> **quids said:**
> Well it just puzzled me were CDs were being mounted since the VBoxGuest additions wouldn't auto run.

Turns out it was mounted in /run/media/myusername/VBox... instead of being under /media

Now thats sorted its time to go breaking something :)

There was some esoteric explanation of when the utterly superfluous /run....../myusername was added, with no explanation of whether we're stuck with this useless data or how to get rd of it or not....

I do have an exec that does umount /dev/sda5 then mkdir /media/whatever and mount /dev/sda5 /media/whatever

Jerry

---

### Post by drs305 on 2012-06-08
Successfully installed Alpha 1 today using the ISO image booted directly from Grub without burning a CD. The first two attempts failed early on but the third time it installed correctly even though I didn't change anything. I couldn't figure out why the first two aborted fairly early in the installation.

---

### Post by pressureman on 2012-06-08
> **jerrylamos said:**
> There was some esoteric explanation of when the utterly superfluous /run....../myusername was added, with no explanation of whether we're stuck with this useless data or how to get rd of it or not....

I do have an exec that does umount /dev/sda5 then mkdir /media/whatever and mount /dev/sda5 /media/whatever

Jerry

There are a few advantages to doing it the new way.

Firstly, /run is tmpfs, whereas /media was (by default) a real directory on the rootfs, meaning that to mount filesystems under /media, the user needed write access to that directory. This also meant that read-only rootfs was out of the question.

Secondly, there existed a possibility for mountpoint collisions. Since the system attempts to mount removable filesystems at a mountpoint that matches the filesystem label (or failing that, volume ID), what if two concurrently logged in users each plugged in a USB stick that had a label like "Photos"?

Thirdly, the filesystem permissions of removable FAT/NTFS are usually set such that only one user can access them (uid/gid set to current user), so it doesn't make much sense to put them somewhere communal like before. If a filesystem really does need to be accessed by multiple users, it's probably more likely that it's permanently attached, and mounted at boot time via /etc/fstab.

How Ubuntu determines under *which user's* name to mount removable media (if multiple users are logged in)... that I'm not sure of.

---

