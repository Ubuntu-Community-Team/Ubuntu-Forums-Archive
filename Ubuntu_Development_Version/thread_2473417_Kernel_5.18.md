---
title: "Kernel 5.18"
date: 2022-04-03
forum: Ubuntu Development Version
---

### Post by zika on 2022-04-03
[URL="https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18-rc1/"]https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18-rc1/

[/URL]```
:~$ uname -r
5.18.0-051800rc1-generic
```

---

### Post by Doug S on 2022-04-03
I got this:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]time make -j13 olddefconfig bindeb-pkg LOCALVERSION=-stock[/COLOR]
...
BTF: .tmp_vmlinux.btf: pahole (pahole) is not available
Failed to generate BTF for vmlinux
Try to disable CONFIG_DEBUG_INFO_BTF
make[4]: *** [Makefile:1158: vmlinux] Error 1
make[3]: *** [debian/rules:7: build-arch] Error 2
dpkg-buildpackage: error: debian/rules binary subprocess returned exit status 2
make[2]: *** [scripts/Makefile.package:83: bindeb-pkg] Error 2
make[1]: *** [Makefile:1542: bindeb-pkg] Error 2
make: *** [Makefile:350: __build_one_by_one] Error 2

real    19m36.015s
user    213m49.723s
sys     17m54.867s
```

If I disable CONFIG_DEBUG_INFO_BTF then somehow the debug kernel is then generated, which means compile time takes twice as long.

```
real    30m0.224s
user    311m43.820s
sys     21m15.744s
```

EDIT 1: [I have had the pahole issue before.]("https://ubuntuforums.org/showthread.php?t=2469413&p=14069081#post14069081")
EDIT 2: I modified my kernel config change script (see [here]("https://ubuntuforums.org/showthread.php?t=2471193&page=3&p=14087031#post14087031") from the previous kernel 5.17 RC thread), and did get rid of the pahole dependency. However, I don't know if some of the collateral config changes matter.

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]cat mod-config[/COLOR]
#! /bin/bash
#
# mod-config 2022.04.04 Smythies
#       Getting the:
#       BTF: .tmp_vmlinux.btf: pahole (pahole) is not available
#       compile error again.
#       and if one disables CONFIG_DEBUG_INFO_BTF
#       then the huge debug kernel is generated.
#       I don't want to install the DWARVES package.
#       Specifically disable this stuff, so it
#       does not override desired no debug kernel.
#
# mod-config 2022.03.22 Smythies
#       The standard changes to the Ubuntu Mainline
#       kernel configuration have become numerous.
#       Automate.
#       The script is located in the base directory of
#       the mainline git clone.

scripts/config --disable DEBUG_INFO_BTF
scripts/config --disable DEBUG_INFO_DWARF4

scripts/config --disable DEBUG_INFO
scripts/config --disable SYSTEM_TRUSTED_KEYS
scripts/config --disable SYSTEM_REVOCATION_KEYS

# convert generic config to lowlatency

scripts/config --disable COMEDI_TESTS_EXAMPLE
scripts/config --disable COMEDI_TESTS_NI_ROUTES
scripts/config --set-val CONFIG_HZ 1000
scripts/config --enable HZ_1000
scripts/config --disable HZ_250

scripts/config --enable LATENCYTOP
scripts/config --enable PREEMPT
scripts/config --disable PREEMPT_VOLUNTARY
scripts/config --set-val TEST_DIV64 m
```

---

### Post by Doug S on 2022-04-11
Oh my goodness, [the mainline PPA build for 5.18-rc2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18-rc2/") (AMD64) failed. This is becoming all too common. Seems to be a bunch of:

```
/bin/sh: 1: Cannot fork
```
followed by a bunch of:
```
Segmentation fault (core dumped)
```

I compiled using the kernel config from -RC1, and it compiled fine:
```
doug@s19:~$ uname -a
Linux s19 5.18.0-rc2-test #1042 SMP PREEMPT_DYNAMIC Mon Apr 11 07:45:16 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-04-11
Daily is available.

 ```
[FONT=monospace][COLOR=#000000]uname -srm [/COLOR]
Linux 5.18.0-051800rc2daily20220411-generic x86_64[/FONT]
```

---

### Post by Doug S on 2022-04-11
O.K. thanks. I observe that the kernel configuration did not change, other than two automatic changes between -RC1 and -RC2:
```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-5.18.0-051800rc1-generic .config-5.18.0-051800rc2-generic[/COLOR]
-SATA_LPM_POLICY 0
+SATA_MOBILE_LPM_POLICY 3
```

---

### Post by Doug S on 2022-04-18
While [kernel 5.18-rc3 is available]("https://kernel.org/"), the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18-rc3/") build is either still busted or busted again, depending on if you count the daily builds that were working for a few days.

Anyway, it seems okay so far for me (compiled myself, obviously):

```
doug@s19:~/kernel/linux$ uname -a
Linux s19 5.18.0-rc3-stock #1044 SMP PREEMPT_DYNAMIC Mon Apr 18 07:43:55 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by zika on 2022-04-28
It's alive: [https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/) ...
```
:~$ uname -r
5.18.0-051800rc4daily20220429-generic
```

---

### Post by Doug S on 2022-04-29
> **zika said:**
> It's alive: [https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/) ...
```
:~$ uname -r
5.18.0-051800rc4daily20220429-generic
```Finally... It seems to be broken more than not lately. I see that someone asked about it on [IRC ]("https://irclogs.ubuntu.com/2022/04/28/%23ubuntu-kernel.html")and that there is now [a discourse page]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/2").

---

### Post by xyz-t on 2022-04-29
Thanks for your feedback!



 The discourse loop is interesting,. Too late for me, I went back to Arch 2 weeks ago. I will give it a go next Sunday and try to upgrade to KK. For the rest, 5.18 is another smooth cycle.

---

### Post by Doug S on 2022-05-01
With Ubuntu mainline kernel 5.18-rc5 comes a relevant configuration change:

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-5.18.0-051800rc2-generic .config-5.18.0-051800rc5-generic
-VIDEO_ZORAN_DC30 n
-VIDEO_ZORAN_ZR36060 n
 BATTERY_SAMSUNG_SDI n -> y
 CC_VERSION_TEXT "gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0" -> "gcc (Ubuntu 11.3.0-1ubuntu1) 11.3.0"
 CRYPTO_DH_RFC7919_GROUPS n -> y
 DEBUG_INFO_DWARF4 y -> n
 [COLOR="#FF0000"]DEBUG_INFO_DWARF5 n -> y[/COLOR]
 F2FS_UNFAIR_RWSEM n -> y
 FPROBE n -> y
 GCC_VERSION 110200 -> 110300
 I2C_DESIGNWARE_AMDPSP n -> y
 I8K n -> y
 INTEGRITY_MACHINE_KEYRING n -> y
 INTEL_HFI_THERMAL n -> y
 SAMPLE_TRACE_CUSTOM_EVENTS m -> n
 SENSORS_LM25066_REGULATOR n -> y
 SENSORS_PLI1209BC_REGULATOR n -> y
 SENSORS_XDPE122_REGULATOR n -> y
 SLS n -> y
 USER_DECRYPTED_DATA n -> y
 VIDEO_ZORAN m -> n
 VMGENID y -> m
+BLK_DEV_FD_RAWCMD n
+NET_DSA_REALTEK_MDIO n
+NET_DSA_REALTEK_RTL8365MB m
+NET_DSA_REALTEK_RTL8366RB m
+NET_DSA_REALTEK_SMI n
+SAMPLE_FPROBE n
```Requiring an update to the script I made to convert the kernel configuration to the low latency version:

```
doug@s19:~/kernel/linux$ cat mod-config
#! /bin/bash
#
# mod-config 2022.05.01 Smythies
#       add disable DEBUG_INFO_DWARF5
#
# mod-config 2022.04.04 Smythies
#       Getting the:
#       BTF: .tmp_vmlinux.btf: pahole (pahole) is not available
#       compile error again.
#       and if one disables CONFIG_DEBUG_INFO_BTF
#       then the huge debug kernel is generated.
#       I don't want to install the DWARVES package.
#       Specifically disable this stuff, so it
#       does not override desired no debug kernel.
#
# mod-config 2022.03.22 Smythies
#       The standard changes to the Ubuntu Mainline
#       kernel configuration have become numerous.
#       Automate.
#       The script is located in the base directory of
#       the mainline git clone.

scripts/config --disable DEBUG_INFO_BTF
scripts/config --disable DEBUG_INFO_DWARF4
[COLOR="#FF0000"]scripts/config --disable DEBUG_INFO_DWARF5[/COLOR]

scripts/config --disable DEBUG_INFO
scripts/config --disable SYSTEM_TRUSTED_KEYS
scripts/config --disable SYSTEM_REVOCATION_KEYS

# convert generic config to lowlatency

scripts/config --disable COMEDI_TESTS_EXAMPLE
scripts/config --disable COMEDI_TESTS_NI_ROUTES
scripts/config --set-val CONFIG_HZ 1000
scripts/config --enable HZ_1000
scripts/config --disable HZ_250

scripts/config --enable LATENCYTOP
scripts/config --enable PREEMPT
scripts/config --disable PREEMPT_VOLUNTARY
scripts/config --set-val TEST_DIV64 m
```

```
doug@s19:~$ uname -a
Linux s19 5.18.0-rc5-stock #1051 SMP PREEMPT_DYNAMIC Sun May 1 17:02:11 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-05-06
I get this weird message at the end even for the stable Kernel. No incidence on stability.
```

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.18.0-051800rc5-generic
Found initrd image: /boot/initrd.img-5.18.0-051800rc5-generic
Found linux image: /boot/vmlinuz-5.15.0-27-generic
Found initrd image: /boot/initrd.img-5.15.0-27-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

I don't know why we still have to install Wayland, set it default for long now.[I] sudo apt install plasma-workspace-wayland
[/I]
```
Operating System: Kubuntu 22.10
KDE Plasma Version: 5.24.5
KDE Frameworks Version: 5.93.0
Qt Version: 5.15.3
Kernel Version: 5.18.0-051800rc5-generic (64-bit)
Graphics Platform: Wayland
```

---

### Post by Doug S on 2022-05-08
There seems to be some changes in the kernel configuration debug settings. Related to:

```
commit f9b3cd24578401e7a392974b3353277286e49cee
Author: Kees Cook <keescook@chromium.org>
Date:   Wed Mar 23 16:05:38 2022 -0700

    Kconfig.debug: make DEBUG_INFO selectable from a choice

    Currently it's not possible to enable DEBUG_INFO for an all*config
    build, since it is marked as "depends on !COMPILE_TEST".

    This generally makes sense because a debug build of an all*config target
    ends up taking much longer and the output is much larger.  Having this
    be "default off" makes sense.
    ....
```

But for whatever reasons, I couldn't isolate only will be taking effect for -rc6, even though the above was included since -rc1 (likely, I am not understanding something):

```
doug@s19:~/kernel/linux$ git tag --contains f9b3cd245784
v5.18-rc1
v5.18-rc2
v5.18-rc3
v5.18-rc4
v5.18-rc5
```

Note: the below is as of part way to -rc6, I'll check again later with actual -rc6:

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config.old .config
-DEBUG_INFO n
-DEBUG_INFO_BTF n
-DEBUG_INFO_COMPRESSED n
-DEBUG_INFO_REDUCED n
-DEBUG_INFO_SPLIT n
-GDB_SCRIPTS y
 [COLOR="#FF0000"]DEBUG_INFO_NONE n -> y[/COLOR]
 SYSTEM_REVOCATION_KEYS n -> ""
 SYSTEM_TRUSTED_KEYS n -> ""
```

and, noting that DEBUG_INFO_NONE is new as of this 5.18 series and the above referenced commit:

```
doug@s19:~/kernel/linux$ grep DEBUG_INFO_NONE .config*
.config:CONFIG_DEBUG_INFO_NONE=y
.config-5.18.0-051800rc1-generic:# CONFIG_DEBUG_INFO_NONE is not set
.config-5.18.0-051800rc2-generic:# CONFIG_DEBUG_INFO_NONE is not set
.config-5.18.0-051800rc5-generic:# CONFIG_DEBUG_INFO_NONE is not set
.config-5.18-rc1:# CONFIG_DEBUG_INFO_NONE is not set
.config-5.18-rc1-2:# CONFIG_DEBUG_INFO_NONE is not set
.config-5.18-rc1-3:CONFIG_DEBUG_INFO_NONE=y
.config-5.18-rc3:CONFIG_DEBUG_INFO_NONE=y
.config-5.18-rc5:# CONFIG_DEBUG_INFO_NONE is not set
.config.old:# CONFIG_DEBUG_INFO_NONE is not set
```

Anyway, the current version of the conversion from generic to lowlatency script:

```
doug@s19:~/kernel/linux$ cat mod-config
#! /bin/bash
#
# mod-config 2022.05.08 Smythies
#       Use the newer DEBUG_INFO_NONE, and enable it.
#       (which actually means disable debug stuff.)
#
# mod-config 2022.05.01 Smythies
#       add disable DEBUG_INFO_DWARF5
#
# mod-config 2022.04.04 Smythies
#       Getting the:
#       BTF: .tmp_vmlinux.btf: pahole (pahole) is not available
#       compile error again.
#       and if one disables CONFIG_DEBUG_INFO_BTF
#       then the huge debug kernel is generated.
#       I don't want to install the DWARVES package.
#       Specifically disable this stuff, so it
#       does not override desired no debug kernel.
#
# mod-config 2022.03.22 Smythies
#       The standard changes to the Ubuntu Mainline
#       kernel configuration have become numerous.
#       Automate.
#       The script is located in the base directory of
#       the mainline git clone.

#scripts/config --disable DEBUG_INFO_DWARF4
scripts/config --disable DEBUG_INFO_DWARF5

#scripts/config --disable DEBUG_INFO
scripts/config --enable DEBUG_INFO_NONE

scripts/config --disable SYSTEM_TRUSTED_KEYS
scripts/config --disable SYSTEM_REVOCATION_KEYS

# convert generic config to lowlatency

scripts/config --disable COMEDI_TESTS_EXAMPLE
scripts/config --disable COMEDI_TESTS_NI_ROUTES
scripts/config --set-val CONFIG_HZ 1000
scripts/config --enable HZ_1000
scripts/config --disable HZ_250

scripts/config --enable LATENCYTOP
scripts/config --enable PREEMPT
scripts/config --disable PREEMPT_VOLUNTARY
scripts/config --set-val TEST_DIV64 m
```

EDIT: -RC6 is available (but not yet on the Ubuntu PPA):
```
doug@s19:~$ uname -a
Linux s19 5.18.0-rc6-stock #1053 SMP PREEMPT_DYNAMIC Sun May 8 14:25:49 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-05-08
Up and early,

It did not restart properly from the terminal and I made a cold shutdown. Partitioning is btrfs and got the same EFI message. Looks like it will be a large one, the 4 deb package size is 111.5Mb.

```
ls /lib/modules
5.15.0-27-generic  5.18.0-051800rc6-generic
```

[https://lkml.org/lkml/2022/5/8/311](https://lkml.org/lkml/2022/5/8/311)

---

### Post by Doug S on 2022-05-08
> **xyz-t said:**
> It did not restart properly from the terminal and I made a cold shutdown. Partitioning is btrfs and got the same EFI message. Looks like it will be a large one, the 4 deb package size is 111.5Mb.I hadn't noticed before, but yes (I get between 9 and 10 more mega bytes depending on which 5.18 RC I compare 5.17-RC3 (my most recent 5.17) to). I assume related to the many kernel configuration changes between Ubuntu mainline 5.17 and 5.18.

---

### Post by Doug S on 2022-05-16
[Kernel 5.18-rc7]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18-rc7/") is available. I have no clue what the new module package is about (well, based on its name, I assume something wifi related):
```
amd64/linux-modules-[COLOR="#FF0000"]iwlwifi[/COLOR]-5.18.0-051800rc7-generic_5.18.0-051800rc7.202205160241_amd64.deb
```There are a few configuration differences between RC6 and RC7:
```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-5.18.0-051800rc6-generic .config-5.18.0-051800rc7-generic
 ACCESSIBILITY n -> y
 INTEL_IOMMU_DEFAULT_ON y -> n
 INTEL_IOMMU_SCALABLE_MODE_DEFAULT_ON y -> n
+A11Y_BRAILLE_CONSOLE n
+SPEAKUP m
+SPEAKUP_SYNTH_ACNTSA m
+SPEAKUP_SYNTH_APOLLO m
+SPEAKUP_SYNTH_AUDPTR m
+SPEAKUP_SYNTH_BNS m
+SPEAKUP_SYNTH_DECEXT m
+SPEAKUP_SYNTH_DECTLK m
+SPEAKUP_SYNTH_DUMMY m
+SPEAKUP_SYNTH_LTLK m
+SPEAKUP_SYNTH_SOFT m
+SPEAKUP_SYNTH_SPKOUT m
+SPEAKUP_SYNTH_TXPRT m
```And:
```
doug@s19:~/kernel/linux$ uname -a
Linux s19 5.18.0-rc7-stock #1056 SMP PREEMPT_DYNAMIC Sun May 15 22:21:52 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2022-05-23
> **Doug S said:**
> [Kernel 5.18-rc7]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18-rc7/") is available. I have no clue what the new module package is about (well, based on its name, I assume something wifi related):
```
amd64/linux-modules-[COLOR="#FF0000"]iwlwifi[/COLOR]-5.18.0-051800rc7-generic_5.18.0-051800rc7.202205160241_amd64.deb
```
And that module package is gone for [kernel 5.18]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18/").

---

### Post by deadflowr on 2022-05-23
> **Doug S said:**
> And that module package is gone for [kernel 5.18]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18/").

I was just reading something about that package here: [https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/34]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/34")

---

### Post by #&amp;thj^% on 2022-05-23
They may have left it out of rc7 in the start.
It's present in 5.17
IE:
```
Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi

```
and:
```
lsmod | grep iwlwifi
iwlwifi               491520  1 iwlmvm
iwlmei                 53248  2 iwlmvm,iwlwifi
cfg80211             1105920  4 iwlmvm,iwlmei,iwlwifi,mac<sniped>
```
It is problematic though.

---

### Post by Doug S on 2022-05-23
> **deadflowr said:**
> I was just reading something about that package here: [https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/34]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/34")Aghhh, thanks for the link.

---

