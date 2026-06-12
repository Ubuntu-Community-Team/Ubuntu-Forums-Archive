---
title: "How do Hardy's 2.6.24-23 and 2.6.24-24 kernels differ?"
date: 2009-05-10
forum: Security
---

### Post by trimeta on 2009-05-10
I'm sorry if I'm asking this in the wrong forum, but I wasn't sure where was appropriate. Recently my Hardy-based servers got a kernel upgrade, going from linux-image-2.6.24-23-server to linux-image-2.6.24-24-server. How do these kernels differ? Since Hardy is an LTS release, theoretically they should only upgrade (and change version numbers) when there are significant security fixes which break ABI compatibility. But there is no Ubuntu Security Notice explaining the change. What happened here? Are the security implications of this update dire enough to necessitate rebooting my servers? Or does this only affect certain architectures and/or platforms which may not concern me?

---

### Post by ptn107 on 2009-05-11
Changes since 2.6.24-23.52[1]:
> 
linux (2.6.24-24.53) hardy-proposed; urgency=low

  [Stefan Bader]

  * Rebuild of 2.6.24-24.51 with 2.6.24-23.52 security patches applied.

 -- Stefan Bader <stefan.bader@canonical.com>  Sun, 05 Apr 2009 08:23:06 -0400

linux (2.6.24-24.51) hardy-proposed; urgency=low

  [Alessio Igor Bogani]

  * rt: Updated PREEMPT_RT support to rt27
    - LP: #324275

  [Steve Beattie]

  * fix apparmor memory leak on deleted file ops
    - LP: #329489

  [Upstream Kernel Changes]

  * KVM: MMU: Add locking around kvm_mmu_slot_remove_write_access()
    - LP: #335097, #333409
  * serial: 8250: fix shared interrupts issues with SMP and RT kernels
    - LP: #280821
  * 8250.c: port.lock is irq-safe
    - LP: #280821
  * ACPI: Clear WAK_STS on resume
    - LP: #251338

 -- Stefan Bader <stefan.bader@canonical.com>  Wed, 25 Feb 2009 10:18:56 +0100

linux (2.6.24-24.50) hardy-proposed; urgency=low

  [Alok Kataria]

  * x86: add X86_FEATURE_HYPERVISOR feature bit
    - LP: #319945
  * x86: add a synthetic TSC_RELIABLE feature bit
    - LP: #319945
  * x86: vmware: look for DMI string in the product serial key
    - LP: #319945
  * x86: Hypervisor detection and get tsc_freq from hypervisor
    - LP: #319945
  * x86: Use the synthetic TSC_RELIABLE bit to workaround virtualization
    anomalies.
    - LP: #319945
  * x86: Skip verification by the watchdog for TSC clocksource.
    - LP: #319945
  * x86: Mark TSC synchronized on VMware.
    - LP: #319945

  [Colin Ian King]

  * SAUCE: Bluetooth USB: fix kernel panic during suspend while streaming
    audio to bluetooth headset
    - LP: #331106

  [James Troup]

  * XEN: Enable architecture specific get_unmapped_area_topdown
    - LP: #237724

  [Stefan Bader]

  * Xen: Fix FTBS after Vmware TSC updates.
    - LP: #319945

  [Upstream Kernel Changes]

  * r8169: fix RxMissed register access
    - LP: #324760
  * r8169: Tx performance tweak helper
    - LP: #326891
  * r8169: use pci_find_capability for the PCI-E features
    - LP: #326891
  * r8169: add 8168/8101 registers description
    - LP: #326891
  * r8169: add hw start helpers for the 8168 and the 8101
    - LP: #326891
  * r8169: additional 8101 and 8102 support
    - LP: #326891
  * Fix memory corruption in console selection
    - LP: #329007

 -- Stefan Bader <stefan.bader@canonical.com>  Fri, 30 Jan 2009 11:35:26 +0100

[1]http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.24-24.53/changelog

---

