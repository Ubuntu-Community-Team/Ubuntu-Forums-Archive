---
title: "3D Acceleration with VirtualBox 4.2.x in Ubuntu 12.04 x64"
date: 2013-05-04
forum: Virtualisation
---

### Post by Lamukra on 2013-05-04
Hallo Guys!

I am trying to make 3D acceleration work on my machine with Ubuntu 12.04.2 guest. ALready a week sitting and cannot find anything useful

Host: Windows 8 x64
Guest Ubuntu 12.04.2 x64

I started with virtualbox 4.2.12 and had no luck, after guest additions are installed, I am getting to black screen after login 
Then I found that maybe problem was in virtualbox version, so I switched to 4.2.10 and again no luck - black screnn after guest additions were installed

I used this Ubuntu with VB 4.2.12:

Ubuntu 12.04.2
linux-header-generic-lts-quantal
linux-headers-3.5.0-23-generic (and all dependant packages)
xserver-xorg-lts-quantal (and all dependencies)

after installing Guest Additions after login I get black screen and VMachine hangs and have to end task

Then I upgraded to headers-3.5.0-28
and the same story

With VB 4.2.10

Exactly the same story as previous with out-of-the box installed headers

then I decided to use other header not linux-headers-generic-lts-quantal, I installed linux-virtual(and all dependencies) and purges lts-quantal ones

now after installation I have installed guest additions and they seem to work, but no 3D still

I am just getting frustrated about this thing, why if there is this problem, NOTHING is there on the web...
not in my Xorg.0.log I get this

```

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.[    15.229] Initializing built-in extension MIT-SCREEN-SAVER
[    15.348] (EE) open /dev/dri/card0: No such file or directory
[    15.630] (EE) [drm] drmOpen failed.
[    15.630] (EE) VBoxVideo(0): DRIScreenInit failed, disabling DRI.
[    15.675] (II) XINPUT: Adding extended input device "VirtualBox mouse integration" (type: TOUCHSCREEN, id 8)

```

glxinfo | grep render - shows that direct rendering is enabled

```

direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend 
```

but unity test 

/usr/lib/nux/unity_support_test -p

show this

```

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string:  2.1 Mesa 9.0.3


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```


So WTF is going on with this VirtualBox??
NEED YOUR HELP!!!

---

