---
title: "Kernel 5.13 RC (Release Candidate) series"
date: 2021-05-09
forum: Ubuntu Development Version
---

### Post by Doug S on 2021-05-09
Hi All,

Kernel 5.13-rc1 has been [released]("https://www.kernel.org/") and is on [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13-rc1/"). I have not tried it yet, but shortly. My knowledge if changes is limited, but I know: turbostat has been fixed for use with recent AMD processors; There is now user space access to TCC offset for a limited number of Intel processors, and turbostat is aware of the offset, but also for a limited number of processors.

EDIT: Compile fails for me:

```
 LD [M]  drivers/iio/pressure/st_pressure.o
error: the following would cause module name conflict:
  drivers/clk/xilinx/xlnx_vcu.ko
  drivers/soc/xilinx/xlnx_vcu.ko
make[4]: *** [Makefile:1758: modules_check] Error 1
make[4]: *** Waiting for unfinished jobs....
...
make[3]: *** [debian/rules:7: build-arch] Error 2
dpkg-buildpackage: error: debian/rules binary subprocess returned exit status 2
make[2]: *** [scripts/Makefile.package:83: bindeb-pkg] Error 2
make[1]: *** [Makefile:1557: bindeb-pkg] Error 2
make: *** [Makefile:346: __build_one_by_one] Error 2
```And from the last cycle, I can't install the Ubuntu compiled version on my 20.04 server due to Requires libc >=2.33.

EDIT: Forgot link back trail:

Previous cycle threads: [5.12]("https://ubuntuforums.org/showthread.php?t=2458625"),[5.11]("https://ubuntuforums.org/showthread.php?t=2455791"), [5.10]("https://ubuntuforums.org/showthread.php?t=2452692"), [5.9]("https://ubuntuforums.org/showthread.php?t=2448933"), [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

EDIT: In a mindless attempt to get it to compile, I changed "CONFIG_XILINX_VCU=m" to not set, but then got other compile errors.

It is not clear to me why mainline compiled properly for Ubuntu, but not on my system.

EDIT: I think this might be the source of my problem, but I do not yet know why.

```
commit 1a998be620a10000c1e1240026e4bd6bc3378c96
Author: Masahiro Yamada <masahiroy@kernel.org>
Date:   [COLOR="#FF0000"]Wed Mar 31 22:38:05 2021[/COLOR] +0900

    kbuild: check module name conflict for external modules as well

    If there are multiple modules with the same name in the same external
    module tree, there is ambiguity about which one will be loaded, and
    very likely something odd is happening.

    Signed-off-by: Masahiro Yamada <masahiroy@kernel.org>
```

EDIT: A "make clean" before compile fixed the problem. Typically, I never run "make clean".

EDIT: O.K., finally: And I'll show an example of the new TCC offset (only available for a few processors so far):

```

$ uname -a
Linux s19 5.13.0-rc1-tcc #888 SMP PREEMPT Mon May 10 06:34:42 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux

# what is the module name?
$ locate tcc | grep "\.ko"
/usr/lib/modules/5.13.0-051300rc1-lowlatency/kernel/drivers/thermal/intel/intel_tcc_cooling.ko

# load it (example only, it is built in in the kernel I am actually running):
$ sudo modprobe intel_tcc_cooling.ko

# and which cooling zone does it turn out to be?
$ grep . /sys/devices/virtual/thermal/cooling_device*/type
/sys/devices/virtual/thermal/cooling_device0/type:Fan
/sys/devices/virtual/thermal/cooling_device10/type:Processor
...
/sys/devices/virtual/thermal/cooling_device17/type:intel_powerclamp
/sys/devices/virtual/thermal/cooling_device18/type:[COLOR="#FF0000"]TCC Offset[/COLOR]
/sys/devices/virtual/thermal/cooling_device1/type:Fan
...

# O.K. so 18. Set a 30 degrees offset, for a test. (I actually use 24 normally)
$ echo 30 | sudo tee /sys/devices/virtual/thermal/cooling_device18/cur_state
30

# Now run turbostat, meanwhile apply a huge load via prime95 torture test:
$ sudo /home/doug/temp-k-git/linux/tools/power/x86/turbostat/turbostat --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 15
turbostat version [COLOR="#FF0000"]21.05.04[/COLOR] - Len Brown <lenb@kernel.org>
...
cpu0: MSR_PKG_POWER_INFO: 0x000003e8 (125 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x428440001b83e8 (UNlocked)
cpu0: PKG [COLOR="#FF0000"]Limit #1: ENabled (125.000000 Watts[/COLOR], 8.000000 sec, clamp ENabled)
cpu0: PKG [COLOR="#FF0000"]Limit #2: ENabled (136.000000 Watts[/COLOR], 0.002441* sec, clamp DISabled)
...
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x1e64140d (70 C) (100 default - [COLOR="#FF0000"]30 offset[/COLOR])
...
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt RAMWatt
0.02    1182    596     35      1.57    0.00    0.89
0.03    1123    605     34      1.64    0.00    0.89
80.21   4530    146921  67      107.26  0.00    0.89 <<< Power limit 2 engaged
98.93   4524    180356  66      130.02  0.00    0.89 <<< Power limits 2 and 1
99.74   4500    180316  67      124.91  0.00    0.89 <<< Power limit 1
99.70   4493    180356  69      124.92  0.00    0.89
99.67   4488    180343  71      124.91  0.00    0.89 <<< Temperature climbs
99.64   4483    180361  72      124.91  0.00    0.89 <<< There is a time constant involved. On this computer set in BIOS.
99.67   4448    181070  71      122.04  0.00    0.89 <<< TCC offset throttles
99.76   4367    180303  69      114.03  0.00    0.89
99.76   4307    180406  71      107.46  0.00    0.89
99.76   4268    180300  70      105.09  0.00    0.89
43.23   4218    78686   47      45.53   0.00    0.89    <<< load removed

```

---

### Post by zika on 2021-05-10
```
:~$ uname -r
5.13.0-051300rc1-lowlatency
```
While Mainline is down there is freshly brewed WIP kernel from Canonical:
```
:~$ uname -r
5.13.0-1-generic
:~$ apt policy linux-generic-wip
linux-generic-wip:
  &#1048;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;: 5.13.0.1.12
  &#1050;&#1072;&#1085;&#1076;&#1080;&#1076;&#1072;&#1090;:   5.13.0.1.12
  &#1058;&#1072;&#1073;&#1077;&#1083;&#1072; &#1080;&#1079;&#1076;&#1072;&#1114;&#1072;:
 *** 5.13.0.1.12 500
        500 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
```Nice.

---

### Post by Doug S on 2021-05-24
I missed [5.13-rc2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13-rc2/"), and now [5.13-rc3]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13-rc3/") failed to compile for AMD64, because the disk seems to be full:

```
ld: vmlinux.o: final close failed: [COLOR="#FF0000"]No space left on device[/COLOR]
make[2]: *** [/home/kernel/COD/linux/Makefile:1197: vmlinux] Error 1
make[2]: Leaving directory '/home/kernel/COD/linux/debian/build/build-lowlatency'
make[1]: *** [Makefile:215: __sub-make] Error 2
make[1]: Leaving directory '/home/kernel/COD/linux'
make: *** [debian/rules.d/2-binary-arch.mk:50: /home/kernel/COD/linux/debian/stamps/stamp-build-lowlatency] Error 2
dpkg-buildpackage: error: debian/rules build subprocess returned exit status 2
```

Anyway, I compiled myself using the slightly modified kernel config file from -rc1, but only have a few minutes use on it so far:

```
doug@s19:~$ uname -a
Linux s19 5.13.0-rc3-stock #891 SMP PREEMPT Mon May 24 07:23:48 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-05-31
Kernel [5.13-rc4]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13-rc4/") is available. This week the AMD64 version compiled O.K. My server is 20.04 based, and so I have to compile it myself, due to [the ongoing library dependency issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938").

Only been running for a few minutes, so far.

```
doug@s19:~$ uname -a
Linux s19 5.13.0-rc4-stock #893 SMP PREEMPT Mon May 31 06:41:36 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2021-06-01
I always liked to wake-up the temple Doug.

```
 ls /boot
config-5.13.0-051300rc4-generic  initrd.img                           System.map-5.13.0-051300rc4-generic  vmlinuz-5.4.0-73-generic
config-5.4.0-73-generic          initrd.img-5.13.0-051300rc4-generic  System.map-5.4.0-73-generic          vmlinuz.old
efi                              initrd.img-5.4.0-73-generic          vmlinuz
grub                             initrd.img.old                       vmlinuz-5.13.0-051300rc4-generic
```
```


 glxinfo | grep "OpenGL version"
OpenGL version string: 4.6 (Compatibility Profile) Mesa 21.2.0-devel (git-bd79c89 2021-06-01 [COLOR=#ff0000]**focal-oibaf-ppa**[/COLOR])
```


Take care of yourself mate,

---

### Post by Doug S on 2021-07-02
I missed all RCs since rc4, and am now trying to compile the 5.13 initial release. It doesn't compile on my 20.04 server:

```
  LD [M]  drivers/infiniband/hw/hfi1/hfi1.o
  GEN     .version
  CHK     include/generated/compile.h
  LD      vmlinux.o
  MODPOST vmlinux.symvers
  MODINFO modules.builtin.modinfo
  GEN     modules.builtin
  LD      .tmp_vmlinux.kallsyms1
  KSYMS   .tmp_vmlinux.kallsyms1.S
  AS      .tmp_vmlinux.kallsyms1.S
  LD      .tmp_vmlinux.kallsyms2
  KSYMS   .tmp_vmlinux.kallsyms2.S
  AS      .tmp_vmlinux.kallsyms2.S
  LD      vmlinux
  SORTTAB vmlinux
  SYSMAP  System.map
  MODPOST modules-only.symvers
  CC      arch/x86/boot/version.o
  VOFFSET arch/x86/boot/compressed/../voffset.h
  OBJCOPY arch/x86/boot/compressed/vmlinux.bin
  RELOCS  arch/x86/boot/compressed/vmlinux.relocs
  CC      arch/x86/boot/compressed/kaslr.o
  ZSTD22  arch/x86/boot/compressed/vmlinux.bin.zst
[COLOR="#FF0000"]/bin/sh: 1: zstd: not found[/COLOR]
make[6]: *** [arch/x86/boot/compressed/Makefile:136: arch/x86/boot/compressed/vmlinux.bin.zst] Error 127
make[6]: *** Deleting file 'arch/x86/boot/compressed/vmlinux.bin.zst'
make[6]: *** Waiting for unfinished jobs....
make[5]: *** [arch/x86/boot/Makefile:115: arch/x86/boot/compressed/vmlinux] Error 2
make[4]: *** [arch/x86/Makefile:274: bzImage] Error 2
make[4]: *** Waiting for unfinished jobs....
  GEN     Module.symvers
  LD [M]  arch/x86/crypto/aegis128-aesni.ko
...
  LD [M]  sound/x86/snd-hdmi-lpe-audio.ko
  LD [M]  sound/xen/snd_xen_front.ko
make[3]: *** [debian/rules:7: build-arch] Error 2
dpkg-buildpackage: error: debian/rules binary subprocess returned exit status 2
make[2]: *** [scripts/Makefile.package:83: bindeb-pkg] Error 2
make[1]: *** [Makefile:1565: bindeb-pkg] Error 2
make: *** [Makefile:346: __build_one_by_one] Error 2

```I'll keep looking into it, and can go back to -rc4 if I have to, but in the meantime if someone knows the solution please chime in.
I grow weary, as everything seems to take 10 times longer than my worst estimate.

EDIT 1: Hmmm... maybe just a kernel config difference:
```
doug@s19:~/temp-k-git/linux$ scripts/diffconfig .config .config-5.13-rc4
-HID_SEMITEK m
-SND_SOC_INTEL_SOUNDWIRE_SOF_MACH m
-SND_SOC_RT1308 m
 BPF_UNPRIV_DEFAULT_OFF y -> n
 [COLOR="#FF0000"]KERNEL_LZ4 n -> y
 KERNEL_ZSTD y -> n[/COLOR]
 SND_SOC_INTEL_USER_FRIENDLY_LONG_NAMES y -> n
+IDLE_LATENCY_SELFTEST n
+IO_MAPPING y
+XILINX_ZYNQMP_DPDMA m
```

EDIT 2: I installed the zstd package and the kernel compile completed.

---

### Post by Doug S on 2021-07-06
I am doing some tests of idle, in particular some stuff for the teo governor. However, I am currently using an unmodified kernel 5.13 and the menu idle governor. The test involves 3 cross core pipe tests threads, using all 6 cores of a i5-10600K, but only 6 of 12 CPUs. I have been getting:

```
Message from syslogd@s19 at Jul  5 08:58:11 ...
 kernel:[ 3300.508871] watchdog: BUG: soft lockup - CPU#5 stuck for 544s! [systemd-udevd:511]
``` type crashes, rarely.

Each test runs for 5 hours.
I didn't have this issue with 5.13-rc4, but also only ran this particular test a few times and only for about 4 hours total.

There is an updated BIOS available for the motherboard. I'll upgrade BIOS later today.

EDIT 1: It crashed again, with MCE errors, just after I posted this message. This was at 172 minutes (2 hours and 52 minutes) into the test run. So I upgraded BIOS and have started the test again. Before even starting the test, I got a turbostat jitter message:

```
doug@s19:~$ sudo /home/doug/temp-k-git/linux/tools/power/x86/turbostat/turbostat --quiet --show Core,CPU,Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 2
turbostat: [COLOR="#FF0000"]cpu5 jitter 1122 5134[/COLOR]
Core    CPU     Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt RAMWatt
-       -       0.02    3202    274     35      1.64    0.00    0.90
0       0       0.01    2752    14      35      1.64    0.00    0.90
0       6       0.01    3294    10
1       1       0.01    3345    14
1       7       0.02    2573    22
2       2       0.04    2013    34
2       8       0.01    2574    18
3       3       0.01    3429    16
3       9       0.01    2743    30
4       4       0.01    3225    32
4       10      0.01    3630    17
5       5       0.01    4825    24
5       11      0.04    4355    43
```Which is something I haven't seen for years. The jitter messages are when there is a lot of latency between system calls to read mperf and aperf.

EDIT 2: No crash. About 35 hours of viscous cross core pipe-test. So, I guess my issue was BIOS upgrade needed, and it was coincidence that it seemed related to kernel 5.13 verses 5.13-rc4.

EDIT3: It did eventually crash again.

---

