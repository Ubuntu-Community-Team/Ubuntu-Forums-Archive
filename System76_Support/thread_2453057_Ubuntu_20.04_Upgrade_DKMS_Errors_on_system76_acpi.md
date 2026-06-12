---
title: "Ubuntu 20.04 Upgrade DKMS Errors on system76 acpi"
date: 2020-11-02
forum: System76 Support
---

### Post by never2late on 2020-11-02
This question is from my system76 Galago UltraPro which I tried to upgrade from 18.04.1. 

During the upgrade from Ubuntu 18.04.1 to 20.04.1 I received multiple  errors referring to system76 modules that encountered errors. Now when I  boot the system it appears to load, however my display remains  blank/black. The only procedure that gets to the login screen is to boot  into GRUB then select Advanced followed by Recovery Mode. I can then  resume normal boot and get to the login screen. I found the following in  the system log. it shows multiple DKMS errors. 

I tried  searching through the forums and other places, plus reinstalling the generic  5.8.0-7625 kernel using Synaptic Package Manager, with no success. 

Here is a snip from Syslog: 

```

Oct  31 18:51:42 gupnote042 AptDaemon.Worker: CRITICAL: system76-dkms:  installed system76-dkms package post-installation script subprocess  returned error exit status 10
Oct 31 18:51:42 gupnote042  org.debian.apt[9102]: 18:51:42 AptDaemon.Worker [CRITICAL]:  system76-dkms: installed system76-dkms package post-installation script  subprocess returned error exit status 10
Oct 31 18:51:45 gupnote042  AptDaemon.Worker: CRITICAL: system76-io-dkms: installed system76-io-dkms  package post-installation script subprocess returned error exit status  10
Oct 31 18:51:45 gupnote042 AptDaemon.Worker: CRITICAL: system76-driver: dependency problems - leaving unconfigured
Oct  31 18:51:45 gupnote042 org.debian.apt[9102]: 18:51:45 AptDaemon.Worker  [CRITICAL]: system76-io-dkms: installed system76-io-dkms package  post-installation script subprocess returned error exit status 10
Oct  31 18:51:45 gupnote042 org.debian.apt[9102]: 18:51:45 AptDaemon.Worker  [CRITICAL]: system76-driver: dependency problems - leaving unconfigured
Oct 31 18:51:46 gupnote042 systemd[1]: pcscd.service: Succeeded.
Oct  31 18:51:48 gupnote042 AptDaemon.Worker: CRITICAL: system76-acpi-dkms:  installed system76-acpi-dkms package post-installation script subprocess  returned error exit status 10
Oct 31 18:51:48 gupnote042  org.debian.apt[9102]: 18:51:48 AptDaemon.Worker [CRITICAL]:  system76-acpi-dkms: installed system76-acpi-dkms package  post-installation script subprocess returned error exit status 10
Oct  31 18:51:52 gupnote042 AptDaemon.Worker: CRITICAL: acpi-call-dkms:  installed acpi-call-dkms package post-installation script subprocess  returned error exit status 10
Oct 31 18:51:52 gupnote042  org.debian.apt[9102]: 18:51:52 AptDaemon.Worker [CRITICAL]:  acpi-call-dkms: installed acpi-call-dkms package post-installation  script subprocess returned error exit status 10
Oct 31 18:52:09  gupnote042 AptDaemon.Worker: CRITICAL: system76-dkms: installed  system76-dkms package post-installation script subprocess returned error  exit status 10
Oct 31 18:52:09 gupnote042 org.debian.apt[9102]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:490: Warning:  Source ID 49 was not found when attempting to remove it
Oct 31 18:52:09 gupnote042 org.debian.apt[9102]:   GLib.source_remove(id)
Oct  31 18:52:09 gupnote042 org.debian.apt[9102]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:490: Warning:  Source ID 50 was not found when attempting to remove it
Oct 31 18:52:09 gupnote042 org.debian.apt[9102]:   GLib.source_remove(id)
Oct  31 18:52:09 gupnote042 org.debian.apt[9102]: 18:52:09 AptDaemon.Worker  [CRITICAL]: system76-dkms: installed system76-dkms package  post-installation script subprocess returned error exit status 10
Oct  31 18:52:11 gupnote042 AptDaemon.Worker: CRITICAL: system76-io-dkms:  installed system76-io-dkms package post-installation script subprocess  returned error exit status 10
Oct 31 18:52:11 gupnote042 AptDaemon.Worker: CRITICAL: system76-driver: dependency problems - leaving unconfigured
Oct  31 18:52:11 gupnote042 org.debian.apt[9102]: 18:52:11 AptDaemon.Worker  [CRITICAL]: system76-io-dkms: installed system76-io-dkms package  post-installation script subprocess returned error exit status 10
Oct  31 18:52:11 gupnote042 org.debian.apt[9102]: 18:52:11 AptDaemon.Worker  [CRITICAL]: system76-driver: dependency problems - leaving unconfigured
Oct  31 18:52:14 gupnote042 AptDaemon.Worker: CRITICAL: system76-acpi-dkms:  installed system76-acpi-dkms package post-installation script subprocess  returned error exit status 10
Oct 31 18:52:14 gupnote042  org.debian.apt[9102]: 18:52:14 AptDaemon.Worker [CRITICAL]:  system76-acpi-dkms: installed system76-acpi-dkms package  post-installation script subprocess returned error exit status 10
Oct  31 18:52:16 gupnote042 AptDaemon.Worker: CRITICAL: acpi-call-dkms:  installed acpi-call-dkms package post-installation script subprocess  returned error exit status 10
Oct 31 18:52:16 gupnote042  org.debian.apt[9102]: 18:52:16 AptDaemon.Worker [CRITICAL]:  acpi-call-dkms: installed acpi-call-dkms package post-installation  script subprocess returned error exit status 10
Oct 31 18:52:22 gupnote042 wpa_supplicant[1222]: wlp3s0: WPA: Group rekeying completed with ac:86:74:41:74:eb [GTK=TKIP]
Oct  31 18:52:29 gupnote042 AptDaemon.Worker: INFO: Finished transaction  /org/debian/apt/transaction/78c57331103043f185a7fa7ce8bac38a
Oct 31  18:52:29 gupnote042 org.debian.apt[9102]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:490: Warning:  Source ID 53 was not found when attempting to remove it
Oct 31 18:52:29 gupnote042 org.debian.apt[9102]:   GLib.source_remove(id)
Oct  31 18:52:29 gupnote042 org.debian.apt[9102]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:490: Warning:  Source ID 54 was not found when attempting to remove it
Oct 31 18:52:29 gupnote042 org.debian.apt[9102]:   GLib.source_remove(id)
Oct  31 18:52:29 gupnote042 org.debian.apt[9102]: 18:52:29 AptDaemon.Worker  [INFO]: Finished transaction  /org/debian/apt/transaction/78c57331103043f185a7fa7ce8bac38a
```

When I tried to run 'sudo dpkg --configure -a' I get the following errors: 

```

$ sudo dpkg --configure -a
Setting up system76-dkms (1.0.9~1597073326~20.04~5b01933~dev) ...
Removing old system76-1.0.9~1597073326~20.04~5b01933~dev DKMS files...

------------------------------
Deleting module version: 1.0.9~1597073326~20.04~5b01933~dev
completely from the DKMS tree.
------------------------------
Done.
Loading new system76-1.0.9~1597073326~20.04~5b01933~dev DKMS files...
Building for 5.8.0-7625-generic
Building initial module for 5.8.0-7625-generic
ERROR (dkms apport): kernel package linux-headers-5.8.0-7625-generic is not supported
Error! Bad return status for module build on kernel: 5.8.0-7625-generic (x86_64)
Consult /var/lib/dkms/system76/1.0.9~1597073326~20.04~5b01933~dev/build/make.log for more information.
dpkg: error processing package system76-dkms (--configure):
 installed system76-dkms package post-installation script subprocess returned error exit status 10
Setting up system76-io-dkms (1.0.1~1559663713~19.10~ea5f61a~dev) ...
Removing old system76-io-1.0.1~1559663713~19.10~ea5f61a~dev DKMS files...

------------------------------
Deleting module version: 1.0.1~1559663713~19.10~ea5f61a~dev
completely from the DKMS tree.
------------------------------
Done.
Loading new system76-io-1.0.1~1559663713~19.10~ea5f61a~dev DKMS files...
Building for 5.8.0-7625-generic
Building initial module for 5.8.0-7625-generic
ERROR (dkms apport): kernel package linux-headers-5.8.0-7625-generic is not supported
Error! Bad return status for module build on kernel: 5.8.0-7625-generic (x86_64)
Consult /var/lib/dkms/system76-io/1.0.1~1559663713~19.10~ea5f61a~dev/build/make.log for more information.
dpkg: error processing package system76-io-dkms (--configure):
 installed system76-io-dkms package post-installation script subprocess returned error exit status 10
Setting up system76-acpi-dkms (1.0.2~1600812457~20.04~0bc966c~dev) ...
Removing old system76_acpi-1.0.2~1600812457~20.04~0bc966c~dev DKMS files...

------------------------------
Deleting module version: 1.0.2~1600812457~20.04~0bc966c~dev
completely from the DKMS tree.
------------------------------
Done.
Loading new system76_acpi-1.0.2~1600812457~20.04~0bc966c~dev DKMS files...
Building for 5.8.0-7625-generic
Building initial module for 5.8.0-7625-generic
ERROR (dkms apport): kernel package linux-headers-5.8.0-7625-generic is not supported
Error! Bad return status for module build on kernel: 5.8.0-7625-generic (x86_64)
Consult /var/lib/dkms/system76_acpi/1.0.2~1600812457~20.04~0bc966c~dev/build/make.log for more information.
dpkg: error processing package system76-acpi-dkms (--configure):
 installed system76-acpi-dkms package post-installation script subprocess returned error exit status 10
Setting up acpi-call-dkms (1.1.0-5) ...
Removing old acpi-call-1.1.0 DKMS files...

------------------------------
Deleting module version: 1.1.0
completely from the DKMS tree.
------------------------------
Done.
Loading new acpi-call-1.1.0 DKMS files...
Building for 5.8.0-7625-generic
Building initial module for 5.8.0-7625-generic
ERROR (dkms apport): kernel package linux-headers-5.8.0-7625-generic is not supported
Error! Bad return status for module build on kernel: 5.8.0-7625-generic (x86_64)
Consult /var/lib/dkms/acpi-call/1.1.0/build/make.log for more information.
dpkg: error processing package acpi-call-dkms (--configure):
 installed acpi-call-dkms package post-installation script subprocess returned error exit status 10
Processing triggers for initramfs-tools (0.136ubuntu6.3) ...
update-initramfs: Generating /boot/initrd.img-5.8.0-7625-generic
Errors were encountered while processing:
 system76-dkms
 system76-io-dkms
 system76-acpi-dkms
 acpi-call-dkms

```

And finally the output in from /var/lib/dkms/system76/1.0.9~1597073326~20.04~5b01933-dev for kernel 5.8.0-7625-generic (x86_64):

```
*******
DKMS make.log for system76-1.0.9~1597073326~20.04~5b01933~dev for kernel 5.8.0-7625-generic (x86_64)
Mon 02 Nov 2020 03:49:09 PM EST
make: Entering directory '/usr/src/linux-headers-5.8.0-7625-generic'

  ERROR: Kernel configuration is invalid.
         include/generated/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

make: *** [Makefile:746: include/config/auto.conf] Error 1
make: Leaving directory '/usr/src/linux-headers-5.8.0-7625-generic'

********
```

---

### Post by QIII on 2020-11-02
Hello.

Please use code tags to encapsulate terminal commands and their results.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

Is this Pop_OS! by chance?

---

### Post by never2late on 2020-11-02
Thanks QIII for the posting guidance. I went to read the Forum Posting Guidelines as a reminder. 

As for the problem, this is straight Ubuntu, not Pop_OS.

---

### Post by stevesonoa on 2020-11-12
I'm having the same error, and I'm on a System76 machine running straight Ubuntu. Very interested in a solution. My additional monitors were working normally 2 days ago; today they're not detected. I've tried several solutions from other threads without any success, including:

* Disabling secure boot
* Reinstalling nvidia drivers from the terminal
* Reinstalling nvidia drivers from their website
* Reinstalling nvidia drivers from the Ubuntu Software & Updates app
* Removing options nvidia-drm modeset=1 from the prime-select configuration

No matter what I do, my monitors are still not detected in settings, nor do they display anything. When I run nvidia-settings, I receive the following output:

```

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system

```

---

