---
title: "which video driver am I using ?"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-28
Off of an apparently successful fresh install I get two different reports. Synaptic tells me that nouveau-firmware is not installed where as 'additonal drivers' tells me that Nouveau driver is installed.

Details tells me that I have VESA.

I am experiemnting with mir and I want to have the right nouveau driver. The current driver is very slow.

---

### Post by cariboo on 2013-03-28
If you have Unity installed, try:

```
/usr/lib/nux/unity_support_test -p -f
```

in a terminal. The results should look something like this:

```
cariboo@alexis:~$  /usr/lib/nux/unity_support_test -p -f 
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string:  **3.3.0 NVIDIA 304.84**

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

I've bolded the driver I'm running.

---

### Post by ventrical on 2013-03-28
Hmmm.. thanks .. Iv'e got the llvmpipe .. not sure why but that was the default install. 

 Or have they obsoleted the GeForce 210/218?

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

```

```

ventrical@ventrical-AcerAMD64bitDual:~$ /usr/lib/nux/unity_support_test -p -f 
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
ventrical@ventrical-AcerAMD64bitDual:~$ 

```

so if I install nouveau-firmware or nvidia  how do I uninstall the current driver. We didn't have these problems that I can remember .. only with this distro . (or maybe I didn't see it before).

---

### Post by ventrical on 2013-03-29
I installed Nvidia driver.

Solved.

---

### Post by ventrical on 2013-03-29
This problem was due to using <nomodeset> and this has happened on a lot of installs. Throughout this cycle, <nomodeset> had been the only way to do a successful install. Since I have a little time ATM I am going to try an install after yesterdays zsync and see if the .iso will install the correct driver without using <nomodeset>  If I can't do .iso testing on Tuesday then this will be my small contribution.

---

### Post by ventrical on 2013-03-29
Using <nomodeset> seems to force llvmpipe on a Unity3D capable machine. I did an install from yesterdays daily zsync and it chose the correct nouveau driver and is working like a charm.  

```

ventrical@ventrical-desktop-intelDual:~$ /usr/lib/nux/unity_support_test -p -f
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA8
OpenGL version string:  3.0 Mesa 9.0.3

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
ventrical@ventrical-desktop-intelDual:~$ 




```

 So one good thing is that the daily .iso -i386 are installing correctly for the most part, without <nomodeset>.

---

### Post by ventrical on 2013-03-29
> **cariboo907 said:**
> If you have Unity installed, try:

```
/usr/lib/nux/unity_support_test -p -f
```

in a terminal. The results should look something like this:

```
cariboo@alexis:~$  /usr/lib/nux/unity_support_test -p -f 
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string:  **3.3.0 NVIDIA 304.84**

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

I've bolded the driver I'm running.

 Sory to be off topic but I have  one machien with exact same  report excpet I have one feature that says 3DNOW!  Any idea what that is ?
 I'll look it up.

```

ventrical@ventrical-AcerAMD64bitDual:~$ /usr/lib/nux/unity_support_test -p -f
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce G210/PCIe/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 304.84

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
ventrical@ventrical-AcerAMD64bitDual:~$ 



```

---

### Post by grahammechanical on 2013-03-29
[http://www.nvidia.com/object/IO_20020109_5677.html](http://www.nvidia.com/object/IO_20020109_5677.html)

---

### Post by ventrical on 2013-03-29
Thanks Graham.

---

