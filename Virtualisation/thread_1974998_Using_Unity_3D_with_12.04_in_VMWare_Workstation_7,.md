---
title: "Using Unity 3D with 12.04 in VMWare Workstation 7, possible?"
date: 2012-05-06
forum: Virtualisation
---

### Post by romandas on 2012-05-06
I'm testing out 12.04 64-bit using VMWare Workstation 7.1.5. My host operating system is a 10.04 64-bit system using the nVidia binary driver with a nVidia G92 (nVidia Corporation G92 [GeForce 9600 GSO] (rev a2)) graphics card.

I have 'Accelerate 3D graphics' checked in the VM settings, and the VM doesn't complain about this when it boots. However, when logging into 12.04, it's obvious it is using Unity 2D. I have the open-vm-tools and open-vm-toolbox installed, and that seems to be working, as the screen resizes appropriately and cut/paste is working between host and guest.

I ran unity_support_test and it says "Not software rendered: no". I'm not sure why. Is there any way I can troubleshoot this? The module vmwgfx is loaded in the VM, so I'm not sure why this isn't working.

Output below:

tester@ubuntu:~$ sudo /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

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

---

### Post by ctene on 2012-07-01
I think you forgot to install on the host and on the guest the DRI + Mesa GL Tools. Your output indicates te presence of OpenGL merely the fact that it is not activated. However I would strongly advise to upgrade to the latest VM Workstation 8 as well.

I am making a different experience here: 

I am running a host PC  (OS X 10.7.4 Lion), VMWare Fusion 4.1.3 and seem to be getting perfect 3D support in the guest OS: Ubuntu 12.04 LTS. My output of unity_support_test is:

pete@PETE-LINUX:~$ sudo /usr/lib/nux/unity_support_test -p
[sudo] password for pete: 
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on SVGA3D; build: RELEASE;  
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

---

