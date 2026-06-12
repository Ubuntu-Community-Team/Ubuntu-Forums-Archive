---
title: "Ubuntu 13.04 guest on VirtualBox not showing unity menus"
date: 2013-05-21
forum: Virtualisation
---

### Post by WhyCali on 2013-05-21
I've installed Ubuntu 13.04 as a guest os in VirtualBox (v4.2.12).  When I enable 3d Acceleration, I lose my Unity top toolbar and side bar.  

I've already installed the guest additions, added vboxvideo to /etc/modules

[SIZE=4][B]lshw -c display:
[/B][/SIZE]
*-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0
       resources: memory:e0000000-e7ffffff



**[SIZE=4]unity_support_test -p:[/SIZE]**

root@VirtualBox:~$ /usr/lib/nux/unity_support_test -p
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

Thanks for your help!

Mike

---

### Post by gordintoronto on 2013-05-21
How did you enable 3D acceleration?

---

### Post by markbl on 2013-05-22
> **gordintoronto said:**
> How did you enable 3D acceleration?
He clicked the option in the settings, (of course?)

OP, you don't say what your host is?

I have found 3D acceleration in VB (current 4.2.12 version and all recent versions) to be very flaky for Ubuntu 12.04 and later guests, most particularly on Mac hosts. My ubuntu 13.10 host seems to run ubuntu guests ok, but my mac (osx 10.8.3) still gets frequent aborts and graphics issues with ubuntu guests.

---

### Post by WhyCali on 2013-05-23
I'm running on a Windows 7 (Home Premium) x64 Host.

---

