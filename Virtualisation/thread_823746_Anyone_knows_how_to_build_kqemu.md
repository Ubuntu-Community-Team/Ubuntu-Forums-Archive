---
title: "Anyone knows how to build kqemu?"
date: 2008-06-09
forum: Virtualisation
---

### Post by Methuselah on 2008-06-09
Well, it turns out qemu is the only vm I can get to work.
KVM and virt-manager fails to boot from hard disk to complete the test OS installation and virtualbox gets caught in a loop because it reboots before the installation is complete resulting in another attempt the next time. However, I was able to get a copy of windows 2000 I have installed on a qemu virtual machine.

I can't build kqemu though. I installed the source and the kinux headers are there. But I get many errors when I try to build. I did try to ./configure and all that but really I'm kind of clueless. My previous experience is with FreeBSD and its build system requires a lot less from you. 

My errors look like

```

:/usr/src/modules/kqemu$ make
make -C common all
make[1]: Entering directory `/usr/src/modules/kqemu/common'
gcc -Wall -O2 -Werror -g -D__KERNEL__ -I.. -o genoffsets genoffsets.c
genoffsets.c:19:20: error: stdlib.h: No such file or directory
genoffsets.c:20:19: error: stdio.h: No such file or directory
genoffsets.c:21:22: error: inttypes.h: No such file or directory
In file included from ../kqemu-kernel.h:8,
                 from kqemu_int.h:49,
                 from genoffsets.c:24:
../kqemu.h:30: error: expected specifier-qualifier-list before ‘uint32_t’
../kqemu.h:45: error: expected specifier-qualifier-list before ‘uint32_t’
../kqemu.h:103: error: expected specifier-qualifier-list before ‘uint8_t’
In file included from genoffsets.c:24:
kqemu_int.h:372: error: expected specifier-qualifier-list before ‘uint16_t’
kqemu_int.h:400: error: expected specifier-qualifier-list before ‘uint16_t’
kqemu_int.h:455: error: expected specifier-qualifier-list before ‘uint32_t’
kqemu_int.h:512: error: expected specifier-qualifier-list before ‘uint64_t’
kqemu_int.h:566: error: expected specifier-qualifier-list before ‘uint32_t’
kqemu_int.h:787: error: expected ‘)’ before ‘e1’
kqemu_int.h:796: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_seg_base’
kqemu_int.h:814: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
kqemu_int.h: In function ‘wrmsrl’:
kqemu_int.h:817: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:817: error: (Each undeclared identifier is reported only once
kqemu_int.h:817: error: for each function it appears in.)
kqemu_int.h: At top level:
kqemu_int.h:874: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getclock’
kqemu_int.h:919: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldub_slow’
kqemu_int.h:921: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lduw_slow’
kqemu_int.h:923: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldl_slow’
kqemu_int.h:925: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldq_slow’
kqemu_int.h:928: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h:930: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h:932: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h:934: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
kqemu_int.h:936: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldub_fast’
kqemu_int.h:953: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lduw_fast’
kqemu_int.h:970: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldl_fast’
kqemu_int.h:987: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldq_fast’
kqemu_int.h:1005: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h: In function ‘stb_fast’:
kqemu_int.h:1010: error: ‘struct kqemu_state’ has no member named ‘soft_tlb’
kqemu_int.h:1012: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1012: error: too many arguments to function ‘stb_slow’
kqemu_int.h:1015: error: ‘uint8_t’ undeclared (first use in this function)
kqemu_int.h:1015: error: expected expression before ‘)’ token
kqemu_int.h: At top level:
kqemu_int.h:1020: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h: In function ‘stw_fast’:
kqemu_int.h:1025: error: ‘struct kqemu_state’ has no member named ‘soft_tlb’
kqemu_int.h:1027: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1027: error: too many arguments to function ‘stw_slow’
kqemu_int.h:1030: error: ‘uint16_t’ undeclared (first use in this function)
kqemu_int.h:1030: error: expected expression before ‘)’ token
kqemu_int.h: At top level:
kqemu_int.h:1035: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h: In function ‘stl_fast’:
kqemu_int.h:1040: error: ‘struct kqemu_state’ has no member named ‘soft_tlb’
kqemu_int.h:1042: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1042: error: too many arguments to function ‘stl_slow’
kqemu_int.h:1045: error: ‘uint32_t’ undeclared (first use in this function)
kqemu_int.h:1045: error: expected expression before ‘)’ token
kqemu_int.h: At top level:
kqemu_int.h:1050: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
kqemu_int.h: In function ‘stq_fast’:
kqemu_int.h:1055: error: ‘struct kqemu_state’ has no member named ‘soft_tlb’
kqemu_int.h:1057: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1057: error: too many arguments to function ‘stq_slow’
kqemu_int.h:1060: error: ‘uint64_t’ undeclared (first use in this function)
kqemu_int.h:1060: error: expected expression before ‘)’ token
kqemu_int.h: At top level:
kqemu_int.h:1078: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldub_mem’
kqemu_int.h:1091: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lduw_mem’
kqemu_int.h:1105: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldl_mem’
kqemu_int.h:1135: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldub_mem_fast’
kqemu_int.h:1146: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lduw_mem_fast’
kqemu_int.h:1157: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ldl_mem_fast’
kqemu_int.h:1168: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h: In function ‘stb_mem’:
kqemu_int.h:1176: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1176: error: ‘uint8_t’ undeclared (first use in this function)
kqemu_int.h:1176: error: expected expression before ‘)’ token
kqemu_int.h: At top level:
kqemu_int.h:1179: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h: In function ‘stw_mem’:
kqemu_int.h:1188: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1188: error: ‘uint8_t’ undeclared (first use in this function)
kqemu_int.h:1188: error: expected expression before ‘)’ token
kqemu_int.h: At top level:
kqemu_int.h:1191: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
kqemu_int.h: In function ‘stl_mem’:
kqemu_int.h:1200: error: ‘val’ undeclared (first use in this function)
kqemu_int.h:1200: error: ‘uint32_t’ undeclared (first use in this function)
kqemu_int.h:1200: error: expected expression before ‘)’ token
kqemu_int.h: In function ‘set_cpu_seg_cache’:
kqemu_int.h:1268: error: ‘uint32_t’ undeclared (first use in this function)
kqemu_int.h:1268: error: expected ‘;’ before ‘sel’
kqemu_int.h:1269: error: ‘uint8_t’ undeclared (first use in this function)
kqemu_int.h:1269: error: ‘ptr’ undeclared (first use in this function)
kqemu_int.h:1273: error: ‘struct kqemu_state’ has no member named ‘regs1’
kqemu_int.h:1274: error: ‘struct kqemu_state’ has no member named ‘regs1’
kqemu_int.h:1276: error: ‘sel’ undeclared (first use in this function)
kqemu_int.h:1277: error: expected expression before ‘)’ token
kqemu_int.h:1278: error: expected expression before ‘)’ token
kqemu_int.h:1278: error: ‘struct kqemu_state’ has no member named ‘seg_desc_cache’
kqemu_int.h:1279: error: expected expression before ‘)’ token
kqemu_int.h:1279: error: ‘struct kqemu_state’ has no member named ‘seg_desc_cache’
kqemu_int.h:1289: error: ‘uint64_t’ undeclared (first use in this function)
kqemu_int.h:1289: error: expected expression before ‘)’ token
cc1: warnings being treated as errors
genoffsets.c: In function ‘main’:
genoffsets.c:36: warning: implicit declaration of function ‘printf’
genoffsets.c:36: warning: incompatible implicit declaration of built-in function ‘printf’
genoffsets.c:36: error: ‘struct kqemu_state’ has no member named ‘monitor_idt’
genoffsets.c:37: error: ‘struct kqemu_state’ has no member named ‘monitor_gdt’
genoffsets.c:38: error: ‘struct kqemu_state’ has no member named ‘monitor_tr_sel’
genoffsets.c:39: error: ‘struct kqemu_state’ has no member named ‘monitor_ldt_sel’
genoffsets.c:40: error: ‘struct kqemu_state’ has no member named ‘monitor_ds_sel’
genoffsets.c:41: error: ‘struct kqemu_state’ has no member named ‘monitor_ss16_sel’
genoffsets.c:42: error: ‘struct kqemu_state’ has no member named ‘monitor_cs_sel’
genoffsets.c:46: error: ‘struct kqemu_state’ has no member named ‘monitor_selector_base’
genoffsets.c:47: error: ‘struct kqemu_state’ has no member named ‘monitor_jmp’
genoffsets.c:48: error: ‘struct kqemu_state’ has no member named ‘monitor_cr3’
genoffsets.c:49: error: ‘struct kqemu_state’ has no member named ‘monitor_dr7’
genoffsets.c:50: error: ‘struct kqemu_state’ has no member named ‘monitor_esp’
genoffsets.c:52: error: ‘struct kqemu_state’ has no member named ‘kernel_idt’
genoffsets.c:53: error: ‘struct kqemu_state’ has no member named ‘kernel_gdt’
genoffsets.c:54: error: ‘struct kqemu_state’ has no member named ‘kernel_tr_sel’
genoffsets.c:55: error: ‘struct kqemu_state’ has no member named ‘kernel_ldt_sel’
genoffsets.c:56: error: ‘struct kqemu_state’ has no member named ‘kernel_esp’
genoffsets.c:57: error: ‘struct kqemu_state’ has no member named ‘kernel_ss_sel’
genoffsets.c:58: error: ‘struct kqemu_state’ has no member named ‘kernel_jmp’
genoffsets.c:59: error: ‘struct kqemu_state’ has no member named ‘kernel_cs_sel’
genoffsets.c:60: error: ‘struct kqemu_state’ has no member named ‘kernel_cr0’
genoffsets.c:61: error: ‘struct kqemu_state’ has no member named ‘kernel_cr3’
genoffsets.c:62: error: ‘struct kqemu_state’ has no member named ‘kernel_cr4’
genoffsets.c:63: error: ‘struct kqemu_state’ has no member named ‘kernel_esp’
genoffsets.c:65: error: ‘struct kqemu_state’ has no member named ‘nexus_orig_pte’
genoffsets.c:66: error: ‘struct kqemu_state’ has no member named ‘nexus_pte’
genoffsets.c:67: error: ‘struct kqemu_state’ has no member named ‘nexus_kaddr’
genoffsets.c:68: error: ‘struct kqemu_state’ has no member named ‘nexus_kaddr_vptep’
genoffsets.c:73: error: ‘struct kqemu_state’ has no member named ‘use_pae’
genoffsets.c:75: error: ‘struct kqemu_state’ has no member named ‘dt_table’
genoffsets.c:77: error: ‘struct kqemu_state’ has no member named ‘seg_desc_cache’
genoffsets.c:79: error: ‘struct kqemu_state’ has no member named ‘tr_desc_cache’
genoffsets.c:80: error: ‘struct kqemu_state’ has no member named ‘cpuid_features’
genoffsets.c:82: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:83: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:84: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:85: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:86: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:87: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:88: error: ‘struct kqemu_state’ has no member named ‘cpu_state’
genoffsets.c:90: error: ‘struct kqemu_state’ has no member named ‘stack’
make[1]: *** [genoffsets] Error 1
make[1]: Leaving directory `/usr/src/modules/kqemu/common'
make: *** [kqemu.ko] Error 2

```

Any help would be appreciated.

---

### Post by stmiller on 2008-07-27
```

genoffsets.c:19:20: error: stdlib.h: No such file or directory

```

Weird looks like it is missing some files. I would scratch that kqemu directory and extract from the tar ball and start again.

---

