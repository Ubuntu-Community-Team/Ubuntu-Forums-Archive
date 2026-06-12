---
title: "Kernel 5.1RC (Release Candidate) series"
date: 2019-03-17
forum: Ubuntu Development Version
---

### Post by Doug S on 2019-03-17
Kernel 5.0-rc1 is available from [kernel.org]("https://www.kernel.org/"), and from the [Ubuntu Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1-rc1/").

Among other things, it contains a new a new Timer Events Oriented (TEO) idle governor. It would be great if users would try it. Testing so far, suggests that performance with the new governor is as good as or slightly better than the menu governor, while at the same time energy consumption is as good as or slightly better then the menu governor. The default remains as the menu governor, with the TEO governor requiring this in the grub command line:

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300 [COLOR="#FF0000"]cpuidle.governor=teo[/COLOR]"
```

If you do not compile the kernel yourself, the governor might not be compiled into the mainline kernel until -rc2. (It isn't as of -rc1.)

Note 1: There seems to be a large number of default kernel configurations changes as compared to the 5.0 Ubuntu kernel low latency configuration (127, not including the needed TEO one).
Note 2: Kernel compile took twice as long as normal. I don't yet know why. (EDIT: It was because I am an idiot sometimes.)

```
$ uname -a
Linux s15 5.1.0-rc1-stock #572 SMP PREEMPT Sun Mar 17 14:56:37 PDT 2019 x86_64 x86_64 x86_64 GNU/Linux
```

One way check the TEO setting in the kernel configuration is:
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]grep -B 6 -A 1 IDLE_GOV_TEO /boot/config-5.1.0-050100rc1-lowlatency[/COLOR]
#
# CPU Idle
#
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR="#FF0000"]# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
CONFIG_INTEL_IDLE=y

```To check which governor is being used (is this example, I had modified the kernel configuration to include TEO and recompiled the kernel):
```
doug@s15:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpuidle/*[/COLOR]
/sys/devices/system/cpu/cpuidle/current_driver:intel_idle
/sys/devices/system/cpu/cpuidle/current_governor_ro:[COLOR="#FF0000"]teo[/COLOR]

```

---

### Post by zika on 2019-03-18
```
# grep -B 6 -A 1 IDLE_GOV_TEO /boot/config-5.1.*
/boot/config-5.1.0-050100rc1-generic-#
/boot/config-5.1.0-050100rc1-generic-# CPU Idle
/boot/config-5.1.0-050100rc1-generic-#
/boot/config-5.1.0-050100rc1-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-050100rc1-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-050100rc1-generic-CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR=#b22222]/boot/config-5.1.0-050100rc1-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
/boot/config-5.1.0-050100rc1-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-# CPU Idle
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR=#ff0000]/boot/config-5.1.0-994-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
/boot/config-5.1.0-994-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-# CPU Idle
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_LADDER=y 
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR=#b22222]/boot/config-5.1.0-999-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
/boot/config-5.1.0-999-generic-CONFIG_INTEL_IDLE=y
# grep . /sys/devices/system/cpu/cpuidle/*
/sys/devices/system/cpu/cpuidle/current_driver:none
/sys/devices/system/cpu/cpuidle/current_governor_ro:menu
# cat /etc/default/grub
...
GRUB_CMDLINE_LINUX_DEFAULT="....cpuidle.governor=teo"
... 

```
Update&#8321;:
```

:~$ grep -B 6 -A 1 IDLE_GOV_TEO /boot/config-5.1.*
/boot/config-5.1.0-050100rc1-generic-#
/boot/config-5.1.0-050100rc1-generic-# CPU Idle
/boot/config-5.1.0-050100rc1-generic-#
/boot/config-5.1.0-050100rc1-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-050100rc1-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-050100rc1-generic-CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR=#ff0000]/boot/config-5.1.0-050100rc1-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
/boot/config-5.1.0-050100rc1-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-050100rc2-generic-#
/boot/config-5.1.0-050100rc2-generic-# CPU Idle
/boot/config-5.1.0-050100rc2-generic-#
/boot/config-5.1.0-050100rc2-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-050100rc2-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-050100rc2-generic-CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR=#ff0000]/boot/config-5.1.0-050100rc2-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
/boot/config-5.1.0-050100rc2-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-# CPU Idle
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-994-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set
/boot/config-5.1.0-994-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-# CPU Idle
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-999-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set
/boot/config-5.1.0-999-generic-CONFIG_INTEL_IDLE=y
:~$ grep . /sys/devices/system/cpu/cpuidle/*
/sys/devices/system/cpu/cpuidle/available_governors:ladder menu 
/sys/devices/system/cpu/cpuidle/current_driver:acpi_idle
/sys/devices/system/cpu/cpuidle/current_governor:menu
GRUB_CMDLINE_LINUX_DEFAULT="....cpuidle.governor=teo"

```
Update&#8322;:
```

:~$ grep -B 6 -A 1 IDLE_GOV_TEO
/boot/config-5.1.*/boot/config-5.1.0-050100rc3-generic-#
/boot/config-5.1.0-050100rc3-generic-# CPU Idle
/boot/config-5.1.0-050100rc3-generic-#
/boot/config-5.1.0-050100rc3-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-050100rc3-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-050100rc3-generic-CONFIG_CPU_IDLE_GOV_MENU=y
[COLOR=#ff0000]/boot/config-5.1.0-050100rc3-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set[/COLOR]
/boot/config-5.1.0-050100rc3-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-# CPU Idle
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-994-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set
/boot/config-5.1.0-994-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-# CPU Idle
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-999-generic:# CONFIG_CPU_IDLE_GOV_TEO is not set
/boot/config-5.1.0-999-generic-CONFIG_INTEL_IDLE=y

```
Update&#8323;:
```

finaly:
zika@miha:~$ grep -B 6 -A 1 IDLE_GOV_TEO /boot/config-5.1.*
/boot/config-5.1.0-050100rc7-generic-#
/boot/config-5.1.0-050100rc7-generic-# CPU Idle
/boot/config-5.1.0-050100rc7-generic-#
/boot/config-5.1.0-050100rc7-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-050100rc7-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-050100rc7-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-050100rc7-generic:CONFIG_CPU_IDLE_GOV_TEO=y
/boot/config-5.1.0-050100rc7-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-# CPU Idle
/boot/config-5.1.0-994-generic-#
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-994-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-994-generic:CONFIG_CPU_IDLE_GOV_TEO=y
/boot/config-5.1.0-994-generic-CONFIG_INTEL_IDLE=y
--
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-# CPU Idle
/boot/config-5.1.0-999-generic-#
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_LADDER=y
/boot/config-5.1.0-999-generic-CONFIG_CPU_IDLE_GOV_MENU=y
/boot/config-5.1.0-999-generic:CONFIG_CPU_IDLE_GOV_TEO=y
/boot/config-5.1.0-999-generic-CONFIG_INTEL_IDLE=y

:~$ grep . /sys/devices/system/cpu/cpuidle/*
/sys/devices/system/cpu/cpuidle/current_driver:none
/sys/devices/system/cpu/cpuidle/current_governor_ro:teo


```

---

### Post by #&amp;thj^% on 2019-03-18
As Doug pointed out>>"If you do not compile the kernel yourself, the governor might not be compiled into the mainline kernel until -rc2. (It isn't as of -rc1.)"
[https://irclogs.ubuntu.com/2019/03/14/%23ubuntu-kernel.html](https://irclogs.ubuntu.com/2019/03/14/%23ubuntu-kernel.html)
Good to see zika active this go round

---

### Post by zika on 2019-03-18
> **1fallen said:**
> As Doug pointed out>>"If you do not compile the kernel yourself, the governor might not be compiled into the mainline kernel until -rc2. (It isn't as of -rc1.)"
[https://irclogs.ubuntu.com/2019/03/14/%23ubuntu-kernel.html](https://irclogs.ubuntu.com/2019/03/14/%23ubuntu-kernel.html)
Good to see zika active this go roundAs ususal I will update that post of mine as soon as kernel available as baked already (mainline ppa) get the TEO... ;) I just wanted to underline already written: that it is not, yet, vailable baked already. I'm active all the time but have some silent periods to let You rest from me ;)

---

### Post by Doug S on 2019-03-23
Do others have an issue with apparmor failing to start?
```
doug@s15:/boot$ systemctl status apparmor.service
&#9679; apparmor.service - LSB: AppArmor initialization
   Loaded: loaded (/etc/init.d/apparmor; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2019-03-22 16:44:17 PDT; 16h ago
     Docs: man:systemd-sysv-generator(8)
  Process: 567 ExecStart=/etc/init.d/apparmor start (code=exited, status=1/FAILURE)

Mar 22 16:44:16 s15 systemd[1]: Starting LSB: AppArmor initialization...
Mar 22 16:44:17 s15 apparmor[567]:  * Starting AppArmor profiles
Mar 22 16:44:17 s15 apparmor[567]:  * AppArmor not available as kernel LSM.
Mar 22 16:44:17 s15 apparmor[567]:    ...fail!
Mar 22 16:44:17 s15 systemd[1]: apparmor.service: Control process exited, code=exited status=1
Mar 22 16:44:17 s15 systemd[1]: Failed to start LSB: AppArmor initialization.
Mar 22 16:44:17 s15 systemd[1]: apparmor.service: Unit entered failed state.
Mar 22 16:44:17 s15 systemd[1]: apparmor.service: Failed with result 'exit-code'.

```It seems to be due to a new kernel config parameter:
```
CONFIG_LSM="yama,loadpin,safesetid,integrity,selinux,smack,tomoyo,apparmor"
```And based on [this]("https://lkml.org/lkml/2019/3/21/620"), perhaps will be fixed in -rc2.

---

### Post by Doug S on 2019-03-25
kernel [5.1-rc2 is available]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1-rc2/").
The expected kernel configuration change to include the TEO (Timer Events Oriented) governor did not make it.
The fix so that apparmor will work didn't make it ( at least I think).
If you compile your own kernel, I think apparmor can be fixed by changing this:
```
CONFIG_LSM="yama,loadpin,safesetid,integrity,selinux,smack,tomoyo,apparmor"
```
to this:
```
CONFIG_LSM="yama,loadpin,safesetid,integrity,apparmor"
```But I actually haven't tested it yet, and won't be able to until tomorrow. [EDIT: Tested, O.K.]

By the way, probably some of you know this already, but I just learned it this week (and now wish I knew about it a couple of months ago): The idle governor can be changed without re-booting if this in on the grub command line:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300 [COLOR="#FF0000"]cpuidle_sysfs_switch[/COLOR] cpuidle.governor=teo"
```And now I get this:
```
doug@s15:~/temp-k-git/linux$ grep . /sys/devices/system/cpu/cpuidle/*
/sys/devices/system/cpu/cpuidle/available_governors:[COLOR="#FF0000"]ladder menu teo[/COLOR]
/sys/devices/system/cpu/cpuidle/current_driver:intel_idle
/sys/devices/system/cpu/cpuidle/current_governor:[COLOR="#FF0000"]teo[/COLOR]
doug@s15:~/temp-k-git/linux$ echo menu | sudo tee /sys/devices/system/cpu/cpuidle/current_governor
menu
doug@s15:~/temp-k-git/linux$ grep . /sys/devices/system/cpu/cpuidle/*
/sys/devices/system/cpu/cpuidle/available_governors:ladder menu teo
/sys/devices/system/cpu/cpuidle/current_driver:intel_idle
/sys/devices/system/cpu/cpuidle/current_governor:[COLOR="#FF0000"]menu[/COLOR]

```However note this extract from Documentation/admin-guide/pm/cpuidle.rst
```
There are three ``CPUIdle`` governors available, ``menu``, `TEO <teo-gov_>`_
and ``ladder``.  Which of them is used by default depends on the configuration
of the kernel and in particular on whether or not the scheduler tick can be
`stopped by the idle loop <idle-cpus-and-tick_>`_.  It is possible to change the
governor at run time if the ``cpuidle_sysfs_switch`` command line parameter has
been passed to the kernel, but that is not safe in general, so it should not be
done on production systems (that may change in the future, though).  The name of
the ``CPUIdle`` governor currently used by the kernel can be read from the
:file:`current_governor_ro` (or :file:`current_governor` if
``cpuidle_sysfs_switch`` is present in the kernel command line) file under
:file:`/sys/devices/system/cpu/cpuidle/` in ``sysfs``.

```

See also [here]("https://irclogs.ubuntu.com/2019/03/25/%23ubuntu-kernel.html") and [here]("https://irclogs.ubuntu.com/2019/03/26/%23ubuntu-kernel.html") for IRC related stuff.

---

### Post by xyz-t on 2019-04-21
There's a bug with the LVM partition scheme for the entire disk in the last 3 rc's. Compiling the .deb packages creates a partition of 754Mb disturbing Nautilus rendering without the Kernel core. . A no end loops requiring a fresh install. Please take a look, at least for Mint Tessa. No bug alongside Ten and 5.1 is same as 5.0: Stable. Still enjoying Sunday's Kernel updates.

Ryzen 2700U Firmware Bug

```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.1.0-050100rc6-generic root=UUID=2af42997-a7c7-4afe-b623-3c7cb089d142 ro [COLOR=#ff0000]**iommu=soft **[/COLOR]quiet splash vt.handoff=1
```

Secure Boot Enabled Unsigned Kernel:

```
mokutil --disable-validation
mokutil --sb-state
SecureBoot enabled
```
```
dpkg --list | grep linux-image 
ii  linux-image-5.0.0-13-generic                 5.0.0-13.14                                amd64        Signed kernel image generic
ii  linux-image-generic                          5.0.0.13.14                                amd64        Generic Linux kernel image
ii  linux-image-unsigned-5.1.0-050100rc5-generic 5.1.0-050100rc5.201904141930               amd64        Linux kernel image for version 5.1.0 on 64 bit x86 SMP
ii  linux-image-unsigned-5.1.0-050100rc6-generic 5.1.0-050100rc6.201904211830               amd64        Linux kernel image for version 5.1.0 on 64 bit x86 SMP
lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco
```


All the best,

---

### Post by Doug S on 2019-04-22
> **xyz-t said:**
> There's a bug with the LVM partition scheme for the entire disk in the last 3 rc's. Compiling the .deb packages creates a partition of 754Mb disturbing Nautilus rendering without the Kernel core. . A no end loops requiring a fresh install. Please take a look, at least for Mint Tessa. No bug alongside Ten and 5.1 is same as 5.0: Stable. I do not understand how your issue is kernel dependent, but...
If kernels 5.1-rc1, 5.1-rc2, and 5.1-rc3 work properly and 5.1-rc4, 5.1-rc5, and 5.1-rc6 (the last three) don't, then my only suggestion would be to bisect the kernel to isolate the exact commit.

---

### Post by xyz-t on 2019-04-24
> **Doug S said:**
> I do not understand how your issue is kernel dependent, but...
If kernels 5.1-rc1, 5.1-rc2, and 5.1-rc3 work properly and 5.1-rc4, 5.1-rc5, and 5.1-rc6 (the last three) don't, then my only suggestion would be to bisect the kernel to isolate the exact commit.

Don't know about previous ones, not always using LVM.

This is very hard to troubleshoot, because previous RC and stock Kernel are unremovable after.  They lose some of their components and Internet collapses after trying to remove them. The terminal still showing them installed, but never the last RC (Synaptic does). It won't compile if an RC is already there = boots in the previous one = works after a fresh install only. 

When we get the extra partition after compiling the latest RC, a fresh install is the only solution to get rid of this mismatch.

---

### Post by Doug S on 2019-04-29
Kernel [5.1-rc7]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1-rc7/") is available.
It finally has the Ubuntu kernel configuration changed such that the teo (Timer Events Oriented) idle governor is included.
Users can try the new idle governor, as described in earlier comments of this thread.

---

### Post by #&amp;thj^% on 2019-04-30
Just started mine today, so nothing intelligent to add yet.
```
grep . /sys/devices/system/cpu/cpuidle/* && uname -a
/sys/devices/system/cpu/cpuidle/available_governors:ladder menu teo 
/sys/devices/system/cpu/cpuidle/current_driver:intel_idle
/sys/devices/system/cpu/cpuidle/current_governor:teo
Linux me-ThinkPad-T430 5.1.0-050100rc7-lowlatency #201904282131 SMP PREEMPT Mon Apr 29 01:41:33 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

---

