---
title: "New Nvidia driver release version available 290.10"
date: 2011-11-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-22
NVidia has just released the new driver (290.10).

Those who want it, can download it from X-Updates PPA quite soon,
here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)

The PPA is for Oneiric, but it works well with Precise ATM.
Oh yes, this driver is built for xserver 1.10 series.

> 
 
[LIST]
[*]Added support for the following GPU:
[LIST]GeForce GTX 460 SE v2
[/LIST]
[*]Fixed a bug that would cause OpenGL applications to crash when run with recent releases  of glibc such as glibc 2.14.90.
[*]Improved the performance of FBO bind operations when using Xinerama by ~30% in some cases.
[*]Fixed a bug that could cause stereo corruption when driving a stereo display and a  non-stereo display from the same GPU.
[*]Fixed a bug that could cause display devices on a secondary GPU to get swapped between X  screens when restarting the X server.
[*]Fixed a bug that could result in line flickering in full-scene anti-aliasing contexts.
[*]Fixed a bug that caused the physical dimensions of rotated monitors to be reported incorrectly.
[*]Add support for the pre-VBO DrawArrays command in the server-side  GLX driver module.  The NVIDIA client-side GLX implementation  never  sends   this command, but the  server needs to support it for compatibility  with other GLX client  implementations.
[*]Fixed a regression that caused blank/white windows when exhausting  video memory on GeForce 6  and 7 series GPUs while using composited   desktops.
[*]Fixed a bug that would cause applications which export custom  allocation functions to our  driver (such as Adobe Flash in Firefox or  Chrome) to crash.
[*]Fixed a bug that prevented the driver from loading on some systems with integrated graphics.
[*]Fixed issues in VDPAU that prevented allocating and displaying extremely large  VdpOutputSurfaces.
[*]Added support for limiting heap allocations in the OpenGL driver  through the use of the  __GL_HEAP_ALLOC_LIMIT environment variable.    See the README   for further details.
[*]Added an "Accel" option to the X driver to allow disabling its use  of the graphics processing  hardware.  This is useful when other   components, such as CUDA, require  exclusive use of the GPU's processing  cores.
[*]Modified how the OpenGL driver allocates executable memory so it  may continue to function  properly if /tmp is mounted noexec. As some  fallback allocation methods  may be prohibited under SELinux policy, the  driver now supports detection of  this policy as well as manual  override of this detection via the  __GL_SELINUX_BOOLEANS environment  variable.
[*]Fixed a bug that caused various GLSL built-in uniforms to not be updated properly  when calling glPopAttrib.
[*]Improved performance by caching compiled OpenGL shaders to disk.  Added a "GLShaderDiskCache"  option to the X driver to enable/disable  this   feature. Added the  __GL_SHADER_DISK_CACHE and  __GL_SHADER_DISK_CACHE_PATH environment variables  for further  configuration. See the README for   further details.
[*]Added GLX protocol support (i.e., for GLX indirect rendering)  for the following OpenGL extension:
[LIST]GL_NV_copy_image
[/LIST]
[/LIST]
  


---

### Post by Harry33 on 2011-11-22
And this piece of info here too:

For xserver 1.11 series, the correct nvidia-current is already available from Xorg-edgers PPA.

---

### Post by MG&amp;TL on 2011-11-22
Is this replacing the one that is usually the 196 series?

---

### Post by effenberg0x0 on 2011-11-22
Thanks for the heads up. 
For those that will get it directly from nvidia, or get stuck in console somehow, it always is a good idea to have this link in a txt in your $HOME. The ftp link (for ftp/wget) is:

**x86**
[ftp://download.nvidia.com/XFree86/Linux-x86/290.10/NVIDIA-Linux-x86-290.10.run](ftp://download.nvidia.com/XFree86/Linux-x86/290.10/NVIDIA-Linux-x86-290.10.run)

**x86-64**
[ftp://download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run)

---

### Post by gwfair on 2011-11-22
Thanks.

Does anyone know if this fixes the problem many of us are having with 11.10 not recognizing the second of our two monitors?

---

### Post by xebian on 2011-11-23
kwin is now working great with this version from NVidia.  Can't get most of the desktop effects to work before plus the flash crashing is gone too.

---

### Post by flammon on 2011-11-24
So far so good. The old driver would start to lag after a few hours this update seems to have corrected that.

---

### Post by kedmond on 2011-11-28
I just upgraded to this driver.  I'm running 11.10 with the Gnome 3 shell.  Things are generally a lot smoother and a bit faster.  There's still a weird delay when I open a new terminal, but otherwise the GUI is much better.

---

### Post by dino99 on 2011-11-28
jockey dont find it again :( & still missing nvidia-settings 290.10

---

### Post by Harry33 on 2011-11-28
> **dino99 said:**
> jockey dont find it again :( & still missing nvidia-settings 290.10

Nvidia-settings_290.10 can be downloaded from X-updates (X-Swat) PPA.
It is in the Oneiric branch, but it works just fine in Precise too.

---

### Post by heldal on 2011-11-29
It's appropriate with a warning about driver releases 290.06 and 290.10 to people with older mobile GPUs (GeForce [67]xxxGo). The new drivers may fail to recognise the built-in display leaving the user with a console login. 

[http://www.nvnews.net/vbulletin/showthread.php?t=168305](http://www.nvnews.net/vbulletin/showthread.php?t=168305)

To use X one will then have to either revert to the nv-driver or downgrade the proprietary driver. A possible workaround is to connect an external screen. 

The 290.X version brings back memories of a badly broken driver-relase from Nvidia a few years ago. There's a lot of problems discussed on their forum [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

