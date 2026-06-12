---
title: "Multipath issue"
date: 2009-11-26
forum: Server Platforms
---

### Post by erpupone10 on 2009-11-26
Hi all,

I'm trying to install multipath-tools package on Ubuntu 9.10 Server AMD64. I need to load block devices via Fiber Channel.

I resolved package dependecies by installing:

-  libdevmapper1.02.1_1.02.27-4ubuntu7_amd64.deb
-  libreadline5_5.1-7build1_amd64.deb
-  libsysfs2_2.0.0-5build1_amd64.deb

but when I try to install multipath-tools package, an error occours and seems that libdevmapper1.02 is noti nstalled..

If I try to run multipath daemon the error is the following:

root@xc273:~# multipathd start
multipathd: error while loading shared libraries: libdevmapper.so.1.02: cannot open shared object file: No such file or directory

Any suggestion?

---

### Post by scorp123 on 2009-11-26
Why did you have to resolve package dependencies manually? That should happen automatically.

As for the error .... can you please check if the file the daemon wants is really really there?

e.g.

```
dpkg -l libdevmapper*
``` ... should list the package as being "ii" = installed.

And this should spit out the list of files within the package:
```
dpkg -L libdevmapper1.02.1
```

Please check if the file which is supposedly missing gets listed or not ...

---

### Post by erpupone10 on 2009-11-27
The machines are not connected to the internet so I need to manually resolve dependecies..

root@xc265:/tmp# dpkg -l libdevmapper*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nome                      Versione                  Descrizione
+++-=========================-=========================-==================================================================
un  libdevmapper              <non definita>            (nessuna descrizione disponibile)
iU  libdevmapper-dev          2:1.02.27-4ubuntu7        The Linux Kernel Device Mapper header files
un  libdevmapper-event1.02.1  <non definita>            (nessuna descrizione disponibile)
un  libdevmapper1.02          <non definita>            (nessuna descrizione disponibile)
ii  libdevmapper1.02.1        2:1.02.27-4ubuntu7        The Linux Kernel Device Mapper userspace library

libdevmapper1.02.1  is installed but libdevmapper1.02 (the one I need) is not defined..

root@xc265:/tmp# dpkg -L libdevmapper1.02.1
/.
/lib
/lib/libdevmapper.so.1.02.1
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libdevmapper1.02.1
/usr/share/doc/libdevmapper1.02.1/changelog.gz
/usr/share/doc/libdevmapper1.02.1/copyright
/usr/share/doc/libdevmapper1.02.1/changelog.Debian.gz

I got the packages from [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/) but only libdevmapper1.02.1 is available...
Have I to unistall libdevmapper1.02.1 ?? Where can I find libdevmapper1.02??

Thnaks..

---

### Post by scorp123 on 2009-11-27
Why are you manually installing packages? Why not let the package manager handle this? What Linux distro and Ubuntu release are you really using?? You should NOT manually mix packages from different releases. That CANNOT work.

---

