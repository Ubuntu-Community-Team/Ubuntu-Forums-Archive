---
title: "Vmware Wrkstation 6.5.2 Vm Mon install fails."
date: 2009-07-20
forum: Virtualisation
---

### Post by Bonzai11 on 2009-07-20
Recently upgraded my Ubuntu install and chose to do a complete wipe.
Today I finally felt like getting Vmware up again and got the newer 6.5.2.
The installation and everything worked fine. I used the 64 bit bundle and I'm on 64bit Karmic.
Just when I start Vmware for the first time it asks to install modules, which I don't remember doing on 6.5.1.
It dumps a log which changes every time it is run.
```

Jul 20 14:45:30.511: app| Log for VMware Workstation pid=25480 version=6.5.2 build=build-156735 option=Release
Jul 20 14:45:30.511: app| Host codepage=UTF-8 encoding=UTF-8
Jul 20 14:45:30.511: app| Logging to /tmp/vmware-root/setup-25480.log
Jul 20 14:45:31.562: app| Extracting the sources of the vmmon module.
Jul 20 14:45:31.601: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-2-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.0
```Everytime I run it it randomly changes the amount of times
```
Jul 20 14:45:31.601: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-2-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make
```is displayed, well ran.

Sometimes it shows up 3 times some 4 its odd because I don't get any errors it just runs it and quits then the dialog resets to the beginning where it asks to install modules.
(note: the log will look just like that but last line just repeated a random number of times. Usually not that many.)
I've looked around made sure build-essentials, ia32-lib, etc. where up to date but it still won't work.
I saw the sticky, but it says for server, but I am using workstation, but I installed the dependencies and libraries anyway.
Anyone have any ideas on how to get this working?
I'm just a 16 year old kid who wants to get back to photoshop and C++ xpress.
Thanks in advance.

---

### Post by darco on 2009-07-21
You may want to check out this link,....

[http://communities.vmware.com/thread/208963?start=0&tstart=0](http://communities.vmware.com/thread/208963?start=0&tstart=0)

or

[http://communities.vmware.com/thread/221724?tstart=30](http://communities.vmware.com/thread/221724?tstart=30)

good luck

darco

---

