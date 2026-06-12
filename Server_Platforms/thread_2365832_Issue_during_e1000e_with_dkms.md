---
title: "Issue during e1000e with dkms"
date: 2017-07-11
forum: Server Platforms
---

### Post by siugh on 2017-07-11
Hi,
I am using

```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial
```

```
# uname -a
Linux nextcloud 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux




```
I need to compile e1000e module in order to use:
```

0a:00.0 Ethernet controller: Intel Corporation Device 0001 (rev 02)
0a:00.1 Ethernet controller: Intel Corporation Device 0001 (rev 02)

```


I am trying to use dkms, basically I followed this url:

[https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging](https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging)

The "add" command went fine:

```
# dkms add -m e1000e -v 3.3.5.3


Creating symlink /var/lib/dkms/e1000e/3.3.5.3/source ->
                 /usr/src/e1000e-3.3.5.3


DKMS: add completed.
```

I get error on "build" phase:

```
# dkms build -m e1000e -v 3.3.5.3   


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=4.4.0-62-generic all KVERSION=4.4.0-62-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for e1000e: 3.3.5.3 not found
Error! Bad return status for module build on kernel: 4.4.0-62-generic (x86_64)
Consult /var/lib/dkms/e1000e/3.3.5.3/build/make.log for more information.

```


```
# cat /var/lib/dkms/e1000e/3.3.5.3/build/make.log 
DKMS make.log for e1000e-3.3.5.3 for kernel 4.4.0-62-generic (x86_64)
Tue Jul 11 10:53:55 CEST 2017
make: *** No rule to make target 'all'.  Stop.
```

Any suggestion? Thank you!

---

### Post by howefield on 2017-07-11
Thread moved to the "*Server Platforms*" forum for a better fit.

---

