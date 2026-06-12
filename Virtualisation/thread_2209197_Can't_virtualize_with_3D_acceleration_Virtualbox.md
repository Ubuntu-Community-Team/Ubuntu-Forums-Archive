---
title: "Can't virtualize with 3D acceleration Virtualbox"
date: 2014-03-04
forum: Virtualisation
---

### Post by joan_carles2 on 2014-03-04
I install the guest addition on the latest version of virtualbox and Ubuntu 14.04. Process works.

Then I enable 3D acceleration in the setings and I give 128Mb. When I run ubuntu  is very slow.I think it's because some errors. The errors are next:

joan@joan-VirtualBox:~$ glxinfo | grep Opengl
libGL error: pci id for fd 4: 80ee:beef, driver (null)
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
joan@joan-VirtualBox:~$ 

joan@joan-VirtualBox:~$ /usr/lib/nux/unity_support_test -p
libGL error: pci id for fd 4: 80ee:beef, driver (null)
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
OpenGL vendor string:   Humper
OpenGL renderer string: Chromium
OpenGL version string:  2.1 Chromium 1.9

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
joan@joan-VirtualBox:~$

---

### Post by eteq on 2014-04-12
I'm seeing the exact same thing from a Windows 8 host.

---

### Post by wn1ytw on 2014-04-12
3D works fine in a iMac host, I  only gave the video 20MB. FWIW

---

### Post by Thomas_Barth on 2014-04-18
Same error messages here with Win7 64 / VirtualBox 4.3.10 host and Ubuntu 14 guest. Is there still no fix? 

tbarth@ubuntu-14:~$ /usr/lib/nux/unity_support_test -p
libGL error: pci id for fd 4: 80ee:beef, driver (null)
OpenGL Warning: [...] not found in mesa table
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
OpenGL vendor string:   Humper
OpenGL renderer string: Chromium
OpenGL version string:  2.1 Chromium 1.9

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


root@ubuntu-14:~# lsmod | grep vbox
vboxsf                 42558  0 
vboxvideo              12578  0 
drm                   243792  1 vboxvideo
vboxguest             219348  8 vboxsf

But vboxvideo dri are located in 
/usr/lib/i386-linux-gnu/dri/vboxvideo_dri.so
/usr/lib/xorg/modules/drivers/vboxvideo_drv.so

Is there a symbolic link missing? I also had to set a link to get vboxsf work in virtualbox 4.3.10 (ln -s /opt/VBoxGuestAdditions-4.3.10/lib/VBoxGuestAdditions /usr/lib/VBoxGuestAdditions)

In Ubuntu 12 everything is ok with the same guest settings.

---

### Post by QwUo173Hy on 2014-04-18
Same issue with a Win 7 host.

---

### Post by bren3 on 2014-04-19
i have the same errors as post no. 1 

imac host
virtualbox 14.04 guest

---

### Post by eteq on 2014-04-20
Note that this might actually be a virtualbox problem, rather than Ubuntu's fault - I created an issue there at [https://www.virtualbox.org/ticket/12941](https://www.virtualbox.org/ticket/12941)

---

### Post by leroy5 on 2014-07-26
I still have the same problem mentionned by OP

Host: Ubuntu 14.04LTS 64 bits
CPU: i7 quad core 2.6Ghz
Graphic adapter: GeForce GT 650M

Guest: Ubuntu 14.04LTS 64 bits

Virtualbox version:  4.3.14 from the official Oracle repo

Result from sudo /usr/lib/nux/unity_support_test -p

libGL error: pci id for fd 4: 80ee:beef, driver (null)
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
OpenGL vendor string:   Humper
OpenGL renderer string: Chromium
OpenGL version string:  2.1 Chromium 1.9

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

The issue is marked as fixed as of may 27 2014 on the official virtualbox ticket related to the issue. However, in my case and many others peoples, there are still graphical issues running Ubuntu Unity 3D with the guest addition.

 I still have a lot of graphical artifacts and the video rendering has issues.

I have already tried many things suggested online with no success. The only workaround I found to get a more decent graphical video experience was:

1-installed the gnome-flashback-session

2- Select to logon in the guest without 3D Compiz (with Metacity)

Anyway, the problem seems to be a conflict with Mesa and the OpenGL driver....

Is there someone here who has found a real fix for this issue?

---

### Post by TheFu on 2014-07-28
Not a fix, but a set of work-arounds to get a useful, fast system again: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)
Basically - don't use a desktop that requires 3D accel hardware until the code it fixed.

---

### Post by miles8 on 2014-08-18
It looks like I got my open gl working using the latest guest additions VBoxGuestAdditions_4.3.14.iso, enabling 3d support in VB,  and installing nvidia-settings 331.20 from the ubuntu software center. It seems to have added some missing X windows libraries.

---

### Post by steve7777777 on 2014-08-19
I have the same problem with **VMware Player**.

[COLOR=#000000]Host: Ubuntu 10.04LTS 64 bits[/COLOR]
[COLOR=#000000]CPU: AMD Phenom II X4 955 3.2Ghz[/COLOR]
[COLOR=#000000]Graphic adapter: on board GPU[/COLOR]

[COLOR=#000000]Guest: Ubuntu 12.04LTS 64 bits[/COLOR]

[COLOR=#000000]VM Player version: 6 - the latest. The tools installed properly on the guest OS.[/COLOR]

---

