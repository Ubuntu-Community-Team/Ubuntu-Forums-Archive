---
title: "ubuntu 9.10 64bit and vmware 2.0.2"
date: 2010-04-13
forum: Virtualisation
---

### Post by anothergene on 2010-04-13
I'm having an issue installing vmware 2.0.2 on my ubuntu 9.10 64bit server.  The current system I am running is:  

Linux thire 2.6.31-20-server #58-Ubuntu SMP Fri Mar 12 05:40:05 UTC 2010 x86_64 GNU/Linux

I have tried following this guide:  [http://bit.ly/csWf5Z](http://bit.ly/csWf5Z)
and this guide:  [http://bit.ly/c4Xhxg](http://bit.ly/c4Xhxg)

The install and patching seem to go ok, but it throws an exception and aborts while trying to configure/compile as follows:  

```
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-server'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.
```


I've tried doing the uninstall along with removing any vmware related files suggested by the guides.  

Any one have any other suggestions that I can try?

---

### Post by stuartsiegler on 2010-04-19
sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
(with the VMWare-server-2.0.1-156745.x86_64.tar.gz in the same dir)
Also threw the vm...o "files exist" errors, but all I had to do was delete all of them (and re-run the script.

I dont remember them being in /tmp though; i seem to remember them being in /lib (and a find points them in /lib/modules/2.6.31-20-generic/misc, fwiw)

I just re-ran it and it was /lib/modules/2.6.31-20-generic/misc, so a
sudo rm /lib/modules/2.6.31-20-generic/misc/vm*.*
did it.


Stuart

---

