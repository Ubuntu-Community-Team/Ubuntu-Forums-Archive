---
title: "Installed VM PLayer 6.0.1 ok, but error &quot;Unable to start service&quot; when starting app"
date: 2014-04-18
forum: Virtualisation
---

### Post by tachum1 on 2014-04-18
Installed on Ubuntu 14.04 LTS 64 bit. Have included the last few lines of log file. Any thoughts?


2014-04-18T17:43:25.674+10:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-18T17:43:25.944+10:00| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-24-generic/misc/vmnet.ko".
2014-04-18T17:43:25.944+10:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-04-18T17:43:25.955+10:00| vthread-3| I120: Successfully extracted the vmnet source.
2014-04-18T17:43:25.955+10:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-9i0ej7/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-24-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-04-18T17:43:27.375+10:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.

cheers

---

### Post by tachum1 on 2014-04-18
Solved. used 6.0.2

---

