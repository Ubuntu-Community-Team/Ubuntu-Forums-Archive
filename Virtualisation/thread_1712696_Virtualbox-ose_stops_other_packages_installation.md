---
title: "Virtualbox-ose stops other packages installation"
date: 2011-03-23
forum: Virtualisation
---

### Post by kumpsath1 on 2011-03-23
Hi,
 Recently I upgraded my kernal from 2.6.35 to 2.6.38 and after installed
 virtualbox-ose; The installation itself failed, and now not able to
 uninstall vb.. or even install/uninstall any applications... for example,
 installation of pidgin is giving exception as below. Pls help other than
 reinstalling my OS. Its urgent; Error:-


 ....
 (Reading database ... 180138 files and directories currently installed.)
 Unpacking pidgin-data (from .../pidgin-data_1%3a2.7.3-1ubuntu3.2_all.deb)
 ...
 Selecting previously deselected package pidgin.
 Unpacking pidgin (from .../pidgin_1%3a2.7.3-1ubuntu3.2_i386.deb) ...
 Selecting previously deselected package pidgin-libnotify.
 Unpacking pidgin-libnotify (from .../pidgin-
 libnotify_0.14-4ubuntu1_i386.deb) ...
 Processing triggers for hicolor-icon-theme ...
 Processing triggers for desktop-file-utils ...
 Processing triggers for python-gmenu ...
 Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
 Processing triggers for man-db ...
 Processing triggers for gconf2 ...
 Processing triggers for python-support ...
 Setting up virtualbox-ose-dkms (3.2.8-dfsg-2ubuntu1) ...
 Removing old virtualbox-ose-3.2.8 DKMS files...

 ------------------------------
 Deleting module version: 3.2.8
 completely from the DKMS tree.
 ------------------------------
 Done.
 Loading new virtualbox-ose-3.2.8 DKMS files...
 First Installation: checking all kernels...
 Building only for 2.6.38-4-generic
 Building initial module for 2.6.38-4-generic

 Error! Bad return status for module build on kernel: 2.6.38-4-generic
 (i686)
 Consult the make.log in the build directory
 /var/lib/dkms/virtualbox-ose/3.2.8/build/ for more information.
 Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
 IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-ose-
 dkms.0.crash'
 dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status
 10
 No apport report written because MaxReports is reached already
 Setting up pidgin-data (1:2.7.3-1ubuntu3.2) ...
 Setting up pidgin (1:2.7.3-1ubuntu3.2) ...
 Setting up pidgin-libnotify (0.14-4ubuntu1) ...
 Errors were encountered while processing:
 virtualbox-ose-dkms
 Setting up virtualbox-ose-dkms (3.2.8-dfsg-2ubuntu1) ...
 Removing old virtualbox-ose-3.2.8 DKMS files...

 ------------------------------
 Deleting module version: 3.2.8
 completely from the DKMS tree.
 ------------------------------
 Done.
 Loading new virtualbox-ose-3.2.8 DKMS files...
 First Installation: checking all kernels...
 Building only for 2.6.38-4-generic
 Building initial module for 2.6.38-4-generic

 Error! Bad return status for module build on kernel: 2.6.38-4-generic (i686)
 Consult the make.log in the build directory  /var/lib/dkms/virtualbox-ose/3.2.8/build/ for more information.
 Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module> report.write(open(apport.fileutils.make_report_path(report), 'w'))
 IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-ose-
 dkms.0.crash'
 dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10



I believe this is because of missing of autoconf.h inside linux folder. Below error is there in make.log

 "/var/lib/dkms/virtualbox-ose/3.2.8/build/include/iprt/types.h:97: fatal
 error: linux/autoconf.h: No such file or directory"



 Here are the file location details:

 sathish@sathish:/var$ locate autoconf.h
 /usr/src/linux-headers-2.6.35-27-generic/include/generated/autoconf.h
 /usr/src/linux-headers-2.6.35-28-generic/include/generated/autoconf.h
 /usr/src/linux-headers-2.6.38-4-generic/include/generated/autoconf.h
 sathish@sathish:/var$ ll /usr/src/linux-
 headers-2.6.38-4-generic/include/generated/autoconf.h
 -rw-r--r-- 1 root root 167231 2011-02-17 02:00 /usr/src/linux-
 headers-2.6.38-4-generic/include/generated/autoconf.h
 sathish@sathish:/var$ ll /usr/src/linux-
 headers-2.6.35-28-generic/include/generated/autoconf.h
 -rw-r--r-- 1 root root 156490 2011-03-01 21:16 /usr/src/linux-
 headers-2.6.35-28-generic/include/generated/autoconf.h

---

### Post by d3v1150m471c on 2011-03-23
my guess would be to revert back to your old kernel. you can leave this one installed, then reboot, hold shift, select the old one at boot. then try to reinstall virtualbox. then, see if it runs with the new kernel. you may just need to run the most recent one until a new one comes out.

---

### Post by kumpsath1 on 2011-03-23
Hi,
Thanks for your reply. I tried uninstalling virtualbox from both the kernal versions. No luck.
Its not allowing to install/uninstall any applications.

---

### Post by alazou on 2011-03-29
Try removing the 2.6.38 kernel then reboot. virtualbox dkms should be removed

---

### Post by kumpsath1 on 2011-03-29
Hi,
Thanks for your reply. I tried by removing the dkms and started working fine. Thanks all for your help

```
sudo apt-get remove dkms
```

---

### Post by alazou on 2011-03-29
You need dkms so make sure you reinstall it

---

