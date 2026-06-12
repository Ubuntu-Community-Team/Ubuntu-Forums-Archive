---
title: "Nvidia 418.56 upgrade error on 18.04 System76"
date: 2019-07-15
forum: System76 Support
---

### Post by bdlabitt on 2019-07-15
This seems like it might belong here?  If I am cross-posting and broken a rule, please let me know.
[https://ubuntuforums.org/showthread.php?t=2422905](https://ubuntuforums.org/showthread.php?t=2422905)

I am trying to install nvidia-driver-418 on my Bonobo6X.  It appears that the driver installation is hanging on an issue with nvidia-340.
```
Preparing to unpack .../libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb (--unpack):
 new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2
```

Have any idea how to fix this?  It's like I am missing a necessary package. It seems the package manager is not calling in all the dependencies.  I've got two System76 ppas enabled.   (LP-PPA-system76-dev-stable/bionic and LP-PPA-system76-dev-stable/now) 

 Currently running nouveau, would like to run a more advanced nvidia driver.   If I install from the package system76-driver-nvidia I get a package failure, similar to installing the nvidia driver alone. ```
E: /tmp/apt-dpkg-install-ZYu6jJ/10-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb: new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2E: /tmp/apt-dpkg-install-ZYu6jJ/11-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb: new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2

```  Here are the details: ```
Selecting previously unselected package libnvidia-cfg1-418:amd64.(Reading database ... 965927 files and directories currently installed.)
Preparing to unpack .../00-libnvidia-cfg1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-cfg1-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-common-418.
Preparing to unpack .../01-libnvidia-common-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_all.deb ...
Unpacking libnvidia-common-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-decode-418:i386.
Preparing to unpack .../02-libnvidia-decode-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
Unpacking libnvidia-decode-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-compute-418:i386.
Preparing to unpack .../03-libnvidia-compute-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
Unpacking libnvidia-compute-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-decode-418:amd64.
Preparing to unpack .../04-libnvidia-decode-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-decode-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-compute-418:amd64.
Preparing to unpack .../05-libnvidia-compute-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-compute-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-encode-418:amd64.
Preparing to unpack .../06-libnvidia-encode-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-encode-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-encode-418:i386.
Preparing to unpack .../07-libnvidia-encode-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
Unpacking libnvidia-encode-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-fbc1-418:amd64.
Preparing to unpack .../08-libnvidia-fbc1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-fbc1-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-fbc1-418:i386.
Preparing to unpack .../09-libnvidia-fbc1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
Unpacking libnvidia-fbc1-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Preparing to unpack .../10-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /tmp/apt-dpkg-install-ZYu6jJ/10-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb (--unpack):
 new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../11-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /tmp/apt-dpkg-install-ZYu6jJ/11-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb (--unpack):
 new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2
Selecting previously unselected package libnvidia-ifr1-418:amd64.
Preparing to unpack .../12-libnvidia-ifr1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-ifr1-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-ifr1-418:i386.
Preparing to unpack .../13-libnvidia-ifr1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
Unpacking libnvidia-ifr1-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libxnvctrl0:amd64.
Preparing to unpack .../14-libxnvctrl0_390.77-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libxnvctrl0:amd64 (390.77-0ubuntu0.18.04.1) ...
Selecting previously unselected package nvidia-compute-utils-418.
Preparing to unpack .../15-nvidia-compute-utils-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-compute-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-kernel-source-418.
Preparing to unpack .../16-nvidia-kernel-source-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-kernel-source-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-kernel-common-418.
Preparing to unpack .../17-nvidia-kernel-common-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-kernel-common-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-dkms-418.
Preparing to unpack .../18-nvidia-dkms-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-dkms-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-utils-418.
Preparing to unpack .../19-nvidia-utils-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package xserver-xorg-video-nvidia-418.
Preparing to unpack .../20-xserver-xorg-video-nvidia-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking xserver-xorg-video-nvidia-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-driver-418.
Preparing to unpack .../21-nvidia-driver-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-driver-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../22-nvidia-settings_390.77-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Selecting previously unselected package system76-driver-nvidia.
Preparing to unpack .../23-system76-driver-nvidia_19.04.9~1562611617~18.04~7371c95~dev_all.deb ...
Unpacking system76-driver-nvidia (19.04.9~1562611617~18.04~7371c95~dev) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-ZYu6jJ/10-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb
 /tmp/apt-dpkg-install-ZYu6jJ/11-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libnvidia-fbc1-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up libnvidia-fbc1-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up libnvidia-common-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up nvidia-kernel-source-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
dpkg: dependency problems prevent configuration of nvidia-driver-418:
 nvidia-driver-418 depends on libnvidia-gl-418 (= 418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev); however:
  Package libnvidia-gl-418:amd64 is not installed.


dpkg: error processing package nvidia-driver-418 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-kernel-common-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libnvidia-cfg1-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Setting up nvidia-dkms-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-oryp3-b
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-bonw11
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-serw10
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-oryp2
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-oryp3-ess
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-oryp2-ess
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/system76-nvidia-quirks-oryp3
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-418.56 DKMS files...
Building for 5.0.0-21-generic
Building for architecture x86_64
Building initial module for 5.0.0-21-generic
Done.


nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


depmod...


DKMS: install completed.
dpkg: dependency problems prevent configuration of libnvidia-ifr1-418:amd64:
 libnvidia-ifr1-418:amd64 depends on libnvidia-gl-418; however:
  Package libnvidia-gl-418:amd64 is not installed.


dpkg: error processing package libnvidia-ifr1-418:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-418:i386:
 libnvidia-ifr1-418:i386 depends on libnvidia-gl-418; however:
  Package libnvidia-gl-418:i386 is not installed.


dpkg: error processing package libnvidia-ifr1-418:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up libxnvctrl0:amd64 (390.77-0ubuntu0.18.04.1) ...
Setting up xserver-xorg-video-nvidia-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
dpkg: dependency problems prevent configuration of system76-driver-nvidia:
 system76-driver-nvidia depends on nvidia-driver-418; however:
  Package nvidia-driver-418 is not configured yet.


dpkg: error processing package system76-driver-nvidia (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Setting up libnvidia-compute-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up libnvidia-compute-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up nvidia-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up nvidia-compute-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Warning: The home dir /nonexistent you specified can't be accessed: No such file or directory
Adding system user `nvidia-persistenced' (UID 117) ...
Adding new group `nvidia-persistenced' (GID 127) ...
Adding new user `nvidia-persistenced' (UID 117) with group `nvidia-persistenced' ...
Not creating home directory `/nonexistent'.
Setting up libnvidia-decode-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up libnvidia-decode-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up libnvidia-encode-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up libnvidia-encode-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-21-generic
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 nvidia-driver-418
 libnvidia-ifr1-418:amd64
 libnvidia-ifr1-418:i386
 system76-driver-nvidia



```
How to fix this?  After this installation apt reports a broken system.  apt --fix-broken install does not fix the problem.

---

### Post by bdlabitt on 2019-07-15
After mucking about in synaptic, the broken installation is fixed.  Still can't install latest System76 nvidia drivers.  Package seems to be broken.  If I install nvidia-340, (successfully) system76-driver-nvidia still has dependency issues and will not install.

---

### Post by Bashing-om on 2019-07-15
bdlabitt; Hello -

As a thought - Maybe System76 has not caught up yet ?
See: [https://www.forbes.com/sites/jasonevangelho/2019/07/12/ubuntu-executes-another-massive-change-to-the-way-it-updates-proprietary-nvidia-drivers/#53e1c8177aa8](https://www.forbes.com/sites/jasonevangelho/2019/07/12/ubuntu-executes-another-massive-change-to-the-way-it-updates-proprietary-nvidia-drivers/#53e1c8177aa8)

-maybe so -

---

### Post by bdlabitt on 2019-07-15
I just read that the other day.  It can't come soon enough.  Video drivers have always been exciting under linux.  

I could do without the excitement, all I want is for it to just work.  That way I can get on with my real work, not debugging video setups.

---

### Post by Bashing-om on 2019-07-15
bdlabitt; Yup !

Totally agree - 
Here lately Nvidia proprietary driver has been a real pain for me also. I am glad to see the effort for support moved to our repo :)
And for me now it "just works".

[INDENT]it only gets better :)
[/INDENT]

---

### Post by bdlabitt on 2019-07-15
[Solved]  Purged all Nvidia.  Used ```
[COLOR=#000000][FONT=&amp]$ sudo apt-get install system76-driver-nvidia[/FONT][/COLOR]
``` Problem fixed.  Curiously, just selecting the same named package in Synaptic did not work.  Using synaptic to install system-drive-nvidia resulted in a broken package manager.

---

### Post by Bashing-om on 2019-07-16
bdlabitt; Great -

Good to know,
Please mark this thread solved - from the thread tools;

aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

