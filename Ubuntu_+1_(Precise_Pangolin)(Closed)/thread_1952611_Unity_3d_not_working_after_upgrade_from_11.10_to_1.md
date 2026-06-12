---
title: "Unity 3d not working after upgrade from 11.10 to 12.04 (intel graphics)"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ccomic on 2012-04-04
Since unity 3d needs hardware acceleration to work properly I started looking into OpenGL related stuff and found out that the system loads the wrong driver. 
It seems to be a linking problem as specifying the library path allows to start unity with "LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/ unity --replace" which actually starts unity 3d.

Is there a way to fix this issue permanently? I guess all software that relies on hardware acceleration would fail otherwise.

I posted some more information and debugging output below.

lspci:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

LIBGL_DEBUG=verbose /usr/lib/nux/unity_support_test -p:
```

libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/i965_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/i965_dri.so: undefined symbol: drm_intel_gem_bo_clear_relocs)
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/core/.drirc: No such file or directory.
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

```

LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/ /usr/lib/nux/unity_support_test -p:
```

libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/core/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/user/.drirc: No such file or directory.
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset
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

```

ldd `which /usr/lib/nux/unity_support_test -p`:
```

        linux-vdso.so.1 =>  (0x00007fff3bbff000)
        libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f1da8dc7000)
        libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007f1da8b67000)
        libXcomposite.so.1 => /usr/lib/x86_64-linux-gnu/libXcomposite.so.1 (0x00007f1da8963000)
        libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f1da8760000)
        libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f1da855a000)
        libpci.so.3 => /lib/x86_64-linux-gnu/libpci.so.3 (0x00007f1da834d000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f1da7f90000)
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f1da7d72000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f1da7b6d000)
        libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007f1da7948000)
        libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f1da7737000)
        libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007f1da7534000)
        libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007f1da731d000)
        libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007f1da7118000)
        libdrm.so.2 => /usr/local/lib/libdrm.so.2 (0x00007f1da6f0c000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f1da6cef000)
        libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f1da6ad7000)
        libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f1da68bb000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f1da9125000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f1da66b8000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f1da64b2000)
        librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f1da62a9000)

```

---

### Post by neu5eeCh on 2012-04-04
You might want to check out this bug too:

[I][https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125](https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125)             
[/I]Your issue may not be related, then again (having upgraded) you might be chasing a wild goose.

I haven't been able to load 3D for about a week. The developers borked compiz somehow.

---

### Post by cariboo on 2012-04-04
Are you running a hard drive installation, or a virtual install using vmware? As I see vmware mentioned in one of your outputs.

---

### Post by ventrical on 2012-04-04
> **VTPoet said:**
> You might want to check out this bug too:

[I][https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125](https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125)             
[/I]Your issue may not be related, then again (having upgraded) you might be chasing a wild goose.

I haven't been able to load 3D for about a week. The developers borked compiz somehow.


 All I had to do is just set up the CCSM modes , enable unity_plugin and it is fine.

---

### Post by ccomic on 2012-04-05
> **VTPoet said:**
> You might want to check out this bug too:

[I][https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125](https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125)             
[/I]Your issue may not be related, then again (having upgraded) you might be chasing a wild goose.

I haven't been able to load 3D for about a week. The developers borked compiz somehow.

I don't think that this bug causes my issue as normally starting the ubuntu desktop just falls back to unity 2d without any crashing and starting unity with the "LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/" prefix seems to work without problems.

I rather have the feeling that something got messed up during the upgrade, maybe related to the migrate to multiarch.


> **cariboo907 said:**
> Are you running a hard drive installation, or a virtual install using vmware? As I see vmware mentioned in one of your outputs.

I'm running a hard drive installation. VMware just gets the credits for llvmpipe which is the software accelerated openGL renderer if I'm not wrong.

---

### Post by richardg1952 on 2012-04-08
I see the same problem on my Lenovo T410 with Intel graphics. 3D/compiz worked fine in 11.10 but not after upgrading to 12.04. I can only get Unity 2D.

---

### Post by ccomic on 2012-04-10
I was able to solve the issue for me.

The problem was an unsupported libdrm.so.2 in /usr/local/lib which I must have installed manually at some point...
Removing these manually installed libdrm files solved the issue, running ldd yields the correct linking now:
```

$ ldd `which /usr/lib/nux/unity_support_test -p` | grep libdrm
        libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007f8db88af000)

```

---

### Post by richardg1952 on 2012-04-12
I'm not sure what's wrong with mine.
ldd `which /usr/lib/nux/unity_support_test -p` | grep libdrm
returns nothing.

locate libdrm.so.2

/usr/lib/i386-linux-gnu/libdrm.so.2
/usr/lib/i386-linux-gnu/libdrm.so.2.4.0
/usr/lib/x86_64-linux-gnu/libdrm.so.2
/usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0

how do I get ldd to use /usr/lib/x86_64-linux-gnu/libdrm.so.2?

this looks bad:
/usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

OK. following the steps on this page got 3D back for me on my Lenovo T410 with integrated Intel graphics.
[http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html](http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html)

after a reboot I get:

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
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

