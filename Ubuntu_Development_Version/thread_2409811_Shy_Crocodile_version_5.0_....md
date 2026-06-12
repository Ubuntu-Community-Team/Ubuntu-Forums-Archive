---
title: "Shy Crocodile version 5.0 ..."
date: 2019-01-07
forum: Ubuntu Development Version
---

### Post by zika on 2019-01-07
[https://www.kernel.org/](https://www.kernel.org/)
[https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=bfeffd155283772bbe78c6a05dec7c0128ee500c](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=bfeffd155283772bbe78c6a05dec7c0128ee500c)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0-rc1/)

---

### Post by corradoventu on 2019-01-07
```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCx
System:
  Host: corrado-p13-dd-1107-x Kernel: 5.0.0-050000rc1-generic x86_64 
  bits: 64 compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.1 
  Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 802 4: 801 
corrado@corrado-p13-dd-1107-x:~$ 


```

---

### Post by #&amp;thj^% on 2019-01-07
zika are you using it yet? I have run it pretty hard so far and all good so far here.
```
dmesg | grep Linux
[    0.000000] Linux version 5.0.0-050000rc1-lowlatency (kernel@tangerine) (gcc version 8.2.0 (Ubuntu 8.2.0-12ubuntu1)) #201901062130 SMP PREEMPT Mon Jan 7 02:41:31 UTC 2019
[    0.165304] ACPI: Added _OSI(Linux-Dell-Video)
[    0.165304] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.165304] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
**[COLOR="#FF0000"][    0.181668] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored[/COLOR]**
[    0.205194] pps_core: LinuxPPS API ver. 1 registered
[    1.256449] Linux agpgart interface v0.103
[    1.335240] usb usb1: Manufacturer: Linux 5.0.0-050000rc1-lowlatency ehci_hcd
[    1.346229] usb usb2: Manufacturer: Linux 5.0.0-050000rc1-lowlatency ehci_hcd
[    1.348190] usb usb3: Manufacturer: Linux 5.0.0-050000rc1-lowlatency xhci-hcd
[    1.348945] usb usb4: Manufacturer: Linux 5.0.0-050000rc1-lowlatency xhci-hcd
[   10.255356] Intel(R) Wireless WiFi driver for Linux
[   10.523447] media: Linux media interface: v0.10
[   10.595399] videodev: Linux video capture interface: v2.00

```
I'm kind of looking forward for this one to hit. ;)
EDIT: Please note>>"[    0.181668] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored"

---

### Post by corradoventu on 2019-01-08
I have message: ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
also with standard kernel

```
corrado@corrado-p6-dd-1227:~$ dmesg | grep Linux
[    0.000000] Linux version 4.18.0-11-generic (buildd@lcy01-amd64-027) (gcc version 8.2.0 (Ubuntu 8.2.0-7ubuntu1)) #12-Ubuntu SMP Tue Oct 23 19:22:37 UTC 2018 (Ubuntu 4.18.0-11.12-generic 4.18.12)
[    0.040712] ACPI: Added _OSI(Linux-Dell-Video)
[    0.040712] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.071977] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.103473] pps_core: LinuxPPS API ver. 1 registered
[    0.557032] Linux agpgart interface v0.103
[    0.559283] usb usb1: Manufacturer: Linux 4.18.0-11-generic xhci-hcd
[    0.560082] usb usb2: Manufacturer: Linux 4.18.0-11-generic xhci-hcd
corrado@corrado-p6-dd-1227:~$ 
```

---

### Post by Doug S on 2019-01-09
I do not seem to have that message:
```
doug@s15:~/bin$ dmesg | grep Linux
[    0.000000] Linux version 5.0.0-rc1-teo11 (doug@s15) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.11)) #535 SMP PREEMPT Tue Jan 8 09:24:08 PST 2019
[    0.302444] ACPI: Added _OSI(Linux-Dell-Video)
[    0.302446] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.302448] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.330033] pps_core: LinuxPPS API ver. 1 registered
[    1.453645] Linux agpgart interface v0.103
[    1.790477] usb usb1: Manufacturer: Linux 5.0.0-rc1-teo11 ehci_hcd
[    1.995137] usb usb2: Manufacturer: Linux 5.0.0-rc1-teo11 ehci_hcd
[    2.578273] usb usb3: Manufacturer: Linux 5.0.0-rc1-teo11 xhci-hcd
[    2.959978] usb usb4: Manufacturer: Linux 5.0.0-rc1-teo11 xhci-hcd
```My kernel is stock except for [version 11 of the Timer Events Orientated idle governor]("https://patchwork.kernel.org/patch/10748273/"), which I have been testing since version1. i.e.:
```
doug@s15:~/bin$ grep . /sys/devices/system/cpu/cpuidle/*
/sys/devices/system/cpu/cpuidle/current_driver:intel_idle
/sys/devices/system/cpu/cpuidle/current_governor_ro:teo

```

---

### Post by corradoventu on 2019-01-09
I have same msg with Ubuntu Cosmic on the same hardware
```
corrado@corrado-p3-cosmic:~$ dmesg | grep Linux
[    0.000000] Linux version 4.18.0-13-generic (buildd@lgw01-amd64-048) (gcc version 8.2.0 (Ubuntu 8.2.0-7ubuntu1)) #14-Ubuntu SMP Wed Dec 5 09:04:24 UTC 2018 (Ubuntu 4.18.0-13.14-generic 4.18.17)
[    0.040702] ACPI: Added _OSI(Linux-Dell-Video)
[    0.040702] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.071984] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.103574] pps_core: LinuxPPS API ver. 1 registered
[    0.549755] Linux agpgart interface v0.103
[    0.552012] usb usb1: Manufacturer: Linux 4.18.0-13-generic xhci-hcd
[    0.552826] usb usb2: Manufacturer: Linux 4.18.0-13-generic xhci-hcd
corrado@corrado-p3-cosmic:~$ inxi -SC
System:    Host: corrado-p3-cosmic Kernel: 4.18.0-13-generic x86_64 bits: 64 Desktop: Gnome 3.30.1 
           Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 801 
corrado@corrado-p3-cosmic:~$ 

```

---

### Post by zika on 2019-01-11
> **1fallen said:**
> zika are you using it yet?Yes, happily, from the first (drm-tip) build... ;)

---

### Post by IanW on 2019-01-11
[This may be problematic soon]("https://www.phoronix.com/scan.php?page=news_item&px=ZFS-On-Linux-5.0-Problem")

---

### Post by #&amp;thj^% on 2019-01-15
No need for alarm: **"BIOS _OSI(Linux) query ignored"** is nothing to worry about it just helps with monitoring batteries is all

---

### Post by corradoventu on 2019-01-16
dpkg: dependency problems prevent configuration of linux-headers-5.0.0-050000rc2-generic:i386:
 linux-headers-5.0.0-050000rc2-generic:i386 depends on libc6 (>= 2.11).
 linux-headers-5.0.0-050000rc2-generic:i386 depends on libssl1.1 (>= 1.1.0).

dpkg: error processing package linux-headers-5.0.0-050000rc2-generic:i386 (--install):
 dependency problems - leaving unconfigured

---

### Post by Doug S on 2019-01-17
> **corradoventu said:**
> dpkg: dependency problems prevent configuration of linux-headers-5.0.0-050000rc2-generic:i386:
 linux-headers-5.0.0-050000rc2-generic:i386 depends on libc6 (>= 2.11).
 linux-headers-5.0.0-050000rc2-generic:i386 depends on libssl1.1 (>= 1.1.0).

dpkg: error processing package linux-headers-5.0.0-050000rc2-generic:i386 (--install):
 dependency problems - leaving unconfiguredFor libssl1.1: As far as I know, that annoying dependency problem has been there since [kernel 4.17-rc1]("https://ubuntuforums.org/showthread.php?t=2389561&p=13761678#post13761678") for systems that still use libssl1.0.0, such as my main 16.04 test server. I say "annoying" because I don't think it is needed. I have been using my steal the kernel config file and compile it myself workaround for over 8 months now without any issue related to libssl.

For libc6: I haven't seen that one, but I wouldn't because even my 16.04 test server is at libc6:
```
doug@s15:~$ [COLOR="#FF0000"]dpkg -l | grep libc6[/COLOR]
ii  libc6:amd64                                   2.23-0ubuntu10                             amd64        GNU C Library: Shared libraries
ii  libc6-dev:amd64                               2.23-0ubuntu10                             amd64        GNU C Library: Development Libraries and Header Files
doug@s15:~$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s15 5.0.0-rc2-teo11 #536 SMP PREEMPT Sun Jan 13 17:35:32 PST 2019 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by #&amp;thj^% on 2019-01-17
> **Doug S said:**
> For libssl1.1: As far as I know, that annoying dependency problem has been there since [kernel 4.17-rc1]("https://ubuntuforums.org/showthread.php?t=2389561&p=13761678#post13761678") for systems that still use libssl1.0.0, such as my main 16.04 test server. I say "annoying" because I don't think it is needed. I have been using my steal the kernel config file and compile it myself workaround for over 8 months now without any issue related to libssl.

For libc6: I haven't seen that one, but I wouldn't because even my 16.04 test server is at libc6:
```
doug@s15:~$ [COLOR="#FF0000"]dpkg -l | grep libc6[/COLOR]
ii  libc6:amd64                                   2.23-0ubuntu10                             amd64        GNU C Library: Shared libraries
ii  libc6-dev:amd64                               2.23-0ubuntu10                             amd64        GNU C Library: Development Libraries and Header Files
doug@s15:~$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s15 5.0.0-rc2-teo11 #536 SMP PREEMPT Sun Jan 13 17:35:32 PST 2019 x86_64 x86_64 x86_64 GNU/Linux


```

+1

```
dmesg | grep Linux
[    0.000000] Linux version 5.0.0-050000rc2-lowlatency (kernel@kathleen) (gcc version 8.2.0 (Ubuntu 8.2.0-12ubuntu1)) #201901171452 SMP PREEMPT Thu Jan 17 14:56:34 UTC 2019
[    0.164617] ACPI: Added _OSI(Linux-Dell-Video)
[    0.164617] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.164617] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.179976] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.204612] pps_core: LinuxPPS API ver. 1 registered
[    1.254283] Linux agpgart interface v0.103
[    1.336594] usb usb1: Manufacturer: Linux 5.0.0-050000rc2-lowlatency ehci_hcd
[    1.347600] usb usb2: Manufacturer: Linux 5.0.0-050000rc2-lowlatency ehci_hcd
[    1.349572] usb usb3: Manufacturer: Linux 5.0.0-050000rc2-lowlatency xhci-hcd
[    1.350320] usb usb4: Manufacturer: Linux 5.0.0-050000rc2-lowlatency xhci-hcd
[   14.635161] media: Linux media interface: v0.10
[   14.761124] videodev: Linux video capture interface: v2.00
[   14.888941] Intel(R) Wireless WiFi driver for Linux

```
And:
```
dpkg -l | grep libc6
ii  libc6:amd64                                                 2.27-3ubuntu1                         amd64        GNU C Library: Shared libraries
ii  libc6:i386                                                  2.27-3ubuntu1                         i386         GNU C Library: Shared libraries
ii  libc6-dbg:amd64                                             2.27-3ubuntu1                         amd64        GNU C Library: detached debugging symbols
ii  libc6-dev:amd64                                             2.27-3ubuntu1                         amd64        GNU C Library: Development Libraries and Header Files

```

---

### Post by zika on 2019-01-21
HU:
**/etc/initramfs-tools/initramfs.conf**
If You use ```
MODULES=dep
``` You could get segmentation fault in kernel image and, no boot next time... ;)
Use ```
MODULES=most
``` for some time...

Update&#8321;: Segmentation fault persists even after proper update-initramfs. Confirmed on two machines rendered unbootable... HU... I'm not sure if that is recoverable, will investigate more...

---

### Post by Doug S on 2019-01-21
Kernel 5.0-rc3 is available from [kernel.org]("https://www.kernel.org/"). For Ubuntu, the daily build seems to be broken again, hence the [Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") doesn't yet have a compiled candidate to try.

---

### Post by Doug S on 2019-01-22
Note that the CFQ IO Scheduler is gone in this kernel 5.0-rc series. It used to be the default IO Scheduler.
see [commit 0e9da3fbf7d81f0f913b491c8de1ba7883d4f217]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=0e9da3fbf7d81f0f913b491c8de1ba7883d4f217").

```
doug@s15:~$ uname -a
Linux s15 [COLOR="#FF0000"]5.0.0-rc3[/COLOR]-teo11 #537 SMP PREEMPT Mon Jan 21 07:54:50 PST 2019 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~$ cat /sys/block/sda/queue/scheduler
[COLOR="#FF0000"][none][/COLOR]

```
```
doug@s15:~$ uname -a
Linux s15 [COLOR="#FF0000"]4.19.0[/COLOR]-stock #511 SMP PREEMPT Fri Oct 26 18:03:55 PDT 2018 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~$ cat /sys/block/sda/queue/scheduler
[COLOR="#FF0000"]noop deadline [cfq][/COLOR]

```For some unknown reason, for the kernel 4.20-rc series the list also shows only "[none]".
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-4.20-rc5-teo8 .config[/COLOR]
...
-CFQ_GROUP_IOSCHED y
-DEFAULT_CFQ y
-DEFAULT_DEADLINE n
-DEFAULT_IOSCHED "cfq"
-DEFAULT_NOOP n
-DMA_DIRECT_OPS y
-INTEL_RDT y
-IOSCHED_CFQ y
-IOSCHED_DEADLINE y
-IOSCHED_NOOP y
...

```

---

### Post by corradoventu on 2019-01-25
Kernel 5.0-rc3 from [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0-rc3/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0-rc3/) seems ok
```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCGx
System:    Host: corrado-p13-dd-1107-x Kernel: 5.0.0-050000rc3-generic x86_64 bits: 64 compiler: gcc 
           v: 8.2.0 Desktop: Gnome 3.30.2 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake 
           rev: 9 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.3 driver: fbdev unloaded: modesetting,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) v: 4.5 Mesa 18.2.6 
           direct render: Yes 
corrado@corrado-p13-dd-1107-x:~$ 



```

---

### Post by Doug S on 2019-01-25
On the subject of the IO scheduler: The ubuntu kernel configuration for kernel 5.0-rc3 has a change, compared to -rc1 (I never used Ubuntu's -rc2 kernel config), that results in this:

```
~$ cat /sys/block/sda/queue/scheduler
[COLOR="#FF0000"][mq-deadline][/COLOR] none

```The diff:
```
$ scripts/diffconfig .config-5.0-rc3-teo11-1 .config-5.0-rc3-teo11-2
 CRYPTO_STATS n -> y
 [COLOR="#FF0000"]MQ_IOSCHED_DEADLINE m -> y[/COLOR]
 MTD_PHYSMAP_GPIO_ADDR n -> y
 VIDEO_SECO_RC n -> y
 X86_RESCTRL n -> y

```

---

### Post by #&amp;thj^% on 2019-01-25
Doug is this on a SSD drive?
I have seen this since 4.19
```
uname -a && cat /sys/block/sda/queue/scheduler
Linux arch 4.20.4.a-1-hardened #1 SMP PREEMPT Fri Jan 25 01:24:51 CET 2019 x86_64 GNU/Linux
[mq-deadline] kyber bfq none

```
I do have a SSD drive
```
inxi -Dz
Drives:
  Local Storage: total: 1.98 TiB used: 256.65 GiB (12.6%) 
  **ID-1: /dev/sda vendor: Intel model: SSDSC2BW180A3L size: 167.68 GiB **
  ID-2: /dev/sdb type: USB vendor: Western Digital model: WD My Passport 25E1 
  size: 1.82 TiB 

```
Also for Ubuntu:
```
uname -a && cat /sys/block/sda/queue/scheduler && inxi -Dz
Linux me-750-417c 5.0.0-050000rc3-lowlatency #201901202030 SMP PREEMPT Mon Jan 21 01:44:29 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
[COLOR="#FF0000"][mq-deadline] none[/COLOR]
Drives:
  Local Storage: total: 2.04 TiB used: 25.86 GiB (1.2%) 
  ID-1: /dev/sda vendor: Intel model: SSDSC2BW180A3L size: 167.68 GiB 
 ** ID-2: /dev/sdb type: USB vendor: SanDisk model: Ultra size: 57.28 GiB **
  ID-3: /dev/sdc type: USB vendor: Western Digital 
  model: WD My Passport 25E1 size: 1.82 TiB 

```
This install is on " ID-2: /dev/sdb type: USB vendor: SanDisk model: Ultra size: 57.28 GiB "

[list]**The Completely Fair Queuing (CFQ) **scheduler is the default algorithm in Red Hat Enterprise Linux 4 which is suitable for a wide variety of applications and provides a good compromise between throughput and latency. In comparison to the CFQ algorithm, the Deadline scheduler caps maximum latency per request and maintains a good disk throughput which is best for disk-intensive database applications.

[*]**The Budget Fair Queuing (BFQ)** is based on CFQ code and brings some enhancements. It does not grant the disk to each process for a fixed time-slice but assigns a "budget" measured in number of sectors to the process and uses heuristics. It is a relatively complex scheduler, it may be more adapted to rotational drives and slow SSDs because its high per-operation overhead, especially if associated with a slow CPU, can slow down fast devices. The objective of BFQ on personal systems is that for interactive tasks, the storage device is virtually as responsive as if it was idle. In its default configuration it focuses on delivering the lowest latency rather than achieving the maximum throughput.

[*]**Kyber is a recent scheduler **inspired by active queue management techniques used for network routing. The implementation is based on "tokens" that serve as a mechanism for limiting requests. A queuing token is required to allocate a request, this is used to prevent starvation of requests. A dispatch token is also needed and limits the operations of a certain priority on a given device. Finally, a target read latency is defined and the scheduler tunes itself to reach this latency goal. The implementation of the algorithm is relatively simple and it is deemed efficient for fast devices.[/list]

```

me on Sat Jan 26 at 08:17 AM in ~ branch: (HEAD) 
>> uname -a && cat /sys/block/sda/queue/scheduler
Linux arch 4.20.4.a-1-hardened #1 SMP PREEMPT Fri Jan 25 01:24:51 CET 2019 x86_64 GNU/Linux
**[mq-deadline] **kyber bfq none

me on Sat Jan 26 at 08:23 AM in ~ branch: (HEAD) 
>> uname -a && cat /sys/block/sda/queue/scheduler
Linux arch 4.20.4.a-1-hardened #1 SMP PREEMPT Fri Jan 25 01:24:51 CET 2019 x86_64 GNU/Linux
mq-deadline kyber** [bfq] **none


me on Sat Jan 26 at 08:23 AM in ~ branch: (HEAD) 
>> uname -a && cat /sys/block/sda/queue/scheduler
Linux arch 4.20.4.a-1-hardened #1 SMP PREEMPT Fri Jan 25 01:24:51 CET 2019 x86_64 GNU/Linux
mq-deadline** [kyber] **bfq none
```

---

### Post by Doug S on 2019-01-25
> **1fallen said:**
> Doug is this on a SSD drive?
I have seen this since 4.19
```
uname -a && cat /sys/block/sda/queue/scheduler
Linux arch 4.20.4.a-1-hardened #1 SMP PREEMPT Fri Jan 25 01:24:51 CET 2019 x86_64 GNU/Linux
[mq-deadline] kyber bfq none

```No, the drive is a regular sata magnetic drive. Very interesting though, what you get on arch. I don't recall how long ago, but I tried to get kyber and bfq to work on an Ubuntu kernel and was not successful. I tried kernel some various kernel configuration changes and also some kernel command line changes. This is one of my old attempts in grub:
```
#GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300 [COLOR="#FF0000"]scsi_mod.use_blk_mq=1 elevator=kyber"[/COLOR]
```

---

### Post by zika on 2019-01-27
5.0.0-999-generic #201901262102 USB NIC works as it did for a long time...
5.0.0-994-generic #201901262102 USB NIC does not work/get_recognized even after loading *usbnet* module... We will see if that just a glitch today or is a decision... Nothing in CHANGES file that I found does not point to deliberate decision...
Will investigate more if/when get some spare time...
Tested, of course, with several USB/NIC products...
Update&#8321;: 5.0.0-994-generic #201901280501 : (re)solved... USB NIC works as it should...
Update&#8322;: 5.0.0-994-generic #201902052101 : again, does not...
Update&#8323;: 5.0.0-994-generic #201902062104 : again, works as it should...

---

### Post by IanW on 2019-01-28
[RC4 has landed]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0-rc4/")

---

### Post by corradoventu on 2019-02-06
also rc5
```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCx
System:
  Host: corrado-p13-dd-1107-x Kernel: 5.0.0-050000rc5-generic x86_64 
  bits: 64 compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.2 
  Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
corrado@corrado-p13-dd-1107-x:~$ 
```
and rc6 too```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCGx
System:    Host: corrado-p13-dd-1107-x Kernel: 5.0.0-050000rc6-generic x86_64 bits: 64 
           compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.2 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake 
           rev: 9 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 801 4: 801 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.3 driver: fbdev unloaded: modesetting,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) v: 4.5 Mesa 18.2.6 
           direct render: Yes 
corrado@corrado-p13-dd-1107-x:~$ 

```

---

### Post by Doug S on 2019-02-12
I missed -rc5, due to some ongoing tests with -rc4. Now running -rc6. There are number of kernel configuration file changes between -rc3 ( I never got the Ubuntu -rc4 config) and -rc6:

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-5.0.0-050000rc3-lowlatency .config-5.0.0-050000rc6-lowlatency[/COLOR]
-SENSORS_OCC y
-X86_RESCTRL y
 ANDROID n -> y
 NCSI_OEM_CMD_GET_MAC n -> y
 PCI_MESON n -> y
 RUNTIME_TESTING_MENU n -> y
 SENSORS_OCC_P8_I2C m -> n
 SND_HDA_POWER_SAVE_DEFAULT 0 -> 1
+ANDROID_BINDER_IPC n
+ANDROID_VSOC m
+ASHMEM n
+ASYNC_RAID6_TEST m
+ATOMIC64_SELFTEST m
+BACKTRACE_SELF_TEST m
+FIND_BIT_BENCHMARK m
+INTERVAL_TREE_TEST m
+ION n
+KPROBES_SANITY_TEST n
+LKDTM m
+PERCPU_TEST m
+RBTREE_TEST m
+TEST_BITFIELD m
+TEST_BITMAP m
+TEST_BPF m
+TEST_FIRMWARE m
+TEST_HASH m
+TEST_HEXDUMP m
+TEST_IDA m
+TEST_KMOD m
+TEST_KSTRTOX m
+TEST_LIST_SORT m
+TEST_LKM m
+TEST_MEMCAT_P m
+TEST_OBJAGG m
+TEST_OVERFLOW m
+TEST_PARMAN m
+TEST_PRINTF m
+TEST_RHASHTABLE m
+TEST_SORT m
+TEST_STATIC_KEYS m
+TEST_STRING_HELPERS m
+TEST_SYSCTL m
+TEST_UDELAY m
+TEST_USER_COPY m
+TEST_UUID m
+TEST_XARRAY m
+X86_CPU_RESCTRL y

```I don't know about differences for GENERIC, I only use LOWLATENCY.

---

### Post by corradoventu on 2019-03-04
Kernel 5.0 landed but not yet in Disco repository.
```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCGx
System:
  Host: corrado-p13-dd-1107-x Kernel: 5.0.0-050000-generic x86_64 bits: 64 
  compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.2 
  Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.3 driver: fbdev unloaded: modesetting,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) 
  v: 4.5 Mesa 18.2.6 direct render: Yes 
corrado@corrado-p13-dd-1107-x:~$ 

```

---

### Post by IanW on 2019-03-04
~kernel-ppa/mainline is now showing 5.0.0-999.201903040202 is available

---

### Post by corradoventu on 2019-03-04
In [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0/) I see:
```
Build for amd64 succeeded (see BUILD.LOG.amd64):
  linux-headers-5.0.0-050000_5.0.0-050000.201903032031_all.deb
  linux-headers-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
  linux-headers-5.0.0-050000-lowlatency_5.0.0-050000.201903032031_amd64.deb
  linux-image-unsigned-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
  linux-image-unsigned-5.0.0-050000-lowlatency_5.0.0-050000.201903032031_amd64.deb
  linux-modules-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
  linux-modules-5.0.0-050000-lowlatency_5.0.0-050000.201903032031_amd64.deb
```
downloaded and successfully installed but i don't see kernel 5 in proposed

---

### Post by corradoventu on 2019-03-06
Kernel 5.0 landed in Ubuntu proposed ```
corrado@corrado-p13-dd-0306:~$ apt policy linux-image-5*
linux-image-5.0.0-7-generic:
  Installed: 5.0.0-7.8
  Candidate: 5.0.0-7.8
  Version table:
 *** 5.0.0-7.8 500
        500 http://archive.ubuntu.com/ubuntu disco-proposed/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2019-03-06
I need to check this for a couple of more days, but performance seems to have picked-up a bit.(For both Ubuntu and Arch)
```
uname -r && cat /sys/block/sda/queue/scheduler
5.0.0-arch1-1-ARCH
[mq-deadline] kyber bfq none

```
Dang i forgot to see if more schedulers were added to the Ubutnu kernel.

---

### Post by Doug S on 2019-03-06
> **1fallen said:**
> 
Dang i forgot to see if more schedulers were added to the Ubutnu kernel.Using the (low latency) kernel configuration file from [the mainline version of 5.0]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0/"), I get the same as I did for [kernel 5.0-rc3]("https://ubuntuforums.org/showthread.php?t=2409811&page=2&p=13833331#post13833331"):

```
doug@s15:~$ uname -r && cat /sys/block/sda/queue/scheduler
5.0.0-teo11-boost2
[mq-deadline] none

```

---

### Post by zika on 2019-03-07
For additional, as always, You need to add their modules, if they are available in the particular kernel build, no matter which edition,You're using. There are more than shown in Your code for sure...
Example:```
$ locate bfq.ko
/usr/lib/modules/5.0.0-7-generic/kernel/block/bfq.ko
/usr/lib/modules/5.0.0-994-generic/kernel/block/bfq.ko
$modprobe bfq
$ cat /sys/block/sda/queue/scheduler
[none] mq-deadline bfq
```

---

### Post by Doug S on 2019-03-08
> **zika said:**
> For additional, as always, You need to add their modules, if they are available in the particular kernel build, no matter which edition,You're using. There are more than shown in Your code for sure...
Example:```
$ locate bfq.ko
/usr/lib/modules/5.0.0-7-generic/kernel/block/bfq.ko
/usr/lib/modules/5.0.0-994-generic/kernel/block/bfq.ko
$modprobe bfq
$ cat /sys/block/sda/queue/scheduler
[none] mq-deadline bfq
```I can also load the bfq module via the modrpobe command, but not kyber. Do you know how to get the system to use the bfq or kyber schedulers? I assumed, but do not know for sure that they would have to be built in and not modules in order to be a boot time option. I got them both to appear by building them in:

```
doug@s15:~$ uname -r && cat /sys/block/sda/queue/scheduler && cat /proc/cmdline
5.0.0-teo11-boost2
[mq-deadline] none
BOOT_IMAGE=/boot/vmlinuz-5.0.0-teo11-boost2 root=UUID=bcbc624b-892b-46ca-9e9e-102daf644170 ro ipv6.disable=1 consoleblank=300 elevator=bfq

doug@s15:~/temp-k-git/linux$ uname -r && cat /sys/block/sda/queue/scheduler && cat /proc/cmdline
5.0.0-teo11-bfq
[mq-deadline] kyber bfq none
BOOT_IMAGE=/boot/vmlinuz-5.0.0-teo11-bfq root=UUID=bcbc624b-892b-46ca-9e9e-102daf644170 ro ipv6.disable=1 consoleblank=300 elevator=bfq

doug@s15:~/temp-k-git/linux$ uname -r && cat /sys/block/sda/queue/scheduler && cat /proc/cmdline
5.0.0-teo11-bfq
[mq-deadline] kyber bfq none
BOOT_IMAGE=/boot/vmlinuz-5.0.0-teo11-bfq root=UUID=bcbc624b-892b-46ca-9e9e-102daf644170 ro ipv6.disable=1 consoleblank=300 scsi_mod.use_blk_mq=1 elevator=kyber
```

```
doug@s15:~/temp-k-git/linux$ scripts/diffconfig .config-5.0-teo11 .config-5.0-bfq
 IOSCHED_BFQ m -> y
 MQ_IOSCHED_KYBER m -> y
```

---

### Post by zika on 2019-03-08
```
$ locate kyber
/usr/lib/modules/4.19.0-13-generic/kernel/block/kyber-iosched.ko
/usr/lib/modules/5.0.0-994-generic/kernel/block/kyber-iosched.ko
/usr/src/linux-headers-4.19.0-13-generic/include/config/mq/iosched/kyber.h
/usr/src/linux-headers-5.0.0-994/include/trace/events/kyber.h
/usr/src/linux-headers-5.0.0-994-generic/include/config/mq/iosched/kyber.h
```
```
$ sudo modprobe kyber-iosched
$ cat /sys/block/sda/queue/scheduler
[mq-deadline] kyber none
```
```
$ cat /etc/modules# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
bfq
kyber-iosched

$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/echo kyber > /sys/block/sda/queue/scheduler
exit 0

$ sudo chmod +x /etc/rc.local
```

---

### Post by Doug S on 2019-03-08
> **zika said:**
> ```

/usr/bin/echo kyber > /sys/block/sda/queue/scheduler

```Oh! Thanks. For unknown reasons I thought it was a boot time only thing. Yes, it works fine:

```
doug@s15:~/temp-k-git/linux$ cat /sys/block/sda/queue/scheduler
[mq-deadline] kyber bfq none
doug@s15:~/temp-k-git/linux$ echo kyber |sudo tee /sys/block/sda/queue/scheduler
kyber
doug@s15:~/temp-k-git/linux$ cat /sys/block/sda/queue/scheduler
mq-deadline [kyber] bfq none
doug@s15:~/temp-k-git/linux$ echo bfq |sudo tee /sys/block/sda/queue/scheduler
bfq
doug@s15:~/temp-k-git/linux$ cat /sys/block/sda/queue/scheduler
mq-deadline kyber [bfq] none

```

edit: I observe that i do not need to force load the module, as it will load when asked for:
```
doug@s15:~$ cat /sys/block/sda/queue/scheduler
mq-deadline [bfq] none
doug@s15:~$ echo kyber |sudo tee /sys/block/sda/queue/scheduler
kyber
doug@s15:~$ cat /sys/block/sda/queue/scheduler
mq-deadline bfq [kyber] none

```

---

### Post by zika on 2019-03-08
In [1]("https://ubuntuforums.org/showthread.php?t=2409811&p=13842884#post13842884") I gave You on-fly method while in [2]("https://ubuntuforums.org/showthread.php?t=2409811&p=13843111#post13843111") there is how to make that permanent...
Reboot is not an often used word in Linux... But, old habbits do die hard... ;)
Do check if the module is actually loaded even though it is present in mentioned file.

---

### Post by #&amp;thj^% on 2019-03-08
Sorry late for party, way to much work (Job) for this old fart.
Along with zika's post, My findings thus far, bfq is about the same performance as prior mq-deadline  scheduler, with a notable difference>> moving files form one disk to another the initial start is a bit laggy but transfer speeds were almost identical. Files sizes ranged from 900mb to 5 Gigs.
media transcodeing was very close to same.
I went about setting this like:>>(If interested)
```
sudoedit /etc/default/grub

```
Adding this:
```
GRUB_CMDLINE_LINUX="scsi_mod.use_blk_mq=1 quiet"

```
Then updated grub;
```
sudo update-grub
```
Next I made a file "60-scheduler.rules"
```
sudoedit /etc/udev/rules.d/60-scheduler.rules
```
With this for the content:
```
# set deadline scheduler for non-rotating disks
ACTION=="add|change", KERNEL=="sd[a-z]", TEST!="queue/rotational",
ATTR{queue/scheduler}="deadline"
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="0",
ATTR{queue/scheduler}="bfq"

# set cfq scheduler for rotating disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="1",
ATTR{queue/scheduler}="cfq" ## Or use the one you want/need

```
This should work for SSD drives and Spinning disks.
Next reload udevadm:
```
sudo udevadm control --reload
sudo udevadm trigger
```
Now on next boot should show you:
```
cat /sys/block/sda/queue/scheduler
mq-deadline kyber [bfq] none

```
**Summary**: Just goes to show, Using a multi-queue scheduler is like using high-octane fuel in a car from the 90s, its not going to make it run better, especially when its worked just fine with regular fuel for the last 3 decades. :)
> Hi 1fallen, Recall that CFQ is now gone.
Not just yet:
```
me on Tue Mar 12 at 02:00 PM in ~ branch: (HEAD) 
>> sudo dmesg | grep cfq && uname -r
[sudo] password for me: 
[    2.166975] io scheduler cfq registered (default)
4.20.15.a-1-hardened

```

---

### Post by Doug S on 2019-03-08
> **1fallen said:**
> Next I made a file "60-scheduler.rules"
```
sudoedit /etc/udev/rules.d/60-scheduler.rules
```
With this for the content:
```
# set deadline scheduler for non-rotating disks
ACTION=="add|change", KERNEL=="sd[a-z]", TEST!="queue/rotational",
ATTR{queue/scheduler}="deadline"
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="0",
ATTR{queue/scheduler}="bfq"

# set cfq scheduler for rotating disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="1",
ATTR{queue/scheduler}="[COLOR="#FF0000"]cfq[/COLOR]"

```
Hi 1fallen, Recall that CFQ is now gone.

> **zika said:**
> In [1]("https://ubuntuforums.org/showthread.php?t=2409811&p=13842884#post13842884") I gave You on-fly method while in [2]("https://ubuntuforums.org/showthread.php?t=2409811&p=13843111#post13843111") there is how to make that permanent...
Reboot is not an often used word in Linux... But, old habbits do die hard... ;)Hi zika, Thanks. My point was that I don't actually need to do either of your steps, as it will load automatically when asked for.

> **zika said:**
> Do check if the module is actually loaded even though it is present in mentioned file.It is:
```
doug@s15:~$ lsmod | grep kyber
kyber_iosched          32768  1
```

Now.... It was so many months ago, that I no longer recall what I wanted to test with bfq or kyber...

---

### Post by zika on 2019-03-08
Old dogs, like me, learn very slowly new tricks but I'll try this on my machine. Last time I've tried I had to provide that module is loaded. Nice to know there is real progress even in that obscure part of this. Thanks.

---

### Post by corradoventu on 2019-03-10
also 5.0.1 is available:  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0.1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0.1/)

---

### Post by moma on 2019-03-13
Thank you.
All good here on Ubuntu 19.04 dev.

$ inxi -SCx
System:
  Host: ubuntu19 Kernel: 5.0.1-050001-generic x86_64 bits: 64 compiler: gcc 
  v: 8.3.0 Desktop: Gnome 3.31.92 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Quad Core model: Intel Core i7-6700HQ bits: 64 type: MT MCP 
  arch: Skylake-S rev: 3 L2 cache: 6144 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 41472 
  Speed: 900 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 900 2: 900 
  3: 900 4: 901 5: 900 6: 900 7: 900 8: 900

---

### Post by Doug S on 2019-03-14
With the pending kernel 5.1-rc1, and already in the daily, there will be a new Timer Events Oriented (TEO) idle governor (I have mentioned it herein before).
Currently, and in today's daily, the related kernel configuration is:

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]grep -B 6 -A 1 IDLE_GOV_TEO .config-5.0.0-999-lowlatency[/COLOR]
#
# CPU Idle
#
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR="#FF0000"]# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
CONFIG_INTEL_IDLE=y

```whereas this would be great, and allow users that do not compile the kernel for themselves to be able try try the new governor:
```
#
# CPU Idle
#
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR="#FF0000"]CONFIG_CPU_IDLE_GOV_TEO=y[/COLOR]
CONFIG_INTEL_IDLE=y

```Does anybody know how to request a mainline kernel configuration change?
I have searched the wikis and such.

---

### Post by #&amp;thj^% on 2019-03-14
> **Doug S said:**
> Does anybody know how to request a mainline kernel configuration change?
I have searched the wikis and such.

There may be a better way to this and maybe you already know  this much but I use these:
IRC
[list]
    [*]We are on FreeNode in the #ubuntu-kernel channel 

Mailing List

    [*]kernel-team@lists.ubuntu.com

    [*]you can subscribe here: [https://lists.ubuntu.com/mailman/listinfo/kernel-team](https://lists.ubuntu.com/mailman/listinfo/kernel-team)[/list]

    We run our mailing list much like the Linux Kernel Mailing List (LKML). Users can propose patches, ask questions and find general info. This list has medium traffic volume. For more info you can read [https://wiki.ubuntu.com/KernelTeam/KernelPatches](https://wiki.ubuntu.com/KernelTeam/KernelPatches)

---

### Post by Doug S on 2019-03-14
@1fallen: Thanks for your reply. I went on [IRC and did get some answers]("https://irclogs.ubuntu.com/2019/03/14/%23ubuntu-kernel.html").

The reason I did not try IRC to start with is that I have noticed it doesn't seem to be used much anymore (as of the last year or so). I often try to look back at IRC stuff via the [logs]("https://irclogs.ubuntu.com/") and the kernel channel has become very quite.

---

