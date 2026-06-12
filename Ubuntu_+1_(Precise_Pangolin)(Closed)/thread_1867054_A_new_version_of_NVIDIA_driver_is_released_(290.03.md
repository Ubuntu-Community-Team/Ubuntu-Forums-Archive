---
title: "A new version of NVIDIA driver is released (290.03)"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by portis on 2011-10-22
Release highlights since 285.05.09:

    Added support for the following GPU:
        GeForce 510
    Fixed a bug that prevented the driver from loading on some systems with integrated graphics.
    Fixed issues in VDPAU that prevented allocating and displaying extremely large VdpOutputSurfaces.
    Added support for limiting heap allocations in the OpenGL driver through the use of the __GL_HEAP_ALLOC_LIMIT environment variable. See the README for further details.
    Added an "Accel" option to the X driver to allow disabling its use of the graphics processing hardware. This is useful when other components, such as CUDA, require exclusive use of the GPU's processing cores.
    Modified how the OpenGL driver allocates executable memory so it may continue to function properly if /tmp is mounted noexec. As some fallback allocation methods may be prohibited under SELinux policy, the driver now supports detection of this policy as well as manual override of this detection via the __GL_SELINUX_BOOLEANS environment variable.
    Fixed a bug that caused various GLSL built-in uniforms to not be updated properly when calling glPopAttrib.
    Improved performance by caching compiled OpenGL shaders to disk. Added a "GLShaderDiskCache" option to the X driver to enable/disable this feature. Added the __GL_SHADER_DISK_CACHE and __GL_SHADER_DISK_CACHE_PATH environment variables for further configuration. See the README for further details.
    Fixed a bug that caused trapezoid and triangle rendering to be very slow on older GPUs with xorg-server 1.11.


The 290.03 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 290.03 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via FTP.

Please see the README (x86 / x86_64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 290.03 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log.gz file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).

---

### Post by effenberg0x0 on 2011-10-22
Thanks for the heads up. 290.03 is running fine here on PP (GTS450).

Effenberg

---

### Post by Harry33 on 2011-10-22
This new NVidia beta driver (nvidia-current_290.03) is available from Xorg-edgers PPA (Oneiric)
and so is the packege nvidia-settigns_290.03 too.

This really works fine in Precise.

---

### Post by paul_in_london on 2011-10-22
> **Harry33 said:**
> This new NVidia beta driver (nvidia-current_290.03) is available from Xorg-edgers PPA (Oneiric)
and so is the packege nvidia-settigns_290.03 too.

This really works fine in Precise.

Yes, those two updates came through for me earlier. :)

---

### Post by ventrical on 2011-10-22
> **paul_in_london said:**
> Yes, those two updates came through for me earlier. :)


How do I set up that repo?

Thanks..

---

### Post by paul_in_london on 2011-10-22
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
```

In my /etc/apt/sources.list.d directory I have:

```
xorg-edgers-ppa-oneiric.list
xorg-edgers-ppa-oneiric.list.save
```

because I added the ppa before I upgraded to PP so if you're adding that ppa now you'll probably need to rename your versions from precise to oneiric and edit them to look like this:

```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main
```

Or instead of that just add those two deb lines to the end of your /etc/apt/sources.list file.

---

### Post by xyzzyman on 2011-10-22
Had to roll back to 285 as it was causing the latest 64-bit Flash to crash on firefox and chrome. Purge and reinstalled chrome and tried flashfix on firefox before realizing what the issue really was. I'll reinstall later and submit bug reports.

---

### Post by ahmed.cnbd on 2011-10-22
> **portis said:**
> Release highlights since 285.05.09:

    Added support for the following GPU:
        GeForce 510
    Fixed a bug that prevented the driver from loading on some systems with integrated graphics.
    Fixed issues in VDPAU that prevented allocating and displaying extremely large VdpOutputSurfaces.
    Added support for limiting heap allocations in the OpenGL driver through the use of the __GL_HEAP_ALLOC_LIMIT environment variable. See the README for further details.
    Added an "Accel" option to the X driver to allow disabling its use of the graphics processing hardware. This is useful when other components, such as CUDA, require exclusive use of the GPU's processing cores.
    Modified how the OpenGL driver allocates executable memory so it may continue to function properly if /tmp is mounted noexec. As some fallback allocation methods may be prohibited under SELinux policy, the driver now supports detection of this policy as well as manual override of this detection via the __GL_SELINUX_BOOLEANS environment variable.
    Fixed a bug that caused various GLSL built-in uniforms to not be updated properly when calling glPopAttrib.
    Improved performance by caching compiled OpenGL shaders to disk. Added a "GLShaderDiskCache" option to the X driver to enable/disable this feature. Added the __GL_SHADER_DISK_CACHE and __GL_SHADER_DISK_CACHE_PATH environment variables for further configuration. See the README for further details.
    Fixed a bug that caused trapezoid and triangle rendering to be very slow on older GPUs with xorg-server 1.11.


The 290.03 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 290.03 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via FTP.

Please see the README (x86 / x86_64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 290.03 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log.gz file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).


thanks for news

---

### Post by ventrical on 2011-10-22
> **paul_in_london said:**
> ```
sudo add-apt-repository ppa:xorg-edgers/ppa 
```In my /etc/apt/sources.list.d directory I have:

```
xorg-edgers-ppa-oneiric.list
xorg-edgers-ppa-oneiric.list.save
```because I added the ppa before I upgraded to PP so if you're adding that ppa now you'll probably need to rename your versions from precise to oneiric and edit them to look like this:

```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main
```Or instead of that just add those two deb lines to the end of your /etc/apt/sources.list file.

  I got half way through .. then I read the warning that the ppa is busted with Unity 3D and will only work with 2D. I'll try again later on that one.

Thanks Paulin London

---

### Post by TerminX on 2011-10-22
> **xyzzyman said:**
> Had to roll back to 285 as it was causing the latest 64-bit Flash to crash on firefox and chrome. Purge and reinstalled chrome and tried flashfix on firefox before realizing what the issue really was.
Yep, same result here.  Reported it to my friend at NVIDIA a few hours ago but he didn't say whether or not a fix was forthcoming soon.  Gotta remember however that this is the first public beta from a newer branch (290 vs 285), so issues like these aren't terribly surprising.

It does however definitively fix the lag caused by X.org 1.11's removal of some trapezoid acceleration helper functions!

---

### Post by paul_in_london on 2011-10-22
> **ventrical said:**
> I got half way through .. then I read the warning that the ppa is busted with Unity 3D and will only work with 2D. I'll try again later on that one.

Thanks Paulin London

No worries. I didn't know about the Unity 3D problem because I don't use Unity at all...

---

