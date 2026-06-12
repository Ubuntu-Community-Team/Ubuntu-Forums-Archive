---
title: "couldn't running vmware-player with the linux kernel that i compiled"
date: 2009-04-01
forum: Virtualisation
---

### Post by Kelen.Chang on 2009-04-01
i compiled a linux kernel 2.6.29 (my first time), :guitar:  
and it's worked for me perfect. but vmware-player couldn't running.
but it's it's worked fine before, completed upgrade from kernel 2.6.24-16 to kernel 2.6.24-23.
more about this error information i was attached. 
i real hope some lucky one could help me. 
```

$ cat /tmp/vmware-root/setup-13941.log 
Apr 02 01:33:48.049: app| Log for VMware Workstation pid=13941 version=6.5.1 build=build-126130 option=Release
Apr 02 01:33:48.049: app| Host codepage=UTF-8 encoding=UTF-8
Apr 02 01:33:48.049: app| Logging to /tmp/vmware-root/setup-13941.log
Apr 02 01:33:49.403: app| Extracting the sources of the vmmon module.
Apr 02 01:33:49.414: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.29-custom-3.2/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.2.4
```

---

### Post by Trail on 2009-04-03
Got it to work on 2.6.29-rc8-5-default.

See this thread: [http://communities.vmware.com/thread/202340](http://communities.vmware.com/thread/202340)

---

