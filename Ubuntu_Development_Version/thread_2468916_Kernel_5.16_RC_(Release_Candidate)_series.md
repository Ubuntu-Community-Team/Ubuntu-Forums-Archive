---
title: "Kernel 5.16 RC (Release Candidate) series"
date: 2021-11-14
forum: Ubuntu Development Version
---

### Post by zika on 2021-11-14
[https://www.phoronix.com/vr.php?view=30686](https://www.phoronix.com/vr.php?view=30686)
Still, waiting it eagerly...
Update&#8321;: Works nicely on several machines. No slowdown that I notice, just as @Doug_S explained...

---

### Post by Doug S on 2021-11-14
It's out now at [kernel.org]("https://www.kernel.org/"), but not yet on the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

I have been running an "almost" 5.16-rc1 for about an hour, and am compiling the actual -rc1 with it now.

As for the Phoronix article Zika referred to: Highly serialized single threaded workflows have always been a struggle for schedulers and CPU frequency scaling drivers. I just use a performance type governor or force CPU affinity via taskset for that type of workflow.

---

### Post by xyz-t on 2021-11-14
Good start for this one.


 Daily kernel wasn't booting here for the last week on 3 occasions, mid-way and last third. Not the case for this one. Our ThinkPad keyboard appears to be cooler with this first release.


 Kick the tires!


 Kernel Version: 5.16.0-051600rc1-generic (64-bit)

---

### Post by Doug S on 2021-11-21
[Kernel 5.16-rc2 is available]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16-rc2/").

I never used the Ubuntu kernel configuration last week, for -rc1. I am using the Ubuntu kernel configuration for -rc2 (lots of differences), which I am compiling now.

This /var/log/syslog entry seems to be new as of -rc1 (didn't notice until -rc2):```
Nov 21 16:20:59 s19 udisksd[858]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
Nov 21 16:20:59 s19 udisksd[858]: Failed to load the 'mdraid' libblockdev plugin
```

---

### Post by Doug S on 2021-11-25
It seems that since 5.16-rc1, I am unable to change CPU frequency scaling drivers. My system just hangs, with the process blocking. It also takes very long to reboot for the various timeouts to occur. I wonder if anyone reading this knows how to shorten the timeouts so that I can debug faster and/or bisect the kernel faster? Extract from "journalctl --since=today", and was after more than 5 minutes:

```
Nov 25 14:21:18 s19 systemd[1]: session-1.scope: Stopping timed out. Killing.
Nov 25 14:21:18 s19 systemd[1]: session-1.scope: Killing process 1192 (sudo) with signal SIGKILL.
Nov 25 14:21:18 s19 systemd[1]: session-1.scope: Killing process 1193 (tee) with signal SIGKILL.
Nov 25 14:21:18 s19 systemd[1]: session-1.scope: Failed with result 'timeout'.
Nov 25 14:21:18 s19 systemd[1]: Stopped Session 1 of user doug.
Nov 25 14:21:18 s19 systemd[1]: Stopping Login Service...
```

By the way I was trying to change from the intel_cpufreq CPU frequency scaling driver (A.K.A. intel_pstate driver in passive mode) to the intel_pstate driver (A.K.A. active mode) via:

```
$ echo active | sudo tee /sys/devices/system/cpu/intel_pstate/status
```
The hang occurs in either direction with or without HWP: passive to active; active to passive;

I am able to launch a "sudo shutdown -r now" command via another terminal.

EDIT 1: I will try shorter hung task timeout:
```
doug@s19:/var/log$ grep . /proc/sys/kernel/hung*
/proc/sys/kernel/hung_task_all_cpu_backtrace:0
/proc/sys/kernel/hung_task_check_count:4194304
/proc/sys/kernel/hung_task_check_interval_secs:0
/proc/sys/kernel/hung_task_panic:0
[COLOR="#FF0000"]/proc/sys/kernel/hung_task_timeout_secs:120[/COLOR]
/proc/sys/kernel/hung_task_warnings:10
```

EDIT 2: "sudo reboot --force" seems to work faster.

EDIT3: Results from kernel bisection:

```
# first bad commit: [7a89d7eacf8e84f2afb94db5ae9d9f9faa93f01c] powercap/drivers/dtpm: Simplify the dtpm table

commit 7a89d7eacf8e84f2afb94db5ae9d9f9faa93f01c
Author: Daniel Lezcano <daniel.lezcano@linaro.org>
Date:   Fri Mar 12 14:04:09 2021 +0100

    powercap/drivers/dtpm: Simplify the dtpm table

    The dtpm table is an array of pointers, that forces the user of the
    table to define initdata along with the declaration of the table
    entry. It is more efficient to create an array of dtpm structure, so
    the declaration of the table entry can be done by initializing the
    different fields.

    Signed-off-by: Daniel Lezcano <daniel.lezcano@linaro.org>
    Reviewed-by: Lukasz Luba <lukasz.luba@arm.com>
    Link: https://lore.kernel.org/r/20210312130411.29833-3-daniel.lezcano@linaro.org

diff --git a/drivers/powercap/dtpm.c b/drivers/powercap/dtpm.c
index 58433b8ef9a1..8c032398f6ce 100644
--- a/drivers/powercap/dtpm.c
+++ b/drivers/powercap/dtpm.c
@@ -467,7 +467,7 @@ int dtpm_register(const char *name, struct dtpm *dtpm, struct dtpm *parent)
...

```[Upstream email thread]("https://marc.info/?l=linux-pm&m=163795510422076&w=2").

Tested workarounds : Revert the commit; disable dtpm in the kernel configuration (it's still experimental anyhow, and shouldn't actually be enabled by default); Apply the temporary upstream patch, which missed -rc3, but hopefully will make -rc4.

---

### Post by Doug S on 2021-11-28
Kernel 5.16-rc3 is available. The [Ubuntu mainline builds]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16-rc3/") seem to have failed. I looked quickly at the log file, but didn't isolate the reason.
I have been running for just a short time so far:

```
Linux s19 5.16.0-rc3-stock #986 SMP PREEMPT Sun Nov 28 14:52:02 PST 2021 x86_64 x86_64 x86_64 GNU/Linux
```

EDIT: Re: Build failure: Never mind. I think I was looking to soon, and compile was still in progress or something. Seems fine.

---

### Post by xyz-t on 2021-11-28
When <<failed>> is not visible let say an hour after Linus, it means that work is in progress.
  
 RC-3 is OK, but splash screen is ain't quite anymore.The two previous ones were rock solid, Arch or Focal. 

  Stable edition:

 ```
Operating System: KDE neon 5.23
KDE Plasma Version: 5.23.3
KDE Frameworks Version: 5.88.0
Qt Version: 5.15.3
Kernel Version: 5.16.0-051600rc3-generic (64-bit)
Graphics Platform: Wayland
```

---

### Post by Doug S on 2021-12-05
> **Doug S said:**
> It seems that since 5.16-rc1, I am unable to change CPU frequency scaling drivers. My system just hangs, with the process blocking. It also takes very long to reboot for the various timeouts to occur. ...
... the temporary upstream patch, which missed -rc3, but hopefully will make -rc4.

Kernel 5.16-rc4 is available. It has the fix for the inability to change CPU frequency scaling drivers.

```
$ uname -a
Linux s19 5.16.0-rc4-stock #990 SMP PREEMPT Sun Dec 5 16:18:21 PST 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jagsdesai on 2021-12-06
Is anyone having issues with AMD GPU and kernel 5.16 RC series? I just installed **5.16 RC 4** and these are the issues I am having (same issues I had with 5.16 RC3):

1, Boot up took way longer than usual (90 sec vs 30 sec with kernel 5.15.4)
2, Extreme lag: Right after the reboot, with no application open, mouse lag is extreme.
3, Hardware sensors monitor for CPU disappeared from taskbar.
4, No sound output through HDMI.
5, Redshift stopped working.

GPU: AMD Radeon R9 290X

I have gone through `journalctl -b` and `sudo dmesg` but couldn't figure out the root cause myself.

So, what should I look for? Many thanks in advance.

---

### Post by Doug S on 2021-12-07
> **jagsdesai said:**
> Is anyone having issues with AMD GPU and kernel 5.16 RC series? I just installed **5.16 RC 4** and these are the issues I am having (same issues I had with 5.16 RC3):

1, Boot up took way longer than usual (90 sec vs 30 sec with kernel 5.15.4)
2, Extreme lag: Right after the reboot, with no application open, mouse lag is extreme.
3, Hardware sensors monitor for CPU disappeared from taskbar.
4, No sound output through HDMI.
5, Redshift stopped working.

GPU: AMD Radeon R9 290X

I have gone through `journalctl -b` and `sudo dmesg` but couldn't figure out the root cause myself.

So, what should I look for? Many thanks in advance.Does 5.16-RC2 or -RC1 work? Does [mainline 5.15]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/") work? I can only think of kernel bisection to isolate the bad commit. I am a server person and don't know about GPU stuff.

---

### Post by pqwoerituytrueiwoq on 2021-12-07
> **jagsdesai said:**
> Is anyone having issues with AMD GPU and kernel 5.16 RC series? I just installed **5.16 RC 4** and these are the issues I am having (same issues I had with 5.16 RC3):

1, Boot up took way longer than usual (90 sec vs 30 sec with kernel 5.15.4)
2, Extreme lag: Right after the reboot, with no application open, mouse lag is extreme.
3, Hardware sensors monitor for CPU disappeared from taskbar.
4, No sound output through HDMI.
5, Redshift stopped working.

GPU: AMD Radeon R9 290X

I have gone through `journalctl -b` and `sudo dmesg` but couldn't figure out the root cause myself.

So, what should I look for? Many thanks in advance.
Seen no such issues using a RX 580 w/ display port or a 5600G w/ HDMI ->DVI (never used redshift though)

---

### Post by jagsdesai on 2021-12-07
> **Doug S said:**
> Does 5.16-RC2 or -RC1 work? Does [mainline 5.15]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/") work? I can only think of kernel bisection to isolate the bad commit. I am a server person and don't know about GPU stuff.

Thanks for the reply.

Yes, kernel 5.15.4-051504-generic is working just fine (and 5.15; 5.15.2; 5.15.3 worked fine too).

Edit: Though I have not tried 5.16_RC1 or 5.16_RC2 but I had the exact same issues with 5.16_RC3 and 5.16_RC4.

---

### Post by Doug S on 2021-12-07
> **jagsdesai said:**
> Edit: Though I have not tried 5.16_RC1 or 5.16_RC2 but I had the exact same issues with 5.16_RC3 and 5.16_RC4.I guess it would only matter if you are planning to bisect the kernel, so as to provide better starting points. I didn't find anything relevant using search term "linux kernel 5.16 amdgpu Radeon R9 290X" with a within the last month time criteria.

---

### Post by pqwoerituytrueiwoq on 2021-12-08
Was it not possible to do this in the past with a AMD GPU?
[FONT=monospace][COLOR=#000000]cat /sys/class/drm/card0/device/pp_table[/COLOR][/FONT]
cause that is not working as i expected it to
edit must have been thinking about the [FONT=monospace][COLOR=#000000]pp_dpm_sclk[/COLOR][/FONT] file, the pp_table is not plain text in the 5.13 kernel

---

### Post by jagsdesai on 2021-12-08
> **Doug S said:**
> I guess it would only matter if you are planning to bisect the kernel, so as to provide better starting points. I didn't find anything relevant using search term "linux kernel 5.16 amdgpu Radeon R9 290X" with a within the last month time criteria.

> **pqwoerituytrueiwoq said:**
> Was it not possible to do this in the past with a AMD GPU?
[FONT=monospace][COLOR=#000000]cat /sys/class/drm/card0/device/pp_table[/COLOR][/FONT]
cause that is not working as i expected it to
edit must have been thinking about the [FONT=monospace][COLOR=#000000]pp_dpm_sclk[/COLOR][/FONT] file, the pp_table is not plain text in the 5.13 kernel

Thank you both. I just remembered that I have modified grub a long time ago.

So, after modifying again

```
From: GRUB_CMDLINE_LINUX_DEFAULT="radeon.si_support=0 amdgpu.si_support=1"
To: GRUB_CMDLINE_LINUX_DEFAULT=""
sudo update-grub
```

the system booted just fine with kernel 5.16 RC4.

One more question though... do I need anything related to `radeon or amdgpu` in the grub or no?

---

### Post by jagsdesai on 2021-12-13
Now I'm getting this **libssl3** error while installing kernel **5.16 RC5** headers on Ubuntu MATE 21.10:

```
dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600rc5-generic: linux-headers-5.16.0-051600rc5-generic depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3 is not installed.


dpkg: error processing package linux-headers-5.16.0-051600rc5-generic (--install):
 dependency problems - leaving unconfigured
```

I was installing these 4 packages:

```
linux-headers-5.16.0-051600rc5_5.16.0-051600rc5.202112121931_all.deb
linux-headers-5.16.0-051600rc5-generic_5.16.0-051600rc5.202112121931_amd64.deb
linux-image-unsigned-5.16.0-051600rc5-generic_5.16.0-051600rc5.202112121931_amd64.deb
linux-modules-5.16.0-051600rc5-generic_5.16.0-051600rc5.202112121931_amd64.deb
```

Is there any workaround for this? Thanks.

---

### Post by Doug S on 2021-12-13
> **jagsdesai said:**
> Now I'm getting this **libssl3** error while installing kernel **5.16 RC5** headers on Ubuntu MATE 21.10:

```
dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600rc5-generic: linux-headers-5.16.0-051600rc5-generic depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3 is not installed.


dpkg: error processing package linux-headers-5.16.0-051600rc5-generic (--install):
 dependency problems - leaving unconfigured
```

I was installing these 4 packages:

```
linux-headers-5.16.0-051600rc5_5.16.0-051600rc5.202112121931_all.deb
linux-headers-5.16.0-051600rc5-generic_5.16.0-051600rc5.202112121931_amd64.deb
linux-image-unsigned-5.16.0-051600rc5-generic_5.16.0-051600rc5.202112121931_amd64.deb
linux-modules-5.16.0-051600rc5-generic_5.16.0-051600rc5.202112121931_amd64.deb
```

Is there any workaround for this? Thanks.Yes, and actually I am surprised you didn't get that error before now. It has been an issue for a few kernel RC series now. I think you'll find the kernel actually works O.K. For my part of it, I compile the kernel myself on a 20.04.3 Ubuntu server using the Ubuntu mainline kernel PPA just to steal the kernel configuration. There is [a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938") you can add to, or at least select "affects me also" (or whatever the exact wording is). The count is currently 63 people affected. The bug report has other workarounds.

EDIT 1: Odd that you have the issue with 21.10.
EDIT 2: Oh crap, your issue is a whole new one, but for the same reasons. The mainline is compiled with a newer compiler with newer requirements.

```
Setting up linux-headers-5.16.0-051600rc5 (5.16.0-051600rc5.202112121931) ...
dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600rc5-lowlatency:
 linux-headers-5.16.0-051600rc5-lowlatency depends on libc6 (>= 2.34); however:  [COLOR="#FF0000"]<<< Old issue[/COLOR]
  Version of libc6:amd64 on system is 2.31-0ubuntu9.2.
 linux-headers-5.16.0-051600rc5-lowlatency depends on libssl3 (>= 3.0.0~~alpha1); however:  [COLOR="#FF0000"]<<< New issue[/COLOR]
  Package libssl3 is not installed.
```As far as I can determine libssl3 is only available for 22.04 and was only added within the last week (which makes sense).

---

### Post by jagsdesai on 2021-12-14
> **Doug S said:**
> Yes, and actually I am surprised you didn't get that error before now. It has been an issue for a few kernel RC series now. I think you'll find the kernel actually works O.K. For my part of it, I compile the kernel myself on a 20.04.3 Ubuntu server using the Ubuntu mainline kernel PPA just to steal the kernel configuration. There is [a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938") you can add to, or at least select "affects me also" (or whatever the exact wording is). The count is currently 63 people affected. The bug report has other workarounds.

EDIT 1: Odd that you have the issue with 21.10.
EDIT 2: Oh crap, your issue is a whole new one, but for the same reasons. The mainline is compiled with a newer compiler with newer requirements.

```
Setting up linux-headers-5.16.0-051600rc5 (5.16.0-051600rc5.202112121931) ...
dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600rc5-lowlatency:
 linux-headers-5.16.0-051600rc5-lowlatency depends on libc6 (>= 2.34); however:  [COLOR=#FF0000]<<< Old issue[/COLOR]
  Version of libc6:amd64 on system is 2.31-0ubuntu9.2.

 linux-headers-5.16.0-051600rc5-lowlatency depends on libssl3 (>= 3.0.0~~alpha1); however:  [COLOR=#FF0000]<<< New issue[/COLOR]
  Package libssl3 is not installed.
```As far as I can determine libssl3 is only available for 22.04 and was only added within the last week (which makes sense).

Thank you for the detailed reply.

I have subscribed to that [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938") already, but it was for **libc6** issue. This time it's **libssl3** issue.

Well, I guess up until Ubuntu MATE 22.04 gets released, I will have to use [TuxInvader's PPA]("https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline") for newer kernels.

---

### Post by Doug S on 2021-12-20
Kernel 5.16-rc6 is available, [Ubuntu PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16-rc6/"), [kernel.org]("https://www.kernel.org/")

```
doug@s19:~$ uname -a
Linux s19 5.16.0-rc6-stock #995 SMP PREEMPT Mon Dec 20 07:51:09 PST 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by tony7622 on 2021-12-23
> [COLOR=#000000]I have subscribed to that [/COLOR][bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938")[COLOR=#000000] already, but it was for [/COLOR]**libc6 issue. This time it's [B]libssl3 issue**[/B]
Or you can add jammy repository, install libssl3 from it and remove it again. I did it and no dependency hell occurred.:)

---

### Post by ubu82 on 2022-01-05
> **tony7622 said:**
> [/B]
Or you can add jammy repository, install libssl3 from it and remove it again. I did it and no dependency hell occurred.:)
What would be the commands for this?

---

### Post by pqwoerituytrueiwoq on 2022-01-10
anyone else notice that when the kernel is removed it is leaving some files behind?
[FONT=monospace][COLOR=#000000]ls /lib/modules/5.16.0-051600rc*[/COLOR][/FONT]

---

### Post by zika on 2022-01-11
It does, for years, now, and You should and probably do get an info about that while removing it. A simple script can remove those leftovers, even if *--purge* switch does not do that for You, as it should, easily...

---

### Post by Doug S on 2022-01-11
@ pqwoerituytrueiwoq : I use [a kernel removal tool]("https://code.launchpad.net/~jarnos/linux-purge/+git/linux-purge/+ref/master"). I searched for years for a good kernel management tool, trying myself a few times and [getting help from others]("https://askubuntu.com/questions/892076/how-to-selectively-purge-old-kernels-all-at-once") a few times.

[Example with screenshot.]("https://ubuntuforums.org/showthread.php?t=2457790&p=14019702#post14019702")

---

### Post by Loranga on 2022-02-09
> **Doug S said:**
> Yes, and actually I am surprised you didn't get that error before now. It has been an issue for a few kernel RC series now. I think you'll find the kernel actually works O.K. For my part of it, I compile the kernel myself on a 20.04.3 Ubuntu server using the Ubuntu mainline kernel PPA just to steal the kernel configuration. There is [a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938") you can add to, or at least select "affects me also" (or whatever the exact wording is). The count is currently 63 people affected. The bug report has other workarounds.

EDIT 1: Odd that you have the issue with 21.10.
EDIT 2: Oh crap, your issue is a whole new one, but for the same reasons. The mainline is compiled with a newer compiler with newer requirements.

```
Setting up linux-headers-5.16.0-051600rc5 (5.16.0-051600rc5.202112121931) ...
dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600rc5-lowlatency:
 linux-headers-5.16.0-051600rc5-lowlatency depends on libc6 (>= 2.34); however:  [COLOR="#FF0000"]<<< Old issue[/COLOR]
  Version of libc6:amd64 on system is 2.31-0ubuntu9.2.
 linux-headers-5.16.0-051600rc5-lowlatency depends on libssl3 (>= 3.0.0~~alpha1); however:  [COLOR="#FF0000"]<<< New issue[/COLOR]
  Package libssl3 is not installed.
```As far as I can determine libssl3 is only available for 22.04 and was only added within the last week (which makes sense).

I've also got the libssl3 problem with all 5.16.x kernels tested, installed with the Ubuntu Mainline Kernel Installer on a Kubuntu 21.10 machine.
Since the issue seems to be related to the fact that the mainline kernels are built on Ubuntu 22.04, wouldn't a better long term solution be to provide an official PPA with kernels purposely built for each Ubuntu version? I'm having a brand new AMD Ryzen 5600U based laptop which benefits a lot from running 5.16 than the standard 5.13 (graphics performance and some bug with the wireless device spontaneously disappearing). Even with the upcoming 22.04 LTS and its 5.15 kernel I'm inclined to run a later kernel due to the extensive development AMD is bringing to later kernel versions.

---

### Post by xyz-t on 2022-02-26
@ pqwoerituytrueiwoq
Before:
```
ls /lib/modules
5.13.0-30-generic  5.17.0-051700rc5-generic  5.4.0-9-generic
```


In Synaptic main page (Status), look for Not Installed (residual config) and it will remove the leftover. Mainline Kernel has its dedicated folder: Installed local or obsolete. If you delete the previous release candidate in that folder, there will be no leftover.

Content of Residual Config Folder:
```
Commit Log for Fri Feb 25 10:19:26 2022


Completely removed the following packages:
apt-config-icons-hidpi
apt-config-icons-large
apt-config-icons-large-hidpi
flatpak
fuse
grub-efi-amd64
linux-image-5.4.0-99-generic
linux-modules-5.4.0-99-generic
linux-modules-extra-5.4.0-100-generic
linux-modules-extra-5.4.0-99-generic
plasma-discover
plasma-discover-backend-snap
plasma-discover-common
xul-ext-ubufox
```

After:
```
ls /lib/modules
5.13.0-30-generic  5.17.0-051700rc5-generic
```

All the best,

---

