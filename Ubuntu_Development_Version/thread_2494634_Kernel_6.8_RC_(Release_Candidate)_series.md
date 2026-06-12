---
title: "Kernel 6.8 RC (Release Candidate) series"
date: 2024-01-22
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-01-22
[Kernel 6.8-rc1]("https://kernel.ubuntu.com/mainline/v6.8-rc1/") is available.

Just starting our usual per kernel RC series thread here. All I have done so far is compile and boot:

```
doug@s19:~$ uname -a
Linux s19 6.8.0-rc1-stock #1199 SMP PREEMPT_DYNAMIC Mon Jan 22 08:07:29 PST 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by fyfe54 on 2024-01-22
Installed. So far, so good.

---

### Post by #&amp;thj^% on 2024-01-22
To be expected breaks nVidia and zfs FYI.

I as well have not been running it long enough to point good or bad. 
```
uname -r
6.8.0-060800rc1-generic

```

---

### Post by corradoventu on 2024-01-27
After installing kernel 6.8.0-060800rc1-generic on my Ubuntu Noble from [https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/) firefox and snap-store do not start 
[https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/2](https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/2)

---

### Post by Bashing-om on 2024-01-27
Introducing Kernel 6.8 for the 24.04 Noble Numbat Release 

[https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/](https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/)

"An experimental build of the latest Ubuntu Noble kernel based on the latest 6.8-rc* is available in ppa:canonical-kernel-team/unstable (Unstable Kernel Builds : &#8220;Canonical Kernel Team&#8221; team 6), this kernel will be updated weekly, until it will replace the main kernel in 24.04."

How about them apples :P Who'da thunk it

---

### Post by Doug S on 2024-01-28
> **Bashing-om said:**
> Introducing Kernel 6.8 for the 24.04 Noble Numbat Release 

[https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/](https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/)

"An experimental build of the latest Ubuntu Noble kernel based on the latest 6.8-rc* is available in ppa:canonical-kernel-team/unstable (Unstable Kernel Builds : &#8220;Canonical Kernel Team&#8221; team 6), this kernel will be updated weekly, until it will replace the main kernel in 24.04."

How about them apples :P Who'da thunk itI am particularly interested in, and have chimed in on:
> Additional non-upstream features that we may consider for inclusion (WIP):

    Enable low-latency features by default ([Bug #2023007 &#8220;kernel .config lowlatency improvements&#8221; : Bugs : linux-lowlatency package : Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2023007"))


EDIT: Sorry, it is [this related bug]("https://bugs.launchpad.net/ubuntu/noble/+source/linux/+bug/2051342") that I chimed in on and would like to be included in 24.04.

---

### Post by Doug S on 2024-01-28
While kernel 6.8-rc2 is available at [kernel.org]("https://kernel.org/"), the [Ubuntu mainline]("https://kernel.ubuntu.com/mainline/v6.8-rc2/") AMD64 compile failed with the good old:

```
make[4]: /bin/sh: Resource temporarily unavailable
```

EDIT: My first time booting -rc2 the system ended up in recovery mode. Another re-boot and it was fine. Operator error or something else, I don't know.

```
doug@s19:~$ uname -a
Linux s19 6.8.0-rc2-stock #1204 SMP PREEMPT_DYNAMIC Sun Jan 28 20:11:00 PST 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by corradoventu on 2024-02-04
6.8.0-060800rc3 from [https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/) works fine
```
corrado@corrado-n9-nn-1210:~$ inxi -SMxc
System:
  Host: corrado-n9-nn-1210 Kernel: 6.8.0-060800rc3-generic arch: x86_64
    bits: 64 compiler: gcc v: 13.2.0
  Desktop: GNOME v: 45.3 Distro: Ubuntu 24.04 (Noble Numbat)
Machine:
  Type: Desktop System: Gigabyte product: H510M H v: -CF
    serial: <superuser required>
  Mobo: Gigabyte model: H510M H v: x.x serial: <superuser required>
    UEFI: American Megatrends LLC. v: F14 date: 03/25/2022
corrado@corrado-n9-nn-1210:~$ 
```

---

### Post by Doug S on 2024-02-09
For these conditions:
CPU frequency scaling driver: intel_cpufreq (a.k.a intel_pstate in passive mode)
CPU frequency scaling governor: schedutil
HWP (HardWare Pstate) control (a.k.a. Intel_speedshift): Enabled

Reduced maximum CPU frequencies are not been enforced. Kernel 6.7 was fine. Kernel 6.8-rc1 is not.
I am about 2/3rds of the way through bisecting the kernel in an attempt to isolate the bad commit.

I have not tried other configurations.

Processor: Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz

EDIT:
```

# first bad commit: [9c0b4bb7f6303c9c4e2e34984c46f5a86478f84d] sched/cpufreq: Rework schedutil governor performance estimation

```

---

### Post by corradoventu on 2024-02-09
I had problems with Kernel 6.8-rc1, Kernel 6.8-rc3 is ok for me.

---

### Post by IanW on 2024-02-12
rc4 has appeared on Mainline

---

### Post by corradoventu on 2024-02-12
```
corrado@corrado-n9-nn-1210:~$ inxi -SCxc
System:
  Host: corrado-n9-nn-1210 Kernel: 6.8.0-060800rc4-generic arch: x86_64
    bits: 64 compiler: gcc v: 13.2.0
  Desktop: GNOME v: 45.3 Distro: Ubuntu 24.04 (Noble Numbat)
CPU:
  Info: 6-core model: 11th Gen Intel Core i5-11400 bits: 64 type: MT MCP
    arch: Rocket Lake rev: 1 cache: L1: 480 KiB L2: 3 MiB L3: 12 MiB
  Speed (MHz): avg: 808 high: 897 min/max: 800/4400 cores: 1: 800 2: 800
    3: 897 4: 800 5: 800 6: 800 7: 800 8: 800 9: 800 10: 800 11: 800 12: 800
    bogomips: 62208
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
corrado@corrado-n9-nn-1210:~$
```

---

### Post by IanW on 2024-02-19
A wild [rc5]("https://kernel.ubuntu.com/mainline/daily/2024-02-19/") appears

---

### Post by corradoventu on 2024-02-19
```
corrado@corrado-n9-nn-1210:~$ inxi -SMxc
System:
  Host: corrado-n9-nn-1210 Kernel: 6.8.0-060800rc5-generic arch: x86_64
    bits: 64 compiler: gcc v: 13.2.0
  Desktop: GNOME v: 45.3 Distro: Ubuntu 24.04 (Noble Numbat)
Machine:
  Type: Desktop System: Gigabyte product: H510M H v: -CF
    serial: <superuser required>
  Mobo: Gigabyte model: H510M H v: x.x serial: <superuser required>
    UEFI: American Megatrends LLC. v: F14 date: 03/25/2022
corrado@corrado-n9-nn-1210:~$
```

---

### Post by Doug S on 2024-02-19
The issue I raised in [post #9 ]("https://ubuntuforums.org/showthread.php?t=2494634&p=14178840#post14178840")above has [been isolated]("https://lore.kernel.org/linux-pm/CAKfTPtC82YXOw5yYPNkHHyF+DYSG+Ts9OjnwsVjbd_HcUsZQMg@mail.gmail.com/") and a [patch submitted upstream]("https://lore.kernel.org/linux-pm/20240217213010.2466-1-dsmythies@telus.net/T/#u"). Hopefully the fix will be included in -rc6.

---

### Post by Claus7 on 2024-02-24
Hello,

are we aware if this:
> index 1 is out of range for type 'SUPGIPCPU [1]'
UBSAN: array-index-out-of-bounds in /var/lib/dkms/virtualbox/7.0.14/build/vboxdrv/common/log/log.c:1558:29
has been fixed?

*Doug S*, if I recall correctly, you had mentioned this bug before in previous kernel versions.

Regards!

---

### Post by Doug S on 2024-02-24
> **Claus7 said:**
> Hello,

are we aware if this:

has been fixed?

*Doug S*, if I recall correctly, you had mentioned this bug before in previous kernel versions.

Regards!Yes, I did experience a similar array out of bounds error message during [the kernel 6.6 RC series]("https://ubuntuforums.org/showthread.php?t=2490640&p=14157681#post14157681"), but it was for different reason/bug and was [fixed as of kernel 6.6-rc3]("https://ubuntuforums.org/showthread.php?t=2490640&page=2&p=14158993#post14158993"). I do not use virtualbox and can not help with this one.

---

### Post by Claus7 on 2024-02-24
Hello,

> **Doug S said:**
> Yes, I did experience a similar array out of bounds error message during [the kernel 6.6 RC series]("https://ubuntuforums.org/showthread.php?t=2490640&p=14157681#post14157681"), but it was for different reason/bug and was [fixed as of kernel 6.6-rc3]("https://ubuntuforums.org/showthread.php?t=2490640&page=2&p=14158993#post14158993"). I do not use virtualbox and can not help with this one.

thank you for your response.

Regards!

---

### Post by corradoventu on 2024-02-26
```
corrado@corrado-n9-nn-1210:~$ inxi -SMxc
System:
  Host: corrado-n9-nn-1210 Kernel: 6.8.0-060800rc6-generic arch: x86_64
    bits: 64 compiler: gcc v: 13.2.0
  Desktop: GNOME v: 45.3 Distro: Ubuntu 24.04 (Noble Numbat)
Machine:
  Type: Desktop System: Gigabyte product: H510M H v: -CF
    serial: <superuser required>
  Mobo: Gigabyte model: H510M H v: x.x serial: <superuser required>
    UEFI: American Megatrends LLC. v: F14 date: 03/25/2022
corrado@corrado-n9-nn-1210:~$
```

---

### Post by 3vi1 on 2024-02-29
Been using RC6 here for a couple of days too.  Been smooth sailing so far.

[FONT=monospace][COLOR=#54FF54]**12:06:47 **[/COLOR][COLOR=#18B2B2]evil[/COLOR][COLOR=#FFFFFF]**@**[/COLOR][COLOR=#5454FF]**H510 **[/COLOR][COLOR=#FFFF54]**~**[/COLOR][COLOR=#54FF54]**» **[/COLOR][COLOR=#000000]inxi -SMxc[/COLOR]
System:
  Host: H510 Kernel: 6.8.0-060800rc6-generic arch: x86_64 bits: 64
    compiler: gcc v: 13.2.0
  Desktop: KDE Plasma v: 5.27.10 Distro: Kubuntu 24.04 (Noble Numbat)
    base: Ubuntu
Machine:
  Type: Desktop Mobo: Micro-Star model: MPG X570 GAMING PLUS (MS-7C37) v: 2.0
    serial: <superuser required> UEFI: American Megatrends v: A.84

[/FONT]

---

### Post by Doug S on 2024-03-03
Kernel 6.8-rc7 is available. The patch for the issue I detailed in [post #9]("https://ubuntuforums.org/showthread.php?t=2494634&p=14178840#post14178840") above is included. See commit:

```
f0a0fc10abb0 cpufreq: intel_pstate: fix pstate limits enforcement for adjust_perf call back
```

...Interesting... I am getting a couple of errors compiling the kernel.

EDIT: The compile issue is a function of GCC version, as determined in [this thread]("https://lore.kernel.org/lkml/CANn89i+4Q2L7Gd5zGrSwT_v2wjL-ZKEFcM=oQ9w090+xc57HTQ@mail.gmail.com/t/#ma010f32d8617b0f8364c0bd4ad50d617417a3c91") (see the end).

Indeed it compiles fine when I boot my test server as 24.04, but not when it is booted as 20.04:
gcc (Ubuntu 9.4.0-1ubuntu1~20.04.2) 9.4.0" -> "gcc (Ubuntu 13.2.0-13ubuntu1) 13.2.0

---

### Post by corradoventu on 2024-03-04
But 6.8 is already arrived in Ubuntu Noble:
```
corrado@corrado-n2-nn-0220:~$ inxi -Scx
System:
  Host: corrado-n2-nn-0220 Kernel: 6.8.0-11-generic arch: x86_64 bits: 64
    compiler: gcc v: 13.2.0
  Desktop: GNOME v: 45.3 Distro: Ubuntu 24.04 (Noble Numbat)
corrado@corrado-n2-nn-0220:~$ 
```

---

### Post by Doug S on 2024-03-04
> **corradoventu said:**
> But 6.8 is already arrived in Ubuntu Noble:
Yes, but it is still only at the RC (Release Candidate) level upstream.

---

### Post by Doug S on 2024-03-10
Kernel 6.8 has been released.

The issue I mentioned in [post #21]("https://ubuntuforums.org/showthread.php?t=2494634&page=3&p=14181388#post14181388") above has been fixed and I am able to compile the kernel under the version of the gcc compiler used in Ubuntu 20.04.

```
doug@s19:~$ uname -a
Linux s19 6.8.0-stock #1245 SMP PREEMPT_DYNAMIC Sun Mar 10 16:29:09 PDT 2024 x86_64 x86_64 x86_64 GNU/Linux
```

EDIT: I don't know why the Ubuntu mainline PPA version never showed up. The daily log says "No space left on device".

---

### Post by TenPlus1 on 2024-03-13
Using 6.8.0-060800rc7 kernel and while scrolling websites it will randomly blank screen for 3 seconds then re-appear, only happens once and journalctl shows this error :-

Mar 13 09:46:13 ThinkPad-P14s-Gen-2a rtkit-daemon[912]: Successfully made thread 4974 of process 3135 ow>
Mar 13 09:46:13 ThinkPad-P14s-Gen-2a rtkit-daemon[912]: Supervising 7 threads of 4 processes of 1 users.
Mar 13 09:47:12 ThinkPad-P14s-Gen-2a kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring vcn_dec tim>
Mar 13 09:47:12 ThinkPad-P14s-Gen-2a kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process informat>
Mar 13 09:47:12 ThinkPad-P14s-Gen-2a kernel: amdgpu 0000:06:00.0: amdgpu: GPU reset begin!
Mar 13 09:47:13 ThinkPad-P14s-Gen-2a kernel: [drm] Register(0) [mmUVD_POWER_STATUS] failed to reach valu>
Mar 13 09:47:13 ThinkPad-P14s-Gen-2a kernel: [drm] Register(0) [mmUVD_RBC_RB_RPTR] failed to reach value>
Mar 13 09:47:13 ThinkPad-P14s-Gen-2a kernel: [drm] Register(0) [mmUVD_POWER_STATUS] failed to reach valu>

---

### Post by fyfe54 on 2024-03-13
Kernel 6.8 has been released.

Now available in Mainline.

---

### Post by Doug S on 2024-03-14
> **fyfe54 said:**
> Kernel 6.8 has been released.

Now available in Mainline.Oh, Thanks. Finally.

I see that "generic" has finally moved to 1000Hz. In my opinion, this is huge news, and about time:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-6.8.0-060800rc7-generic .config-6.8.0-060800-generic[/COLOR]
-GCC11_NO_ARRAY_BOUNDS y
-TICK_CPU_ACCOUNTING y
 CC_VERSION_TEXT "x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-16ubuntu1) 13.2.0" -> "x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-17ubuntu2) 13.2.0"
 CONSOLE_LOGLEVEL_QUIET 4 -> 3
[COLOR="#FF0000"] HZ 250 -> 1000[/COLOR]
 [COLOR="#FF0000"]HZ_1000 n -> y[/COLOR]
 HZ_250 y -> n
 LATENCYTOP n -> y
 NO_HZ_FULL n -> y
 NO_HZ_IDLE y -> n
 VIRT_CPU_ACCOUNTING_GEN n -> y
+CONTEXT_TRACKING_USER y
+CONTEXT_TRACKING_USER_FORCE n
+GCC10_NO_ARRAY_BOUNDS y
+RCU_LAZY y
+RCU_NOCB_CPU y
+RCU_NOCB_CPU_DEFAULT_ALL n
+VIRT_CPU_ACCOUNTING y
```

---

### Post by corradoventu on 2024-03-14
For the change HZ 250 -> 1000 see:
[https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255](https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255)

---

