---
title: "Beware! Compiz updates will wipe your Unity 3D DE out."
date: 2012-09-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-03
Just found out that the most recent update had removed all my CCSM settings and wiped out Unity 3D.

  I breached the subject in another sig but just wanted to bring it to attention.

---

### Post by fjgaude on 2012-09-03
Thanks, I've had the issue here on my Intel HD3000 box.

Doing this might fix it:

```
sudo apt-get install --reinstall ubuntu-desktop

```

Happy the days of the breakage!

---

### Post by stinkeye on 2012-09-03
> **ventrical said:**
> Just found out that the most recent update had removed all my CCSM settings and wiped out Unity 3D.

  I breached the subject in another sig but just wanted to bring it to attention.
Yes, and **unity --reset** or setting back to default in ccsm doesn't
seem to work anymore.
Had to open ccsm and enable unity, window decorations, resize windows and
various other plugins to get a working desktop back.
Also needed to run **compiz --replace** a couple of times during the process.

Get a garbled screen for a few secs just after login, but then compiz and unity loads fine.

Cube back and running.

---

### Post by ventrical on 2012-09-03
> **stinkeye said:**
> Yes, and **unity --reset** or setting back to default in ccsm doesn't
seem to work anymore.
Had to open ccsm and enable unity, window decorations, resize windows and
various other plugins to get a working desktop back.
Also needed to run **compiz --replace** a couple of times during the process.

Get a garbled screen for a few secs just after login, but then compiz and unity loads fine.

Cube back and running.


This has happened across the board , even with my Intel based graphics boxes. With Intel based graphics it will disabled cube and cube rotate, but Unity will not work at first.

Thanks for your report.

---

### Post by ventrical on 2012-09-03
> **fjgaude said:**
> Thanks, I've had the issue here on my Intel HD3000 box.

Doing this might fix it:

```
sudo apt-get install --reinstall ubuntu-desktop

```Happy the days of the breakage!


Thanks fjgaude. I'll try that.

---

### Post by VinDSL on 2012-09-03
> **ventrical said:**
> I breached the subject in another sig but just wanted to bring it to attention.
Yummy!  Breakage!!!  :D

I'm bored.

Okay, here goes 'nuttin...

---

### Post by VinDSL on 2012-09-03
Well, DRAT!

Working perfectly fine, here...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-sep-2012-2.png")[/INDENT]


```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~
Current Date/Time: Mon Sep  3 12:29:43 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc4-generic
Unity Release: unity 6.4.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.43

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
  Installed: 2:1.12.99.905+git20120830.148583d6-0ubuntu0ricotz

vindsl@Zuul:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.8.0-0ubuntu1
  Candidate: 1:0.9.8.0-0ubuntu1
  Version table:
 *** 1:0.9.8.0-0ubuntu1 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```

I did a full upgrade.  What am I doing wrong?!?!?

Did I get the wrong Compiz?  :(

---

### Post by cecilpierce on 2012-09-03
Works ok here.

---

### Post by VinDSL on 2012-09-03
Oh, okay!

Just read this in the dupe thread...

> **mc4man said:**
> Didn't see any issue when upgrading compiz/unity here the other day from proposed
 - other then a few custom compiz settings where lost as was the run history. (gsettings & ccsm don't always seem to communicate well..

Do get a kick out of your bug report which now has been duped to a 2 week old bug marked 'incomplete' & **[COLOR="DarkRed"]was on an intel display adapter[/COLOR]**

Guess it's an Intel issue.  ;)

---

### Post by cecilpierce on 2012-09-03
Oops, sorry wrong QQ, using nouveau here

---

### Post by VinDSL on 2012-09-03
There's gotta be a way to break this thing!  :guitar:

Hrm...

---

### Post by ventrical on 2012-09-03
> **VinDSL said:**
> Well, DRAT!

Working perfectly fine, here...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-sep-2012-2.png")[/INDENT]
```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~
Current Date/Time: Mon Sep  3 12:29:43 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc4-generic
Unity Release: unity 6.4.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.43

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
  Installed: 2:1.12.99.905+git20120830.148583d6-0ubuntu0ricotz

vindsl@Zuul:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.8.0-0ubuntu1
  Candidate: 1:0.9.8.0-0ubuntu1
  Version table:
 *** 1:0.9.8.0-0ubuntu1 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```I did a full upgrade.  What am I doing wrong?!?!?

Did I get the wrong Compiz?  :(

Gee .. .another one of your killer wallpapers eh ? :) lol

Nice work Vin.

 Not sure what happened.  I went into compiz settings and reset everything and it's all working again.

---

### Post by mc4man on 2012-09-03
> **ventrical said:**
> 

 Not sure what happened.  I went into compiz settings and reset everything and it's all working again.
If compiz crashes or you cause it to crash then it's **possible **any custom changes you made will be lost
Updates to either compiz/unity (few & far between), may also unset some settings

---

### Post by VinDSL on 2012-09-03
> **ventrical said:**
> Gee .. .another one of your killer wallpapers eh ? :) lol

Nice work Vin.[...]
Thanks!

I've been working on a new Conky weather script, for several days. 

Google turned off their Weather API service last week, without notice.

I needed something pretty to look at, hence the "Fantasy Fairy".  LoL!

Here's a clean screen...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-sep-2012-1.png")[/INDENT]

---

### Post by ventrical on 2012-09-03
Avril Leviegns's little sister :) <sp>

---

### Post by ventrical on 2012-09-03
> **mc4man said:**
> If compiz crashes or you cause it to crash then it's **possible **any custom changes you made will be lost
Updates to either compiz/unity (few & far between), may also unset some settings

 You are absolutely correct.   I should know better especially with what happened during Oneiric and Precise testing, however, I never thought this type of redundancy with compiz updates and subsequent behaviour was so inherent with every cycle. So it caught me off guard.

---

### Post by VinDSL on 2012-09-03
> **ventrical said:**
> Avril Leviegns's little sister :) <sp>
Bwahahahaha!

That's a bouquet in her hands... not brass knuckles! :D

---

### Post by Hobble on 2012-09-03
> **VinDSL said:**
> Thanks!

I've been working on a new Conky weather script, for several days. 

Google turned off their Weather API service last week, without notice.

I needed something pretty to look at, hence the "Fantasy Fairy".  LoL!

Here's a clean screen...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-sep-2012-1.png")[/INDENT]

What type of icons are those?

---

### Post by VinDSL on 2012-09-03
> **Hobble said:**
> What type of icons are those?
I made those with "Any Color You Like 0.9.4" (aka ACYL) ;)

---

