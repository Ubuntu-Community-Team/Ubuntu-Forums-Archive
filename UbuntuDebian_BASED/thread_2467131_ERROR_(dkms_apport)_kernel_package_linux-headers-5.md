---
title: "ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supporte"
date: 2021-09-16
forum: Ubuntu/Debian BASED
---

### Post by spe050812 on 2021-09-16
I'm getting an error I don;t know how to fix. Every time I do ```
sudo apt upgrade
``` I get a kernel related error:

```
myusername@pop-os:~$ sudo apt upgrade
[sudo] password for myusername: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up rtl88x2bu-dkms (5.8.7.4.37264.20200922-3) ...
Removing old rtl88x2bu-5.8.7.4.37264.20200922 DKMS files...


------------------------------
Deleting module version: 5.8.7.4.37264.20200922
completely from the DKMS tree.
------------------------------
Done.
Loading new rtl88x2bu-5.8.7.4.37264.20200922 DKMS files...
Building for 5.13.0-7614-generic
Building initial module for 5.13.0-7614-generic
ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supported
Error! Bad return status for module build on kernel: 5.13.0-7614-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.8.7.4.37264.20200922/build/make.log for more information.
dpkg: error processing package rtl88x2bu-dkms (--configure):
 installed rtl88x2bu-dkms package post-installation script subprocess returned error exit stat
us 10
Setting up rtl8812au-dkms (5.9.3.37279.20201012-3) ...
Removing old rtl8812au-5.9.3.37279.20201012 DKMS files...


------------------------------
Deleting module version: 5.9.3.37279.20201012
completely from the DKMS tree.
------------------------------
Done.
Loading new rtl8812au-5.9.3.37279.20201012 DKMS files...
Building for 5.13.0-7614-generic
Building initial module for 5.13.0-7614-generic
ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supported
Error! Bad return status for module build on kernel: 5.13.0-7614-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/5.9.3.37279.20201012/build/make.log for more information.
dpkg: error processing package rtl8812au-dkms (--configure):
 installed rtl8812au-dkms package post-installation script subprocess returned error exit stat
us 10
Errors were encountered while processing:
 rtl88x2bu-dkms
 rtl8812au-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

```

myusername@pop-os:~$ hostnamectl
   Static hostname: pop-os
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: ee127d98d3be347dd8a28b105fbe998f
           Boot ID: 54da44b5e03c43b78b112d297748d03b
  Operating System: Pop!_OS 21.04
            Kernel: Linux 5.13.0-7614-generic
      Architecture: x86-64

```

---

### Post by zvacet on 2021-09-16
```
sudo dpkg --configure rtl88x2bu-dkms
```

```
sudo dpkg --configure rtl8812au-dkms
```

Let us know what happened after these commands.

---

### Post by spe050812 on 2021-09-16
> **zvacet said:**
> ```
sudo dpkg --configure rtl88x2bu-dkms
```

```
sudo dpkg --configure rtl8812au-dkms
```

Let us know what happened after these commands.


```
myusername@pop-os:~$ sudo dpkg --configure rtl88x2bu-dkms
[sudo] password for myusername: 
Setting up rtl88x2bu-dkms (5.8.7.4.37264.20200922-3) ...
Removing old rtl88x2bu-5.8.7.4.37264.20200922 DKMS files...


------------------------------
Deleting module version: 5.8.7.4.37264.20200922
completely from the DKMS tree.
------------------------------
Done.
Loading new rtl88x2bu-5.8.7.4.37264.20200922 DKMS files...
Building for 5.13.0-7614-generic
Building initial module for 5.13.0-7614-generic
ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supported
Error! Bad return status for module build on kernel: 5.13.0-7614-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.8.7.4.37264.20200922/build/make.log for more information.
dpkg: error processing package rtl88x2bu-dkms (--configure):
 installed rtl88x2bu-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 rtl88x2bu-dkms

```


and

```

myusername@pop-os:~$ sudo dpkg --configure rtl8812au-dkms
Setting up rtl8812au-dkms (5.9.3.37279.20201012-3) ...
Removing old rtl8812au-5.9.3.37279.20201012 DKMS files...


------------------------------
Deleting module version: 5.9.3.37279.20201012
completely from the DKMS tree.
------------------------------
Done.
Loading new rtl8812au-5.9.3.37279.20201012 DKMS files...
Building for 5.13.0-7614-generic
Building initial module for 5.13.0-7614-generic
ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supported
Error! Bad return status for module build on kernel: 5.13.0-7614-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/5.9.3.37279.20201012/build/make.log for more information.
dpkg: error processing package rtl8812au-dkms (--configure):
 installed rtl8812au-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 rtl8812au-dkms

```

---

### Post by jeremy31 on 2021-09-16
Moved to Ubuntu/Debian based

---

