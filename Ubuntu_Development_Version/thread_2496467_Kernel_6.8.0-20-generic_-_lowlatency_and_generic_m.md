---
title: "Kernel 6.8.0-20-generic - lowlatency and generic merge into one"
date: 2024-03-29
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-03-29
Finally, as of the just released kernel 6.8.0-20-generic, the low latency kernel configuration has been put into the generic kernel.
The kernel configuration differences are:

```
doug@s19:~/kernel/linux$ scripts/diffconfig /boot/config-6.8.0-11-generic /boot/config-6.8.0-20-generic
-GCC11_NO_ARRAY_BOUNDS y
-TICK_CPU_ACCOUNTING y
 CC_VERSION_TEXT "x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-13ubuntu1) 13.2.0" -> "x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-19ubuntu1) 13.2.0"
 CONSOLE_LOGLEVEL_QUIET 4 -> 3
 [COLOR="#FF0000"]HZ 250 -> 1000
 HZ_1000 n -> y
 HZ_250 y -> n[/COLOR]
 INTEL_IOMMU_DEFAULT_ON n -> y
 INTEL_IOMMU_SCALABLE_MODE_DEFAULT_ON n -> y
 LATENCYTOP n -> y
 [COLOR="#FF0000"]NO_HZ_FULL n -> y
 NO_HZ_IDLE y -> n[/COLOR]
 VERSION_SIGNATURE "Ubuntu 6.8.0-11.11-generic 6.8.0-rc4" -> "Ubuntu 6.8.0-20.20-generic 6.8.1"
 VIRT_CPU_ACCOUNTING_GEN n -> y
+CONTEXT_TRACKING_USER y
+CONTEXT_TRACKING_USER_FORCE n
+CRYPTO_DEV_QAT_ERROR_INJECTION n
+DRM_NOUVEAU_GSP_DEFAULT n
+GCC10_NO_ARRAY_BOUNDS y
+GCC_ASM_GOTO_OUTPUT_WORKAROUND y
+HDC3020 m
+MITIGATION_RFDS y
+RCU_LAZY y
+RCU_LAZY_DEFAULT_OFF y
+RCU_NOCB_CPU y
+RCU_NOCB_CPU_DEFAULT_ALL n
+VIRT_CPU_ACCOUNTING y
```

Users should be aware and watch for anything odd.
I am very happy about this change and think it is years overdue.

I do wonder about this difference between lowlatency and the new combined:

```
doug@s19:~/kernel/linux$ scripts/diffconfig /boot/config-6.8.0-7-lowlatency /boot/config-6.8.0-20-generic
...
 PREEMPT y -> n
 PREEMPT_VOLUNTARY n -> y
...

```

References:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051342]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051342")
[https://www.phoronix.com/news/Ubuntu-Generic-LL-Kernel]("https://www.phoronix.com/news/Ubuntu-Generic-LL-Kernel")
[https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255]("https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255")

---

### Post by #&amp;thj^% on 2024-03-29
> **Doug S said:**
> 
Users should be aware and watch for anything odd.
I am very happy about this change and think it is years overdue.

I do wonder about this difference between lowlatency and the new combined:


That makes two of us on both statements:
```
root@me-on-zfs:/sys/kernel/tracing# tail -10 trace
          <idle>-0       [007] d.h1.  2313.235147: #167376 context    irq timer_latency      6795 ns
           <...>-47436   [007] ....1  2313.235152: #167376 context thread timer_latency     10985 ns
          <idle>-0       [008] d.h1.  2313.235178: #167376 context    irq timer_latency      6589 ns
           <...>-47437   [008] ....1  2313.235182: #167376 context thread timer_latency     10919 ns
          <idle>-0       [009] d.h1.  2313.235216: #167376 context    irq timer_latency      6315 ns
           <...>-47438   [009] ....1  2313.235220: #167376 context thread timer_latency     10576 ns
          <idle>-0       [010] d.h1.  2313.235260: #167376 context    irq timer_latency      6880 ns
           <...>-47439   [010] ....1  2313.235264: #167376 context thread timer_latency     11140 ns
          <idle>-0       [011] d.h1.  2313.235291: #167376 context    irq timer_latency      6465 ns
           <...>-47440   [011] ....1  2313.235295: #167376 context thread timer_latency     10725 ns

```
And:
```
root@me-on-zfs:/sys/kernel/tracing#  echo 500 > osnoise/stop_tracing_total_us
root@me-on-zfs:/sys/kernel/tracing# tail -21 per_cpu/cpu7/trace
           <...>-47436   [007] ....1  2549.953151: #404094 context thread timer_latency     10963 ns
          <idle>-0       [007] d.h1.  2549.954147: #404095 context    irq timer_latency      6944 ns
           <...>-47436   [007] ....1  2549.954151: #404095 context thread timer_latency     10715 ns
          <idle>-0       [007] d.h1.  2549.955147: #404096 context    irq timer_latency      6626 ns
           <...>-47436   [007] ....1  2549.955152: #404096 context thread timer_latency     10956 ns
          <idle>-0       [007] d.h1.  2549.956147: #404097 context    irq timer_latency      6727 ns
           <...>-47436   [007] ....1  2549.956151: #404097 context thread timer_latency     10988 ns
          <idle>-0       [007] d.h1.  2549.957147: #404098 context    irq timer_latency      6409 ns
           <...>-47436   [007] ....1  2549.957151: #404098 context thread timer_latency     10600 ns
          <idle>-0       [007] d.h1.  2549.958148: #404099 context    irq timer_latency      7069 ns
           <...>-47436   [007] ....1  2549.958152: #404099 context thread timer_latency     11330 ns
          <idle>-0       [007] d.h1.  2549.959147: #404100 context    irq timer_latency      6821 ns
           <...>-47436   [007] ....1  2549.959152: #404100 context thread timer_latency     11152 ns
          <idle>-0       [007] d.h1.  2549.960148: #404101 context    irq timer_latency      7132 ns
           <...>-47436   [007] ....1  2549.960152: #404101 context thread timer_latency     10974 ns
          <idle>-0       [007] d.h1.  2549.961147: #404102 context    irq timer_latency      6884 ns
           <...>-47436   [007] ....1  2549.961152: #404102 context thread timer_latency     10586 ns
          <idle>-0       [007] d.h1.  2549.962147: #404103 context    irq timer_latency      6985 ns
           <...>-47436   [007] ....1  2549.962151: #404103 context thread timer_latency     11316 ns
          <idle>-0       [007] d.h1.  2549.963147: #404104 context    irq timer_latency      6737 ns
           <...>-47436   [007] ....1  2549.963152: #404104 context thread timer_latency     11068 ns

```

I see very little difference between the two

---

### Post by corradoventu on 2024-03-30
Kernel 6.8.0-20 released? but on my Noble just updated i'm still on 6.8.0-11 (also on partition with proposed enabled)

---

### Post by Doug S on 2024-03-30
> **corradoventu said:**
> Kernel 6.8.0-20 released? but on my Noble just updated i'm still on 6.8.0-11 (also on partition with proposed enabled)Yes, I am confused. My Ubuntu 24.04 server updated to kernel 6.8.0-20. However, my Ubuntu 24.04 Desktop VM is still at kernel 6.8.0-11. My Desktop VM is still a mess after the upgrade fiasco that started a few days ago, so I wasn't going to worry about it until after the mess is all sorted.

---

### Post by corradoventu on 2024-03-30
Kernel 6.8.0.20 seems rolled back: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by deadflowr on 2024-03-30
Most likely has to do with the fact they are rolling back everything.
Cause is the xz-utils debacle.

---

### Post by #&amp;thj^% on 2024-03-30
> **deadflowr said:**
> Most likely has to do with the fact they are rolling back everything.
Cause is the xz-utils debacle.

Yep I'm going to trash this install very soon.
```
 xz --version
xz (XZ Utils) 5.4.5
liblzma 5.4.5

```

I got the new kernel on desktop:
```
uname -r
6.8.0-20-generic

```
The bad news:
```
apt policy xz-utils
xz-utils:
  Installed: 5.4.5-0.3
  Candidate: 5.4.5-0.3
  Version table:
     5.6.1+really5.4.5-1 100
        100 http://archive.ubuntu.com/ubuntu noble-proposed/main amd64 Packages
 *** 5.4.5-0.3 500
        500 http://us.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by corradoventu on 2024-03-31
After today updates:
```
corrado@corrado-n5-nn-0324:~$ apt policy xz-utils
xz-utils:
  Installed: 5.6.1+really5.4.5-1
  Candidate: 5.6.1+really5.4.5-1
  Version table:
 *** 5.6.1+really5.4.5-1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-n5-nn-0324:~$ apt changelog xz-utils
xz-utils (5.6.1+really5.4.5-1) unstable; urgency=critical
  * Non-maintainer upload by the Security Team.
  * Revert back to the 5.4.5-0.2 version 
 -- Salvatore Bonaccorso <carnil@debian.org>  Thu, 28 Mar 2024 15:59:38 +0100
```
But i have kernel 6.8.0-11-generic where did the 6.8.0-20 kernel go?

Edit: discourse.ubuntu.com is down from Yesterday

---

### Post by dajonaga on 2024-03-31
> **corradoventu said:**
> After today updates:
```
corrado@corrado-n5-nn-0324:~$ apt policy xz-utils
xz-utils:
  Installed: 5.6.1+really5.4.5-1
  Candidate: 5.6.1+really5.4.5-1
  Version table:
 *** 5.6.1+really5.4.5-1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-n5-nn-0324:~$ apt changelog xz-utils
xz-utils (5.6.1+really5.4.5-1) unstable; urgency=critical
  * Non-maintainer upload by the Security Team.
  * Revert back to the 5.4.5-0.2 version 
 -- Salvatore Bonaccorso <carnil@debian.org>  Thu, 28 Mar 2024 15:59:38 +0100
```
But i have kernel 6.8.0-11-generic where did the 6.8.0-20 kernel go?

Edit: discourse.ubuntu.com is down from Yesterday

Now I'm wondering... is that 5.6.1+really5.4.5-1 the latest patched, non vulnerable, "we're good".... version... or not?

---

### Post by MAFoElffen on 2024-03-31
Not sure either(???) Upstream Debian also shows that version as the source.

---

### Post by #&amp;thj^% on 2024-03-31
A nice check ie:
```
ldd "$(command -v sshd)"
```

A look from Arch:
```
ldd "$(command -v sshd)"
        linux-vdso.so.1 (0x00007ffe96a52000)
        libcrypt.so.2 => /usr/lib/libcrypt.so.2 (0x0000781b92471000)
        libpam.so.0 => /usr/lib/libpam.so.0 (0x0000781b9245f000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x0000781b92404000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x0000781b9231a000)
        libcrypto.so.3 => /usr/lib/libcrypto.so.3 (0x0000781b91c00000)
        libz.so.1 => /usr/lib/libz.so.1 (0x0000781b922fb000)
        libc.so.6 => /usr/lib/libc.so.6 (0x0000781b91800000)
        libaudit.so.1 => /usr/lib/libaudit.so.1 (0x0000781b922c9000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x0000781b92296000)
        libcom_err.so.2 => /usr/lib/libcom_err.so.2 (0x0000781b92290000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x0000781b92282000)
        libkeyutils.so.1 => /usr/lib/libkeyutils.so.1 (0x0000781b9227b000)
        libresolv.so.2 => /usr/lib/libresolv.so.2 (0x0000781b92267000)
        /lib64/ld-linux-x86-64.so.2 => /usr/lib64/ld-linux-x86-64.so.2 (0x0000781b925e2000)
        libcap-ng.so.0 => /usr/lib/libcap-ng.so.0 (0x0000781b9225f000)

```

---

### Post by MAFoElffen on 2024-03-31
The thing I'm looking out for is... The canned warnings that were posted in the Wiki pages with low-latency kernels previous to 'this push' where that some modules may not work, or failed to build... That was for both the RT and low-latency series kernels. But I have heard that there have been a lot of patches to get around those issues, and maybe those warnings might not be relevant "today".

Honestly: IDK. Time will tell how this goes.

@Doug S --- How do you feel about all this as it relates to Server?

---

### Post by Doug S on 2024-04-03
> **MAFoElffen said:**
> The thing I'm looking out for is... The canned warnings that were posted in the Wiki pages with low-latency kernels previous to 'this push' where that some modules may not work, or failed to build... That was for both the RT and low-latency series kernels. But I have heard that there have been a lot of patches to get around those issues, and maybe those warnings might not be relevant "today".

Honestly: IDK. Time will tell how this goes.

@Doug S --- How do you feel about all this as it relates to Server?As you know, I am happy about the merging of low-latency into generic. I have never been aware of any issues, although I mainly use the upstream mainline kernel, with no patches and no graphics. I have no experience with the RT kernel.

---

### Post by MyMurry on 2024-04-07
Today I got 6.8.0-22

Now my graphics flickers from time to time.

i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun

---

### Post by Doug S on 2024-04-07
> **MyMurry said:**
> Today I got 6.8.0-22

Now my graphics flickers from time to time.

i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrunWhat is your processor make and model? Do "grep --max-count=1 "model name" /proc/cpuinfo".
How many idle states does your system have? Do "ls -l -d /sys/devices/system/cpu/cpu6/cpuidle/state*".
Try disabling the deepest idle states, one by one, does it make a difference?
Were you previously using kernel 6.8.0-11 generic and did it work properly?

Example of what I am asking:

```

$ [COLOR="#FF0000"]grep --max-count=1 "model name" /proc/cpuinfo[/COLOR]
model name      : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
$ [COLOR="#FF0000"]ls -l -d /sys/devices/system/cpu/cpu6/cpuidle/state*[/COLOR]
drwxr-xr-x 2 root root 0 Apr  7 11:01 /sys/devices/system/cpu/cpu6/cpuidle/state0
drwxr-xr-x 3 root root 0 Apr  7 11:01 /sys/devices/system/cpu/cpu6/cpuidle/state1
drwxr-xr-x 3 root root 0 Apr  7 11:01 /sys/devices/system/cpu/cpu6/cpuidle/state2
drwxr-xr-x 3 root root 0 Apr  7 11:01 /sys/devices/system/cpu/cpu6/cpuidle/state3
$ [COLOR="#FF0000"]echo 1 | sudo tee /sys/devices/system/cpu/cpu*/cpuidle/state3/disable[/COLOR]
1
$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpuidle/state3/disable[/COLOR]
/sys/devices/system/cpu/cpu0/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu10/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu11/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu1/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu2/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu3/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu4/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu5/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu6/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu7/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu8/cpuidle/state3/disable:1
/sys/devices/system/cpu/cpu9/cpuidle/state3/disable:1
$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu1/cpuidle/state*/disable[/COLOR]
/sys/devices/system/cpu/cpu1/cpuidle/state0/disable:0
/sys/devices/system/cpu/cpu1/cpuidle/state1/disable:0
/sys/devices/system/cpu/cpu1/cpuidle/state2/disable:0
/sys/devices/system/cpu/cpu1/cpuidle/state3/disable:1

```

---

### Post by MyMurry on 2024-04-07
norbert@norbert-Latitude-5580:~$ grep --max-count=1 "model name" /proc/cpuinfo
model name    : Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz

norbert@norbert-Latitude-5580:~$ sudo ls -l -d /sys/devices/system/cpu/cpu0/cpuidle/state*
drwxr-xr-x 2 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state0
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state1
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state2
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state3
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state4
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state5
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state6
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state7
drwxr-xr-x 3 root root 0 Apr  7 21:20 /sys/devices/system/cpu/cpu0/cpuidle/state8

I added "i915.enable_psr=0" to my boot config. This solve the problem. I will try to disable the deepest idle state.I used kernel 6.8.0-11 generic before without any problems.

---

### Post by Doug S on 2024-04-07
> **MyMurry said:**
> ...
I will try to disable the deepest idle state.I used kernel 6.8.0-11 generic before without any problems.

If you are willing, it would be good to try to isolate why 6.8.0-11 generic worked and 6.8.0-20  has this issue.

You might need to disable more than just the deepest idle state, but try one state at a time. It would also be good to know the state names:

```
doug@s19:/media/nvme/home/doug/idle$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu1/cpuidle/state*/name[/COLOR]
/sys/devices/system/cpu/cpu1/cpuidle/state0/name:POLL
/sys/devices/system/cpu/cpu1/cpuidle/state1/name:C1_ACPI
/sys/devices/system/cpu/cpu1/cpuidle/state2/name:C2_ACPI
/sys/devices/system/cpu/cpu1/cpuidle/state3/name:C3_ACPI
```

and:

```
doug@s15:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu1/cpuidle/state*/name[/COLOR]
/sys/devices/system/cpu/cpu1/cpuidle/state0/name:POLL
/sys/devices/system/cpu/cpu1/cpuidle/state1/name:C1
/sys/devices/system/cpu/cpu1/cpuidle/state2/name:C1E
/sys/devices/system/cpu/cpu1/cpuidle/state3/name:C3
/sys/devices/system/cpu/cpu1/cpuidle/state4/name:C6

```

I wonder if adding "preempt=none" to the grub command line makes a difference? (hope I have the syntax correct, I didn't test it.) EDIT: after re-reading my first post on this thread, this shouldn't be the reason.

---

### Post by MyMurry on 2024-04-08
both commands are the same:

norbert@norbert-Latitude-5580:~$ grep . /sys/devices/system/cpu/cpu1/cpuidle/state*/name
/sys/devices/system/cpu/cpu1/cpuidle/state0/namePOLL
/sys/devices/system/cpu/cpu1/cpuidle/state1/name:C1
/sys/devices/system/cpu/cpu1/cpuidle/state2/name:C1E
/sys/devices/system/cpu/cpu1/cpuidle/state3/name:C3
/sys/devices/system/cpu/cpu1/cpuidle/state4/name:C6
/sys/devices/system/cpu/cpu1/cpuidle/state5/name:C7s
/sys/devices/system/cpu/cpu1/cpuidle/state6/name:C8
/sys/devices/system/cpu/cpu1/cpuidle/state7/name:C9
/sys/devices/system/cpu/cpu1/cpuidle/state8/name:C10

---

### Post by Doug S on 2024-04-08
> **MyMurry said:**
> both commands are the same:I'm not sure what you mean there. If you were referring to my grub command line suggestion,  "preempt=none", that was about your original issue, not what you would expect to see for idle state names. My two examples were from 2 different computers, one that has a specific intel_idle entry and one that doesn't, so it uses the relevant default ACPI states.

Anyway, I see that kernel 6.8.0-22-generic has been released. Does the issue still occur with the new kernel?

---

### Post by Doug S on 2024-04-20
Hmmm... there seems to be generic and lowlatency kernels again, with the kernel configuration differences:

```
doug@s19:~/kernel/linux$ scripts/diffconfig /boot/config-6.8.0-28-generic /boot/config-6.8.0-28-lowlatency
 PREEMPT n -> y
 PREEMPT_VOLUNTARY y -> n
 RCU_NOCB_CPU_DEFAULT_ALL n -> y
 VERSION_SIGNATURE "Ubuntu 6.8.0-28.28-generic 6.8.1" -> "Ubuntu 6.8.0-28.28.1-lowlatency 6.8.1"
```

---

### Post by #&amp;thj^% on 2024-04-20
Since the beginning of testing Noble, Ive always had a choice between the two.
EDIT Let me clean that up first.
```
apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-6.8.0-28-generic/noble,now 6.8.0-28.28 amd64 [installed,automatic]
linux-image-6.8.0-28-lowlatency/noble,now 6.8.0-28.28.1 amd64 [installed]
linux-image-generic/noble,now 6.8.0-28.28 amd64 [installed,automatic]


```

On my end Doug I've always seen both.
```
uname -r
6.8.0-28-lowlatency

```

---

### Post by corradoventu on 2024-04-20
On my Ubuntu noble installed from today ISO I see
```
corrado@corrado-n7-nn-0420:~$ uname -r
6.8.0-28-generic
corrado@corrado-n7-nn-0420:~$ apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-6.8.0-28-generic/noble,now 6.8.0-28.28 amd64 [installed,automatic]
linux-image-generic-hwe-24.04/noble,now 6.8.0-28.28 amd64 [installed,automatic]
corrado@corrado-n7-nn-0420:~$ 

```

---

### Post by #&amp;thj^% on 2024-04-20
Humm, dose it show here:
```
apt list  | grep linux-image-lowlatency

```

I did install the lowlat kernel myself.

---

### Post by Doug S on 2024-04-20
Thanks for the replies. I had thought there was not a lowlatency version of kernels since 6.8.0.20, at the start of this thread. But I just did updates and got both 6.8.0-28-generic and 6.8.0-28-lowlatency.

```
doug@s19:~/kernel/linux$ dpkg -l | grep linux-image-6.8.0
rc  linux-image-6.8.0-11-generic                 6.8.0-11.11                             amd64        Signed kernel image generic
ii  linux-image-6.8.0-20-generic                 6.8.0-20.20                             amd64        Signed kernel image generic
ii  linux-image-6.8.0-22-generic                 6.8.0-22.22                             amd64        Signed kernel image generic
ii  linux-image-6.8.0-28-generic                 6.8.0-28.28                             amd64        Signed kernel image generic
ii  linux-image-6.8.0-28-lowlatency              6.8.0-28.28.1                           amd64        Signed kernel image lowlatency
ii  linux-image-6.8.0-7-lowlatency               6.8.0-7.7.1                             amd64        Signed kernel image lowlatency
```

However, I did install the linux-lowlatency package at some point, and not sure exactly when I did it, or even why (I thought is was way back so I could get 6.8.0-7-lowlatency):

```
sudo apt install linux-lowlatency
```

EDIT: I think this is my mistake, I found a comment on the related discourse page that [says their is no plan to deprecate the lowlatency kernel for 24.04]("https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255/2")

EDIT: But there is also this, from [the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051342"), which suggests the objective is only one kernel, and which also makes a lot of sense:

```
Maintaining a separate kernel for a single config option seems a bit overkill and it is a significant
cost of engineering hours, build time, regression testing time and resources. Not to mention the risk of
the low-latency kernel falling behind and not being perfectly in sync with the latest generic kernel.
```

---

