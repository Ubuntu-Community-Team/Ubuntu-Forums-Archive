---
title: "Kernel 4.16RC (Release Candidate) series"
date: 2018-02-12
forum: Ubuntu Development Version
---

### Post by Doug S on 2018-02-12
Kernel 4.16-rc1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc1/").

It has been O.K. for me so far.

The ubuntu version seems to have been compiled with a retpoline-aware compiler, whereas the one I compiled on my up to date 16.04 Server seems to not have been compiled with a retpoline-aware compiler.
```
doug@s15:~/temp3$ [COLOR="#FF0000"]sudo ./spectre-meltdown-checker.034[/COLOR]
Spectre and Meltdown mitigation detection tool v0.34+

Checking for vulnerabilities on current system
Kernel is Linux 4.16.0-rc1-stock2 #372 SMP PREEMPT Sun Feb 11 21:23:20 PST 2018 x86_64
CPU is Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO
    * CPU indicates IBRS capability:  NO
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO
    * CPU indicates IBPB capability:  NO
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO
    * CPU indicates STIBP capability:  NO
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO
  * CPU microcode is known to cause stability problems:  NO  (model 42 stepping 7 ucode 0x29)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES
  * Vulnerable to Variant 2:  YES
  * Vulnerable to Variant 3:  YES

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  YES  (1 occurence(s) found of 64 bits array_index_mask_nospec())
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  NO  (kernel confirms your system is vulnerable)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  NO
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO
    * IBRS enabled for User space:  NO
    * IBPB enabled:  NO
* Mitigation 2
  * Kernel compiled with retpoline option:  YES
[COLOR="#FF0000"]  * Kernel compiled with a retpoline-aware compiler:  NO  (kernel reports minimal retpoline compilation)
> STATUS:  VULNERABLE  (Vulnerable: Minimal generic ASM retpoline)[/COLOR]

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES
* PTI enabled and active:  YES
* Running as a Xen PV DomU:  NO
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

```

---

### Post by bcschmerker on 2018-02-18
**Thanks for the progress point.**  Retpoline is in heavy development between Kernel 4.16 and the GNU® Compiler Collection&#8482;; I'm awaiting Retpoline updates to a slew of Packages including but not limited to glibc, gcc, gpp, grub, and xserver-xorg-*.  Kernel Images, Headers and Tools 4.16.0-*nn*-generic should be depends for the 2018 versions of all Metapackages linux-*-generic-hwe-edge to access backports from 18.04.*m*-LTS Bionic in 16.04.*p*-LTS Xenial.

---

### Post by Doug S on 2018-02-20
Kernel 4.16-rc2 has been available for a couple of days. I updated my test 16.04 server and built the kernel. All is good now.

```
$ [COLOR="#FF0000"]sudo ./spectre-meltdown-checker.034[/COLOR]
Spectre and Meltdown mitigation detection tool v0.34+

Checking for vulnerabilities on current system
Kernel is Linux 4.16.0-rc2-stock2 #374 SMP PREEMPT Tue Feb 20 16:51:47 PST 2018 x86_64
CPU is Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO
    * CPU indicates IBRS capability:  NO
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO
    * CPU indicates IBPB capability:  NO
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO
    * CPU indicates STIBP capability:  NO
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO
  * CPU microcode is known to cause stability problems:  NO  (model 42 stepping 7 ucode 0x29)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES
  * Vulnerable to Variant 2:  YES
  * Vulnerable to Variant 3:  YES

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  YES  (1 occurence(s) found of 64 bits array_index_mask_nospec())
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  NO
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO
    * IBRS enabled for User space:  NO
    * IBPB enabled:  NO
* Mitigation 2
  * Kernel compiled with retpoline option:  YES
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES
* PTI enabled and active:  YES
* Running as a Xen PV DomU:  NO
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer

```

---

### Post by Doug S on 2018-02-26
Kernel 4.16-rc3 is available from [kernel.org]("https://www.kernel.org/"), but not yet from the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").
It seems that something ([some infrastructure is down]("https://irclogs.ubuntu.com/2018/02/26/%23ubuntu-kernel.html#t08:50")) is wrong and the daily kernel builds are not occurring.

EDIT: Now available from [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc3/").

---

