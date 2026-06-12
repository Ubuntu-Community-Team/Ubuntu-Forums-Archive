---
title: "Kernel 4.13RC (Release Candidate) series"
date: 2017-07-16
forum: Ubuntu Development Version
---

### Post by Doug S on 2017-07-16
[Kernel 4.13rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc1/") has been released, a day earlier than normal.

I've only been running it for a few minutes, so all I can really say is that it booted O.K. on my test 16.04 server.

EDIT: The output of the "cpu MHz" line of /proc/cpuinfo has changed. On my computer it always just prints TSC, regardless of what is going on. The related email thread for this is [here]("http://marc.info/?t=149766883400002&r=1&w=2"), and I did see it at the time, and was worried about it at the time, but waited for 4.13-rc1 to see the results of the change. I do not like it, however it is true that one can use "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" to observe actual CPU frequencies (close enough, in my opinion).

Example (my server is fairly idle):

```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
1605192
1605474
1606982
1605552
1605181
1605209
1605716
1605563

```

---

### Post by rrnbtter on 2017-07-18
Greetings,
There has been extensive improvement and support added for RTL WIFI devices added to this kernel. RTL wifi now working fine. 

inxi -Sxx && $DESKTOP_SESSION
System:    Host: rrnbtter-110-15ISK Kernel: 4.13.0-041300rc1-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2) dm: gdm3
           Distro: Ubuntu Artful Aardvark (development branch)
gnome-wayland
$XDG_SESSION_TYPE
wayland

*-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller

---

### Post by Doug S on 2017-08-07
> **Doug S said:**
> ... however it is true that one can use "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" to observe actual CPU frequencies (close enough, in my opinion).For anyone else that has observed extremely stale data when using "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" to observe actual CPU frequencies (on modern Intel processors), the issue should be fixed in the now available [4.13-rc4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc4/").

---

### Post by #&amp;thj^% on 2017-08-07
> **Doug S said:**
> For anyone else that has observed extremely stale data when using "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" to observe actual CPU frequencies (on modern Intel processors), the issue should be fixed in the now available [4.13-rc4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc4/").

Thanks Doug
Current:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
899945
899945
899945
899945

```
```
grep MHz /proc/cpuinfo
cpu MHz         : 2900.225
cpu MHz		: 2900.225
cpu MHz		: 2900.555
cpu MHz		: 2894.293

```

---

### Post by Doug S on 2017-08-17
... Just catching up...
I am compiling kernel 4.13-rc5 now. It doesn't seem to be available on the [Ubuntu Kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). (I am compiling using the [Ubuntu kernel 4.13-rc4 kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc4/") configuration file.) There are a few [dailiys]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/") missing also. I'd suggest users that do not compile their own, just use the [daily kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/") until -rc6 is available.

... later ...
kernel seems O.K. so far, but haven't done much.```
$ uname -a
Linux s15 4.13.0-rc5-stock #273 SMP Thu Aug 17 08:11:15 PDT 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2017-08-21
[Kernel 4.13-rc6 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc6/"). Glad to see the Ubuntu PPA is working again.
I am not running it yet, but do observe a number of kernel configuration changes between -rc4 and -rc6.

---

### Post by amano on 2017-08-22
Do we know if 17.10 will ship with 4.12 or 4.13?

---

### Post by deadflowr on 2017-08-22
> **amano said:**
> Do we know if 17.10 will ship with 4.12 or 4.13?

The aim is 4.13.
[https://insights.ubuntu.com/2017/06/15/kernel-team-summary-june-15-2017/]("https://insights.ubuntu.com/2017/06/15/kernel-team-summary-june-15-2017/")
> We intend to target a 4.13 kernel for the Ubuntu 17.10 release. The Ubuntu 17.10 Kernel Freeze is Thurs Oct 5, 2017.
Unless the 4.13 kernel is totally broken I cannot see any reason why they won't hit the target.

---

### Post by Doug S on 2017-08-28
Kernel [4.13-rc7]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc7/") is available. I have only been running it for a few minutes, so far.

---

### Post by IanW on 2017-09-04
The final version of kernel 4.13 has been released, and is [in the PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13/")

---

### Post by Doug S on 2017-11-05
> **Doug S said:**
> [Kernel 4.13rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc1/") has been released, a day earlier than normal.

I've only been running it for a few minutes, so all I can really say is that it booted O.K. on my test 16.04 server.

EDIT: The output of the "cpu MHz" line of /proc/cpuinfo has changed. On my computer it always just prints TSC, regardless of what is going on. The related email thread for this is [here]("http://marc.info/?t=149766883400002&r=1&w=2"), and I did see it at the time, and was worried about it at the time, but waited for 4.13-rc1 to see the results of the change. I do not like it, however it is true that one can use "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" to observe actual CPU frequencies (close enough, in my opinion).

Example (my server is fairly idle):

```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
cpu MHz         : 3411.073
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
1605192
1605474
1606982
1605552
1605181
1605209
1605716
1605563

```This behavior has been reverted (and queued for backporting) in kernel 4.14-rc8.

---

