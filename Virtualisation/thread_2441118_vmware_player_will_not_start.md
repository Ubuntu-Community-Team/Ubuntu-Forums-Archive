---
title: "vmware player will not start?"
date: 2020-04-19
forum: Virtualisation
---

### Post by LMH1 on 2020-04-19
Get error can not comple kernel?
```
sudo vmware-modconfig --console --install-all 
[AppLoader] Use shipped Linux kernel AIO access library.
An up-to-date "libaio" or "libaio1" package from your system is preferred.
[AppLoader] GLib does not have GSettings support.
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
make: Entering directory '/tmp/modconfig-2NnvAk/vmmon-only'
Using kernel build system.
/usr/bin/make -C /lib/modules/5.4.0-24-generic/build/include/.. M=$PWD SRCROOT=$PWD/. \
  MODULEBUILDDIR= modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-24-generic'
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/memtrack.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/apic.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/statVarsVmmon.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/sharedAreaVmmon.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/cpuid.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/task.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/comport.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/common/phystrack.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/bootstrap/monLoaderVmmon.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/bootstrap/monLoader.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/bootstrap/vmmblob.o
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/bootstrap/bootstrap.o
In file included from ./arch/x86/include/asm/processor.h:5,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./arch/x86/include/asm/mmu.h:5,
                 from ./arch/x86/include/asm/desc.h:7,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:71:
./arch/x86/include/asm/processor-flags.h:39: warning: "CR3_PCID_MASK" redefined
   39 | #define CR3_PCID_MASK 0xFFFull
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm_x86.h:41,
                 from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:44,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:53:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86_basic_defs.h:78: note: this is the location of the previous definition
   78 | #define CR3_PCID_MASK  0xFFF
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/paravirt_types.h:46,
                 from ./arch/x86/include/asm/ptrace.h:94,
                 from ./arch/x86/include/asm/math_emu.h:5,
                 from ./arch/x86/include/asm/processor.h:12,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./arch/x86/include/asm/mmu.h:5,
                 from ./arch/x86/include/asm/desc.h:7,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:71:
./arch/x86/include/asm/msr-index.h:512: warning: "MSR_K7_HWCR_SMMLOCK" redefined
  512 | #define MSR_K7_HWCR_SMMLOCK  BIT_ULL(MSR_K7_HWCR_SMMLOCK_BIT)
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:51:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:474: note: this is the location of the previous definition
  474 | #define MSR_K7_HWCR_SMMLOCK        0x00000001ULL // Lock SMM environment
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/paravirt_types.h:46,
                 from ./arch/x86/include/asm/ptrace.h:94,
                 from ./arch/x86/include/asm/math_emu.h:5,
                 from ./arch/x86/include/asm/processor.h:12,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./arch/x86/include/asm/mmu.h:5,
                 from ./arch/x86/include/asm/desc.h:7,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:71:
./arch/x86/include/asm/msr-index.h:702: warning: "MSR_MISC_FEATURES_ENABLES" redefined
  702 | #define MSR_MISC_FEATURES_ENABLES 0x00000140
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:51:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:134: note: this is the location of the previous definition
  134 | #define MSR_MISC_FEATURES_ENABLES            0x140
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/paravirt_types.h:46,
                 from ./arch/x86/include/asm/ptrace.h:94,
                 from ./arch/x86/include/asm/math_emu.h:5,
                 from ./arch/x86/include/asm/processor.h:12,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./arch/x86/include/asm/mmu.h:5,
                 from ./arch/x86/include/asm/desc.h:7,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:71:
./arch/x86/include/asm/msr-index.h:711: warning: "MSR_TSX_FORCE_ABORT" redefined
  711 | #define MSR_TSX_FORCE_ABORT  0x0000010F
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/task.c:51:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:633: note: this is the location of the previous definition
  633 | #define MSR_TSX_FORCE_ABORT                      0x0000010f
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:43:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:134: warning: "MSR_MISC_FEATURES_ENABLES" redefined
  134 | #define MSR_MISC_FEATURES_ENABLES            0x140
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:31:
./arch/x86/include/asm/msr-index.h:702: note: this is the location of the previous definition
  702 | #define MSR_MISC_FEATURES_ENABLES 0x00000140
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:43:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:474: warning: "MSR_K7_HWCR_SMMLOCK" redefined
  474 | #define MSR_K7_HWCR_SMMLOCK        0x00000001ULL // Lock SMM environment
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:31:
./arch/x86/include/asm/msr-index.h:512: note: this is the location of the previous definition
  512 | #define MSR_K7_HWCR_SMMLOCK  BIT_ULL(MSR_K7_HWCR_SMMLOCK_BIT)
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:43:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:633: warning: "MSR_TSX_FORCE_ABORT" redefined
  633 | #define MSR_TSX_FORCE_ABORT                      0x0000010f
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:31:
./arch/x86/include/asm/msr-index.h:711: note: this is the location of the previous definition
  711 | #define MSR_TSX_FORCE_ABORT  0x0000010F
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.c:35:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:134: warning: "MSR_MISC_FEATURES_ENABLES" redefined
  134 | #define MSR_MISC_FEATURES_ENABLES            0x140
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.c:31:
./arch/x86/include/asm/msr-index.h:702: note: this is the location of the previous definition
  702 | #define MSR_MISC_FEATURES_ENABLES 0x00000140
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.c:35:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:474: warning: "MSR_K7_HWCR_SMMLOCK" redefined
  474 | #define MSR_K7_HWCR_SMMLOCK        0x00000001ULL // Lock SMM environment
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.c:31:
./arch/x86/include/asm/msr-index.h:512: note: this is the location of the previous definition
  512 | #define MSR_K7_HWCR_SMMLOCK  BIT_ULL(MSR_K7_HWCR_SMMLOCK_BIT)
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.c:35:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:633: warning: "MSR_TSX_FORCE_ABORT" redefined
  633 | #define MSR_TSX_FORCE_ABORT                      0x0000010f
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm_x86.h:41,
                 from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:44,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:45:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86_basic_defs.h:78: warning: "CR3_PCID_MASK" redefined
   78 | #define CR3_PCID_MASK  0xFFF
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/vmcore/moduleloop.c:31:
./arch/x86/include/asm/msr-index.h:711: note: this is the location of the previous definition
  711 | #define MSR_TSX_FORCE_ABORT  0x0000010F
      | 
In file included from ./arch/x86/include/asm/irqflags.h:5,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from /tmp/modconfig-2NnvAk/vmmon-only/common/vmx86.c:31:
./arch/x86/include/asm/processor-flags.h:39: note: this is the location of the previous definition
   39 | #define CR3_PCID_MASK 0xFFFull
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.h:33,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:47:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:134: warning: "MSR_MISC_FEATURES_ENABLES" redefined
  134 | #define MSR_MISC_FEATURES_ENABLES            0x140
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/paravirt_types.h:46,
                 from ./arch/x86/include/asm/ptrace.h:94,
                 from ./arch/x86/include/asm/math_emu.h:5,
                 from ./arch/x86/include/asm/processor.h:12,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/wait.h:9,
                 from ./include/linux/wait_bit.h:8,
                 from ./include/linux/fs.h:6,
                 from ./include/linux/highmem.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:25:
./arch/x86/include/asm/msr-index.h:702: note: this is the location of the previous definition
  702 | #define MSR_MISC_FEATURES_ENABLES 0x00000140
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.h:33,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:47:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:474: warning: "MSR_K7_HWCR_SMMLOCK" redefined
  474 | #define MSR_K7_HWCR_SMMLOCK        0x00000001ULL // Lock SMM environment
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:60:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:134: warning: "MSR_MISC_FEATURES_ENABLES" redefined
  134 | #define MSR_MISC_FEATURES_ENABLES            0x140
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/paravirt_types.h:46,
                 from ./arch/x86/include/asm/ptrace.h:94,
                 from ./arch/x86/include/asm/math_emu.h:5,
                 from ./arch/x86/include/asm/processor.h:12,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/wait.h:9,
                 from ./include/linux/wait_bit.h:8,
                 from ./include/linux/fs.h:6,
                 from ./include/linux/highmem.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:25:
./arch/x86/include/asm/msr-index.h:512: note: this is the location of the previous definition
  512 | #define MSR_K7_HWCR_SMMLOCK  BIT_ULL(MSR_K7_HWCR_SMMLOCK_BIT)
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from ./include/linux/binfmts.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:32:
./arch/x86/include/asm/msr-index.h:702: note: this is the location of the previous definition
  702 | #define MSR_MISC_FEATURES_ENABLES 0x00000140
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./common/vmx86.h:32,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.h:33,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:47:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:633: warning: "MSR_TSX_FORCE_ABORT" redefined
  633 | #define MSR_TSX_FORCE_ABORT                      0x0000010f
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/paravirt_types.h:46,
                 from ./arch/x86/include/asm/ptrace.h:94,
                 from ./arch/x86/include/asm/math_emu.h:5,
                 from ./arch/x86/include/asm/processor.h:12,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/wait.h:9,
                 from ./include/linux/wait_bit.h:8,
                 from ./include/linux/fs.h:6,
                 from ./include/linux/highmem.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:25:
./arch/x86/include/asm/msr-index.h:711: note: this is the location of the previous definition
  711 | #define MSR_TSX_FORCE_ABORT  0x0000010F
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:60:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:474: warning: "MSR_K7_HWCR_SMMLOCK" redefined
  474 | #define MSR_K7_HWCR_SMMLOCK        0x00000001ULL // Lock SMM environment
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from ./include/linux/binfmts.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:32:
./arch/x86/include/asm/msr-index.h:512: note: this is the location of the previous definition
  512 | #define MSR_K7_HWCR_SMMLOCK  BIT_ULL(MSR_K7_HWCR_SMMLOCK_BIT)
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:60:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86msr.h:633: warning: "MSR_TSX_FORCE_ABORT" redefined
  633 | #define MSR_TSX_FORCE_ABORT                      0x0000010f
      | 
In file included from ./arch/x86/include/asm/nospec-branch.h:11,
                 from ./arch/x86/include/asm/irqflags.h:9,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from ./include/linux/binfmts.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:32:
./arch/x86/include/asm/msr-index.h:711: note: this is the location of the previous definition
  711 | #define MSR_TSX_FORCE_ABORT  0x0000010F
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm_x86.h:41,
                 from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:44,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:60:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86_basic_defs.h:78: warning: "CR3_PCID_MASK" redefined
   78 | #define CR3_PCID_MASK  0xFFF
      | 
In file included from ./arch/x86/include/asm/irqflags.h:5,
                 from ./include/linux/irqflags.h:16,
                 from ./include/linux/rcupdate.h:26,
                 from ./include/linux/rculist.h:11,
                 from ./include/linux/pid.h:5,
                 from ./include/linux/sched.h:14,
                 from ./include/linux/binfmts.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/hostif.c:32:
./arch/x86/include/asm/processor-flags.h:39: note: this is the location of the previous definition
   39 | #define CR3_PCID_MASK 0xFFFull
      | 
In file included from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm_x86.h:41,
                 from /tmp/modconfig-2NnvAk/vmmon-only/./include/vm_asm.h:44,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:49:
/tmp/modconfig-2NnvAk/vmmon-only/./include/x86_basic_defs.h:78: warning: "CR3_PCID_MASK" redefined
   78 | #define CR3_PCID_MASK  0xFFF
      | 
In file included from ./arch/x86/include/asm/processor.h:5,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/wait.h:9,
                 from ./include/linux/wait_bit.h:8,
                 from ./include/linux/fs.h:6,
                 from ./include/linux/highmem.h:5,
                 from /tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:25:
./arch/x86/include/asm/processor-flags.h:39: note: this is the location of the previous definition
   39 | #define CR3_PCID_MASK 0xFFFull
      | 
/tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:1536:5: warning: "VMX86_DEVEL" is not defined, evaluates to 0 [-Wundef]
 1536 | #if VMX86_DEVEL
      |     ^~~~~~~~~~~
At top level:
/tmp/modconfig-2NnvAk/vmmon-only/linux/driver.c:961:1: warning: always_inline function might not be inlinable [-Wattributes]
  961 | LinuxDriverSyncReadTSCs(uint64 *delta) // OUT: TSC max - TSC min
      | ^~~~~~~~~~~~~~~~~~~~~~~
  LD [M]  /tmp/modconfig-2NnvAk/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC [M]  /tmp/modconfig-2NnvAk/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/modconfig-2NnvAk/vmmon-only/vmmon.ko
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-24-generic'
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
  MODULEBUILDDIR= postbuild
make[1]: Entering directory '/tmp/modconfig-2NnvAk/vmmon-only'
make[1]: 'postbuild' is up to date.
make[1]: Leaving directory '/tmp/modconfig-2NnvAk/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory '/tmp/modconfig-2NnvAk/vmmon-only'
make: Entering directory '/tmp/modconfig-2NnvAk/vmnet-only'
Using kernel build system.
/usr/bin/make -C /lib/modules/5.4.0-24-generic/build/include/.. M=$PWD SRCROOT=$PWD/. \
  MODULEBUILDDIR= modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-24-generic'
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/driver.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/hub.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/userif.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/netif.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/bridge.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/procfs.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/smac_compat.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/smac.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/vnetEvent.o
  CC [M]  /tmp/modconfig-2NnvAk/vmnet-only/vnetUserListener.o
/tmp/modconfig-2NnvAk/vmnet-only/userif.c: In function &#8216;VNetCsumCopyDatagram&#8217;:
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:571:15: error: &#8216;skb_frag_t&#8217; {aka &#8216;const struct bio_vec&#8217;} has no member named &#8216;size&#8217;
  571 |       if (frag->size > 0) {
      |               ^~
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:575:29: error: &#8216;skb_frag_t&#8217; {aka &#8216;const struct bio_vec&#8217;} has no member named &#8216;page&#8217;; did you mean &#8216;bv_page&#8217;?
  575 |   vaddr = compat_kmap(frag->page);
      |                             ^~~~
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:84:36: note: in definition of macro &#8216;compat_kmap&#8217;
   84 | #   define compat_kmap(page) kmap((page).p)
      |                                    ^~~~
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:576:49: error: &#8216;skb_frag_t&#8217; {aka &#8216;const struct bio_vec&#8217;} has no member named &#8216;page_offset&#8217;; did you mean &#8216;bv_offset&#8217;?
  576 |   tmpCsum = csum_and_copy_to_user(vaddr + frag->page_offset,
      |                                                 ^~~~~~~~~~~
      |                                                 bv_offset
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:577:17: error: &#8216;skb_frag_t&#8217; {aka &#8216;const struct bio_vec&#8217;} has no member named &#8216;size&#8217;
  577 |       curr, frag->size, 0, &err);
      |                 ^~
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:578:23: error: &#8216;skb_frag_t&#8217; {aka &#8216;const struct bio_vec&#8217;} has no member named &#8216;page&#8217;; did you mean &#8216;bv_page&#8217;?
  578 |   compat_kunmap(frag->page);
      |                       ^~~~
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:85:40: note: in definition of macro &#8216;compat_kunmap&#8217;
   85 | #   define compat_kunmap(page) kunmap((page).p)
      |                                        ^~~~
/tmp/modconfig-2NnvAk/vmnet-only/userif.c:584:15: error: &#8216;skb_frag_t&#8217; {aka &#8216;const struct bio_vec&#8217;} has no member named &#8216;size&#8217;
  584 |   curr += frag->size;
      |               ^~
make[2]: *** [scripts/Makefile.build:273: /tmp/modconfig-2NnvAk/vmnet-only/userif.o] Error 1
make[2]: *** Waiting for unfinished jobs....
In file included from ./include/linux/pci.h:43,
                 from /tmp/modconfig-2NnvAk/vmnet-only/compat_netdevice.h:27,
                 from /tmp/modconfig-2NnvAk/vmnet-only/netif.c:44:
./include/linux/pci_ids.h:2285: warning: "PCI_VENDOR_ID_VMWARE" redefined
 2285 | #define PCI_VENDOR_ID_VMWARE  0x15ad
      | 
In file included from /tmp/modconfig-2NnvAk/vmnet-only/net.h:38,
                 from /tmp/modconfig-2NnvAk/vmnet-only/vnetInt.h:26,
                 from /tmp/modconfig-2NnvAk/vmnet-only/netif.c:43:
/tmp/modconfig-2NnvAk/vmnet-only/vm_device_version.h:56: note: this is the location of the previous definition
   56 | #define PCI_VENDOR_ID_VMWARE                    0x15AD
      | 
In file included from ./include/linux/pci.h:43,
                 from /tmp/modconfig-2NnvAk/vmnet-only/compat_netdevice.h:27,
                 from /tmp/modconfig-2NnvAk/vmnet-only/netif.c:44:
./include/linux/pci_ids.h:2286: warning: "PCI_DEVICE_ID_VMWARE_VMXNET3" redefined
 2286 | #define PCI_DEVICE_ID_VMWARE_VMXNET3 0x07b0
      | 
In file included from /tmp/modconfig-2NnvAk/vmnet-only/net.h:38,
                 from /tmp/modconfig-2NnvAk/vmnet-only/vnetInt.h:26,
                 from /tmp/modconfig-2NnvAk/vmnet-only/netif.c:43:
/tmp/modconfig-2NnvAk/vmnet-only/vm_device_version.h:74: note: this is the location of the previous definition
   74 | #define PCI_DEVICE_ID_VMWARE_VMXNET3            0x07B0
      | 
In file included from /tmp/modconfig-2NnvAk/vmnet-only/net.h:38,
                 from /tmp/modconfig-2NnvAk/vmnet-only/vnetInt.h:26,
                 from /tmp/modconfig-2NnvAk/vmnet-only/bridge.c:53:
/tmp/modconfig-2NnvAk/vmnet-only/vm_device_version.h:56: warning: "PCI_VENDOR_ID_VMWARE" redefined
   56 | #define PCI_VENDOR_ID_VMWARE                    0x15AD
      | 
In file included from ./include/linux/pci.h:43,
                 from /tmp/modconfig-2NnvAk/vmnet-only/compat_netdevice.h:27,
                 from /tmp/modconfig-2NnvAk/vmnet-only/bridge.c:52:
./include/linux/pci_ids.h:2285: note: this is the location of the previous definition
 2285 | #define PCI_VENDOR_ID_VMWARE  0x15ad
      | 
In file included from /tmp/modconfig-2NnvAk/vmnet-only/net.h:38,
                 from /tmp/modconfig-2NnvAk/vmnet-only/vnetInt.h:26,
                 from /tmp/modconfig-2NnvAk/vmnet-only/bridge.c:53:
/tmp/modconfig-2NnvAk/vmnet-only/vm_device_version.h:74: warning: "PCI_DEVICE_ID_VMWARE_VMXNET3" redefined
   74 | #define PCI_DEVICE_ID_VMWARE_VMXNET3            0x07B0
      | 
In file included from ./include/linux/pci.h:43,
                 from /tmp/modconfig-2NnvAk/vmnet-only/compat_netdevice.h:27,
                 from /tmp/modconfig-2NnvAk/vmnet-only/bridge.c:52:
./include/linux/pci_ids.h:2286: note: this is the location of the previous definition
 2286 | #define PCI_DEVICE_ID_VMWARE_VMXNET3 0x07b0
      | 
make[1]: *** [Makefile:1719: /tmp/modconfig-2NnvAk/vmnet-only] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-24-generic'
make: *** [Makefile:117: vmnet.ko] Error 2
make: Leaving directory '/tmp/modconfig-2NnvAk/vmnet-only'
Unable to install all modules.  See log for details.


```

---

