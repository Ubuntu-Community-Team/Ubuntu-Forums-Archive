---
title: "Kerne 6.9 RC (Release Candidate) series"
date: 2024-03-24
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-03-24
The kernel 6.9 release candidate (RC) series has started.

```
doug@s19:~$ uname -a
Linux s19 6.9.0-060900rc1-generic #202403242136 SMP PREEMPT_DYNAMIC Sun Mar 24 21:49:17 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

The Ubuntu kernel configuration is now the proposed low latency settings for the generic kernel. So it is a 1000Hz kernel by default, among other differences.
It is intended that 24.04 will be released with kernel 6.8 with the same kernel confiruation, but for some reason it is still sitting in "proposed".

```
doug@s19:~$ uname -a
Linux s19 6.9.0-060900rc1-generic #202403242136 SMP PREEMPT_DYNAMIC Sun Mar 24 21:49:17 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

doug@s19:~$ grep CONFIG_HZ /boot/config-6.9.0-060900rc1-generic
# CONFIG_HZ_PERIODIC is not set
# CONFIG_HZ_100 is not set
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ_1000=y
CONFIG_HZ=1000

doug@s19:~$ grep NO_HZ /boot/config-6.9.0-060900rc1-generic
CONFIG_NO_HZ_COMMON=y
# CONFIG_NO_HZ_IDLE is not set
CONFIG_NO_HZ_FULL=y
CONFIG_NO_HZ=y

```

I have some new issue with certificates to figure out before I can compile this kernel myself:

```
make[7]: *** No rule to make target 'debian/canonical-certs.pem', needed by 'certs/x509_certificate_list'.  Stop.
make[6]: *** [scripts/Makefile.build:485: certs] Error 2
make[6]: *** Waiting for unfinished jobs....
```

EDIT: How stupid am I? I edited my script that coverts the Ubuntu configuration to my desired configuration. However, I forgot to actually execute it. Duh. Kernel seems to be compiling now. By the way, and in case anyone is interested, my script:

```
doug@s19:~/kernel/linux$ cat mod-config
#! /bin/bash
#
# mod-config 2024.03.24 Smythies
#       Ubuntu is making the low latency and generic the same, at 1000Hz.
#       So eliminate a bunch of stuff.
#
# mod-config 2024.01.31 Smythies
#       Try to resync with the actual Ubuntu low latency kernel.
#       There have been changes that I wasn't aware of.
#
# mod-config 2022.07.24 Smythies
#       Prevent kern.log entries and terminal messages when using
#       some snap commands by disabling AMIGA_PARTITION
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

#scripts/config --disable COMEDI_TESTS_EXAMPLE
#scripts/config --disable COMEDI_TESTS_NI_ROUTES
#scripts/config --set-val CONFIG_HZ 1000
#scripts/config --enable HZ_1000
#scripts/config --disable HZ_250

#scripts/config --enable LATENCYTOP
#scripts/config --enable PREEMPT
#scripts/config --disable PREEMPT_VOLUNTARY
#scripts/config --set-val TEST_DIV64 m

#scripts/config --enable NO_HZ_FULL
#scripts/config --disable NO_HZ_IDLE
#scripts/config --enable RCU_LAZY
#scripts/config --enable RCU_NOCB_CPU
#scripts/config --enable RCU_NOCB_CPU_DEFAULT_ALL
#scripts/config --enable VIRT_CPU_ACCOUNTING
#scripts/config --enable VIRT_CPU_ACCOUNTING_GEN
#scripts/config --disable TICK_CPU_ACCOUNTING
#scripts/config --enable CONTEXT_TRACKING_USER
#scripts/config --disable CONTEXT_TRACKING_USER_FORCE

# Just prevents some harmless kern.log and terminal messages

scripts/config --disable AMIGA_PARTITION
```

---

### Post by fyfe54 on 2024-03-24
Installed from Mainline.  So far, so good.

---

### Post by Doug S on 2024-04-08
I missed kernel 6.9-rc2. Kernel 6.9-rc3 is available:

```
doug@s19:~$ uname -a
Linux s19 6.9.0-rc3-stk24 #21 SMP PREEMPT_DYNAMIC Mon Apr  8 16:37:45 PDT 2024 x86_64 x86_64 x86_64 GNU/Linux
```

Curious, compile time was longer than usual (~23 minutes) by a considerable amount (~37%):

```
real    31m34.633s
user    344m32.707s
sys     27m17.678s
```

EDIT: Interesting, the above was on 24.04. With the exact same hardware, but 20.04 the compile time is:

```
real    27m26.343s
user    297m47.211s
sys     26m22.081s
```

---

### Post by Swiftjay on 2024-04-10
Has Ubuntu provided packages for 6.9 to install or does it require building the kernel to use it for now?  A fix that might enable some drivers for me was in rc3 so hoping to try and install 6.9 to test

---

### Post by IanW on 2024-04-10
> **Swiftjay said:**
> Has Ubuntu provided packages for 6.9 to install or does it require building the kernel to use it for now?  A fix that might enable some drivers for me was in rc3 so hoping to try and install 6.9 to test

Mainline is a PPA. [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
These kernels are not officially supported by Ubuntu.

---

