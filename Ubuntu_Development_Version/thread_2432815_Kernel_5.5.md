---
title: "Kernel 5.5"
date: 2019-12-09
forum: Ubuntu Development Version
---

### Post by zika on 2019-12-09
RC1 is out.
```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.5.0-050500rc1-lowlatency
Found initrd image: /boot/initrd.img-5.5.0-050500rc1-lowlatency
Found linux image: /boot/vmlinuz-5.5.0-050500rc1-generic
Found initrd image: /boot/initrd.img-5.5.0-050500rc1-generic
Found linux image: /boot/vmlinuz-5.5.0-999-lowlatency
Found initrd image: /boot/initrd.img-5.5.0-999-lowlatency
Found linux image: /boot/vmlinuz-5.5.0-999-generic
Found initrd image: /boot/initrd.img-5.5.0-999-generic
Found linux image: /boot/vmlinuz-5.5.0-994-lowlatency
Found initrd image: /boot/initrd.img-5.5.0-994-lowlatency
Found linux image: /boot/vmlinuz-5.5.0-994-generic
Found initrd image: /boot/initrd.img-5.5.0-994-generic
Found linux image: /boot/vmlinuz-5.3.0-25-lowlatency
Found initrd image: /boot/initrd.img-5.3.0-25-lowlatency
Found linux image: /boot/vmlinuz-5.3.0-25-generic
Found initrd image: /boot/initrd.img-5.3.0-25-generic
```;)

---

### Post by mrfelker on 2019-12-11
Kernel 5.5 rc1 is available and is owrking fine here.

---

### Post by zika on 2019-12-12
[https://ubuntuforums.org/showthread.php?t=2432815](https://ubuntuforums.org/showthread.php?t=2432815)

---

### Post by slickymaster on 2019-12-12
Threads merged

---

### Post by Doug S on 2019-12-16
[Kernel 5.5-rc2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.5-rc2/") is available:

```
doug@s18:~$ uname -a
Linux s18 5.5.0-050500rc2-lowlatency #201912151930 SMP PREEMPT Mon Dec 16 00:45:08 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```I have only been running it for a few minutes, but I ran 5.5-rc1 for most of the week without issues.

Link back trail to previous Kernel rc series threads: [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

---

### Post by Doug S on 2019-12-27
Among other kernel configuration changes, sometime during the kernel 5.4-rc series Ubuntu changed from "CONFIG_UCLAMP_TASK_GROUP is not set" to "CONFIG_UCLAMP_TASK_GROUP=y".
The new cgroup v2 related code involved was only added as of kernel 5.4-rc1, and it has issues.
On one of two Ubuntu server test computers, when the schedutil CPU frequency scaling governor is used with either the acpi-cpufreq or intel_cpufreq CPU frequency scaling drivers, the system response is more like the performance governor as opposed to the expected response of the schedutil governor.
From what I've experienced, and been challenged by, it is premature to be setting CONFIG_UCLAMP_TASK_GROUP in the kernel configuration, and if I reset it, the resulting system response is as expected for the schedutil governor.

This issue has being driving me crazy for over a month. I have misdiagnosed it and come to incorrect conclusions several times. After a few weeks, someone upstream followed up, and now it is finally understood.

References:
[Proposed patch]("https://marc.info/?l=linux-kernel&m=157718847019076&w=2")
[proposed patch test results]("https://marc.info/?l=linux-kernel&m=157715025411694&w=2")
[pre-patch test reaults]("https://marc.info/?l=linux-kernel&m=157708724811397&w=2")

---

### Post by corradoventu on 2020-01-13
also rc6 is here
```
corrado@corrado-p9-ff-0104-x:~$ inxi -Sxx
System:
  Host: corrado-p9-ff-0104-x Kernel: 5.5.0-050500rc6-generic x86_64 bits: 64 
  compiler: gcc v: 9.2.1 Desktop: Gnome 3.34.3 wm: gnome-shell dm: GDM3 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
corrado@corrado-p9-ff-0104-x:~$ 
```

---

### Post by IanW on 2020-01-26
Hope Ubuntu releases a _signed_ 5.5 kernel soon. Due to needing to "secure boot" for reasons, I'm currently stuck on 5.4.0-9, which is based on 5.4.3.

The problem is that 5.4 3 introduced a nasty audio bug ([#204477]("https://bugzilla.kernel.org/show_bug.cgi?id=204477"))for those of us using Nvidia GPU's to send audio over HDMI & Bluetooth to our monitor's speakers.

EDIT: Today's 5.4.0-12 release fixes the issue I described. Also, 5.5 was finally released by Linus.

---

### Post by corradoventu on 2020-02-09
Also 5.5.2 is released but unfortunately on focal we will have the 5.4 kernel
[https://www.omgubuntu.co.uk/2020/02/ubuntu-20-04-kernel-5-4-lts](https://www.omgubuntu.co.uk/2020/02/ubuntu-20-04-kernel-5-4-lts)

---

