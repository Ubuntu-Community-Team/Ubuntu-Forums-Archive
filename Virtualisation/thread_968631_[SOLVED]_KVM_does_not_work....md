---
title: "[SOLVED] KVM does not work..."
date: 2008-11-02
forum: Virtualisation
---

### Post by smartboyathome on 2008-11-02
I've read the sticky, as well as the wiki page, and have done tons of google searching on this. I've tried changing my BIOS, and have turned on virtualization in there. I still can't get KVM to run though.

When I run KVM, it says:
```
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
```
When I run lsmod | grep kvm, I get:
```
kvm                   142912  0
```
When I run sudo modprobe kvm-intel, I get:
```
FATAL: Error inserting kvm_intel (/lib/modules/2.6.27-7-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported
```
So how come I can't use KVM? :(

EDIT: I compiled KVM according to [this guide]("http://redbrain.co.uk/?page_id=29"), replacing the 72 with 78, and it still doesn't work. I ran dmesg | egrep kvm, and it gives me:
```
[   36.655323] kvm: disabled by bios
[  129.652554] kvm: disabled by bios
[ 3536.074919] kvm_intel: disagrees about version of symbol kvm_clear_guest_page
[ 3536.074938] kvm_intel: Unknown symbol kvm_clear_guest_page
[ 3536.075946] kvm_intel: disagrees about version of symbol kvm_timer_intr_post
[ 3536.075952] kvm_intel: Unknown symbol kvm_timer_intr_post
[ 3536.076394] kvm_intel: disagrees about version of symbol gfn_to_page
[ 3536.076400] kvm_intel: Unknown symbol gfn_to_page
[ 3536.076862] kvm_intel: disagrees about version of symbol kvm_get_msr_common
[ 3536.076867] kvm_intel: Unknown symbol kvm_get_msr_common
[ 3536.077086] kvm_intel: disagrees about version of symbol __kvm_set_memory_region
[ 3536.077091] kvm_intel: Unknown symbol __kvm_set_memory_region
[ 3536.077341] kvm_intel: disagrees about version of symbol kvm_vcpu_uninit
[ 3536.077346] kvm_intel: Unknown symbol kvm_vcpu_uninit
[ 3536.077556] kvm_intel: disagrees about version of symbol kvm_emulate_halt
[ 3536.077563] kvm_intel: Unknown symbol kvm_emulate_halt
[ 3536.077775] kvm_intel: disagrees about version of symbol kvm_set_apic_base
[ 3536.077781] kvm_intel: Unknown symbol kvm_set_apic_base
[ 3536.077993] kvm_intel: disagrees about version of symbol kvm_report_emulation_failure
[ 3536.077999] kvm_intel: Unknown symbol kvm_report_emulation_failure
[ 3536.078245] kvm_intel: disagrees about version of symbol kvm_lapic_find_highest_irr
[ 3536.078251] kvm_intel: Unknown symbol kvm_lapic_find_highest_irr
[ 3536.078464] kvm_intel: disagrees about version of symbol kvm_task_switch
[ 3536.078470] kvm_intel: Unknown symbol kvm_task_switch
[ 3536.079108] kvm_intel: disagrees about version of symbol kvm_lmsw
[ 3536.079113] kvm_intel: Unknown symbol kvm_lmsw
[ 3536.079332] kvm_intel: disagrees about version of symbol kvm_set_memory_region
[ 3536.079339] kvm_intel: Unknown symbol kvm_set_memory_region
[ 3536.079550] kvm_intel: disagrees about version of symbol kvm_queue_exception
[ 3536.079555] kvm_intel: Unknown symbol kvm_queue_exception
[ 3536.079770] kvm_intel: disagrees about version of symbol emulate_instruction
[ 3536.079777] kvm_intel: Unknown symbol emulate_instruction
[ 3536.079985] kvm_intel: disagrees about version of symbol kvm_write_guest_page
[ 3536.079990] kvm_intel: Unknown symbol kvm_write_guest_page
[ 3536.080295] kvm_intel: disagrees about version of symbol fx_init
[ 3536.080300] kvm_intel: Unknown symbol fx_init
[ 3536.080632] kvm_intel: disagrees about version of symbol kvm_cpu_has_interrupt
[ 3536.080640] kvm_intel: Unknown symbol kvm_cpu_has_interrupt
[ 3536.080853] kvm_intel: disagrees about version of symbol kvm_lapic_get_cr8
[ 3536.080858] kvm_intel: Unknown symbol kvm_lapic_get_cr8
[ 3536.081090] kvm_intel: disagrees about version of symbol kvm_set_cr3
[ 3536.081095] kvm_intel: Unknown symbol kvm_set_cr3
[ 3536.081340] kvm_intel: disagrees about version of symbol kvm_get_cr8
[ 3536.081346] kvm_intel: Unknown symbol kvm_get_cr8
[ 3536.081659] kvm_intel: Unknown symbol kvm_x86_ops
[ 3536.082102] kvm_intel: disagrees about version of symbol kvm_emulate_hypercall
[ 3536.082108] kvm_intel: Unknown symbol kvm_emulate_hypercall
[ 3536.082326] kvm_intel: disagrees about version of symbol load_pdptrs
[ 3536.082332] kvm_intel: Unknown symbol load_pdptrs
[ 3536.082742] kvm_intel: disagrees about version of symbol kvm_mmu_unprotect_page_virt
[ 3536.082748] kvm_intel: Unknown symbol kvm_mmu_unprotect_page_virt
[ 3536.082969] kvm_intel: disagrees about version of symbol kvm_set_cr4
[ 3536.082975] kvm_intel: Unknown symbol kvm_set_cr4
[ 3536.083207] kvm_intel: disagrees about version of symbol kvm_set_cr0
[ 3536.083213] kvm_intel: Unknown symbol kvm_set_cr0
[ 3536.083421] kvm_intel: disagrees about version of symbol kvm_set_cr8
[ 3536.083426] kvm_intel: Unknown symbol kvm_set_cr8
[ 3536.083635] kvm_intel: disagrees about version of symbol kvm_lapic_enabled
[ 3536.083641] kvm_intel: Unknown symbol kvm_lapic_enabled
[ 3536.083850] kvm_intel: disagrees about version of symbol kvm_mmu_page_fault
[ 3536.083856] kvm_intel: Unknown symbol kvm_mmu_page_fault
[ 3536.084087] kvm_intel: disagrees about version of symbol kvm_mmu_reset_context
[ 3536.084093] kvm_intel: Unknown symbol kvm_mmu_reset_context
[ 3536.084476] kvm_intel: disagrees about version of symbol kvm_queue_exception_e
[ 3536.084482] kvm_intel: Unknown symbol kvm_queue_exception_e
[ 3536.084688] kvm_intel: disagrees about version of symbol kvm_emulate_cpuid
[ 3536.084694] kvm_intel: Unknown symbol kvm_emulate_cpuid
[ 3536.084901] kvm_intel: disagrees about version of symbol kvm_vcpu_init
[ 3536.084907] kvm_intel: Unknown symbol kvm_vcpu_init
[ 3536.085110] kvm_intel: disagrees about version of symbol gfn_to_hva
[ 3536.085116] kvm_intel: Unknown symbol gfn_to_hva
[ 3536.085413] kvm_intel: Unknown symbol kvm_mmu_invlpg
[ 3536.085688] kvm_intel: disagrees about version of symbol kvm_set_msr_common
[ 3536.085694] kvm_intel: Unknown symbol kvm_set_msr_common
[ 3536.086337] kvm_intel: disagrees about version of symbol kvm_cpu_get_interrupt
[ 3536.086343] kvm_intel: Unknown symbol kvm_cpu_get_interrupt
[ 3536.086569] kvm_intel: disagrees about version of symbol kvm_emulate_pio
[ 3536.086574] kvm_intel: Unknown symbol kvm_emulate_pio
[ 3536.086820] kvm_intel: disagrees about version of symbol kvm_mmu_set_mask_ptes
[ 3536.086828] kvm_intel: Unknown symbol kvm_mmu_set_mask_ptes
```

Looks like I still can't get KVM? Is there probably another option I have to enable besides Virtualization in my bios?

EDIT2: Rebooted, checked BIOS, and KVM still not able to be used. When I run it then run dmesg, I get:
```
[  105.177860] kvm: disabled by bios
```
So, basically, its not picking up that I can have enabled KVM in my bios?

FINAL EDIT: I got it to work by upgrading my BIOS. :D

---

