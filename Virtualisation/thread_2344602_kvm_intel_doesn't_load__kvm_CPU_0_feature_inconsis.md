---
title: "kvm_intel doesn't load :: kvm: CPU 0 feature inconsistency!"
date: 2016-11-26
forum: Virtualisation
---

### Post by donbowman on 2016-11-26
This system is a supermicro X10DRi-LN4+ with 2 Haswell 2699.
It is running Xenial.
With the stock kernel (and also upgrading to latest kernel-mainline today 4.9.0-040900rc6-generic) it refuses to load kvm_intel module. The reason given in dmesg is:
```
kvm: CPU 0 feature inconsistency!
```
I have updated the bios (2.0a, 2016-09-16).
I have VT-X (and VT-D) enabled in bios.
The BIOS doesn't seem to have options for TXT (Trusted Execution)
All 72 entries in /proc/cpuinfo look lile below:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 63
model name      : Intel(R) Xeon(R) CPU E5-2696 v3 @ 2.30GHz
stepping        : 2
microcode       : 0x38
cpu MHz         : 1199.975
cache size      : 46080 KB
physical id     : 0
siblings        : 36
core id         : 0
cpu cores       : 18
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 15
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall
 nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_
cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm
 abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cqm xsaveopt cqm_llc cqm_occup_llc dtherm ida
 arat pln pts
bugs            :
bogomips        : 4599.77
clflush size    : 64
cache_alignment : 64
address sizes   : 46 bits physical, 48 bits virtual
power management:
```

This is a fresh install of xenial 16.04 on this server.



Does anyone have any suggestions as to why kvm_intel won't load or how to debug it?

---

### Post by donbowman on 2016-11-26
Tracked this a bit more.
vmcs_config cpu_based_2nd_exec_ctrl 20057FB != 57FB
is where this is coming from in arch/x86/kvm/vmx.c

So, SECONDARY_EXEC_TSC_SCALING is the bit(?).
Its telling me that one socket (?) supports tsc scaling and the other (?) doesn't.

Does anyone have a suggestion on this?

---

### Post by donbowman on 2016-11-26
OK, in case anyone else runs into the same issue, the below patch (and then setting enable_tsc_scaling=0 in grub) resolves the issue.

I think its a bit more general a problem. If you have 2 sockets, and they report slightly different capabilities, you probably would prefer to mask the additional capabilities off rather than have nothing. There are quite a lot of flags here, and i suppose any one could be different.

As to why two otherwise identical processors, one returns the tsc-scaling flag, one not, how this could occur, I do not know.
(TSC scaling is a new feature discussed [here]("http://www.intel.com/content/dam/www/public/us/en/documents/white-papers/timestamp-counter-scaling-virtualization-white-paper.pdf") that is designed for hot-migration of a VM from one physical host to another, which might have different clock-rates).

```

diff --git a/arch/x86/kvm/vmx.c b/arch/x86/kvm/vmx.c
index 5382b82..5ace575 100644
--- a/arch/x86/kvm/vmx.c
+++ b/arch/x86/kvm/vmx.c
@@ -103,6 +103,9 @@ module_param_named(enable_shadow_vmcs, enable_shadow_vmcs, bool, S_IRUGO);
 static bool __read_mostly nested = 0;
 module_param(nested, bool, S_IRUGO);
 
+static bool __read_mostly enable_tsc_scaling = true;
+module_param(enable_tsc_scaling, bool, S_IRUGO);
+
 static u64 __read_mostly host_xss;
 
 static bool __read_mostly enable_pml = 1;
@@ -3449,6 +3452,8 @@ static __init int setup_vmcs_config(struct vmcs_config *vmcs_conf)
        vmcs_conf->pin_based_exec_ctrl = _pin_based_exec_control;
        vmcs_conf->cpu_based_exec_ctrl = _cpu_based_exec_control;
        vmcs_conf->cpu_based_2nd_exec_ctrl = _cpu_based_2nd_exec_control;
+        if (!enable_tsc_scaling)
+            vmcs_conf->cpu_based_2nd_exec_ctrl &= ~SECONDARY_EXEC_TSC_SCALING;
        vmcs_conf->vmexit_ctrl         = _vmexit_control;
        vmcs_conf->vmentry_ctrl        = _vmentry_control;

```

---

