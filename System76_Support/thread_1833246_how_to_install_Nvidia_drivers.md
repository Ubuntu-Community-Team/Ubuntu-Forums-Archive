---
title: "how to install Nvidia drivers"
date: 2011-08-25
forum: System76 Support
---

### Post by wakajawaqa on 2011-08-25
Hi, I have a Gazelle laptop. I reinstalled Ubuntu but I'm not sure how to use the Nvidia driver. "Additional Drivers" shows that it is activated but not in use. How do I enable it for use?

I downloaded a .run file from the Nvidia website and ran it but it gave me an error "pre-install script failed" so I cancelled the installation.

This is /var/log/nvidia-installer.log

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug 25 17:25:57 2011
installer version: 280.13

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 280.13.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: No)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

Any ideas?

Thanks.

---

### Post by wakajawaqa on 2011-08-26
The contents of /usr/lib/nvidia/preinstall reads:

```
#!/bin/sh

# Trigger an error exit status to prevent the installer from overwriting
# Ubuntu's nvidia packages.

exit 1
```

Does that mean it's an automatic message and I can ignore it and continue with the installation? ... or is it going to f**k something up?:confused:

---

### Post by dave01945 on 2011-08-26
mine also says that it's not in use but i know it is because i can't run unity without it i will have a look around see if i can find a way of checking it

---

### Post by wakajawaqa on 2011-08-26
Thanks for your reply.

I have desktop effects, but I thought it was the Nouveau driver that Ubuntu uses by default.

---

### Post by realzippy on 2011-08-26
```
lshw -c video
```

shows you which driver/card aso

---

### Post by wakajawaqa on 2011-08-26
```
 *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f4000000-f5ffffff memory:e8000000-efffffff memory:f0000000-f3ffffff ioport:e000(size=128) memory:f6000000-f607ffff
```

Does that mean I'm already using the Nvidia driver?](*,)

---

### Post by realzippy on 2011-08-26
> **wakajawaqa said:**
> ```
 *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="SeaGreen"]driver=nvidia[/COLOR] latency=0
       resources: irq:16 memory:f4000000-f5ffffff memory:e8000000-efffffff memory:f0000000-f3ffffff ioport:e000(size=128) memory:f6000000-f607ffff
```

yes.

---

### Post by wakajawaqa on 2011-08-26
Thanks, sorry to waste your time on that one!

---

### Post by realzippy on 2011-08-26
nothing gets wasted  ;-)

---

