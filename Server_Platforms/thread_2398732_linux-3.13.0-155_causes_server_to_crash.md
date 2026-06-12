---
title: "linux-3.13.0-155 causes server to crash"
date: 2018-08-16
forum: Server Platforms
---

### Post by walt-k on 2018-08-16
Hello

Ubuntu 14.04 kernel 3.13.0-155 causes server to crash.
Please help how to find kernel 3.13.0-153, i.e. particular packages:
linux-generic
linux-headers-generic
linux-image-generic
linux-libc-dev
for version 3.13.0-153.xxx

Best regards
Walter

---

### Post by amaranthnet on 2018-08-16
Seeing issues with this latest update as well. Rebooting got past the crash, but vsftpd crashes and burns. Having to disable it on servers running 14.04LTS. Even at that, it appears 3.13.0-155 or something else that came along with it last night caused some damage.

---

### Post by walt-k on 2018-08-16
I found a good mirror at China:
[http://mirrors.aliyun.com/ubuntu/](http://mirrors.aliyun.com/ubuntu/)
I'v downgraded to 153 and everything is OK

---

### Post by mconz on 2018-08-16
I'm seeing the same issue on a few servers, but I can't quite pinpoint what's wrong. Two went entirely dark after the upgrade and will not respond to network requests, but another just had services break, and runs fine as long as the broken services are stopped. 

Has anyone had luck in diagnosing the underlying cause?

---

### Post by walt-k on 2018-08-16
> **mconz said:**
> Has anyone had luck in diagnosing the underlying cause?

linux (3.13.0-155.205) trusty; urgency=medium

  * CVE-2017-18344
    - posix-timer: Properly check sigevent->sigev_notify

  * CVE-2018-5390
    - tcp: avoid collapses in tcp_prune_queue() if possible
    - tcp: detect malicious patterns in tcp_collapse_ofo_queue()

  * CVE-2018-5391
    - Revert "net: increase fragment memory usage limits"

  * CVE-2018-3620 // CVE-2018-3646
    - SAUCE: x86/cpufeatures: Add CPUID_7_EDX CPUID leaf
    - x86/speculation/l1tf: Increase 32bit PAE __PHYSICAL_PAGE_SHIFT
    - x86/speculation/l1tf: Change order of offset/type in swap entry
    - x86/speculation/l1tf: Protect swap entries against L1TF
    - x86/speculation/l1tf: Protect PROT_NONE PTEs against speculation
    - x86/speculation/l1tf: Make sure the first page is always reserved
    - x86/speculation/l1tf: Add sysfs reporting for l1tf
    - x86/speculation/l1tf: Disallow non privileged high MMIO PROT_NONE mappings
    - x86/speculation/l1tf: Limit swap file size to MAX_PA/2
    - x86/topology: Create logical package id
    - x86/topology: Fix logical package mapping
    - x86/topology: Fix Intel HT disable
    - x86/topology: Use total_cpus not nr_cpu_ids for logical packages
    - x86/topology: Fix AMD core count
    - x86/smp: Provide topology_is_primary_thread()
    - x86/topology: Provide topology_smt_supported()
    - cpu/hotplug: Split do_cpu_down()
    - x86/topology: Add topology_max_smt_threads()
    - cpu/hotplug: Provide knobs to control SMT
    - [Config] updateconfigs - enable CONFIG_HOTPLUG_SMT
    - x86/CPU: Modify detect_extended_topology() to return result
    - x86/CPU/AMD: Derive CPU topology from CPUID function 0xB when available
    - x86/cpu: Remove the pointless CPU printout
    - x86/cpu/AMD: Remove the pointless detect_ht() call
    - x86/cpu/common: Provide detect_ht_early()
    - x86/cpu/topology: Provide detect_extended_topology_early()
    - x86/cpu/intel: Evaluate smp_num_siblings early
    - x86/cpu/AMD: Evaluate smp_num_siblings early
    - x86/apic: Ignore secondary threads if nosmt=force
    - x86/speculation/l1tf: Extend 64bit swap file size limit
    - x86/cpufeatures: Add detection of L1D cache flush support.
    - x86/CPU/AMD: Move TOPOEXT reenablement before reading smp_num_siblings
    - x86/speculation/l1tf: Protect PAE swap entries against L1TF
    - x86/speculation/l1tf: Fix up pte->pfn conversion for PAE
    - Revert "x86/apic: Ignore secondary threads if nosmt=force"
    - cpu/hotplug: Boot HT siblings at least once
    - SAUCE: Alternative approach to boot nosmt
    - SAUCE: x86/mce: Try register mce notifier earlier
    - KVM: x86: Introducing kvm_x86_ops VM init/destroy hooks
    - x86/KVM: Warn user if KVM is loaded SMT and L1TF CPU bug being present.
    - x86/KVM/VMX: Add module argument for L1TF mitigation
    - x86/KVM/VMX: Add L1D flush algorithm
    - x86/KVM/VMX: Add L1D MSR based flush
    - KVM: add kvm_arch_sched_in
    - x86/KVM/VMX: Add L1D flush logic
    - x86/KVM/VMX: Split the VMX MSR LOAD structures to have an host/guest numbers
    - x86/KVM/VMX: Add find_msr() helper function
    - x86/KVM/VMX: Seperate the VMX AUTOLOAD guest/host number accounting
    - x86/KVM/VMX: Extend add_atomic_switch_msr() to allow VMENTER only MSRs
    - x86/KVM/VMX: Use MSR save list for IA32_FLUSH_CMD if required
    - cpu/hotplug: Online siblings when SMT control is turned on
    - x86/litf: Introduce vmx status variable
    - x86/kvm: Drop L1TF MSR list approach
    - x86/l1tf: Handle EPT disabled state proper
    - x86/kvm: Move l1tf setup function
    - x86/kvm: Add static key for flush always
    - x86/kvm: Serialize L1D flush parameter setter
    - x86/kvm: Allow runtime control of L1D flush
    - cpu/hotplug: Expose SMT control init function
    - cpu/hotplug: Set CPU_SMT_NOT_SUPPORTED early
    - x86/bugs, kvm: Introduce boot-time control of L1TF mitigations
    - Documentation: Add section about CPU vulnerabilities
    - x86/speculation/l1tf: Unbreak !__HAVE_ARCH_PFN_MODIFY_ALLOWED architectures
    - x86/KVM/VMX: Initialize the vmx_l1d_flush_pages' content
    - Documentation/l1tf: Fix typos
    - cpu/hotplug: detect SMT disabled by BIOS
    - x86/KVM/VMX: Don't set l1tf_flush_l1d to true from vmx_l1d_flush()
    - x86/KVM/VMX: Replace 'vmx_l1d_flush_always' with 'vmx_l1d_flush_cond'
    - x86/KVM/VMX: Move the l1tf_flush_l1d test to vmx_l1d_flush()
    - x86/irq: Demote irq_cpustat_t::__softirq_pending to u16
    - x86/KVM/VMX: Introduce per-host-cpu analogue of l1tf_flush_l1d
    - x86: Don't include linux/irq.h from asm/hardirq.h
    - x86/apic: Order irq_enter/exit() calls correctly vs. ack_APIC_irq()
    - SAUCE: Move __this_cpu_{read,write} to percpu-ubuntu.h
    - x86/irq: Let interrupt handlers set kvm_cpu_l1tf_flush_l1d
    - x86/KVM/VMX: Don't set l1tf_flush_l1d from vmx_handle_external_intr()
    - Documentation/l1tf: Remove Yonah processors from not vulnerable list
    - x86/speculation: Simplify sysfs report of VMX L1TF vulnerability
    - x86/speculation: Use ARCH_CAPABILITIES to skip L1D flush on vmentry
    - cpu/hotplug: Fix SMT supported evaluation
    - x86/speculation/l1tf: Invert all not present mappings
    - x86/speculation/l1tf: Make pmd/pud_mknotpresent() invert
    - x86/mm/pat: Ensure cpa->pfn only contains page frame numbers
    - SAUCE: Add pfn_pud() and pud_mkhuge()
    - x86/mm/pat: Make set_memory_np() L1TF safe

 -- Juerg Haefliger <juergh@canonical.com>  Fri, 10 Aug 2018 16:18:20 +0200

---

### Post by walt-k on 2018-08-16
It's seems that it's:
- x86/speculation/l1tf: Protect PROT_NONE PTEs against speculation

---

