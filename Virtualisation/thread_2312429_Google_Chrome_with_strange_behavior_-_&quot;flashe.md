---
title: "Google Chrome with strange behavior - &quot;flashes&quot; upon opening program"
date: 2016-02-04
forum: Virtualisation
---

### Post by cycopy on 2016-02-04
Hi,

I run Xubuntu inside Virtualbox. Whenever I start up google-chrome (either from terminal or from xfce panel) the browser flashes (opens and closes) for 4-5 times before chilling down. Before, it would produce an error as well when this happened. I can't remember the error any longer, since I selected not to show that error in the future in a dialog box that would appear at every startup of chrome. Below is the stuff it spits out when I run it from a terminal. Does anyone know how I can make this flashing go away?

Software versions:
Google Chrome: 48.0.2564.103 (64-bit)
Xubuntu: Ubuntu 14.04.3 LTS (Kernel: 3.13.0-46-generic)
Xfce: 4.10
Virtualbox: 5.0.13 r104845

```

erlend@xubuntux:~$ google-chrome
libGL error: pci id for fd 14: 80ee:beef, driver (null)
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
[2549:2549:0204/134813:ERROR:logging.h(808)] Failed to call method: org.freedesktop.DBus.ObjectManager.GetManagedObjects: object_path= /: org.freedesktop.DBus.Error.UnknownMethod: Method "GetManagedObjects" with signature "" on interface "org.freedesktop.DBus.ObjectManager" doesn't exist

[2605:2605:0204/134813:ERROR:sandbox_linux.cc(338)] InitializeSandbox() called with multiple threads in process gpu-process
[2549:2549:0204/134813:ERROR:logging.h(808)] Failed to call method: org.freedesktop.DBus.ObjectManager.GetManagedObjects: object_path= /: org.freedesktop.DBus.Error.UnknownMethod: Method "GetManagedObjects" with signature "" on interface "org.freedesktop.DBus.ObjectManager" doesn't exist

[2605:2605:0204/134813:ERROR:texture_manager.cc(2202)] [.Compositor-0x3935f5c1d000]GL ERROR :GL_INVALID_ENUM : glTexImage2D: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_ENUM : GLES2DecoderImpl::DoBindTexImage2DCHROMIUM: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134813:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2605:2605:0204/134814:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5c1d840]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
libGL error: pci id for fd 14: 80ee:beef, driver (null)
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
[2672:2672:0204/134814:ERROR:sandbox_linux.cc(338)] InitializeSandbox() called with multiple threads in process gpu-process
[2672:2672:0204/134815:ERROR:texture_manager.cc(2202)] [.Compositor-0x3935f62ed000]GL ERROR :GL_INVALID_ENUM : glTexImage2D: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_ENUM : GLES2DecoderImpl::DoBindTexImage2DCHROMIUM: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2672:2672:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e160]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
libGL error: pci id for fd 14: 80ee:beef, driver (null)
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
[2689:2689:0204/134815:ERROR:sandbox_linux.cc(338)] InitializeSandbox() called with multiple threads in process gpu-process
[2689:2689:0204/134815:ERROR:texture_manager.cc(2202)] [.Compositor-0x3935f5e5e420]GL ERROR :GL_INVALID_ENUM : glTexImage2D: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_ENUM : GLES2DecoderImpl::DoBindTexImage2DCHROMIUM: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2689:2689:0204/134815:ERROR:gles2_cmd_decoder.cc(2308)] [.CompositorWorker-0x3935f5e5e000]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command


```

Edit: corrected Xubuntu version

---

### Post by howefield on 2016-02-04
Thread moved to the "*Virtualisation*" forum given most of the errors seem to relate to vboxvideo.

---

### Post by MAFoElffen on 2016-02-04
This ***is*** a bug in vBoxVideo in vBoxGuestAddititions as noted in this Bug: [https://www.virtualbox.org/ticket/12746](https://www.virtualbox.org/ticket/12746)

It affected VirtualBox version 4.3.12 through current 5.1. As of 3 months ago, they are still working on it, and still having problems with some machines. 

Please go over to that bug and subscribe, so that they might be able to use your information to try to work out a fix on that.

---

### Post by cycopy on 2016-02-04
Hi,

Alright, will do. Thank you for your response.

---

