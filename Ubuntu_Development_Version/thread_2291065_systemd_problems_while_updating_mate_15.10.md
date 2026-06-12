---
title: "systemd problems while updating mate 15.10"
date: 2015-08-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-08-17
Have some major problems with mate while upgrading an install.

```

Setting up util-linux (2.26.2-6ubuntu3) ...
Setting up systemd (224-1ubuntu3) ...
Installing new version of config file /etc/dbus-1/system.d/org.freedesktop.login1.conf ...
Installing new version of config file /etc/dbus-1/system.d/org.freedesktop.machine1.conf ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
addgroup: The group `systemd-journal-remote' already exists as a system group. Exiting.
(Reading database ... 343576 files and directories currently installed.)
Preparing to unpack .../bluez_5.33-0ubuntu4_amd64.deb ...
Unpacking bluez (5.33-0ubuntu4) over (4.101-0ubuntu25) ...
Preparing to unpack .../brltty-x11_5.2~20141018-4ubuntu4_amd64.deb ...
Unpacking brltty-x11 (5.2~20141018-4ubuntu4) over (5.2~20141018-4ubuntu1) ...
Preparing to unpack .../brltty_5.2~20141018-4ubuntu4_amd64.deb ...
Unpacking brltty (5.2~20141018-4ubuntu4) over (5.2~20141018-4ubuntu1) ...
Preparing to unpack .../libudev1_224-1ubuntu3_amd64.deb ...
Unpacking libudev1:amd64 (224-1ubuntu3) over (220-7ubuntu2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up libudev1:amd64 (224-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 343537 files and directories currently installed.)
Preparing to unpack .../udev_224-1ubuntu3_amd64.deb ...
Unpacking udev (224-1ubuntu3) over (220-7ubuntu2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up udev (224-1ubuntu3) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
dpkg: dependency problems prevent processing triggers for dbus:
 dbus depends on libexpat1 (>= 2.0.1); however:
  Package libexpat1:amd64 is not configured yet.

dpkg: error processing archive /var/cache/apt/archives/systemd-sysv_224-1ubuntu3_amd64.deb (--unpack):
 dependency problems - leaving triggers unprocessed
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-asus-mate-test:~$ 

```

```
ventrical@ventrical-asus-mate-test:~$ inxi -Fxz
System:    Host: ventrical-asus-mate-test Kernel: 3.19.0-22-generic x86_64 (64 bit gcc: 4.9.2)
           Desktop: Gnome  (Gtk 3.16.4-2ubuntu1) Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 16021
           clock speeds: max: 4005 MHz 1: 4005 MHz 2: 4005 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1440x900@59.9hz
           GLX Renderer: GeForce 210/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 304.125 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k3.19.0-22-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (11.2% used)
           ID-1: /dev/sda model: WDC_WD800JD size: 80.0GB
Partition: ID-1: / size: 72G used: 6.5G (10%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 43.0C mobo: 35.0C gpu: 0.0:36C
           Fan Speeds (in rpm): cpu: 4272 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 168 Uptime: 1:06 Memory: 679.5/2000.3MB
           Init: systemd runlevel: 5 Gcc sys: 4.9.2
           Client: Shell (bash 4.3.301) inxi: 2.2.16 
ventrical@ventrical-asus-mate-test:~$ 

```

will restart and see what happens.

---

### Post by ventrical on 2015-08-17
Tried to fix with this first but no go.

```

ventrical@ventrical-asus-mate-test:~$ sudo dpkg --configure -a
[sudo] password for ventrical: 
Setting up libquadmath0:amd64 (5.2.1-15ubuntu1) ...
Setting up libgomp1:amd64 (5.2.1-15ubuntu1) ...
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libmwaw-0.3-3v5; however:
  Package libmwaw-0.3-3v5 is not installed.
 libreoffice-draw depends on libodfgen-0.1-1v5; however:
  Package libodfgen-0.1-1v5 is not installed.

dpkg: error processing package libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
Setting up libatomic1:amd64 (5.2.1-15ubuntu1) ...
Setting up libicu55:amd64 (55.1-4) ...
Setting up libexpat1:amd64 (2.1.0-7) ...
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libabw-0.1-1v5; however:
  Package libabw-0.1-1v5 is not installed.
 libreoffice-writer depends on libmwaw-0.3-3v5; however:
  Package libmwaw-0.3-3v5 is not installed.
 libreoffice-writer depends on libodfgen-0.1-1v5; however:
  Package libodfgen-0.1-1v5 is not installed.
 libreoffice-writer depends on libwpd-0.10-10v5; however:
  Package libwpd-0.10-10v5 is not installed.
 libreoffice-writer depends on libwps-0.4-4v5; however:
  Package libwps-0.4-4v5 is not installed.

dpkg: error processing package libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
Setting up xserver-common (2:1.17.2-1ubuntu3) ...
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-draw (= 1:4.4.4~rc3-0ubuntu2); however:
  Package libreoffice-draw is not configured yet.
 libreoffice-impress depends on libmwaw-0.3-3v5; however:
  Package libmwaw-0.3-3v5 is not installed.
 libreoffice-impress depends on libodfgen-0.1-1v5; however:
  Package libodfgen-0.1-1v5 is not installed.

dpkg: error processing package libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
Setting up libcilkrts5:amd64 (5.2.1-15ubuntu1) ...
Setting up libelf1:amd64 (0.163-4ubuntu1) ...
Setting up libubsan0:amd64 (5.2.1-15ubuntu1) ...
Setting up libtsan0:amd64 (5.2.1-15ubuntu1) ...
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libclucene-contribs1v5 (>= 2.3.3.4); however:
  Package libclucene-contribs1v5 is not installed.
 libreoffice-core depends on libclucene-core1v5 (>= 2.3.3.4); however:
  Package libclucene-core1v5 is not installed.
 libreoffice-core depends on libcmis-0.5-5v5; however:
  Package libcmis-0.5-5v5 is not installed.
 libreoffice-core depends on libhunspell-1.3-0v5 (>= 1.3.3); however:
  Package libhunspell-1.3-0v5 is not installed.

dpkg: error processing package libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:4.4.4~rc3-0ubuntu2); however:
  Package libreoffice-core is not configured yet.
 libreoffice-calc depends on libboost-iostreams1.58.0; however:
  Package libboost-iostreams1.58.0 is not installed.
 libreoffice-calc depends on libboost-system1.58.0; however:
  Package libboost-system1.58.0 is not installed.
 libreoffice-calc depends on libmwaw-0.3-3v5; however:
  Package libmwaw-0.3-3v5 is not installed.
 libreoffice-calc depends on libodfgen-0.1-1v5; however:
  Package libodfgen-0.1-1v5 is not installed.
 libreoffice-calc depends on libwps-0.4-4v5; however:
  Package libwps-0.4-4v5 is not installed.

dpkg: error processing package libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Setting up libreoffice-style-human (1:4.4.4~rc3-0ubuntu2) ...
Setting up libdrm2:amd64 (2.4.63-1) ...
Setting up liblsan0:amd64 (5.2.1-15ubuntu1) ...
Setting up libglib2.0-data (2.45.4-2) ...
dpkg: dependency problems prevent configuration of libwayland-egl1-mesa:amd64:
 libwayland-egl1-mesa:amd64 depends on libegl1-mesa (= 10.6.3-1ubuntu1); however:
  Version of libegl1-mesa:amd64 on system is 10.5.7-1ubuntu1.

dpkg: error processing package libwayland-egl1-mesa:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libcdr-0.1-1v5 (0.1.1-2ubuntu1) ...
Setting up libpcre16-3:amd64 (2:8.35-7ubuntu5) ...
Setting up brltty (5.2~20141018-4ubuntu4) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Setting up libpoppler52:amd64 (0.33.0-0ubuntu3) ...
Setting up uno-libs3 (4.4.4~rc3-0ubuntu2) ...
Setting up bluez (5.33-0ubuntu4) ...
Installing new version of config file /etc/bluetooth/input.conf ...
Installing new version of config file /etc/bluetooth/main.conf ...
Installing new version of config file /etc/dbus-1/system.d/bluetooth.conf ...
Installing new version of config file /etc/init.d/bluetooth ...
Installing new version of config file /etc/init/bluetooth.conf ...
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.45.4-2); however:
  Version of libglib2.0-0:amd64 on system is 2.45.2-1.

dpkg: error processing package libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
Setting up ure (4.4.4~rc3-0ubuntu2) ...
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:4.4.4~rc3-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up libitm1:amd64 (5.2.1-15ubuntu1) ...
dpkg: dependency problems prevent configuration of libreoffice-pdfimport:
 libreoffice-pdfimport depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-pdfimport (--configure):
 dependency problems - leaving unconfigured
Setting up lib32gcc1 (1:5.2.1-15ubuntu1) ...
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:4.4.4~rc3-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up libqt5core5a:amd64 (5.4.2+dfsg-2ubuntu3) ...
Setting up brltty-x11 (5.2~20141018-4ubuntu4) ...
dpkg: dependency problems prevent configuration of libreoffice-ogltrans:
 libreoffice-ogltrans depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-ogltrans depends on libreoffice-impress; however:
  Package libreoffice-impress is not configured yet.

dpkg: error processing package libreoffice-ogltrans (--configure):
 dependency problems - leaving unconfigured
Setting up libqt5dbus5:amd64 (5.4.2+dfsg-2ubuntu3) ...
Setting up libpam-systemd:amd64 (224-1ubuntu3) ...
Setting up libreoffice-common (1:4.4.4~rc3-0ubuntu2) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.4.4~rc3-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:4.4.4~rc3-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
Setting up libqt5xml5:amd64 (5.4.2+dfsg-2ubuntu3) ...
Setting up libaccounts-qt5-1:amd64 (1.13+14.10.20140819.1-0ubuntu4~gcc5.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
dpkg: warning: --compare-versions used with obsolete relation operator '>'
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 libreoffice-draw
 libreoffice-writer
 libreoffice-impress
 libreoffice-core
 libreoffice-calc
 libwayland-egl1-mesa:amd64
 libglib2.0-bin
 libreoffice-gnome
 libreoffice-pdfimport
 libreoffice-gtk
 libreoffice-ogltrans
 libreoffice-math
 libreoffice-base-core
ventrical@ventrical-asus-mate-test:~$ 

```

---

### Post by QDR06VV9 on 2015-08-17
Hey Vent I was having some problems as of Thursday and Friday I had to bounce back and forth on the servers.
One Day the main sever was good then the following day I had to change again?:confused:
Bucky Ball was having troubles with getting complete updates also (Due to bad sigs), with the Australian Severs it looked like in the General Forums.
But hey it was a little excitement though:D But I still get a few Bad Sigs warnings on Wily
Oh and I am still not using systemd but upstart.
I am all ready for some of that good old Honey you been camping on though.[IMG]http://orig00.deviantart.net/701c/f/2012/224/9/b/bee_avatar_by_kezzi_rose-d1moks5.gif[/IMG]
Kind Regards

---

### Post by ventrical on 2015-08-17
Seems to have fixed itself with 

```

sudo apt-get dist-upgrade -f

```

---

### Post by dino99 on 2015-08-17
Wonder about what have pushed it; i got it while upgrading systemd  [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1480122](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1480122)
Also not seen it since; waiting a week or so before closing it.

---

### Post by ventrical on 2015-08-17
No ... not fixed!!
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1485703](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1485703)

---

### Post by ventrical on 2015-08-17
> **dino99 said:**
> Wonder about what have pushed it; i got it while upgrading systemd  [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1480122](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1480122)
Also not seen it since; waiting a week or so before closing it.

Confirmed your bug. Please confirm mine.

Regards..

---

### Post by ventrical on 2015-08-17
> **runrickus said:**
> Hey Vent I was having some problems as of Thursday and Friday I had to bounce back and forth on the servers.
One Day the main sever was good then the following day I had to change again?:confused:
Bucky Ball was having troubles with getting complete updates also (Due to bad sigs), with the Australian Severs it looked like in the General Forums.
But hey it was a little excitement though:D But I still get a few Bad Sigs warnings on Wily
Oh and I am still not using systemd but upstart.
I am all ready for some of that good old Honey you been camping on though.[IMG]http://orig00.deviantart.net/701c/f/2012/224/9/b/bee_avatar_by_kezzi_rose-d1moks5.gif[/IMG]
Kind Regards

Thanks ! I did'nt think that there would be  big systemd probs like this.  But I guess there is. .. and I can always use upstart for compare :)  I also  thought it might be due to having the libwayland /ppa installed.

We have had a drought up here for a couple of weeks and so the bees are slow to make hunny :)

Regards..

---

### Post by dino99 on 2015-08-17
> **ventrical said:**
> No ... not fixed!!
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1485703](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1485703)

here is your dpkg error:
********
dpkg: dependency problems prevent processing triggers for dbus:
 dbus depends on libexpat1 (>= 2.0.1); however:
  Package libexpat1:amd64 is not configured yet.

dpkg: error processing archive /var/cache/apt/archives/systemd-sysv_224-1ubuntu3_amd64.deb (--unpack):
 dependency problems - leaving triggers unprocessed
************

[PHP]if you reinstall systemd, do you still get that error ?[/PHP]

my system is a 32 bits installation, and i've not got that issue as you got (mine was only the ">" warning; but the upgrade was done completly)
maybe it was only the 64 deb package with your issue.
note that libexpat1 is a dependency of many packages

---

### Post by ventrical on 2015-08-17
> **dino99 said:**
> here is your dpkg error:
********
dpkg: dependency problems prevent processing triggers for dbus:
 dbus depends on libexpat1 (>= 2.0.1); however:
  Package libexpat1:amd64 is not configured yet.

dpkg: error processing archive /var/cache/apt/archives/systemd-sysv_224-1ubuntu3_amd64.deb (--unpack):
 dependency problems - leaving triggers unprocessed
************

[PHP]if you reinstall systemd, do you still get that error ?[/PHP]

my system is a 32 bits installation, and i've not got that issue as you got (mine was only the ">" warning; but the upgrade was done completly)
maybe it was only the 64 deb package with your issue.
note that libexpat1 is a dependency of many packages

The error is gone  after-
```

sudo apt-get dist-upgrade -f

```

but apport automatically reported the bug.

 I am having a lot of problems with ubuntu-gnome and ubuntu-mate  both using systemd and upstart on slightly older machines (circa 2005/6 and earlier). There are a lot of APCI errors and fsck errors on boot up .. and these are on good drives. I do not have the problem on other older HP machines and newer machines. I experiment with nVidia but prefer to use nouveau. Simply .. this cycle has been very touchy about hybrid form factors. I would fair better if I used the alternate method of install. Also ubuntu-mate is very touchy when installing other desktops like gnome-metacity and gnome-flashback compiz. I think also there was most likely an early compiz bug that can only be rectified by a fresh install of those two distributions.

Regards..

---

### Post by dino99 on 2015-08-18
I too have lot of ACPI errors, but they started with the kernels 3 family. The Linus team still have some work about that, but i've recently read they are working on rewritting some old part of code, mainly moving from asm to c++ as languages have different capabilities nowadays.
About compiz, on ubuntu with gnome-shell (unity fully purged) i've also purged it (does not see what compiz really do than gnome does not)
The fsck errors have been seen some times ago on ubu and i remember having read some changelogs to fix them (does not remember which of initramfs/systemd/... it was)

---

### Post by dino99 on 2015-08-18
> **ventrical said:**
> No ... not fixed!!
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1485703](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1485703)


Seems to be the faulty lib upgrade in your case
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1485970](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1485970)

---

### Post by ventrical on 2015-08-18
> **dino99 said:**
> Seems to be the faulty lib upgrade in your case
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1485970](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1485970)

I see.  Also .. I was surprised to see that command:

```

sudo apt-get dist-upgrade -f

```

be presented as a fix by apt (which btw solved the verbose report  problem) but has left mate-DE in shambles. I have mate working on other machines just fine.

---

