---
title: "Kernel 5.4RC (Release Candidate) series"
date: 2019-10-08
forum: Ubuntu Development Version
---

### Post by Doug S on 2019-10-08
Kernel 5.4-rc2 is available from the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc2/") or [kernel.org]("https://www.kernel.org/").

We have a running thread during each mainline kernel release cycle.

Previous cycle threads:
[5.3]("https://ubuntuforums.org/showthread.php?t=2423441")
[5.2]("https://ubuntuforums.org/showthread.php?t=2419363")
[5.1]("https://ubuntuforums.org/showthread.php?t=2414938")
[5.0]("https://ubuntuforums.org/showthread.php?t=2409811")
[4.20]("https://ubuntuforums.org/showthread.php?t=2405365")
4.19 ?
[4.18]("https://ubuntuforums.org/showthread.php?t=2394500")
[4.17]("https://ubuntuforums.org/showthread.php?t=2389561")
[4.16]("https://ubuntuforums.org/showthread.php?t=2384781")
[4.15]("https://ubuntuforums.org/showthread.php?t=2378956")
[4.14]("https://ubuntuforums.org/showthread.php?t=2371638")

Incremental kernel compiles are taking longer than they should, by a factor of between 2 and 4 times slower. It seems as though something has become overzealous when deciding which files need to be recompiled if only one file (drivers/cpuidle/governors/teo.c, in my case) is touched. I don't know when I'll have time to investigate.

Otherwise I have been using kernel 5.4-rc1 extensively for a week without issues. Switching to -rc2 now.

---

### Post by corradoventu on 2019-10-10
zfs modules install failed on Ubuntu 19.10 with Kernel 5.4RC2. 
zfs modules installed ok on Ubuntu 19.10 with Kernel 5.3.0-13 - same hardware, different partition, both installed from Ubuntu 19.10 "Eoan Ermine" - Beta amd64 (20191006).
should I report a problem? how can I do?

from unattended-upgrades-dpkg.log:
```
Log started: 2019-10-10  08:46:37
(Reading database ... 
(Reading database ... 5%
....
(Reading database ... 100%
(Reading database ... 187119 files and directories currently installed.)
Preparing to unpack .../python3-apport_2.20.11-0ubuntu8_all.deb ...
Unpacking python3-apport (2.20.11-0ubuntu8) over (2.20.11-0ubuntu7) ...
Preparing to unpack .../apport-gtk_2.20.11-0ubuntu8_all.deb ...
Unpacking apport-gtk (2.20.11-0ubuntu8) over (2.20.11-0ubuntu7) ...
Setting up python3-apport (2.20.11-0ubuntu8) ...
Setting up zfsutils-linux (0.8.1-1ubuntu13) ...
zfs-import-scan.service is a disabled or a static unit not running, not starting it.
A dependency job for zfs-import-cache.service failed. See 'journalctl -xe' for details.
Job for zfs-load-module.service failed because the control process exited with error code.
See "systemctl status zfs-load-module.service" and "journalctl -xe" for details.
Job for zfs-mount.service failed because the control process exited with error code.
See "systemctl status zfs-mount.service" and "journalctl -xe" for details.
invoke-rc.d: initscript zfs-mount, action "restart" failed.
&#9679; zfs-mount.service - Mount ZFS filesystems
   Loaded: loaded (/lib/systemd/system/zfs-mount.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2019-10-10 08:46:43 CEST; 9ms ago
     Docs: man:zfs(8)
  Process: 4179 ExecStart=/sbin/zfs mount -a (code=exited, status=1/FAILURE)
 Main PID: 4179 (code=exited, status=1/FAILURE)

ott 10 08:46:43 corrado-p9-ee-1006 systemd[1]: Starting Mount ZFS filesystems...
ott 10 08:46:43 corrado-p9-ee-1006 zfs[4179]: The ZFS modules are not loaded.
ott 10 08:46:43 corrado-p9-ee-1006 zfs[4179]: Try running '/sbin/modprobe zfs' as root to load them.
ott 10 08:46:43 corrado-p9-ee-1006 systemd[1]: zfs-mount.service: Main process exited, code=exited, status=1/FAILURE
ott 10 08:46:43 corrado-p9-ee-1006 systemd[1]: zfs-mount.service: Failed with result 'exit-code'.
ott 10 08:46:43 corrado-p9-ee-1006 systemd[1]: Failed to start Mount ZFS filesystems.
dpkg: error processing package zfsutils-linux (--configure):
 installed zfsutils-linux package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of zfs-initramfs:
 zfs-initramfs depends on zfsutils-linux (>= 0.8.1-1ubuntu13); however:
  Package zfsutils-linux is not configured yet.

dpkg: error processing package zfs-initramfs (--configure):
 dependency problems - leaving unconfigured
Setting up apport-gtk (2.20.11-0ubuntu8) ...
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of zfs-zed:
 zfs-zed depends on zfsutils-linux (>= 0.8.1-1ubuntu13); however:
  Package zfsutils-linux is not configured yet.

dpkg: error processing package zfs-zed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Errors were encountered while processing:
 zfsutils-linux
 zfs-initramfs
 zfs-zed
Log ended: 2019-10-10  08:46:44

```

same with upgrade from terminal: 
```
corrado@corrado-p9-ee-1006:~$ sudo apt update && sudo apt upgrade
Hit:1 http://archive.ubuntu.com/ubuntu eoan InRelease
Hit:2 http://archive.ubuntu.com/ubuntu eoan-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu eoan-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu eoan-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
10 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  command-not-found-data
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  apport gnome-shell gnome-shell-common libplymouth4 plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text ppp python3-problem-report
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1.696 kB of archives.
After this operation, 3.072 B of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 187119 files and directories currently installed.)
Preparing to unpack .../0-libplymouth4_0.9.4git20190712-0ubuntu4_amd64.deb ...
Unpacking libplymouth4:amd64 (0.9.4git20190712-0ubuntu4) over (0.9.4git20190712-0ubuntu3) ...
Preparing to unpack .../1-plymouth-theme-ubuntu-logo_0.9.4git20190712-0ubuntu4_amd64.deb ...
Unpacking plymouth-theme-ubuntu-logo (0.9.4git20190712-0ubuntu4) over (0.9.4git20190712-0ubuntu3) ...
Preparing to unpack .../2-plymouth-label_0.9.4git20190712-0ubuntu4_amd64.deb ...
Unpacking plymouth-label (0.9.4git20190712-0ubuntu4) over (0.9.4git20190712-0ubuntu3) ...
Preparing to unpack .../3-plymouth-theme-ubuntu-text_0.9.4git20190712-0ubuntu4_amd64.deb ...
Unpacking plymouth-theme-ubuntu-text (0.9.4git20190712-0ubuntu4) over (0.9.4git20190712-0ubuntu3) ...
Preparing to unpack .../4-plymouth_0.9.4git20190712-0ubuntu4_amd64.deb ...
Unpacking plymouth (0.9.4git20190712-0ubuntu4) over (0.9.4git20190712-0ubuntu3) ...
Preparing to unpack .../5-apport_2.20.11-0ubuntu8_all.deb ...
Unpacking apport (2.20.11-0ubuntu8) over (2.20.11-0ubuntu7) ...
Preparing to unpack .../6-gnome-shell_3.34.1-1ubuntu1_amd64.deb ...
Unpacking gnome-shell (3.34.1-1ubuntu1) over (3.34.0-1ubuntu1) ...
Preparing to unpack .../7-gnome-shell-common_3.34.1-1ubuntu1_all.deb ...
Unpacking gnome-shell-common (3.34.1-1ubuntu1) over (3.34.0-1ubuntu1) ...
Preparing to unpack .../8-ppp_2.4.7-2+4.1ubuntu4_amd64.deb ...
Unpacking ppp (2.4.7-2+4.1ubuntu4) over (2.4.7-2+4.1ubuntu3) ...
Preparing to unpack .../9-python3-problem-report_2.20.11-0ubuntu8_all.deb ...
Unpacking python3-problem-report (2.20.11-0ubuntu8) over (2.20.11-0ubuntu7) ...
Setting up python3-problem-report (2.20.11-0ubuntu8) ...
Setting up gnome-shell-common (3.34.1-1ubuntu1) ...
Setting up apport (2.20.11-0ubuntu8) ...
Installing new version of config file /etc/apport/crashdb.conf ...
apport-autoreport.service is a disabled or a static unit, not starting it.
Setting up zfsutils-linux (0.8.1-1ubuntu13) ...
zfs-import-scan.service is a disabled or a static unit not running, not starting it.
A dependency job for zfs-import-cache.service failed. See 'journalctl -xe' for details.
Job for zfs-load-module.service failed because the control process exited with error code.
See "systemctl status zfs-load-module.service" and "journalctl -xe" for details.
Job for zfs-mount.service failed because the control process exited with error code.
See "systemctl status zfs-mount.service" and "journalctl -xe" for details.
invoke-rc.d: initscript zfs-mount, action "restart" failed.
&#9679; zfs-mount.service - Mount ZFS filesystems
   Loaded: loaded (/lib/systemd/system/zfs-mount.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2019-10-10 08:50:00 CEST; 7ms ago
     Docs: man:zfs(8)
  Process: 5403 ExecStart=/sbin/zfs mount -a (code=exited, status=1/FAILURE)
 Main PID: 5403 (code=exited, status=1/FAILURE)

ott 10 08:50:00 corrado-p9-ee-1006 systemd[1]: Starting Mount ZFS filesystems...
ott 10 08:50:00 corrado-p9-ee-1006 zfs[5403]: The ZFS modules are not loaded.
ott 10 08:50:00 corrado-p9-ee-1006 zfs[5403]: Try running '/sbin/modprobe zfs' as root to load them.
ott 10 08:50:00 corrado-p9-ee-1006 systemd[1]: zfs-mount.service: Main process exited, code=exited, status=1/FAI
LURE
ott 10 08:50:00 corrado-p9-ee-1006 systemd[1]: zfs-mount.service: Failed with result 'exit-code'.
ott 10 08:50:00 corrado-p9-ee-1006 systemd[1]: Failed to start Mount ZFS filesystems.
dpkg: error processing package zfsutils-linux (--configure):
 installed zfsutils-linux package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of zfs-initramfs:
 zfs-initramfs depends on zfsutils-linux (>= 0.8.1-1ubuntu13); however:
  Package zfsutils-linux is not configured yet.

dpkg: error processing package zfs-initramfs (--configure):
 dependency problems - leaving unconfigured
Setting up ppp (2.4.7-2+4.1ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Settin
g up libplymouth4:amd64 (0.9.4git20190712-0ubuntu4) ...
Setting up plymouth (0.9.4git20190712-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
dpkg: dependency problems prevent configuration of zfs-zed:
 zfs-zed depends on zfsutils-linux (>= 0.8.1-1ubuntu13); however:
  Package zfsutils-linux is not configured yet.

dpkg: error processing package zfs-zed (--configure):
 dependency problems - leaving unconfigured
Setting up plymouth-theme-ubuntu-text (0.9.4git20190712-0ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          update
-initramfs: deferring update (trigger activated)
Setting up plymouth-label (0.9.4git20190712-0ubuntu4) ...
Setting up plymouth-theme-ubuntu-logo (0.9.4git20190712-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.62.0-1) ...
Processing triggers for libc-bin (2.30-0ubuntu2) ...
Processing triggers for systemd (242-7ubuntu1) ...
Processing triggers for man-db (2.8.7-3) ...
Setting up gnome-shell (3.34.1-1ubuntu1) ...
Processing triggers for initramfs-tools (0.133ubuntu10) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-050400rc2-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=c86a81fa-1d97-483c-99f8-318382983ed7)
I: Set the RESUME variable to override this.
Errors were encountered while processing:
 zfsutils-linux
 zfs-initramfs
 zfs-zed
E: Sub-process /usr/bin/dpkg returned an error code (1)
corrado@corrado-p9-ee-1006:~$ 
corrado@corrado-p9-ee-1006:~$ inxi -SCGx
System:    Host: corrado-p9-ee-1006 Kernel: 5.4.0-050400rc2-generic x86_64 bits: 64 compiler: gcc v: 9.2.1 
           Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31199 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 802 4: 827 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.5 driver: i915 resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) v: 4.5 Mesa 19.2.0 
           direct render: Yes 
corrado@corrado-p9-ee-1006:~$ 
```

---

### Post by Doug S on 2019-10-12
> **corradoventu said:**
> zfs modules install failed on Ubuntu 19.10 with Kernel 5.4RC2. 
zfs modules installed ok on Ubuntu 19.10 with Kernel 5.3.0-13 - same hardware, different partition, both installed from Ubuntu 19.10 "Eoan Ermine" - Beta amd64 (20191006).
should I report a problem? how can I do?
Isn't ZFS still a distribution dependent ability? Something to do with the license? I do not know for certain, but if true I would not expect the mainline kernel to work.

---

### Post by Doug S on 2019-11-06
Quiet on these mainline kernel threads of late.
Due to ongoing testing, I stayed with 5.4-rc2 until now.
I have been running kernel [5.4-rc6]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc6/") for a couple of days without problems.

---

### Post by corradoventu on 2019-11-11
```
corrado@corrado-p9-ff-1105x:~$ inxi -SCGx
System:
  Host: corrado-p9-ff-1105x Kernel: 5.4.0-050400rc7-generic x86_64 bits: 64 
  compiler: gcc v: 9.2.1 Desktop: Gnome 3.34.1 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 31199 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: wayland server: X.Org 1.20.5 driver: i915 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) 
  v: 4.5 Mesa 19.2.1 direct render: Yes 
corrado@corrado-p9-ff-1105x:~$ 

```

---

### Post by Doug S on 2019-11-20
There is an RC8 this cycle. I have been running it for a couple of days. While this has been a quiet cycle on this thread, for my minor part it has been extremely busy. Hopefully the final 5.4 will be the better for it.

---

### Post by corradoventu on 2019-11-25
Kernel 5.4 available on [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4/)
```
orrado@corrado-p13-ff-1113:~$ inxi -SCGx
System:
  Host: corrado-p13-ff-1113 Kernel: 5.4.0-050400-generic x86_64 bits: 64 
  compiler: gcc v: 9.2.1 Desktop: Gnome 3.34.1 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 31199 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 801 2: 802 
  3: 800 4: 800 
Graphics:
  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.5 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) 
  v: 4.5 Mesa 19.2.1 direct render: Yes 
corrado@corrado-p13-ff-1113:~$ 


```

---

### Post by zika on 2019-11-29
Warning:
```
update-initramfs: Generating /boot/initrd.img-5.4.0-999-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168fp-3.fw for module r8169
```
Solution:
```
cd /lib/firmware/rtl_nic
sudo wget https://kernel.googlesource.com/pub/scm/linux/kernel/git/firmware/linux-firmware/+/e8a0f4c9314754d8b2cbe9840357d88a861c438a/rtl_nic/rtl8168fp-3.fw
```
and do update-initramfs on that image again...

---

### Post by mrfelker on 2019-12-08
Not sure where your running kernel thread is but kernel 5.4.2 is available and works (with the exception of the kludge in grub.cfg  for RAID  0  introduced in kernel 5.3. which apparently was introduced on purpose or inadvertently by Torvalds <based on rather extreme reactions from others>)

---

