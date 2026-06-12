---
title: "cannot install the ati fglrx driver after upgrading to 13.04"
date: 2013-03-16
forum: Ubuntu Development Version
---

### Post by petru.marginean on 2013-03-16
Hi,

Just upgraded to 13.04, and now I cannot install the ATI drivers.

I see the following message in the log:

```
$> cat /var/lib/dkms/fglrx/9.002/build/make.log
DKMS make.log for fglrx-9.002 for kernel 3.8.0-12-generic (i686)
Sat Mar 16 14:45:04 EDT 2013
AMD kernel module generator version 2.1
kernel includes at /lib/modules/3.8.0-12-generic/build/include not found or incomplete
file: /lib/modules/3.8.0-12-generic/build/include/linux/version.h

```

Indeed the version.h file is not in the /lib/modules/3.8.0-12... but in the /usr/src/linux-headers-3.8.0-12....

Any idea how to solve this?

I also tried to install using apt-get but the driver crashes on reboot:

```
$> sudo apt-get install fglrx
```

Thanks,
PM

---

### Post by MAFoElffen on 2013-03-17
The reason both are failing is it can't find linux-headers-3.8.0-12-generic... ? 

First make sure linux-headers-3.8.0-12-generic is installed (You say it's there, but just to make sure dpkg see's it...)
```

dpkg -l | grep -i linux-headers-3.8.0.12*

```
If it is installed (located at /usr/src/linux-3.8.0-12-generic) then in /lib/modules/3.8.0-12-generic/ there should be a symbolic link called "build" that links to the /usr/src/linux-3.8.0-12-generic folder... If not, you could create it by-
```

[COLOR=#000000][FONT=verdana]ln -s /usr/src/linux-3.8.0-12-generic [/FONT][/COLOR]/lib/modules/3.8.0-12-generic/build
ls -ld /lib/modules/3.8.0-12-generic/build

```
2nd command there will confirm that the link is there and where it points to.

Note- linux-header-* packages should create that symbolic link when they install, but remember that 13.04 is still in +1 Dev. Should be reported as a bug through apport so they can change it in the dailys.

---

### Post by codemaniac on 2013-03-17
Moved to Ubuntu +1 (Raring Ringtail).

---

### Post by jfernyhough on 2013-03-17
You'll have to update to linux-image-3.8.0-13 and linux-headers-3.8.0-13. -12 isn't in the repo any more. Reboot, and remove linux-image-3.8.0-12 (so DKMS doesn't build kernel modules for it), and reinstall fglrx. It should then rebuild correctly.

---

### Post by sentfanwyaerda on 2013-05-11
I'm having the same/similar problem, while (downgrading) to [fglrx-8.970/Catalyst 13.1]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx") [I need legacy-support for HD2400PRO PCI alongside HD6850 PCIe for my quadhead desktop setup]. On Quantal/12.10 I got it working... The distributed fglrx-9.010 works, even as the manually installed (for testing) [fglrx-12.104/Catalyst 13.4]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") from ATI/AMD, both only work with the HD6850 (due to AMD their obsolete "new" support model).

```
sudo ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --buildandinstallpkg Ubuntu/raring --force
```
> Building for architecture x86_64
Building initial module for 3.8.0-19-generic
Error! Bad return status for module build on kernel: 3.8.0-19-generic (x86_64)
Consult /var/lib/dkms/fglrx/8.970/build/make.log for more information.
[QUOTE=/var/lib/dkms/fglrx/8.970/build/make.log]DKMS make.log for fglrx-8.970 for kernel 3.8.0-19-generic (x86_64)
Sat May 11 15:47:24 CEST 2013
AMD kernel module generator version 2.1
kernel includes at /lib/modules/3.8.0-19-generic/build/include not found or incomplete
file: /lib/modules/3.8.0-19-generic/build/include/linux/version.h[/QUOTE]

[**$** *ll /lib/modules/3.8.0-19-generic/build/include/linux/v** ] tells me the link to *version.h* isn't generated, even not by (re)installing the 3.8.0 versions of **linux-headers**, **linux-source** and **linux-image** packages. It's incomplete.

P.S. downgrading to 3.5.0/quantal (from [Ubuntu 12.10]("http://packages.ubuntu.com/quantal/")) results into a whole new set of problems

---

### Post by cariboo on 2013-05-11
Thread closed, as this has nothing to do with Saucy.

---

