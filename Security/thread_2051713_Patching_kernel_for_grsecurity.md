---
title: "Patching kernel for grsecurity?"
date: 2012-09-01
forum: Security
---

### Post by Stonecold1995 on 2012-09-01
I'm trying to install the grsecurity patch for my Kubuntu desktop.  I'm currently running on kernel 3.2.0 as installed by apt-get, but the version I'm going to patch and install is 3.2.28 (vanilla kernel, downloaded directly from kernel.org).

This is what's in the directory with the stuff for grsecurity that I've downloaded:
```
alex@kubuntu:~/grsecurity stuff$ ls
[COLOR="Red"]gradm-2.9.1-201207201554.tar.gz[/COLOR]  gradm-2.9.1-201207201554.tar.gz.sig  grsecurity-2.9.1-3.2.28-201208302014.patch  grsecurity-2.9.1-3.2.28-201208302014.patch.sig  [COLOR="blue"]linux-3.2.8[/COLOR]  [COLOR="Red"]linux-3.2.8.tar[/COLOR]  linux-3.2.8.tar.sign  spender-gpg-key.asc
```

I tried patching the kernel source and this was the output:
```
alex@kubuntu:~/grsecurity stuff/linux-3.2.8$ patch -p1 < ../grsecurity-2.9.1-3.2.28-201208302014.patch
patching file Documentation/dontdiff
patching file Documentation/kernel-parameters.txt
patching file Documentation/sysctl/fs.txt
patching file Makefile
Hunk #8 succeeded at 1144 (offset -3 lines).
Hunk #9 succeeded at 1161 (offset -3 lines).
Hunk #10 succeeded at 1220 (offset -3 lines).
Hunk #11 succeeded at 1258 (offset -3 lines).
Hunk #12 succeeded at 1419 (offset -3 lines).
Hunk #13 succeeded at 1547 (offset -3 lines).
Hunk #14 succeeded at 1571 (offset -3 lines).
patching file arch/alpha/include/asm/atomic.h
patching file arch/alpha/include/asm/cache.h
patching file arch/alpha/include/asm/elf.h
patching file arch/alpha/include/asm/pgalloc.h
patching file arch/alpha/include/asm/pgtable.h
patching file arch/alpha/kernel/module.c
patching file arch/alpha/kernel/osf_sys.c
patching file arch/alpha/mm/fault.c
patching file arch/arm/include/asm/atomic.h
patching file arch/arm/include/asm/cache.h
patching file arch/arm/include/asm/cacheflush.h
patching file arch/arm/include/asm/elf.h
patching file arch/arm/include/asm/kmap_types.h
patching file arch/arm/include/asm/outercache.h
patching file arch/arm/include/asm/page.h
patching file arch/arm/include/asm/pgalloc.h
patching file arch/arm/include/asm/system.h
patching file arch/arm/include/asm/thread_info.h
patching file arch/arm/include/asm/uaccess.h
patching file arch/arm/kernel/armksyms.c
patching file arch/arm/kernel/entry-common.S
patching file arch/arm/kernel/process.c
Hunk #3 succeeded at 133 (offset -1 lines).
Hunk #4 succeeded at 247 (offset -2 lines).
Hunk #5 succeeded at 484 (offset -2 lines).
patching file arch/arm/kernel/ptrace.c
patching file arch/arm/kernel/setup.c
patching file arch/arm/kernel/traps.c
patching file arch/arm/lib/copy_from_user.S
patching file arch/arm/lib/copy_page.S
patching file arch/arm/lib/copy_to_user.S
patching file arch/arm/lib/uaccess.S
patching file arch/arm/lib/uaccess_with_memcpy.c
patching file arch/arm/mach-omap2/board-n8x0.c
patching file arch/arm/mach-ux500/mbox-db5500.c
patching file arch/arm/mm/fault.c
Hunk #2 succeeded at 391 (offset -2 lines).
Hunk #3 succeeded at 662 (offset -2 lines).
patching file arch/arm/mm/mmap.c
patching file arch/arm/plat-samsung/include/plat/dma-ops.h
patching file arch/arm/plat-samsung/include/plat/ehci.h
patching file arch/avr32/include/asm/cache.h
patching file arch/avr32/include/asm/elf.h
patching file arch/avr32/include/asm/kmap_types.h
patching file arch/avr32/mm/fault.c
patching file arch/blackfin/include/asm/cache.h
patching file arch/cris/include/arch-v10/arch/cache.h
patching file arch/cris/include/arch-v32/arch/cache.h
patching file arch/frv/include/asm/atomic.h
patching file arch/frv/include/asm/cache.h
patching file arch/frv/include/asm/kmap_types.h
patching file arch/frv/mm/elf-fdpic.c
patching file arch/h8300/include/asm/cache.h
patching file arch/hexagon/include/asm/cache.h
patching file arch/ia64/include/asm/atomic.h
patching file arch/ia64/include/asm/cache.h
patching file arch/ia64/include/asm/elf.h
patching file arch/ia64/include/asm/pgalloc.h
patching file arch/ia64/include/asm/pgtable.h
patching file arch/ia64/include/asm/spinlock.h
patching file arch/ia64/include/asm/uaccess.h
patching file arch/ia64/kernel/module.c
patching file arch/ia64/kernel/sys_ia64.c
patching file arch/ia64/kernel/vmlinux.lds.S
patching file arch/ia64/mm/fault.c
patching file arch/ia64/mm/hugetlbpage.c
patching file arch/ia64/mm/init.c
patching file arch/m32r/include/asm/cache.h
patching file arch/m32r/lib/usercopy.c
patching file arch/m68k/include/asm/cache.h
patching file arch/microblaze/include/asm/cache.h
patching file arch/mips/include/asm/atomic.h
patching file arch/mips/include/asm/cache.h
patching file arch/mips/include/asm/elf.h
patching file arch/mips/include/asm/page.h
patching file arch/mips/include/asm/pgalloc.h
patching file arch/mips/include/asm/system.h
patching file arch/mips/include/asm/thread_info.h
patching file arch/mips/kernel/binfmt_elfn32.c
patching file arch/mips/kernel/binfmt_elfo32.c
patching file arch/mips/kernel/process.c
patching file arch/mips/kernel/ptrace.c
patching file arch/mips/kernel/scall32-o32.S
patching file arch/mips/kernel/scall64-64.S
patching file arch/mips/kernel/scall64-n32.S
patching file arch/mips/kernel/scall64-o32.S
patching file arch/mips/mm/fault.c
patching file arch/mips/mm/mmap.c
patching file arch/mn10300/proc-mn103e010/include/proc/cache.h
patching file arch/mn10300/proc-mn2ws0050/include/proc/cache.h
patching file arch/openrisc/include/asm/cache.h
patching file arch/parisc/include/asm/atomic.h
patching file arch/parisc/include/asm/cache.h
patching file arch/parisc/include/asm/elf.h
patching file arch/parisc/include/asm/pgalloc.h
patching file arch/parisc/include/asm/pgtable.h
patching file arch/parisc/include/asm/uaccess.h
patching file arch/parisc/kernel/module.c
patching file arch/parisc/kernel/sys_parisc.c
patching file arch/parisc/kernel/traps.c
patching file arch/parisc/mm/fault.c
patching file arch/powerpc/include/asm/atomic.h
patching file arch/powerpc/include/asm/cache.h
patching file arch/powerpc/include/asm/elf.h
patching file arch/powerpc/include/asm/kmap_types.h
patching file arch/powerpc/include/asm/mman.h
patching file arch/powerpc/include/asm/page.h
patching file arch/powerpc/include/asm/page_64.h
patching file arch/powerpc/include/asm/pgalloc-64.h
patching file arch/powerpc/include/asm/pgtable.h
patching file arch/powerpc/include/asm/pte-hash32.h
patching file arch/powerpc/include/asm/reg.h
patching file arch/powerpc/include/asm/system.h
patching file arch/powerpc/include/asm/thread_info.h
patching file arch/powerpc/include/asm/uaccess.h
patching file arch/powerpc/kernel/exceptions-64e.S
patching file arch/powerpc/kernel/exceptions-64s.S
patching file arch/powerpc/kernel/irq.c
patching file arch/powerpc/kernel/module_32.c
patching file arch/powerpc/kernel/process.c
patching file arch/powerpc/kernel/ptrace.c
patching file arch/powerpc/kernel/signal_32.c
patching file arch/powerpc/kernel/signal_64.c
patching file arch/powerpc/kernel/syscalls.c
patching file arch/powerpc/kernel/traps.c
patching file arch/powerpc/kernel/vdso.c
patching file arch/powerpc/lib/usercopy_64.c
patching file arch/powerpc/mm/fault.c
patching file arch/powerpc/mm/mmap_64.c
patching file arch/powerpc/mm/slice.c
patching file arch/s390/include/asm/atomic.h
patching file arch/s390/include/asm/cache.h
patching file arch/s390/include/asm/elf.h
patching file arch/s390/include/asm/system.h
patching file arch/s390/include/asm/uaccess.h
patching file arch/s390/kernel/module.c
patching file arch/s390/kernel/process.c
Hunk #1 succeeded at 321 (offset 1 line).
patching file arch/s390/mm/mmap.c
Hunk #2 succeeded at 179 (offset -8 lines).
patching file arch/score/include/asm/cache.h
patching file arch/score/include/asm/system.h
patching file arch/score/kernel/process.c
patching file arch/sh/include/asm/cache.h
patching file arch/sh/mm/mmap.c
patching file arch/sparc/Kconfig
patching file arch/sparc/Makefile
patching file arch/sparc/include/asm/atomic_32.h
patching file arch/sparc/include/asm/atomic_64.h
patching file arch/sparc/include/asm/cache.h
patching file arch/sparc/include/asm/elf_32.h
patching file arch/sparc/include/asm/elf_64.h
patching file arch/sparc/include/asm/page_32.h
patching file arch/sparc/include/asm/pgalloc_32.h
patching file arch/sparc/include/asm/pgalloc_64.h
patching file arch/sparc/include/asm/pgtable_32.h
patching file arch/sparc/include/asm/pgtsrmmu.h
patching file arch/sparc/include/asm/spinlock_64.h
patching file arch/sparc/include/asm/thread_info_32.h
patching file arch/sparc/include/asm/thread_info_64.h
patching file arch/sparc/include/asm/uaccess.h
patching file arch/sparc/include/asm/uaccess_32.h
patching file arch/sparc/include/asm/uaccess_64.h
patching file arch/sparc/kernel/Makefile
patching file arch/sparc/kernel/process_32.c
patching file arch/sparc/kernel/process_64.c
patching file arch/sparc/kernel/ptrace_64.c
patching file arch/sparc/kernel/sys_sparc_32.c
patching file arch/sparc/kernel/sys_sparc_64.c
patching file arch/sparc/kernel/syscalls.S
patching file arch/sparc/kernel/traps_32.c
patching file arch/sparc/kernel/traps_64.c
patching file arch/sparc/kernel/unaligned_64.c
patching file arch/sparc/lib/Makefile
patching file arch/sparc/lib/atomic_64.S
patching file arch/sparc/lib/ksyms.c
patching file arch/sparc/mm/Makefile
patching file arch/sparc/mm/fault_32.c
patching file arch/sparc/mm/fault_64.c
patching file arch/sparc/mm/hugetlbpage.c
patching file arch/sparc/mm/init_32.c
patching file arch/sparc/mm/srmmu.c
patching file arch/tile/include/asm/atomic_64.h
patching file arch/tile/include/asm/cache.h
patching file arch/tile/include/asm/uaccess.h
patching file arch/um/Makefile
patching file arch/um/include/asm/cache.h
patching file arch/um/include/asm/kmap_types.h
patching file arch/um/include/asm/page.h
patching file arch/um/include/asm/pgtable-3level.h
patching file arch/um/kernel/process.c
patching file arch/unicore32/include/asm/cache.h
patching file arch/x86/Kconfig
patching file arch/x86/Kconfig.cpu
patching file arch/x86/Kconfig.debug
patching file arch/x86/Makefile
Hunk #2 succeeded at 196 (offset -4 lines).
patching file arch/x86/boot/Makefile
patching file arch/x86/boot/bitops.h
patching file arch/x86/boot/boot.h
patching file arch/x86/boot/compressed/Makefile
patching file arch/x86/boot/compressed/head_32.S
patching file arch/x86/boot/compressed/head_64.S
patching file arch/x86/boot/compressed/misc.c
patching file arch/x86/boot/cpucheck.c
patching file arch/x86/boot/header.S
patching file arch/x86/boot/memory.c
patching file arch/x86/boot/video-vesa.c
patching file arch/x86/boot/video.c
patching file arch/x86/crypto/aes-x86_64-asm_64.S
patching file arch/x86/crypto/aesni-intel_asm.S
Hunk #18 succeeded at 2523 (offset -2 lines).
Hunk #19 succeeded at 2551 (offset -2 lines).
Hunk #20 succeeded at 2580 (offset -2 lines).
Hunk #21 succeeded at 2641 (offset -2 lines).
patching file arch/x86/crypto/blowfish-x86_64-asm_64.S
patching file arch/x86/crypto/salsa20-x86_64-asm_64.S
patching file arch/x86/crypto/sha1_ssse3_asm.S
patching file arch/x86/crypto/twofish-x86_64-asm_64-3way.S
patching file arch/x86/crypto/twofish-x86_64-asm_64.S
patching file arch/x86/ia32/ia32_aout.c
patching file arch/x86/ia32/ia32_signal.c
patching file arch/x86/ia32/ia32entry.S
patching file arch/x86/ia32/sys_ia32.c
patching file arch/x86/include/asm/alternative-asm.h
patching file arch/x86/include/asm/alternative.h
patching file arch/x86/include/asm/apic.h
patching file arch/x86/include/asm/apm.h
patching file arch/x86/include/asm/atomic.h
patching file arch/x86/include/asm/atomic64_32.h
patching file arch/x86/include/asm/atomic64_64.h
patching file arch/x86/include/asm/bitops.h
patching file arch/x86/include/asm/boot.h
patching file arch/x86/include/asm/cache.h
patching file arch/x86/include/asm/cacheflush.h
patching file arch/x86/include/asm/checksum_32.h
patching file arch/x86/include/asm/cmpxchg.h
patching file arch/x86/include/asm/cpufeature.h
patching file arch/x86/include/asm/desc.h
patching file arch/x86/include/asm/desc_defs.h
patching file arch/x86/include/asm/e820.h
patching file arch/x86/include/asm/elf.h
patching file arch/x86/include/asm/emergency-restart.h
patching file arch/x86/include/asm/futex.h
patching file arch/x86/include/asm/hw_irq.h
patching file arch/x86/include/asm/i387.h
patching file arch/x86/include/asm/io.h
patching file arch/x86/include/asm/irqflags.h
patching file arch/x86/include/asm/kprobes.h
patching file arch/x86/include/asm/kvm_host.h
patching file arch/x86/include/asm/local.h
patching file arch/x86/include/asm/mman.h
patching file arch/x86/include/asm/mmu.h
patching file arch/x86/include/asm/mmu_context.h
patching file arch/x86/include/asm/module.h
patching file arch/x86/include/asm/page_64_types.h
patching file arch/x86/include/asm/paravirt.h
patching file arch/x86/include/asm/paravirt_types.h
patching file arch/x86/include/asm/pgalloc.h
patching file arch/x86/include/asm/pgtable-2level.h
patching file arch/x86/include/asm/pgtable-3level.h
Hunk #1 succeeded at 38 (offset -54 lines).
patching file arch/x86/include/asm/pgtable.h
patching file arch/x86/include/asm/pgtable_32.h
patching file arch/x86/include/asm/pgtable_32_types.h
patching file arch/x86/include/asm/pgtable_64.h
patching file arch/x86/include/asm/pgtable_64_types.h
patching file arch/x86/include/asm/pgtable_types.h
patching file arch/x86/include/asm/processor.h
Hunk #1 succeeded at 268 (offset 2 lines).
Hunk #2 succeeded at 861 (offset 2 lines).
Hunk #3 succeeded at 886 (offset 2 lines).
Hunk #4 succeeded at 897 (offset 2 lines).
Hunk #5 succeeded at 912 (offset 2 lines).
Hunk #6 succeeded at 922 (offset 2 lines).
Hunk #7 succeeded at 939 (offset 2 lines).
Hunk #8 succeeded at 965 (offset 2 lines).
patching file arch/x86/include/asm/ptrace.h
patching file arch/x86/include/asm/reboot.h
patching file arch/x86/include/asm/rwsem.h
patching file arch/x86/include/asm/segment.h
patching file arch/x86/include/asm/smp.h
patching file arch/x86/include/asm/spinlock.h
patching file arch/x86/include/asm/stackprotector.h
patching file arch/x86/include/asm/stacktrace.h
patching file arch/x86/include/asm/sys_ia32.h
patching file arch/x86/include/asm/system.h
patching file arch/x86/include/asm/thread_info.h
patching file arch/x86/include/asm/uaccess.h
patching file arch/x86/include/asm/uaccess_32.h
patching file arch/x86/include/asm/uaccess_64.h
patching file arch/x86/include/asm/vdso.h
patching file arch/x86/include/asm/x86_init.h
patching file arch/x86/include/asm/xsave.h
patching file arch/x86/kernel/acpi/realmode/Makefile
patching file arch/x86/kernel/acpi/realmode/wakeup.S
patching file arch/x86/kernel/acpi/sleep.c
patching file arch/x86/kernel/acpi/wakeup_32.S
patching file arch/x86/kernel/alternative.c
patching file arch/x86/kernel/apic/apic.c
Hunk #2 succeeded at 1853 (offset -4 lines).
patching file arch/x86/kernel/apic/io_apic.c
patching file arch/x86/kernel/apm_32.c
patching file arch/x86/kernel/asm-offsets.c
patching file arch/x86/kernel/asm-offsets_64.c
patching file arch/x86/kernel/cpu/Makefile
patching file arch/x86/kernel/cpu/amd.c
Hunk #1 succeeded at 664 (offset -16 lines).
patching file arch/x86/kernel/cpu/common.c
Hunk #3 succeeded at 790 (offset 5 lines).
Hunk #4 succeeded at 974 (offset 5 lines).
Hunk #5 succeeded at 992 (offset 5 lines).
Hunk #6 succeeded at 1057 (offset 5 lines).
Hunk #7 succeeded at 1112 (offset 5 lines).
Hunk #8 succeeded at 1138 (offset 5 lines).
Hunk #9 succeeded at 1147 (offset 5 lines).
Hunk #10 succeeded at 1200 (offset 5 lines).
patching file arch/x86/kernel/cpu/intel.c
patching file arch/x86/kernel/cpu/mcheck/mce.c
Hunk #2 succeeded at 203 (offset 2 lines).
Hunk #3 succeeded at 236 (offset 2 lines).
Hunk #4 succeeded at 263 (offset 2 lines).
Hunk #5 succeeded at 271 (offset 2 lines).
Hunk #6 succeeded at 611 (offset -6 lines).
Hunk #7 succeeded at 1399 (offset -6 lines).
Hunk #8 succeeded at 1422 (offset -6 lines).
Hunk #9 succeeded at 1438 (offset -6 lines).
Hunk #10 succeeded at 1446 (offset -6 lines).
Hunk #11 succeeded at 1454 (offset -6 lines).
Hunk #12 succeeded at 1465 (offset -6 lines).
Hunk #13 succeeded at 2174 (offset -6 lines).
patching file arch/x86/kernel/cpu/mcheck/p5.c
patching file arch/x86/kernel/cpu/mcheck/winchip.c
patching file arch/x86/kernel/cpu/mtrr/main.c
patching file arch/x86/kernel/cpu/mtrr/mtrr.h
patching file arch/x86/kernel/cpu/perf_event.c
patching file arch/x86/kernel/crash.c
patching file arch/x86/kernel/doublefault_32.c
patching file arch/x86/kernel/dumpstack.c
patching file arch/x86/kernel/dumpstack_32.c
patching file arch/x86/kernel/dumpstack_64.c
patching file arch/x86/kernel/early_printk.c
patching file arch/x86/kernel/entry_32.S
Hunk #1 succeeded at 186 (offset 6 lines).
Hunk #2 succeeded at 355 (offset 6 lines).
Hunk #3 succeeded at 363 (offset 6 lines).
Hunk #4 succeeded at 457 (offset 6 lines).
Hunk #5 succeeded at 482 with fuzz 2 (offset -3 lines).
Hunk #6 succeeded at 502 (offset -3 lines).
Hunk #7 succeeded at 518 (offset -3 lines).
Hunk #8 succeeded at 552 (offset -3 lines).
Hunk #9 succeeded at 588 (offset -3 lines).
Hunk #10 succeeded at 606 (offset -3 lines).
Hunk #11 succeeded at 640 (offset -3 lines).
Hunk #12 succeeded at 669 (offset -3 lines).
Hunk #13 succeeded at 694 (offset -3 lines).
Hunk #14 succeeded at 717 (offset -3 lines).
Hunk #15 succeeded at 785 (offset -3 lines).
Hunk #16 succeeded at 841 (offset -3 lines).
Hunk #17 succeeded at 870 (offset -3 lines).
Hunk #18 succeeded at 890 (offset -3 lines).
Hunk #19 succeeded at 981 (offset -3 lines).
Hunk #20 succeeded at 1020 (offset -3 lines).
Hunk #21 succeeded at 1081 (offset -3 lines).
Hunk #22 succeeded at 1129 (offset -3 lines).
Hunk #23 succeeded at 1150 (offset -3 lines).
Hunk #24 succeeded at 1158 (offset -3 lines).
Hunk #25 succeeded at 1167 (offset -3 lines).
Hunk #26 succeeded at 1181 (offset -3 lines).
Hunk #27 succeeded at 1189 (offset -3 lines).
Hunk #28 succeeded at 1197 (offset -3 lines).
Hunk #29 succeeded at 1205 (offset -3 lines).
Hunk #30 succeeded at 1241 (offset -3 lines).
Hunk #31 succeeded at 1250 (offset -3 lines).
Hunk #32 succeeded at 1259 (offset -3 lines).
Hunk #33 succeeded at 1374 (offset -3 lines).
Hunk #34 succeeded at 1403 (offset -3 lines).
Hunk #35 succeeded at 1439 (offset -3 lines).
Hunk #36 succeeded at 1460 (offset -3 lines).
Hunk #37 succeeded at 1474 (offset -3 lines).
Hunk #38 succeeded at 1519 (offset -3 lines).
Hunk #39 succeeded at 1572 (offset -3 lines).
Hunk #40 succeeded at 1609 (offset -3 lines).
Hunk #41 succeeded at 1648 (offset -3 lines).
Hunk #42 succeeded at 1668 (offset -3 lines).
Hunk #43 succeeded at 1683 (offset -3 lines).
patching file arch/x86/kernel/entry_64.S
patching file arch/x86/kernel/ftrace.c
patching file arch/x86/kernel/head32.c
patching file arch/x86/kernel/head_32.S
patching file arch/x86/kernel/head_64.S
patching file arch/x86/kernel/i386_ksyms_32.c
patching file arch/x86/kernel/i8259.c
patching file arch/x86/kernel/init_task.c
patching file arch/x86/kernel/ioport.c
patching file arch/x86/kernel/irq.c
patching file arch/x86/kernel/irq_32.c
patching file arch/x86/kernel/irq_64.c
patching file arch/x86/kernel/kdebugfs.c
patching file arch/x86/kernel/kgdb.c
Hunk #1 succeeded at 124 (offset -2 lines).
Hunk #2 succeeded at 473 (offset -2 lines).
Hunk #3 succeeded at 543 (offset -2 lines).
patching file arch/x86/kernel/kprobes.c
patching file arch/x86/kernel/kvm.c
patching file arch/x86/kernel/ldt.c
patching file arch/x86/kernel/machine_kexec_32.c
patching file arch/x86/kernel/microcode_intel.c
patching file arch/x86/kernel/module.c
patching file arch/x86/kernel/nmi.c
patching file arch/x86/kernel/paravirt-spinlocks.c
patching file arch/x86/kernel/paravirt.c
patching file arch/x86/kernel/pci-iommu_table.c
patching file arch/x86/kernel/process.c
patching file arch/x86/kernel/process_32.c
patching file arch/x86/kernel/process_64.c
patching file arch/x86/kernel/ptrace.c
patching file arch/x86/kernel/pvclock.c
patching file arch/x86/kernel/reboot.c
Hunk #5 succeeded at 570 (offset -8 lines).
Hunk #6 succeeded at 694 (offset -8 lines).
Hunk #7 succeeded at 709 (offset -8 lines).
Hunk #8 succeeded at 720 (offset -8 lines).
Hunk #9 succeeded at 729 (offset -8 lines).
patching file arch/x86/kernel/relocate_kernel_64.S
patching file arch/x86/kernel/setup.c
patching file arch/x86/kernel/setup_percpu.c
Hunk #3 succeeded at 205 (offset -12 lines).
Hunk #4 succeeded at 250 (offset -12 lines).
patching file arch/x86/kernel/signal.c
patching file arch/x86/kernel/smpboot.c
patching file arch/x86/kernel/step.c
patching file arch/x86/kernel/sys_i386_32.c
patching file arch/x86/kernel/sys_x86_64.c
patching file arch/x86/kernel/syscall_table_32.S
patching file arch/x86/kernel/tboot.c
patching file arch/x86/kernel/time.c
patching file arch/x86/kernel/tls.c
patching file arch/x86/kernel/trampoline_32.S
patching file arch/x86/kernel/trampoline_64.S
patching file arch/x86/kernel/traps.c
patching file arch/x86/kernel/verify_cpu.S
patching file arch/x86/kernel/vm86_32.c
Hunk #3 succeeded at 209 (offset -2 lines).
Hunk #4 succeeded at 246 (offset -2 lines).
Hunk #5 succeeded at 340 (offset -2 lines).
Hunk #6 succeeded at 545 (offset -2 lines).
patching file arch/x86/kernel/vmlinux.lds.S
patching file arch/x86/kernel/vsyscall_64.c
patching file arch/x86/kernel/x8664_ksyms_64.c
patching file arch/x86/kernel/xsave.c
patching file arch/x86/kvm/emulate.c
patching file arch/x86/kvm/lapic.c
patching file arch/x86/kvm/mmu.c
patching file arch/x86/kvm/paging_tmpl.h
patching file arch/x86/kvm/svm.c
Hunk #1 succeeded at 3400 (offset -5 lines).
Hunk #2 succeeded at 3782 (offset -5 lines).
patching file arch/x86/kvm/vmx.c
Hunk #2 succeeded at 2637 (offset -1 lines).
Hunk #3 succeeded at 3655 (offset -1 lines).
Hunk #4 succeeded at 6176 (offset -3 lines).
Hunk #5 succeeded at 6230 (offset -3 lines).
Hunk #6 succeeded at 6263 (offset -3 lines).
patching file arch/x86/kvm/x86.c
Hunk #6 succeeded at 5173 (offset -26 lines).
patching file arch/x86/lguest/boot.c
patching file arch/x86/lib/atomic64_32.c
patching file arch/x86/lib/atomic64_386_32.S
patching file arch/x86/lib/atomic64_cx8_32.S
patching file arch/x86/lib/checksum_32.S
patching file arch/x86/lib/clear_page_64.S
patching file arch/x86/lib/cmpxchg16b_emu.S
patching file arch/x86/lib/copy_page_64.S
patching file arch/x86/lib/copy_user_64.S
patching file arch/x86/lib/copy_user_nocache_64.S
patching file arch/x86/lib/csum-copy_64.S
patching file arch/x86/lib/csum-wrappers_64.c
patching file arch/x86/lib/getuser.S
patching file arch/x86/lib/insn.c
patching file arch/x86/lib/iomap_copy_64.S
patching file arch/x86/lib/memcpy_64.S
patching file arch/x86/lib/memmove_64.S
patching file arch/x86/lib/memset_64.S
patching file arch/x86/lib/mmx_32.c
patching file arch/x86/lib/msr-reg.S
patching file arch/x86/lib/putuser.S
patching file arch/x86/lib/rwlock.S
patching file arch/x86/lib/rwsem.S
patching file arch/x86/lib/thunk_64.S
patching file arch/x86/lib/usercopy_32.c
patching file arch/x86/lib/usercopy_64.c
patching file arch/x86/mm/extable.c
patching file arch/x86/mm/fault.c
patching file arch/x86/mm/gup.c
patching file arch/x86/mm/highmem_32.c
patching file arch/x86/mm/hugetlbpage.c
patching file arch/x86/mm/init.c
patching file arch/x86/mm/init_32.c
patching file arch/x86/mm/init_64.c
patching file arch/x86/mm/iomap_32.c
patching file arch/x86/mm/ioremap.c
patching file arch/x86/mm/kmemcheck/kmemcheck.c
patching file arch/x86/mm/mmap.c
patching file arch/x86/mm/mmio-mod.c
patching file arch/x86/mm/pageattr-test.c
patching file arch/x86/mm/pageattr.c
patching file arch/x86/mm/pat.c
patching file arch/x86/mm/pf_in.c
patching file arch/x86/mm/pgtable.c
patching file arch/x86/mm/pgtable_32.c
patching file arch/x86/mm/setup_nx.c
patching file arch/x86/mm/tlb.c
patching file arch/x86/net/bpf_jit.S
patching file arch/x86/net/bpf_jit_comp.c
Hunk #3 FAILED at 485.
Hunk #4 FAILED at 500.
Hunk #5 succeeded at 594 (offset 4 lines).
Hunk #6 succeeded at 626 (offset 4 lines).
Hunk #7 succeeded at 644 (offset 4 lines).
Hunk #8 succeeded at 655 (offset 4 lines).
2 out of 8 hunks FAILED -- saving rejects to file arch/x86/net/bpf_jit_comp.c.rej
patching file arch/x86/oprofile/backtrace.c
patching file arch/x86/pci/mrst.c
patching file arch/x86/pci/pcbios.c
patching file arch/x86/platform/efi/efi_32.c
patching file arch/x86/platform/efi/efi_stub_32.S
patching file arch/x86/platform/efi/efi_stub_64.S
patching file arch/x86/platform/mrst/mrst.c
patching file arch/x86/power/cpu.c
can't find file to patch at input line 26972
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/arch/x86/tools/relocs.c b/arch/x86/tools/relocs.c
|index e529730..8d08690 100644
|--- a/arch/x86/tools/relocs.c
|+++ b/arch/x86/tools/relocs.c
--------------------------
File to patch: 
```

It's currently waiting for input...  How do I fix this?  Should I just skip that file and let it continue?  I'm using [https://secure.wikimedia.org/wikibooks/en/wiki/Grsecurity]("https://secure.wikimedia.org/wikibooks/en/wiki/Grsecurity") for instructions on how to patch my system.


Also, is there anything I should know about grsecurity (or compiling a hardened kernel in general) before installing?  Because although I'm not totally new to Linux, I'm still learning and I don't want to make any major mistakes.

---

### Post by bodhi.zazen on 2012-09-02
You should know:

1. By default, Ubuntu uses apparmor, so I would use apparmor rather then grsecurity. What makes you think you need grsecurity ?

2. Custom kernels are not supported here.

3. If you wish to use grsecurity, you will need to read

[http://www.gentoo.org/proj/en/hardened/grsecurity.xml](http://www.gentoo.org/proj/en/hardened/grsecurity.xml)

[http://en.wikibooks.org/wiki/Grsecurity](http://en.wikibooks.org/wiki/Grsecurity)

The patch is generally against the Vanilla kernel, not the Ubuntu Kernel (which is patched by the Ubuntu kernel team).

[http://kernel.org/](http://kernel.org/)

If you have a problem, you will need to contact grsecurity ;)

Other then those issues, grsecurity works well ( I use gentoo hardened).

---

### Post by Stonecold1995 on 2012-09-02
OK.  So is there a way I can get some of the features in grsecurity without compiling a new kernel?

---

### Post by Hungry Man on 2012-09-02
@bhodizazen,

You can use Apparmor and RBAC (the access control module) at the same time. RBAC doesn't use LSM.

@StoneCold

[https://insanitybit.wordpress.com/?s=patch+pax+custom+kernel](https://insanitybit.wordpress.com/?s=patch+pax+custom+kernel)

I wrote a guide there for 3.8.3. It will work the same with 3.x.

No, there is no way to get the features in grsecurity without compiling your own kernel.

---

### Post by Stonecold1995 on 2012-09-02
If I do install a patched kernel, would it be easy to revert the changes (e.g. selecting "Use an older kernel" on GRUB or making another entry, one for booting into the hardened kernel and one for the normal kernel)?

---

### Post by Hungry Man on 2012-09-02
You should be able to boot into an old kernel.

---

### Post by muppetmania on 2012-09-02
Hi,

Long time grsecurity user here.

If you want to use grsecurity, you need to download a vanilla kernel from ftp.kernel.org (or a mirror) and patch that.  Trying to a patch the Ubuntu kernel *will not work* because Ubuntu already put a lot of their own patches in.

You can get grsecurity to work quite happily with Ubuntu, you just need to be careful which settings you enable (don't turn everything on straight away!) and have the appropriate tools (paxctl) installed so you can modify the binaries that might get killed because of the enhanced grsecurity protection features.

From your output above, it looks like you've downloaded **3.2.8** and not **3.2.*28***.  If you download the correct kernel and patch it, it should work a lot better.

Hope this helps.

Tim

---

### Post by Stonecold1995 on 2012-09-02
> **muppetmania said:**
> Hi,

Long time grsecurity user here.

If you want to use grsecurity, you need to download a vanilla kernel from ftp.kernel.org (or a mirror) and patch that.  Trying to a patch the Ubuntu kernel *will not work* because Ubuntu already put a lot of their own patches in.

You can get grsecurity to work quite happily with Ubuntu, you just need to be careful which settings you enable (don't turn everything on straight away!) and have the appropriate tools (paxctl) installed so you can modify the binaries that might get killed because of the enhanced grsecurity protection features.

From your output above, it looks like you've downloaded **3.2.8** and not **3.2.*28***.  If you download the correct kernel and patch it, it should work a lot better.

Hope this helps.

Tim

Oh wow thank you the version was just wrong.  Epic fail on my part lol.

Anyways, can you link me to a good resource that'll allow me to know what features to give my kernel for my specific hardware (and for grsecurity's features)?  Will it automatically detect all my hardware/CPU capabilities etc or do I have to choose each option manually?  There are sooooo many options... -_-

Also, about the "learning mode", how accurate is that?  If it'll cause problems I want things like that and (and maybe PaX) disabled and just keep the patches that reduce vulnerabilities.

---

### Post by muppetmania on 2012-09-02
> **Stonecold1995 said:**
> Oh wow thank you the version was just wrong.  Epic fail on my part lol.

Anyways, can you link me to a good resource that'll allow me to know what features to give my kernel for my specific hardware (and for grsecurity's features)?  Will it automatically detect all my hardware/CPU capabilities etc or do I have to choose each option manually?  There are sooooo many options... -_-

Also, about the "learning mode", how accurate is that?  If it'll cause problems I want things like that and (and maybe PaX) disabled and just keep the patches that reduce vulnerabilities.

I would read the **[Grsecurity Wikibook]("http://en.wikibooks.org/wiki/Grsecurity")** and turn options on slowly.   mprotect will probably cause you the most grief, as software that does "Just In Time" will often error out (Java, Firefox, Chrome) and refuse to run.

Also the CONFIG_GRKERNSEC_IO option can cause X not to run, so I'd advise against turning that on!

The RBAC system of Grsecurity (which is where the learning comes in) is very powerful, but I'd actually hold off using any RBAC stuff on a standard desktop system.  That's because it's a "default deny" policy.  So as soon as you try to do something you didn't do during learning, it won't work.  The policy will get in your way more often than not.

For a server system, where you know exactly what it's supposed to be doing, RBAC is great.  And with a lot of tweaking you can get RBAC to work on a Desktop system, but I'd suggest it's more trouble than the benefit you'd get from it.

The other protections that grsecurity offers will all work to make your system less-exploitable than a standard Ubuntu configuration.

Key points:

1) Take it slowly! Understand what an option does before you turn it on.
2) Read all the documentation. Understand how to use the *paxctl* command.
3) Don't think because you've got a grsec enabled kernel, you're immune to all/any exploits.  The recent EXIM exploit worked regardless of grsecurity, for example.

Hope this helps!

Tim

---

### Post by Hungry Man on 2012-09-02
All of the options in my guide are compatible with Ubuntu. I use the same settings.

If you have a dedicated ati GPU you need to disable one setting.

---

### Post by Stonecold1995 on 2012-09-02
> **muppetmania said:**
> I would read the **[Grsecurity Wikibook]("http://en.wikibooks.org/wiki/Grsecurity")** and turn options on slowly.   mprotect will probably cause you the most grief, as software that does "Just In Time" will often error out (Java, Firefox, Chrome) and refuse to run.

Also the CONFIG_GRKERNSEC_IO option can cause X not to run, so I'd advise against turning that on!

The RBAC system of Grsecurity (which is where the learning comes in) is very powerful, but I'd actually hold off using any RBAC stuff on a standard desktop system.  That's because it's a "default deny" policy.  So as soon as you try to do something you didn't do during learning, it won't work.  The policy will get in your way more often than not.

For a server system, where you know exactly what it's supposed to be doing, RBAC is great.  And with a lot of tweaking you can get RBAC to work on a Desktop system, but I'd suggest it's more trouble than the benefit you'd get from it.

The other protections that grsecurity offers will all work to make your system less-exploitable than a standard Ubuntu configuration.

Key points:

1) Take it slowly! Understand what an option does before you turn it on.
2) Read all the documentation. Understand how to use the *paxctl* command.
3) Don't think because you've got a grsec enabled kernel, you're immune to all/any exploits.  The recent EXIM exploit worked regardless of grsecurity, for example.

Hope this helps!

Tim

I am reading the Grsecurity wiki, but most of the options are really confusing.  How do I turn off CONFIG_GRKERNSEC_IO?  And by not using mprotect do you mean selecting "Restrict mprotect()", or deselecting it?  Also, what non-grsecurity options should I select (just kernel options, and other kernel security settings), or where can I go to get more info on which ones to use?

---

### Post by rookcifer on 2012-09-02
> **Stonecold1995 said:**
> I am reading the Grsecurity wiki, but most of the options are really confusing.  How do I turn off CONFIG_GRKERNSEC_IO?  And by not using mprotect do you mean selecting "Restrict mprotect()", or deselecting it?  Also, what non-grsecurity options should I select (just kernel options, and other kernel security settings), or where can I go to get more info on which ones to use?

GrSecurity is a pain to configure.  It breaks most things.  It is better for servers where there is no Xorg environment.

It's best to use a distro that comes with GRsec already.  Compiling it on Ubuntu is not worth the trouble.

---

### Post by bodhi.zazen on 2012-09-03
> **rookcifer said:**
> GrSecurity is a pain to configure.  It breaks most things.  It is better for servers where there is no Xorg environment.

It's best to use a distro that comes with GRsec already.  Compiling it on Ubuntu is not worth the trouble.

+1 to that.

As I said earlier, Ubuntu uses Apparmor, so using grsecurity on Ubuntu makes about as much sense as using selinux on Ubuntu.

grsecurity works well on gentoo hardened, with X.

PaX is easy enough to learn. The documentation is easy enough to follow, you will be able to run PaX within an hour.

The 'problem' I have always had is with the RBAC. Why would you want to start writing security policy for yourself from scratch ? If you are not familiar with Linux, it makes no sense. How do you know what is normal ? What to allow and what to deny ?

Sure, if you are experienced with Linux you can derive a set of rules, but it is not easy.

Better by far, IMO, to use apparmor (on Ubuntu) or selinux (on Fedora) as these tools include a default set of rules.

"CONFIG_GRKERNSEC_IO" is an option you have when compiling your (patched) kernel. Again, it sounds as if you have a bit of reading to do both on compiling kernels and compiling / configuring grsecurity.

[http://bodhizazen.net/Tutorials/kernel](http://bodhizazen.net/Tutorials/kernel)

---

### Post by Stonecold1995 on 2012-09-03
> **bodhi.zazen said:**
> I said earlier, Ubuntu uses Apparmor, so using grsecurity on Ubuntu makes about as much sense as using selinux on Ubuntu.

I do use AppArmor, but it does nothing to protect from 0day attacks or really advanced attacks.  Plus it's limited in what it's  able to do (you can't configure *everything* to be protected by AppArmor, only those apps you have, or make, profiles for).  I just want a kernel with naturally greater security, no new visible features but just simply more secure, and I don't know when, or if, the features in grsecurity will ever be included in the natural Linux kernel.  And all I'm trying to do is find good resources to learn.  So far everything I've seen says the same thing.  I know *how* to compile and install a custom kernel, but I don't know what options should be selected and I don't know where to find that information for my specific laptop.

---

### Post by bodhi.zazen on 2012-09-03
> **Stonecold1995 said:**
> I do use AppArmor, but it does nothing to protect from 0day attacks or really advanced attacks.  Plus it's limited in what it's  able to do (you can't configure *everything* to be protected by AppArmor, only those apps you have, or make, profiles for).  I just want a kernel with naturally greater security, no new visible features but just simply more secure, and I don't know when, or if, the features in grsecurity will ever be included in the natural Linux kernel.  And all I'm trying to do is find good resources to learn.  So far everything I've seen says the same thing.  I know *how* to compile and install a custom kernel, but I don't know what options should be selected and I don't know where to find that information for my specific laptop.

Well, there is nothing that protects against all zero day attacks and apparmor does a nice job.

Apparmor with the default policies is a better place for you to start then RBAC. With RBAC you start with no policies by default and have to write them all yourself. With apparmor you have default policies you can start with, use as templates, and support on the ubuntu forums.

If you need more then apparmor, I highly suggest selinux.

Fedora uses selinux and the major advantage for you over grsecurity is that there is an entire team of people to maintain selinux policy.

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/)

[http://fedoraproject.org/wiki/SELinux](http://fedoraproject.org/wiki/SELinux)

If you want grsecurity, I highly suggest gentoo hardened.

The problem you will have with grsecurity is that , for the most part, you are on your own and you seem to be a little new to Linux to be starting with custom kernels and writing security policy.

---

### Post by Stonecold1995 on 2012-09-03
> **bodhi.zazen said:**
> The problem you will have with grsecurity is that , for the most part, you are on your own and you seem to be a little new to Linux to be starting with custom kernels and writing security policy.

I'm not asking how to write custom security policies or set up RBAC.  I only want the security patches which don't require too much experience and take effect automatically, like hiding kernel symbols, making chroots more tight (apparently Chromium's sandbox uses chroots to keep processes isolated, so that would even make Chromium more safe), etc which all don't require extensive knowledge of Linux.

I understand the basics of how to compile and install a custom kernel, and I can do that, I'm just wondering what the optimal options are or *where I can find out* for my specific computer.

---

### Post by rookcifer on 2012-09-03
> **Stonecold1995 said:**
> I'm not asking how to write custom security policies or set up RBAC.  I only want the security patches which don't require too much experience and take effect automatically, like hiding kernel symbols, making chroots more tight (apparently Chromium's sandbox uses chroots to keep processes isolated, so that would even make Chromium more safe), etc which all don't require extensive knowledge of Linux.

I understand the basics of how to compile and install a custom kernel, and I can do that, I'm just wondering what the optimal options are or *where I can find out* for my specific computer.

You could try the Grsecurity forums, but beware most of those guys are uber geeks and are kind of snotty.  I tried compiling a Grsec kernel for Ubuntu a while back (just for testing).  I went to the Grsec forums for help and was told basically to not use Ubuntu.

---

### Post by Stonecold1995 on 2012-09-07
Those forums are way to advanced for me. 0_0

I'm compiling the kernel right now.  Is there a way I can boot from it just to "try it out" before actually installing it?

---

### Post by bodhi.zazen on 2012-09-07
> **Stonecold1995 said:**
> Those forums are way to advanced for me. 0_0

I'm compiling the kernel right now.  Is there a way I can boot from it just to "try it out" before actually installing it?

There is a learning curve to grsecurity, but you will need to read the documentation.

First step is to compile the kernel. You can then boot it and start to read about PaX. PaX is easy enough and the gentoo links I gave you are straight forward enough to get you started.

---

### Post by wacky_sung on 2012-09-08
> **bodhi.zazen said:**
> There is a learning curve to grsecurity, but you will need to read the documentation.

First step is to compile the kernel. You can then boot it and start to read about PaX. PaX is easy enough and the gentoo links I gave you are straight forward enough to get you started.

I do agree with bodhi.zazen after reading the whole thread.:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by Stonecold1995 on 2012-09-08
I tried installing, and this is what I got:

```
alex@kubuntu:~/grsecurity_stuff$ sudo dpkg -i *.deb
(Reading database ... 295191 files and directories currently installed.)
Unpacking linux-firmware-image (from linux-firmware-image_3.2.28-grsec-1_amd64.deb) ...
dpkg: error processing linux-firmware-image_3.2.28-grsec-1_amd64.deb (--install):
 trying to overwrite '/lib/firmware/korg/k1212.dsp', which is also in package linux-firmware 1.79.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-3.2.28-grsec.
Unpacking linux-headers-3.2.28-grsec (from linux-headers-3.2.28-grsec_3.2.28-grsec-1_amd64.deb) ...
Selecting previously unselected package linux-image-3.2.28-grsec.
Unpacking linux-image-3.2.28-grsec (from linux-image-3.2.28-grsec_3.2.28-grsec-1_amd64.deb) ...
Preparing to replace linux-libc-dev 3.2.28-grsec-1 (using linux-libc-dev_3.2.28-grsec-1_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-headers-3.2.28-grsec (3.2.28-grsec-1) ...
Setting up linux-image-3.2.28-grsec (3.2.28-grsec-1) ...
ERROR (dkms apport): kernel package linux-headers-3.2.28-grsec is not supported
Error! Bad return status for module build on kernel: 3.2.28-grsec (x86_64)
Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information.
update-initramfs: Generating /boot/initrd.img-3.2.28-grsec

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.28-grsec with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.28-grsec 
Found linux image: /boot/vmlinuz-3.2.0-31-generic 
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found memtest86+ image: /memtest86+.bin
  No volume groups found
done
dpkg: error processing linux-image-3.2.28-grsec (--install):
 subprocess installed post-installation script returned error exit status 1 
Setting up linux-libc-dev (3.2.28-grsec-1) ... 
Errors were encountered while processing:  
 linux-firmware-image_3.2.28-grsec-1_amd64.deb  
 linux-image-3.2.28-grsec
```

It says "No space left on device", but /boot has plenty of free space.  I tried rebooting, and several seconds after the grsec kernel loaded it went into a kernel panic, so I had to select a previous kernel version, reboot, and uninstall grsec.
```
alex@kubuntu:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/sdb5_crypt   30G   15G   13G  54% /
udev                    7.8G   12K  7.8G   1% /dev
tmpfs                   7.8G  184K  7.8G   1% /tmp
tmpfs                   3.2G  964K  3.2G   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    7.8G  2.2M  7.8G   1% /run/shm
**/dev/sdb1               228M   62M  154M  29% /boot**
/dev/mapper/sda1_crypt  688G  502G  151G  77% /home
```

Anyone know why this is happening?

---

### Post by Stonecold1995 on 2013-05-31
> **muppetmania said:**
> Hi,

Long time grsecurity user here.

If you want to use grsecurity, you need to download a vanilla kernel from ftp.kernel.org (or a mirror) and patch that.  Trying to a patch the Ubuntu kernel *will not work* because Ubuntu already put a lot of their own patches in.

You can get grsecurity to work quite happily with Ubuntu, you just need to be careful which settings you enable (don't turn everything on straight away!) and have the appropriate tools (paxctl) installed so you can modify the binaries that might get killed because of the enhanced grsecurity protection features.

From your output above, it looks like you've downloaded **3.2.8** and not **3.2.*28***.  If you download the correct kernel and patch it, it should work a lot better.

Hope this helps.

Tim

What kind of patches are put on the Ubuntu kernel?  Will losing them and using the grsecurity patch instead cause any problems once I am no longer using a kernel optimized for *buntu?

---

### Post by Hungry Man on 2013-05-31
I am currently using a Grsecurity kernel with very few issues, nothing critical. 

If you're getting a kernel panic it may be due to some kind of driver incompatibility. Try the 3.9.4 kernel + 3.9.4 patch, that's what I'm currently running.

---

