---
title: "Kernel 6.0 RC (Release Candidate) Series"
date: 2022-08-17
forum: Ubuntu Development Version
---

### Post by Doug S on 2022-08-17
Kernel 6.0-rc1 was released a few days ago. It failed to compile on the [Ubuntu Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.0-rc1/") with the old "can not fork" error.
I compiled starting with the kernel configuration from kernel 5.19.
```

doug@s19:~$ uname -a
Linux s19 6.0.0-rc1-stock #1084 SMP PREEMPT_DYNAMIC Wed Aug 17 07:37:58 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux

```

There are many default differences between kernel configurations:
```

doug@s19:~/kernel/linux$ scripts/diffconfig .config-5.19 .config-6.0-rc1
-ANDROID y
-ARCH_HAS_VM_GET_PAGE_PROT y
-ARCH_RANDOM y
-BLK_DEV_SX8 m
-CAN_ESD_USB2 m
-CRYPTO_BLAKE2S m
-EFI_VARS y
-HAVE_CONTEXT_TRACKING y
-HAVE_CONTEXT_TRACKING_OFFSTACK y
-LEDS_CLEVO_MAIL m
-NET_DSA_MICROCHIP_KSZ8795 m
-NET_DSA_MICROCHIP_KSZ8795_SPI m
-NET_DSA_MICROCHIP_KSZ9477 m
-NET_DSA_MICROCHIP_KSZ9477_SPI m
-PMC_ATOM y
-SCSI_DPT_I2O m
-SENSORS_ADM1021 m
-SENSORS_MAX6642 m
-STACK_HASH_ORDER 20
-USB_STKWEBCAM m
-VIRTIO_HARDEN_NOTIFICATION n
-VIRT_TO_BUS y
-VME_CA91CX42 m
-VMIVME_7805 m
-VXGE m
-VXGE_DEBUG_TRACE_ALL n
 CRYPTO_BLAKE2S_X86 m -> y
+APERTURE_HELPERS y
+BCM_NET_PHYPTP m
+BLK_DEV_UBLK n
+CAN_CAN327 n
+CAN_ESD_USB n
+CAN_NETLINK y
+CAN_RX_OFFLOAD y
+CGROUP_FAVOR_DYNMODS n
+CONTEXT_TRACKING y
+CONTEXT_TRACKING_IDLE y
+CRYPTO_ARIA n
+CRYPTO_HCTR2 n
+CRYPTO_LIB_SHA1 y
+CRYPTO_POLYVAL_CLMUL_NI n
+CXL_REGION y
+DLM_DEPRECATED_API n
+ENVELOPE_DETECTOR n
+FPGA_MGR_MICROCHIP_SPI n
+GET_FREE_REGION y
+GPIO_I8255 m
+HAVE_CONTEXT_TRACKING_USER y
+HAVE_CONTEXT_TRACKING_USER_OFFSTACK y
+HAVE_IMA_KEXEC y
+IMA_KEXEC n
+INFINIBAND_ERDMA n
+LEDS_IS31FL319X n
+NET_DSA_MICROCHIP_KSZ_SPI n
+NET_DSA_TAG_RZN1_A5PSW n
+NET_VENDOR_WANGXUN y
+NF_FLOW_TABLE_PROCFS n
+NVME_AUTH n
+NVME_TARGET_AUTH n
+P2SB y
+PCI_DOE y
+PCI_EPF_VNTB n
+PINCTRL_METEORLAKE n
+PM_USERSPACE_AUTOSLEEP n
+POLYNOMIAL m
+PWM_CLK n
+RESET_SIMPLE n
+RESET_TI_TPS380X n
+RV n
+SD_ADC_MODULATOR n
+SECURITY_APPARMOR_EXPORT_BINARY y
+SECURITY_APPARMOR_INTROSPECT_POLICY y
+SECURITY_APPARMOR_PARANOID_LOAD y
+SENSORS_LT7182S n
+SHRINKER_DEBUG n
+SND_AMD_ASOC_REMBRANDT n
+SND_CTL_FAST_LOOKUP y
+SND_CTL_INPUT_VALIDATION n
+SND_HDA_CS_DSP_CONTROLS m
+SND_SOC_AMD_RPL_ACP6x n
+SND_SOC_AMD_ST_ES8336_MACH n
+SND_SOC_FSL_UTILS m
+SND_SOC_HDA m
+SND_SOC_INTEL_AVS_MACH_DA7219 n
+SND_SOC_INTEL_AVS_MACH_DMIC n
+SND_SOC_INTEL_AVS_MACH_HDAUDIO n
+SND_SOC_INTEL_AVS_MACH_I2S_TEST n
+SND_SOC_INTEL_AVS_MACH_MAX98357A n
+SND_SOC_INTEL_AVS_MACH_MAX98373 n
+SND_SOC_INTEL_AVS_MACH_NAU8825 n
+SND_SOC_INTEL_AVS_MACH_RT274 n
+SND_SOC_INTEL_AVS_MACH_RT286 n
+SND_SOC_INTEL_AVS_MACH_RT298 n
+SND_SOC_INTEL_AVS_MACH_RT5682 n
+SND_SOC_INTEL_AVS_MACH_SSM4567 n
+SND_SOC_SOF_INTEL_IPC4 y
+SND_SOC_SOF_INTEL_MTL m
+SND_SOC_SOF_IPC3 y
+SND_SOC_SOF_METEORLAKE m
+SND_SOC_TAS2780 n
+SND_SOC_WSA883X n
+SPI_MICROCHIP_CORE n
+SURFACE_AGGREGATOR_HUB n
+SURFACE_AGGREGATOR_TABLET_SWITCH n
+TCG_TIS_I2C n
+TXGBE n
+TYPEC_ANX7411 n
+UCSI_STM32G0 n
+VF610_ADC n
+VIDEO_AR0521 n
+VIDEO_STKWEBCAM n
+VIRTIO_ANCHOR y
+XEN_VIRTIO_FORCE_GRANT n

```

The usual link back trail to previous rc series threads:
[5.19]("https://ubuntuforums.org/showthread.php?t=2475710"),[5.18]("https://ubuntuforums.org/showthread.php?t=2473417"),[5.17]("https://ubuntuforums.org/showthread.php?t=2471193"),[5.16]("https://ubuntuforums.org/showthread.php?t=2468916"),[5.15]("https://ubuntuforums.org/showthread.php?t=2466991"),[5.14]("https://ubuntuforums.org/showthread.php?t=2464835"),[5.13]("https://ubuntuforums.org/showthread.php?t=2461891"), [5.12]("https://ubuntuforums.org/showthread.php?t=2458625"), [5.11]("https://ubuntuforums.org/showthread.php?t=2455791"), [5.10]("https://ubuntuforums.org/showthread.php?t=2452692"), [5.9]("https://ubuntuforums.org/showthread.php?t=2448933"), [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

A non relevant tangential note: Under the category "How stupid am I?":
I was helping someone on these forums or over on askubuntu with some iptables rules and totally forgot about some very restrictive rules I had installed on the same test server on which I compile the kernel. "git pull" did not work, just hanging. It took me about 20 minutes to figure out. How stupid.

---

### Post by xyz-t on 2022-08-21
[FONT=monospace]This is the best we can do this week. It contains commits made on the 19th (UTC time). Let's hope we have rc-2 tomorrow?

[/FONT]```
[FONT=monospace][COLOR=#000000]6.0.0-060000rc1daily20220820-generic[/COLOR][/FONT]
```

Edit: They both have the same issue: won't shutdown or restart. Magic key or cold shutdown. Removed both for being unusable.

```
6.0.0-060000rc1daily20220817-generic
```

20220814 ISO
Operating System: KDE neon Unstable Edition
KDE Plasma Version: 5.25.80
KDE Frameworks Version: 5.98.0
Qt Version: 5.15.5
Kernel Version: 5.19.2-051902-generic (64-bit)
Graphics Platform: Wayland

---

### Post by Doug S on 2022-08-21
> **xyz-t said:**
> 
Edit: They both have the same issue: won't shutdown or restart. Magic key or cold shutdown. Removed both for being unusable.
I do not have your issue, shutdown and restart work fine for me.

My test computer is a 20.04.4 server and I use "sudo shutdown -r now" or "sudo shutdown -h now".

---

### Post by xyz-t on 2022-08-21
Did not try -r now and will see if rc-2 comes out properly. For the rest, maybe frameworks 5.98 beta causes this issue.
 
For shutdown, last line when pressing ESC is this one:

systemd-shut down: waiting for process: systemd-udevd, systemd-udevd.

---

### Post by Doug S on 2022-08-22
Kernel 6.0-rc2 has been released, but [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.0-rc2/") compile failed for AMD64 again.

```
doug@s19:~/kernel/linux$ uname -a
Linux s19 6.0.0-rc2-stock #1085 SMP PREEMPT_DYNAMIC Sun Aug 21 22:35:37 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```
There is one default kernel configuration change:

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-6.0-rc1 .config-6.0-rc2
-CC_HAS_ASM_GOTO y
```
Due this this:

```
commit a0a12c3ed057af57552bf6c0aeaca6835693df04
Author: Nick Desaulniers <ndesaulniers@google.com>
Date:   Fri Aug 19 12:06:40 2022 -0700

    asm goto: eradicate CC_HAS_ASM_GOTO

    GCC has supported asm goto since 4.5, and Clang has since version 9.0.0.
    The minimum supported versions of these tools for the build according to
    Documentation/process/changes.rst are [COLOR="#FF0000"]5.1[/COLOR] and 11.0.0 respectively.
    ...
```

I am using:

```
doug@s19:~/kernel/linux$ dpkg -l | grep gcc
ii  gcc                                           [COLOR="#FF0000"]4:9.3.0-1ubuntu2 [/COLOR]                     amd64        GNU C compiler
ii  gcc-10-base:amd64                             10.3.0-1ubuntu1~20.04                 amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-9                                         9.4.0-1ubuntu1~20.04.1                amd64        GNU C compiler
ii  gcc-9-base:amd64                              9.4.0-1ubuntu1~20.04.1                amd64        GCC, the GNU Compiler Collection (base package)
ii  libgcc-9-dev:amd64                            9.4.0-1ubuntu1~20.04.1                amd64        GCC support library (development files)
ii  libgcc-s1:amd64                               10.3.0-1ubuntu1~20.04                 amd64        GCC support library
ii  libgcc1                                       1:10.3.0-1ubuntu1~20.04               amd64        GCC support library (dependency package)
```Time to get on with moving from 20.04 to 22.04.

---

### Post by xyz-t on 2022-08-26
After tweaking a few things, the restart/shutdown issue is gone.

```
hostnamectl | grep -i kernel
            Kernel: Linux 6.0.0-060000rc2daily20220824-generic
```

Now there's a new bug even if the package is marked optionnal in Synaptic. In Focal, the system wants to remove the biggest header:

```

$ sudo apt autoremove

Reading package lists... Done
Building dependency tree
Reading state information... Done
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done

The following packages will be REMOVED:
  linux-headers-6.0.0-060000rc2daily20220824
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 80.1 MB disk space will be freed.
Do you want to continue? [Y/n] n
```

**To fix it or to keep it:**

```
$ sudo su
#  apt-mark hold linux-headers-6.0.0-060000rc2daily20220824
linux-headers-6.0.0-060000rc2daily20220824 set on hold.
# exit
$ reboot
```

```
$ sudo apt-get clean && sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ exit
```

Happy camper,

---

### Post by Doug S on 2022-08-29
> **xyz-t said:**
> 
Now there's a new bug even if the package is marked optionnal in Synaptic. In Focal, the system wants to remove the biggest header:

```

$ sudo apt autoremove

Reading package lists... Done
Building dependency tree
Reading state information... Done
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done

The following packages will be REMOVED:
  linux-headers-6.0.0-060000rc2daily20220824
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 80.1 MB disk space will be freed.
Do you want to continue? [Y/n] n
```

I am not finding the same:

```

doug@s19:~$ sudo apt autoremove
[sudo] password for doug:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-5.15.0-41-generic linux-headers-5.4.0-122 linux-headers-5.4.0-122-generic linux-hwe-5.15-headers-5.15.0-41 linux-image-5.11.0-41-generic linux-image-5.13.0-52-generic linux-image-5.15.0-41-generic linux-image-5.4.0-122-generic linux-modules-5.11.0-41-generic linux-modules-5.13.0-52-generic
  linux-modules-5.15.0-41-generic linux-modules-5.4.0-122-generic linux-modules-extra-5.11.0-41-generic linux-modules-extra-5.13.0-52-generic linux-modules-extra-5.15.0-41-generic linux-modules-extra-5.4.0-122-generic
0 upgraded, 0 newly installed, 16 to remove and 15 not upgraded.
After this operation, 1,743 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
doug@s19:~$ uname -a
Linux s19 5.15.0-46-generic #49~20.04.1-Ubuntu SMP Thu Aug 4 19:15:44 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
doug@s19:~$ dpkg -l | grep linux-image
ii  linux-image-5.11.0-41-generic                 5.11.0-41.45~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.11.0-stock                      5.11.0-stock-851                      amd64        Linux kernel, version 5.11.0-stock
ii  linux-image-5.12.0-stock                      5.12.0-stock-874                      amd64        Linux kernel, version 5.12.0-stock
ii  linux-image-5.13.0-52-generic                 5.13.0-52.59~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.13.0-stock                      5.13.0-stock-899                      amd64        Linux kernel, version 5.13.0-stock
ii  linux-image-5.14.0-stock                      5.14.0-stock-931                      amd64        Linux kernel, version 5.14.0-stock
ii  linux-image-5.15.0-41-generic                 5.15.0-41.44~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.15.0-46-generic                 5.15.0-46.49~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.15.0-rc2-stock                  5.15.0-rc2-stock-3                    amd64        Linux kernel, version 5.15.0-rc2-stock
ii  linux-image-5.15.0-stock                      5.15.0-stock-952                      amd64        Linux kernel, version 5.15.0-stock
ii  linux-image-5.16.0-stock                      5.16.0-stock-999                      amd64        Linux kernel, version 5.16.0-stock
ii  linux-image-5.17.0-rc3-stock                  5.17.0-rc3-stock-1019                 amd64        Linux kernel, version 5.17.0-rc3-stock
ii  linux-image-5.18.0-stock                      5.18.0-stock-1058                     amd64        Linux kernel, version 5.18.0-stock
ii  linux-image-5.19.0-c1e                        5.19.0-c1e-1083                       amd64        Linux kernel, version 5.19.0-c1e
ii  linux-image-5.19.0-rc1-stock                  5.19.0-rc1-stock-1061                 amd64        Linux kernel, version 5.19.0-rc1-stock
ii  linux-image-5.19.0-rc2-stock                  5.19.0-rc2-stock-1062                 amd64        Linux kernel, version 5.19.0-rc2-stock
ii  linux-image-5.19.0-rc4-stock                  5.19.0-rc4-stock-1066                 amd64        Linux kernel, version 5.19.0-rc4-stock
ii  linux-image-5.19.0-rc5-stock                  5.19.0-rc5-stock-1072                 amd64        Linux kernel, version 5.19.0-rc5-stock
ii  linux-image-5.19.0-rc6-stock                  5.19.0-rc6-stock-1073                 amd64        Linux kernel, version 5.19.0-rc6-stock
ii  linux-image-5.19.0-rc7-amiga                  5.19.0-rc7-amiga-1078                 amd64        Linux kernel, version 5.19.0-rc7-amiga
ii  linux-image-5.19.0-rc7-c1e                    5.19.0-rc7-c1e-1079                   amd64        Linux kernel, version 5.19.0-rc7-c1e
ii  linux-image-5.19.0-rc7-stock                  5.19.0-rc7-stock-1074                 amd64        Linux kernel, version 5.19.0-rc7-stock
ii  linux-image-5.19.0-rc8-c1e                    5.19.0-rc8-c1e-1080                   amd64        Linux kernel, version 5.19.0-rc8-c1e
ii  linux-image-5.19.0-stock                      5.19.0-stock-1082                     amd64        Linux kernel, version 5.19.0-stock
ii  linux-image-5.4.0-122-generic                 5.4.0-122.138                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-124-generic                 5.4.0-124.140                         amd64        Signed kernel image generic
ii  linux-image-5.8.0-stock                       5.8.0-stock-811                       amd64        Linux kernel, version 5.8.0-stock
ii  linux-image-5.9.0-stock                       5.9.0-stock-829                       amd64        Linux kernel, version 5.9.0-stock
ii  linux-image-6.0.0-rc1-stock                   6.0.0-rc1-stock-1084                  amd64        Linux kernel, version 6.0.0-rc1-stock
ii  linux-image-6.0.0-rc2-stock                   6.0.0-rc2-stock-1085                  amd64        Linux kernel, version 6.0.0-rc2-stock
ii  linux-image-6.0.0-rc3-stock                   6.0.0-rc3-stock-1086                  amd64        Linux kernel, version 6.0.0-rc3-stock
ii  linux-image-generic                           5.4.0.124.125                         amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-20.04                 5.15.0.46.49~20.04.16                 amd64        Generic Linux kernel image
ii  linux-image-unsigned-5.10.0-051000-lowlatency 5.10.0-051000.202012132330            amd64        Linux kernel image for version 5.10.0 on 64 bit x86 SMP

```I don't use autoremove anyhow.

I see the mainline compile worked this week and there are kernel configuration differences (I didn't determine if automatic or Ubuntu did them).

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-6.0-rc2 .config
 CAN_CAN327 n -> m
 CAN_ESD_USB n -> m
 CRYPTO_ARIA n -> m
 CRYPTO_HCTR2 n -> m
 CRYPTO_POLYVAL_CLMUL_NI n -> m
 ENVELOPE_DETECTOR n -> m
 FPGA_MGR_MICROCHIP_SPI n -> m
 GPIO_CDEV_V1 n -> y
 IMA_KEXEC n -> y
 INFINIBAND_ERDMA n -> m
 LEDS_IS31FL319X n -> m
 NET_DSA_MICROCHIP_KSZ_SPI n -> m
 NET_DSA_TAG_RZN1_A5PSW n -> m
 NVME_AUTH n -> y
 NVME_TARGET_AUTH n -> y
 PCI_EPF_VNTB n -> m
 PINCTRL_METEORLAKE n -> m
 PWM_CLK n -> m
 RESET_SIMPLE n -> y
 RESET_TI_TPS380X n -> m
 RV n -> y
 SD_ADC_MODULATOR n -> m
 SENSORS_LT7182S n -> m
 SND_AMD_ASOC_REMBRANDT n -> m
 SND_CTL_FAST_LOOKUP y -> n
 SND_SOC_AMD_RPL_ACP6x n -> m
 SND_SOC_AMD_ST_ES8336_MACH n -> m
 SND_SOC_INTEL_AVS_MACH_DA7219 n -> m
 SND_SOC_INTEL_AVS_MACH_DMIC n -> m
 SND_SOC_INTEL_AVS_MACH_HDAUDIO n -> m
 SND_SOC_INTEL_AVS_MACH_I2S_TEST n -> m
 SND_SOC_INTEL_AVS_MACH_MAX98357A n -> m
 SND_SOC_INTEL_AVS_MACH_MAX98373 n -> m
 SND_SOC_INTEL_AVS_MACH_NAU8825 n -> m
 SND_SOC_INTEL_AVS_MACH_RT274 n -> m
 SND_SOC_INTEL_AVS_MACH_RT286 n -> m
 SND_SOC_INTEL_AVS_MACH_RT298 n -> m
 SND_SOC_INTEL_AVS_MACH_RT5682 n -> m
 SND_SOC_INTEL_AVS_MACH_SSM4567 n -> m
 SND_SOC_TAS2780 n -> m
 SND_SOC_WSA883X n -> m
 SPI_MICROCHIP_CORE n -> m
 SURFACE_AGGREGATOR_HUB n -> m
 SURFACE_AGGREGATOR_TABLET_SWITCH n -> m
 TCG_TIS_I2C n -> m
 TXGBE n -> m
 TYPEC_ANX7411 n -> m
 UCSI_STM32G0 n -> m
 VF610_ADC n -> m
 VIDEO_AR0521 n -> m
 X86_AMD_PSTATE m -> y
+CRYPTO_POLYVAL m
+CRYPTO_XCTR m
+DA_MON_EVENTS y
+DA_MON_EVENTS_ID y
+NVME_COMMON m
+RV_MON_WWNR y
+RV_REACTORS y
+RV_REACT_PANIC y
+RV_REACT_PRINTK y
+SND_SOC_RT274 m
+TOUCHSCREEN_COLIBRI_VF50 m
```

and:

```
doug@s19:~/kernel/linux$ uname -a
Linux s19 6.0.0-rc3-stock #1086 SMP PREEMPT_DYNAMIC Mon Aug 29 07:07:17 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-09-25
They made a manual intervention on the 22nd and the last rc's are available. Kinetic a no go here without mainline Kernel.

---

### Post by IanW on 2022-09-26
6.0rc7 has appeared on [mainline]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/")
[Linus has said]("https://lore.kernel.org/lkml/CAHk-=wjc_CDPy5WbN=e_FtPrd0Yn2Wp4JcdRByeyDoM9azK1mA@mail.gmail.com/T/#u") it's unlikely to need an rc8 before final release.

---

### Post by Doug S on 2022-09-26
Hi all,

Yes, mainline seems to have compiled, for a change. I have not had any issues of note this cycle.
Actually I did have some "critical medium error, dev nvme0n1" on September 16th, but don't know the root issue or if it could have been kernel version related.

```
doug@s19:~/kernel/linux$ uname -a
Linux s19 6.0.0-rc7-stock #1094 SMP PREEMPT_DYNAMIC Sun Sep 25 16:28:19 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by IanW on 2022-09-27
Linus accepted a last minute change to 6.0 -[The AMD Performance Fix For The Old "Dummy Wait" Workaround]("https://www.phoronix.com/news/Linux-6.0-AMD-Chipset-WA")

---

### Post by Doug S on 2022-09-27
> **IanW said:**
> Linus accepted a last minute change to 6.0 -[The AMD Performance Fix For The Old "Dummy Wait" Workaround]("https://www.phoronix.com/news/Linux-6.0-AMD-Chipset-WA")Interesting. The only kernel list I am on is the linux-pm (Power Management) one. Over the last few days there has been a thread about the same thing, but the patch looks a little different.

Reference: [https://lore.kernel.org/linux-pm/YzIDyLbGgzEv0wzP@rhlx01.hs-esslingen.de/T/#t ]("https://lore.kernel.org/linux-pm/YzIDyLbGgzEv0wzP@rhlx01.hs-esslingen.de/T/#t")

---

### Post by zika on 2022-10-03
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.0/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.0/)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

---

