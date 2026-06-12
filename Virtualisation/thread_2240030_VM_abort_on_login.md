---
title: "VM abort on login"
date: 2014-08-17
forum: Virtualisation
---

### Post by satimis on 2014-08-17
Hi all,

AMD core-8
RAM 32G
VRAM 1024M

Host  Ubuntu12.04 desktop 64bit
VM Ubuntu 14.04 desktop 64bit
Oracle VirtualBox

I can't enable 3D Acceleration on VM.  It aborts automatically on login

$ glxinfo | grep OpenGL
```
libGL error: pci id for fd 4: 80ee:beef, driver (null)
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL extensions:
```

I need to enable 3D to run "blender"

I suspect whether it is the problem on the OS of the VM (Ubuntu 14.04).  I have another VM on this box running LinuxMint 17.  3D Acceleration can be enabled without problem, no crash on login.  

$ glxinfo | grep OpenGL```

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
OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 1.20
OpenGL extensions:

```


I have posted this problem on VirtualBox forum but without response.

Help would be appreciated.

Thanks

Regards
satimis

---

### Post by JKyleOKC on 2014-08-18
> **satimis said:**
> Hi all,

AMD core-8
RAM 32G
VRAM 1024M

Host  Ubuntu12.04 desktop 64bit
VM Ubuntu 14.04 desktop 64bit
**Oracle VirtualBox**

I can't enable 3D Acceleration on VM.  It aborts automatically on login

$ glxinfo | grep OpenGL
```
libGL error: pci id for fd 4: 80ee:beef, driver (null)
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
**OpenGL vendor string: VMware, Inc.**
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL extensions:
```

I need to enable 3D to run "blender"I'm confused by the two lines in your message that I've put into boldface above. VMWare and VirtualBox are not necessarily compatible at all when it comes to video drivers...

---

