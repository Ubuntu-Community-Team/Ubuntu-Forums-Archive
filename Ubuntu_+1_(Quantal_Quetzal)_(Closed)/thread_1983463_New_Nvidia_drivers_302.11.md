---
title: "New Nvidia drivers 302.11"
date: 2012-05-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-05-20
The newest version (beta) of Nvidia proprietary drivers are available from Xorg-Edgers.
Note, that this is built against xserver 1.12, also available from that PPA.

---

### Post by paul_in_london on 2012-05-20
> **Harry33 said:**
> The newest version (beta) of Nvidia proprietary drivers are available from Xorg-Edgers.
Note, that this is built against xserver 1.12, also available from that PPA.

Hi Harry. Didn't build for me with the 3.4.0-2-generic kernel (64 bit). Was going to downgrade nvidia-current via synaptic, but synaptic wanted to remove it.

Didn't really want to purge xorg-edgers so back in precise for now.

302.11 did build ok for me with this kernel on my precise install:

```
paul@precise:~$ uname -a
Linux precise 3.4.0-030400rc5-generic-pae #201205011817 SMP Tue May 1 22:31:34 UTC 2012 i686 i686 i386 GNU/Linux
paul@precise:~$
```

---

### Post by ronacc on 2012-05-20
302.11 updated and built ok for me with 3.4.0-2 on my amd64 quantal sys with the xorg-edgers PPA .

---

### Post by Harry33 on 2012-05-20
> **ronacc said:**
> 302.11 updated and built ok for me with 3.4.0-2 on my amd64 quantal sys with the xorg-edgers ppa .

+ 1

---

### Post by Harry33 on 2012-05-20
> **paul_in_london said:**
> Hi Harry. Didn't build for me with the 3.4.0-2-generic kernel (64 bit). Was going to downgrade nvidia-current via synaptic, but synaptic wanted to remove it.

Didn't really want to purge xorg-edgers so back in precise for now.

302.11 did build ok for me with this kernel on my precise install:

```
paul@precise:~$ uname -a
Linux precise 3.4.0-030400rc5-generic-pae #201205011817 SMP Tue May 1 22:31:34 UTC 2012 i686 i686 i386 GNU/Linux
paul@precise:~$
```

Hi there,

Yes, you cannot downgrade with Synaptic, the older (built on 5th May 2012) xserver 1.12.1 git version is no longer available from xorg-edgers PPA.
Or did you use some other xserver-xorg-core with video abi 12?

---

### Post by paul_in_london on 2012-05-20
> **ronacc said:**
> 302.11 updated and built ok for me with 3.4.0-2 on my amd64 quantal sys with the xorg-edgers ppa.

Hmmm. Not sure what happened in my case then. Will have to look in more detail when I next boot QQ.

> **Harry33 said:**
> Hi there,

Yes, you cannot downgrade with Synaptic, the older (built on 5th May 2012) xserver 1.12.1 git version is no longer available from xorg-edgers PPA.
Or did you use some other xserver-xorg-core with video abi 12?

Thanks Harry. Just the xorg-edgers ppa packages. Still using precise right now.

Will check later which version of xserver-xorg-core I have in quantal.

---

### Post by markbl on 2012-05-20
The [changelog for 302.11](http://www.geeks3d.com/forums/index.php/topic,2637.0.html) looks pretty boring though. Certainly no indication that the xorg segmentation fault occurring (for me and others) in 295.40, 295.49, and 302.07 is fixed. I have not tried 295.53 as I doubt the crash is fixed there, and nouveau is working well for me in 3D etc.

---

### Post by VinDSL on 2012-05-20
Working great!

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~
Current Date/Time: Sun May 20 17:00:11 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.4.0-2-generic-pae
Unity Release: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.11

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
  Installed: 2:1.12.1.902+git20120520+server-1.12-branch.4a2b8eeb-0ubuntu0ricotz

vindsl@Zuul:~$
```

Thanks, Harry!

---

### Post by paul_in_london on 2012-05-21
All good now after latest updates:

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 302.11-0ubuntu1~xedgers~quantal2
  Candidate: 302.11-0ubuntu1~xedgers~quantal2
  Version table:
 *** 302.11-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 
Packages
        100 /var/lib/dpkg/status
     295.49-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
```

```
paul@quantal-64:~$ apt-cache policy  xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.12.1.902+git20120520+server-1.12-branch.4a2b8eeb-0ubuntu0ricotz
  Candidate: 2:1.12.1.902+git20120520+server-1.12-branch.4a2b8eeb-0ubuntu0ricotz
  Version table:
 *** 2:1.12.1.902+git20120520+server-1.12-branch.4a2b8eeb-0ubuntu0ricotz 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.11.4-0ubuntu11 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
```

```
paul@quantal-64:~$ uname -a
Linux quantal-64 3.4.0-2-generic #6-Ubuntu SMP Wed May 16 21:01:43 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@quantal-64:~$
```

---

