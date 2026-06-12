---
title: "Kernel 5.15 RC (Release Candidate) series"
date: 2021-09-12
forum: Ubuntu Development Version
---

### Post by Doug S on 2021-09-12
Hi All,

Just starting the kernel 5.15-rc series thread. The kernel has been released on [kernel.org]("https://www.kernel.org/"), and I assume will appear shortly on [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

I haven't compiled it yet.

The usual link back trail to previous rc series threads:
[5.14]("https://ubuntuforums.org/showthread.php?t=2464835"),[5.13]("https://ubuntuforums.org/showthread.php?t=2461891"), [5.12]("https://ubuntuforums.org/showthread.php?t=2458625"), [5.11]("https://ubuntuforums.org/showthread.php?t=2455791"), [5.10]("https://ubuntuforums.org/showthread.php?t=2452692"), [5.9]("https://ubuntuforums.org/showthread.php?t=2448933"), [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

EDIT 1: O.K. so compiling using my .config file from kernel 5.14:
```

...
 CC [M]  drivers/spmi/spmi.o
  CC [M]  drivers/target/target_core_device.o
  CC [M]  drivers/target/target_core_fabric_configfs.o
make[5]: *** [scripts/Makefile.build:540: drivers/staging] Error 2
make[5]: *** Waiting for unfinished jobs....
  CC [M]  drivers/target/target_core_fabric_lib.o
  CC [M]  drivers/net/dsa/sja1105/sja1105_vl.o
...
  LD [M]  drivers/mtd/ubi/ubi.o
  LD [M]  drivers/target/iscsi/cxgbit/cxgbit.o
make[4]: *** [Makefile:1874: drivers] Error 2
make[3]: *** [debian/rules:7: build-arch] Error 2
dpkg-buildpackage: error: debian/rules binary subprocess returned exit status 2
make[2]: *** [scripts/Makefile.package:83: bindeb-pkg] Error 2
make[1]: *** [Makefile:1582: bindeb-pkg] Error 2
make: *** [Makefile:350: __build_one_by_one] Error 2

real    14m28.365s
user    157m55.412s
sys     13m49.699s
```Sigh...

EDIT 2: Well there are only 3 commits involved so it shouldn't be too difficult to find. My work:
```

doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]git log --oneline scripts/Makefile.build | head -5[/COLOR]
a8390ba9ddce kbuild: remove stale *.symversions
f01ac2a15218 kbuild: remove unused quiet_cmd_update_lto_symversions
850ded46c642 kbuild: Fix TRIM_UNUSED_KSYMS with LTO_CLANG
1d11053dc630 Kbuild: lto: fix module versionings mismatch in GNU make 3.X
81361b837a34 Merge tag 'kbuild-v5.14' of git://git.kernel.org/pub/scm/linux/kernel/git/masahiroy/linux-kbuild
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]git tag --contains 1d11053dc630[/COLOR]
v5.14
v5.14-rc2
v5.14-rc3
v5.14-rc4
v5.14-rc5
v5.14-rc6
v5.14-rc7
v5.15-rc1
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]git tag --contains f01ac2a15218[/COLOR]
v5.15-rc1
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]git tag --contains 850ded46c642[/COLOR]
v5.15-rc1

```

EDIT 3: I think I missed the real problem:
```
  CC [M]  drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.o
drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c: In function ‘input_system_configure_channel_sensor’:
drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c:1649:1: error: control reaches end of non-void function [-Werror=return-type]
 1649 | }
      | ^
  CC [M]  drivers/comedi/comedi_pci.o
  CC [M]  drivers/comedi/comedi_pcmcia.o
  CC [M]  drivers/rpmsg/rpmsg_core.o
cc1: some warnings being treated as errors
```

EDIT 4: Reverting the last 2 edits of that file results in compiling completing:

```

doug@s19:~/temp-k-git/linux$ git log --oneline drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c | head -7
11e0e28faa85 Revert "media: atomisp: remove dublicate code"
d4796ce7fe29 Revert "media: atomisp: remove useless returns"
264f59089914 media: atomisp: remove useless returns
728a5c64ae5f media: atomisp: remove dublicate code
9763267eda9d media: atomisp: remove useless breaks
284be89176e5 media: atomisp: de-duplicate names at *_input_system_global.h
39bc26e49a5f media: atomisp: unify INPUT error return type
```

EDIT 5: I see the Ubuntu Mainline PPA compile failed with the same error. I couldn't work on this more at the time, so surely someone has complained upstream by now. For example, [here]("https://lkml.org/lkml/2021/9/6/107") and [here]("https://lkml.org/lkml/2021/9/13/1740"), which is weird, because the referenced patches are not in the tree.

EDIT 6:
```
doug@s19:~$ uname -a
Linux s19 5.15.0-rc1-stock #944 SMP PREEMPT Tue Sep 14 07:20:53 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```
For the above compile I simply got rid of the problematic code:
```
doug@s19:~/temp-k-git/linux$ scripts/config --disable INTEL_ATOMISP
```

---

### Post by zika on 2021-09-18
```
linux-headers-5.15.0-051500rc1daily20210918/now 5.15.0-051500rc1daily20210918.202109172201 all [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]linux-headers-5.15.0-051500rc1daily20210918-generic/now 5.15.0-051500rc1daily20210918.202109172201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-headers-5.15.0-051500rc1drmtip20210918/now 5.15.0-051500rc1drmtip20210918.202109180201 all [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-headers-5.15.0-051500rc1drmtip20210918-generic/now 5.15.0-051500rc1drmtip20210918.202109180201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-headers-5.15.0-1-generic/impish,now 5.15.0-1.1 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1072;&#1091;&#1090;&#1086;&#1084;&#1072;&#1090;&#1089;&#1082;&#1080;]
linux-image-5.15.0-1-generic/impish,now 5.15.0-1.1 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1072;&#1091;&#1090;&#1086;&#1084;&#1072;&#1090;&#1089;&#1082;&#1080;]
linux-image-unsigned-5.15.0-051500rc1daily20210918-generic/now 5.15.0-051500rc1daily20210918.202109172201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-image-unsigned-5.15.0-051500rc1drmtip20210918-generic/now 5.15.0-051500rc1drmtip20210918.202109180201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-modules-5.15.0-051500rc1daily20210918-generic/now 5.15.0-051500rc1daily20210918.202109172201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-modules-5.15.0-051500rc1drmtip20210918-generic/now 5.15.0-051500rc1drmtip20210918.202109180201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-modules-5.15.0-1-generic/impish,now 5.15.0-1.1 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1072;&#1091;&#1090;&#1086;&#1084;&#1072;&#1090;&#1089;&#1082;&#1080;]
linux-modules-extra-5.15.0-1-generic/impish,now 5.15.0-1.1 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1072;&#1091;&#1090;&#1086;&#1084;&#1072;&#1090;&#1089;&#1082;&#1080;]
linux-unstable-headers-5.15.0-1/impish,impish,now 5.15.0-1.1 all [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1072;&#1091;&#1090;&#1086;&#1084;&#1072;&#1090;&#1089;&#1082;&#1080;]
linux-headers-5.15.0-051500rc1drmintelnext20210918/now 5.15.0-051500rc1drmintelnext20210918.202109180201 all [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-headers-5.15.0-051500rc1drmintelnext20210918-generic/now 5.15.0-051500rc1drmintelnext20210918.202109180201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-image-unsigned-5.15.0-051500rc1drmintelnext20210918-generic/now 5.15.0-051500rc1drmintelnext20210918.202109180201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]
linux-modules-5.15.0-051500rc1drmintelnext20210918-generic/now 5.15.0-051500rc1drmintelnext20210918.202109180201 amd64 [&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;,&#1084;&#1077;&#1089;&#1085;&#1080;]

```
Looks OK and fast.

---

### Post by Doug S on 2021-09-18
Thanks zika. I have been watching the daily. The code itself still has has not had the patch, that has existed since August 2nd, applied. They have disabled compiling the problematic code.

```
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-5.14 .config | grep INTEL_ATOM[/COLOR]
 INTEL_ATOMISP y -> n
+INTEL_ATOMISP2_PDX86 y
+INTEL_ATOMISP2_PM n
``` Where .config-5.14 is based on config-5.14.0-051400-lowlatency and .config is based on .config-5.15.0-051500rc1daily20210918-lowlatency
> **zika said:**
> Looks OK and fast.Do You have an example of what is faster? Just curious, and would like to try myself.

---

### Post by zika on 2021-09-18
> **Doug S said:**
> Do You have an example of what is faster? Just curious, and would like to try myself.Not yet, this was just my first impression (Saturday...;)) I've stopped timing things quite some time ago so... Most of my impressions come from wip kernel 5.15 and not from those from Mainline...

---

### Post by Doug S on 2021-09-20
Kernel 5.15-rc2 is available.

Recall, for the last 2 months I have been having BIOS issues related to BIOS forcing HWP (A.K.A. Intel Speed Shift) force enabled, rather than letting the OS (linux) decide. This revealed some issues with the CPU frequency scaling drivers, both acpi-cpufreq and intel_pstate), which assumed the OS had control of enabling HWP or not. Kernel 5.15-rc2 contains a fix:

```
commit d9a7e9df731670acdc69e81748941ad338f47fab
Author: Doug Smythies
Date:   Sun Sep 12 11:50:29 2021 -0700

    cpufreq: intel_pstate: Override parameters if HWP forced by BIOS

    If HWP has been already been enabled by BIOS, it may be
    necessary to override some kernel command line parameters.
    Once it has been enabled it requires a reset to be disabled.
```

By the way, ASUS sent me a special test BIOS, with the issue fixed. I don't know how long some official version will take.

```
doug@s19:~$ uname -a
Linux s19 5.15.0-rc2-stock #946 SMP PREEMPT Mon Sep 20 07:24:32 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-09-26
Kernel 5.15-rc3 is available from [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15-rc3/") and [kernel.org]("https://www.kernel.org/").

I have only been running it for a couple of minutes:

```
doug@s19:~$ uname -a
Linux s19 5.15.0-rc3-stock #948 SMP PREEMPT Sun Sep 26 20:11:18 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-10-05
O.K. so, mainline PPA kernel 5.15-rc4 amd64 compile failed for the same reasons as earlier in this series. However, the daily for today compiled fine. I see that fix from August 2nd was finally applied.

```
f6274b06e326 (HEAD -> master, origin/master, origin/HEAD) Merge tag 'linux-kselftest-fixes-5.15-rc5' of git://git.kernel.org/pub/scm/linux/kernel/git/shuah/linux-kselftest
84b3e42564ac Merge tag 'media/v5.15-3' of git://git.kernel.org/pub/scm/linux/kernel/git/mchehab/linux-media
b60be028fc1a Merge tag 'ovl-fixes-5.15-rc5' of git://git.kernel.org/pub/scm/linux/kernel/git/mszeredi/vfs
df5c18838ea8 Merge tag 'mips-fixes_5.15_1' of git://git.kernel.org/pub/scm/linux/kernel/git/mips/linux
[COLOR="#FF0000"]206704a1fe0b media: atomisp: restore missing 'return' statement[/COLOR]
9e1ff307c779 (tag: v5.15-rc4) [COLOR="#FF0000"]Linux 5.15-rc4[/COLOR]
9b2f72cc0aa4 elf: don't use MAP_FIXED_NOREPLACE for elf interpreter mappings
```

```
doug@s19:~/temp-k-git/linux$ git show 206704a1fe0b
commit 206704a1fe0bcaaa036d3e90358bb168fac8bea1
Author: Arnd Bergmann <arnd@arndb.de>
Date:   Mon Aug 2 16:38:14 2021 +0200

    media: atomisp: restore missing 'return' statement

    The input_system_configure_channel_sensor() function lost its final
    return code in a previous patch:

    drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c: In function 'input_system_configure_channel_sensor':
    drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c:1649:1: error: control reaches end of non-void function [-Werror=return-type]

    Restore what was there originally.

    Link: https://lore.kernel.org/linux-media/20210802143820.1150099-1-arnd@kernel.org
    Fixes: 728a5c64ae5f ("media: atomisp: remove dublicate code")
    Signed-off-by: Arnd Bergmann <arnd@arndb.de>
    Acked-by: Sakari Ailus <sakari.ailus@linux.intel.com>
    Signed-off-by: Mauro Carvalho Chehab <mchehab+huawei@kernel.org>

diff --git a/drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c b/drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c
index 8e085dda0c18..712e01c37870 100644
--- a/drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c
+++ b/drivers/staging/media/atomisp/pci/hive_isp_css_common/host/input_system.c
@@ -1646,6 +1646,8 @@ static input_system_err_t input_system_configure_channel_sensor(
        default:
                return INPUT_SYSTEM_ERR_PARAMETER_NOT_SUPPORTED;
        }
+
+       return INPUT_SYSTEM_ERR_NO_ERROR;
 }

 // Test flags and set structure.
```

---

### Post by Doug S on 2021-10-11
[Mainline kernel 5.15-rc5]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15-rc5/") is available. It makes sense that it compiled properly, since we know the required patch, for the kernel configuration that Ubuntu seems to want to use, finally got added just after -rc4 was released.

```
doug@s19:~$ uname -a
Linux s19 5.15.0-rc5-stock #950 SMP PREEMPT Mon Oct 11 08:36:13 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-11-01
[Mainline PPA Kernel 5.15]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/") is available.
I only have a few minutes running it so far.

```
doug@s19:~$ uname -a
Linux s19 5.15.0-stock #952 SMP PREEMPT Sun Oct 31 16:44:20 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by fyfe54 on 2021-11-01
Running 5.15 too. So far so good....

---

### Post by tome74 on 2021-12-31
Any idea why UBSAN is enabled for the kernel since 5.15.8 ?  It is not enabled for the 5.16 rc kernels.

Thanks.

[https://gitlab.freedesktop.org/drm/amd/-/issues/1779](https://gitlab.freedesktop.org/drm/amd/-/issues/1779)

---

