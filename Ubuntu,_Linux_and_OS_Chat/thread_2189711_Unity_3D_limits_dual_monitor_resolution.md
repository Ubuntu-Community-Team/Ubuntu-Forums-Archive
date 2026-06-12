---
title: "Unity 3D limits dual monitor resolution"
date: 2013-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by madnordski on 2013-11-23
After upgrading from 12.10 to 13.10 the resolution across dual monitors must be reduced if it is greater than 2400ish.
After installing the gnome-flashback, the desired resolution was obtained on 13.10.

Perhaps we all know about this or perhaps this is the wrong place for this post?  I wasn't able to find anything about it.

It turned out my good monitor was stuck in a fairly low-res mode due to this Unity 3d restriction.  One monitor is the laptop screen and is shaped differently.  This was not a problem for unity 2d on 12.10.  After installing unity 2d on 13.10 nothing changed as far as I could tell but perhaps I goofed.

The resolutions currently in use are 1280 x 800 and 1280 x 1024.  It seems unity 3d was apparently unhappy with 2560 across the two screens.

---

### Post by cariboo on 2013-11-23
Resolution is dependent on your video driver, what  make graphics chipset and and driver are you using?

---

### Post by madnordski on 2013-11-24
~ % lsmod | grep video
video                  19318  1 i915
~ % lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
~ % 

fyi: High res (more than 2400 pix across two monitors) worked under Unity 2d on 12.10 and works using 13.10 (same install) when the genome-flashback window manager is used instead of Unity.  When I log in there are only two choice, flashback and unity even though Unity2d is installed.

The 

log # /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 945GM 
OpenGL version string:  1.4 Mesa 9.2.1

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

% printenv DESKTOP_SESSION
% 

There's probably something I need to do to enable Unity2D which is missing.

---

### Post by ssam on 2013-11-26
Your GPU probably has a max texture size of 2048x2048, so you wont be able to use a composited desktop wider (or taller than that). One possible work around is to arrange the vertically rather than horizontally.

---

