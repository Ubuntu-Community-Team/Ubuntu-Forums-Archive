---
title: "Upgrading to Ubuntu 18.04 giving Nvidia Graphics driver issues"
date: 2018-06-16
forum: System76 Support
---

### Post by skade88 on 2018-06-16
Howdy Y'all!

I done upgraded my Bonobo Extreme laptop to Ubuntu 18.04 this here morning. Everything seemed'ta have upgraded smoothly until I tried to load my favorite games up n let me tell you! It was not runnin' the official Nvidia drivier! I was fixin' to fix the issue by running sudo apt --fix-broken install but it bailed with this error code 1 faster thank you can say Amarillo! Please give me some advice so I get back to gaming.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  i965-va-driver:i386 libgnome-desktop-3-12 libva2:i386 mesa-va-drivers:i386 va-driver-all:i386 wine-stable-amd64
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-396 libnvidia-gl-396:i386
The following NEW packages will be installed:
  libnvidia-gl-396 libnvidia-gl-396:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 33.3 MB of archives.
After this operation, 158 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu) bionic/main i386 libnvidia-gl-396 i386 396.24-0ubuntu1~pop1 [16.7 MB]
Get:2 [http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu) bionic/main amd64 libnvidia-gl-396 amd64 396.24-0ubuntu1~pop1 [16.6 MB]                                                                                 
Fetched 33.3 MB in 2min 17s (244 kB/s)                                                                                                                                                                            
(Reading database ... 246334 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-396_396.24-0ubuntu1~pop1_i386.deb ...
dpkg-query: no packages found matching libnvidia-gl-390
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-396'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-396_396.24-0ubuntu1~pop1_i386.deb (--unpack):
 new libnvidia-gl-396:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-396_396.24-0ubuntu1~pop1_amd64.deb ...
dpkg-query: no packages found matching libnvidia-gl-390
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-396'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-396_396.24-0ubuntu1~pop1_amd64.deb (--unpack):
 new libnvidia-gl-396:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-396_396.24-0ubuntu1~pop1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-396_396.24-0ubuntu1~pop1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2018-06-16
skade88; Hummmm ...

I do not find with a quick look that libnvidia-gl-396** packages are in the repository, I will "assume" that they are provided within the proprietary driver.
Let us consider to clean up the cache and re-install the nvidia driver.

Do we have the tools presently installed to install the proprietary driver ?
post back the results - within code tags - of terminal commands:
```

sudo dkms status
lspci -k | grep -EA2 'VGA|3D'

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

[INDENT]we see what
[INDENT]tale gets told
[/INDENT][/INDENT]

---

### Post by skade88 on 2018-06-17
Howdy Bashing-om,

Thanks for your reply. I have pasted the output below.

sudo dkms status
[INDENT]nvidia, 396.24, 4.15.0-23-generic, x86_64: installed[/INDENT]
[INDENT]system76, 0.0.3~1527703256~18.04~2d0b3d9~dev, 4.15.0-23-generic, x86_64: installed[/INDENT]
[INDENT]virtualbox, 5.2.10, 4.13.0-45-generic, x86_64: installed[/INDENT]
[INDENT]virtualbox, 5.2.10, 4.15.0-23-generic, x86_64: installed

[/INDENT]
lspci -k | grep -EA2 'VGA|3D'
[INDENT]01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 880M] (rev a1)[/INDENT]
[INDENT]Subsystem: CLEVO/KAPOK Computer GK104M [GeForce GTX 880M][/INDENT]
[INDENT]Kernel driver in use: nvidia[/INDENT]

Best,
David Brooks

---

### Post by Bashing-om on 2018-06-17
skade88; Humm ...

where did you get the 396 version driver ? Presently nvidia recommends the 390 driver:
 [http://www.nvidia.com/download/driverResults.aspx/134859/en-us](http://www.nvidia.com/download/driverResults.aspx/134859/en-us)

I just installed the 390 version driver, and can attest of improved performance over nouveau.

And is this in a VM ? That too can have it's effect for the pass through .

Got to be a reason -

---

### Post by skade88 on 2018-06-17
This is not a VM. The driver came from the System76 repo. I think it tried to upgrade to 396 after I did the dist upgrade from 17.10 to 18.04.

[COLOR=#000000]Get:1 [/COLOR][http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu)[COLOR=#000000] bionic/main i386 libnvidia-gl-396 i386 396.24-0ubuntu1~pop1 [16.7 MB][/COLOR]
[COLOR=#000000]Get:2 [/COLOR][http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu)[COLOR=#000000] bionic/main amd64 libnvidia-gl-396 amd64 396.24-0ubuntu1~pop1 [16.6 MB][/COLOR]

[COLOR=#000000]I went and removed the 340 stuff I could find to see if that would help. My package manager is at least telling me the problems with the broken packages went away. I went one by one removing the files it was complaining about and that seemed to have cleared it up. Do you have any graphics benchmark tools I could use to compare results with you?[/COLOR]

 1941  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/i386-linux-gnu/libGL.so.1
 1942  sudo apt-get --fix-broken install
 1943  sudo apt-get update
 1944  sudo apt-get upgrade
 1945  sudo apt --fix-broken install
 1946  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/i386-linux-gnu/libGL.so.
 1947  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/i386-linux-gnu/libGL.so
 1948  sudo apt --fix-broken install
 1949  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/i386-linux-gnu/libEGL.so.1
 1950  sudo apt --fix-broken install
 1951  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/i386-linux-gnu/libEGL.so.1
 1952  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/i386-linux-gnu/libEGL.so
 1953  sudo apt --fix-broken install
 1954  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/x86_64-linux-gnu/libGL.so.1
 1955  sudo apt --fix-broken install
 1956  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/x86_64-linux-gnu/libGL.so
 1957  sudo apt --fix-broken install
 1958  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/x86_64-linux-gnu/libEGL.so.1
 1959  sudo apt --fix-broken install
 1960  sudo dpkg-divert --package nvidia-340 --remove /usr/lib/x86_64-linux-gnu/libEGL.so
 1961  sudo apt --fix-broken install

Best,
David Brooks

---

### Post by skade88 on 2018-06-17
I just ran the glmark2 benchmark tool and got these results. I am not sure if they are good results or not.

=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 880M/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 396.24
=======================================================
[build] use-vbo=false: FPS: 3788 FrameTime: 0.264 ms
[build] use-vbo=true: FPS: 4528 FrameTime: 0.221 ms
[texture] texture-filter=nearest: FPS: 4299 FrameTime: 0.233 ms
[texture] texture-filter=linear: FPS: 4301 FrameTime: 0.233 ms
[texture] texture-filter=mipmap: FPS: 4404 FrameTime: 0.227 ms
[shading] shading=gouraud: FPS: 4309 FrameTime: 0.232 ms
[shading] shading=blinn-phong-inf: FPS: 4345 FrameTime: 0.230 ms
[shading] shading=phong: FPS: 4299 FrameTime: 0.233 ms
[shading] shading=cel: FPS: 4309 FrameTime: 0.232 ms
[bump] bump-render=high-poly: FPS: 4103 FrameTime: 0.244 ms
[bump] bump-render=normals: FPS: 4497 FrameTime: 0.222 ms
[bump] bump-render=height: FPS: 4531 FrameTime: 0.221 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4170 FrameTime: 0.240 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3909 FrameTime: 0.256 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4354 FrameTime: 0.230 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2529 FrameTime: 0.395 ms
[desktop] effect=shadow:windows=4: FPS: 3903 FrameTime: 0.256 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1128 FrameTime: 0.887 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1373 FrameTime: 0.728 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1202 FrameTime: 0.832 ms
[ideas] speed=duration: FPS: 4259 FrameTime: 0.235 ms
[jellyfish] <default>: FPS: 4003 FrameTime: 0.250 ms
[terrain] <default>: FPS: 601 FrameTime: 1.664 ms
[shadow] <default>: FPS: 4104 FrameTime: 0.244 ms
[refract] <default>: FPS: 1548 FrameTime: 0.646 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4243 FrameTime: 0.236 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4244 FrameTime: 0.236 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4283 FrameTime: 0.233 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4275 FrameTime: 0.234 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4105 FrameTime: 0.244 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3971 FrameTime: 0.252 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4123 FrameTime: 0.243 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4125 FrameTime: 0.242 ms
=======================================================
                                  glmark2 Score: 3701 
=======================================================

---

### Post by Bashing-om on 2018-06-17
skade88; Yeah ...

Having 2 graphic's drivers installed will cause issues .. Make sure that the 340 is completely purged.
```

dpkg -l | grep -i nvidia

```
my result for the glmark2 benchmark - looked suburb !
Old old 2007 dual core Athlon:
```

sysop@x1810:~/uwn$ glmark2
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GT 710/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.67
=======================================================
[build] use-vbo=false: FPS: 1403 FrameTime: 0.713 ms
[build] use-vbo=true: FPS: 2731 FrameTime: 0.366 ms
[texture] texture-filter=nearest: FPS: 2042 FrameTime: 0.490 ms
[texture] texture-filter=linear: FPS: 2025 FrameTime: 0.494 ms
[texture] texture-filter=mipmap: FPS: 2191 FrameTime: 0.456 ms
[shading] shading=gouraud: FPS: 1972 FrameTime: 0.507 ms
[shading] shading=blinn-phong-inf: FPS: 1937 FrameTime: 0.516 ms
[shading] shading=phong: FPS: 1917 FrameTime: 0.522 ms
[shading] shading=cel: FPS: 1928 FrameTime: 0.519 ms
[bump] bump-render=high-poly: FPS: 1376 FrameTime: 0.727 ms
[bump] bump-render=normals: FPS: 2650 FrameTime: 0.377 ms
[bump] bump-render=height: FPS: 2567 FrameTime: 0.390 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1457 FrameTime: 0.686 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 735 FrameTime: 1.361 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2317 FrameTime: 0.432 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 639 FrameTime: 1.565 ms
[desktop] effect=shadow:windows=4: FPS: 1097 FrameTime: 0.912 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 219 FrameTime: 4.566 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 254 FrameTime: 3.937 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 265 FrameTime: 3.774 ms
[ideas] speed=duration: FPS: 1888 FrameTime: 0.530 ms
[jellyfish] <default>: FPS: 1127 FrameTime: 0.887 ms
[terrain] <default>: FPS: 134 FrameTime: 7.463 ms
[shadow] <default>: FPS: 1662 FrameTime: 0.602 ms
[refract] <default>: FPS: 319 FrameTime: 3.135 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 2003 FrameTime: 0.499 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1906 FrameTime: 0.525 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1964 FrameTime: 0.509 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1911 FrameTime: 0.523 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1902 FrameTime: 0.526 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1909 FrameTime: 0.524 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1908 FrameTime: 0.524 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1875 FrameTime: 0.533 ms
=======================================================
                                  glmark2 Score: 1582 
=======================================================
sysop@x1810:~/uwn$

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by skade88 on 2018-06-17
It looks like I have some old drivers that I need to clean up?

dpkg -l | grep -i nvidia[INDENT]ii  libnvidia-cfg1-396:amd64                      396.24-0ubuntu1~pop1                       amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-396                          396.24-0ubuntu1~pop1                       all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-396:amd64                   396.24-0ubuntu1~pop1                       amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386                    396.24-0ubuntu1~pop1                       i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64                    396.24-0ubuntu1~pop1                       amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386                     396.24-0ubuntu1~pop1                       i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64                    396.24-0ubuntu1~pop1                       amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386                     396.24-0ubuntu1~pop1                       i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64                      396.24-0ubuntu1~pop1                       amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386                       396.24-0ubuntu1~pop1                       i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                        396.24-0ubuntu1~pop1                       amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                         396.24-0ubuntu1~pop1                       i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64                      396.24-0ubuntu1~pop1                       amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386                       396.24-0ubuntu1~pop1                       i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-375                                    384.130-0ubuntu0.17.10.1                   amd64        Transitional package for nvidia-384
rc  nvidia-384                                    390.48-0ubuntu3                            amd64        Transitional package for nvidia-driver-390
rc  nvidia-390                                    390.25-0ubuntu1~17.10.0                    amd64        NVIDIA binary driver - version 390.25
ii  nvidia-compute-utils-396                      396.24-0ubuntu1~pop1                       amd64        NVIDIA compute utilities
ii  nvidia-dkms-396                               396.24-0ubuntu1~pop1                       amd64        NVIDIA DKMS package
rc  nvidia-docker                                 1.0.1-1                                    amd64        NVIDIA Docker container tools
ii  nvidia-driver-396                             396.24-0ubuntu1~pop1                       amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-396                      396.24-0ubuntu1~pop1                       amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396                      396.24-0ubuntu1~pop1                       amd64        NVIDIA kernel source package
rc  nvidia-opencl-icd-340                         340.106-0ubuntu3                           amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-390                         390.25-0ubuntu1~17.10.0                    amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                  0.8.8                                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               390.42-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                              396.24-0ubuntu1~pop1                       amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396                 396.24-0ubuntu1~pop1                       amd64        NVIDIA binary Xorg driver


[/INDENT]

---

### Post by Bashing-om on 2018-06-17
skade88; Well ..

Do not "think" they are an issue,
'rc' is (r)emoved but (c)onfig files remain.
We can clean up:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```


[INDENT][INDENT]I do like clean :)
[/INDENT][/INDENT]

Edit: Ouch , missed this one:
> 
ii nvidia-settings 390.42-0ubuntu1 amd64 Tool for configuring the NVIDIA graphics driver

need to insure all of the 390 version is gone too.

---

### Post by skade88 on 2018-06-18
Thanks so much for the help! You saved the day for me! : )

Best,
David Brooks

---

### Post by Bashing-om on 2018-06-18
skade88; Great -

Glad2help :)

If this matter is now concluded to your satisfaction -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

