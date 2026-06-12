---
title: "Touchpad stopped workng after dist-upgrade"
date: 2013-06-29
forum: Ubuntu Development Version
---

### Post by Chanath on 2013-06-29
After dist-upgrade, the touchpad stopped workng in my laptop. The cursor is stationary in the middle, neither the red button mouse in the keyboard or the touchpad are responding at all, but the external mouse works. I even reinstalled Synaptics, but to no avail. Could it be a hardware problem of a software problem?

---

### Post by jfernyhough on 2013-06-30
What sort of laptop do you have (make, model)? Which kernel are you running (e.g. run $ uname -a )? Do you have any PPAs enabled?

I just noticed that the touchpad on my Dell 1749 is also not responding, but the X61 is fine.

---

### Post by Chanath on 2013-06-30
After another dist-upgrade, the touchpad came back. Well, as we are using Ubuntu+1, anything can happen. :)

---

### Post by EricKit on 2013-07-06
Hello, glad to see this post.  I also have issues with my touch pad mouse.  I have a Lenovo Twist.  Here are my symptoms:

When it boots up the mouse is frozen in the middle of the screen for 1-2 seconds then goes away
A reboot will sometimes fix it.  It seems to be that 25% of boot-ups the touchpad doesn't work
Logging-out never fixes it, but it does redisplay the mouse in the center of the screen for 1-2 seconds
As you said, external mice (is that the plural?) still work
The touch screen works (though it degrades over time, eventually it'll stop clicking but still hovers when I tap the screen like it will do if you hover the mouse over something)
When the mouse is working on boot, it keeps working the entire time, even if I use the touchscreen or anything else.

Running another dist-upgrade will let you know if the problem goes away!
Edit: It did not, still doesn't work on some boot ups.

---

### Post by cariboo on 2013-07-07
Dmesg, should indicate if the touchpad is detected properly, can you post the output of dmesg, when the mosue pointer seems to be stuck? To do so, switch to a console, using Ctrl-Alt-F2, the run the following commend:

```
dmeg > dmesg.txt
```

then attach the resulting dmesg.txt file to you next post.

---

### Post by EricKit on 2013-07-08
It appears that it works after a restart but not after a shutdown and boot-up... but I haven't tried it multiple times to verify.  Anyways I made two .txt files and named them working and broken in reference to the touchpad.  Well turns out they are took big to upload.  Here is the one where it is broken.  I can uplaod what it looks like working also if you need.  Sorry for such a long list, wish the upload would alow 60kB.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.10.0-2-generic (buildd@panlong) (gcc version 4.8.1 (Ubuntu 4.8.1-5ubuntu1) ) #10-Ubuntu SMP Fri Jul 5 18:03:52 UTC 2013 (Ubuntu 3.10.0-2.10-generic 3.10.0)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.10.0-2-generic.efi.signed root=UUID=4ed0903a-c5d2-4b4d-b66c-3970006a769a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c000-0x000000000009cfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000c7f6cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c7f6d000-0x00000000c816efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c816f000-0x00000000d6813fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d6814000-0x00000000dae9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dae9f000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db000000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f80f8000-0x00000000f80f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011e5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by Lenovo
[    0.000000] efi:  ACPI=0xdaffe000  ACPI 2.0=0xdaffe014  SMBIOS=0xdac0f000 
[    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x0000000000087000) (0MB)
[    0.000000] efi: mem01: type=4, attr=0xf, range=[0x0000000000087000-0x0000000000088000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000088000-0x000000000009c000) (0MB)
[    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000009c000-0x000000000009d000) (0MB)
[    0.000000] efi: mem04: type=4, attr=0xf, range=[0x000000000009d000-0x000000000009e000) (0MB)
[    0.000000] efi: mem05: type=0, attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014e9000) (19MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x00000000014e9000-0x0000000002000000) (11MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033e9000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x00000000033e9000-0x0000000020000000) (460MB)
[    0.000000] efi: mem10: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000020200000-0x0000000035fdc000) (349MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000035fdc000-0x0000000036fe6000) (16MB)
[    0.000000] efi: mem13: type=7, attr=0xf, range=[0x0000000036fe6000-0x0000000040004000) (144MB)
[    0.000000] efi: mem14: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem15: type=7, attr=0xf, range=[0x0000000040005000-0x00000000910a9000) (1296MB)
[    0.000000] efi: mem16: type=2, attr=0xf, range=[0x00000000910a9000-0x00000000c5932000) (840MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x00000000c5932000-0x00000000c5952000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x00000000c5952000-0x00000000c7d9d000) (36MB)
[    0.000000] efi: mem19: type=2, attr=0xf, range=[0x00000000c7d9d000-0x00000000c7f57000) (1MB)
[    0.000000] efi: mem20: type=4, attr=0xf, range=[0x00000000c7f57000-0x00000000c7f6d000) (0MB)
[    0.000000] efi: mem21: type=0, attr=0xf, range=[0x00000000c7f6d000-0x00000000c816f000) (2MB)
[    0.000000] efi: mem22: type=4, attr=0xf, range=[0x00000000c816f000-0x00000000c8922000) (7MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x00000000c8922000-0x00000000c892f000) (0MB)
[    0.000000] efi: mem24: type=2, attr=0xf, range=[0x00000000c892f000-0x00000000c8931000) (0MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x00000000c8931000-0x00000000c89fd000) (0MB)
[    0.000000] efi: mem26: type=1, attr=0xf, range=[0x00000000c89fd000-0x00000000c8b31000) (1MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x00000000c8b31000-0x00000000ca8cf000) (29MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x00000000ca8cf000-0x00000000caa1b000) (1MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x00000000caa1b000-0x00000000cab3e000) (1MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x00000000cab3e000-0x00000000cc3e3000) (24MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x00000000cc3e3000-0x00000000cc3f5000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x00000000cc3f5000-0x00000000cdc14000) (24MB)
[    0.000000] efi: mem33: type=7, attr=0xf, range=[0x00000000cdc14000-0x00000000d640d000) (135MB)
[    0.000000] efi: mem34: type=2, attr=0xf, range=[0x00000000d640d000-0x00000000d6417000) (0MB)
[    0.000000] efi: mem35: type=3, attr=0xf, range=[0x00000000d6417000-0x00000000d6814000) (3MB)
[    0.000000] efi: mem36: type=5, attr=0x800000000000000f, range=[0x00000000d6814000-0x00000000d68e6000) (0MB)
[    0.000000] efi: mem37: type=5, attr=0x800000000000000f, range=[0x00000000d68e6000-0x00000000d6a14000) (1MB)
[    0.000000] efi: mem38: type=6, attr=0x800000000000000f, range=[0x00000000d6a14000-0x00000000d7622000) (12MB)
[    0.000000] efi: mem39: type=6, attr=0x800000000000000f, range=[0x00000000d7622000-0x00000000da65a000) (48MB)
[    0.000000] efi: mem40: type=0, attr=0xf, range=[0x00000000da65a000-0x00000000dac0e000) (5MB)
[    0.000000] efi: mem41: type=0, attr=0xf, range=[0x00000000dac0e000-0x00000000dae9f000) (2MB)
[    0.000000] efi: mem42: type=10, attr=0xf, range=[0x00000000dae9f000-0x00000000daef4000) (0MB)
[    0.000000] efi: mem43: type=10, attr=0xf, range=[0x00000000daef4000-0x00000000daf9f000) (0MB)
[    0.000000] efi: mem44: type=9, attr=0xf, range=[0x00000000daf9f000-0x00000000dafe0000) (0MB)
[    0.000000] efi: mem45: type=9, attr=0xf, range=[0x00000000dafe0000-0x00000000dafff000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x00000000dafff000-0x00000000db000000) (0MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x0000000100000000-0x000000011e600000) (486MB)
[    0.000000] efi: mem48: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem49: type=0, attr=0x0, range=[0x00000000db000000-0x00000000dfa00000) (74MB)
[    0.000000] efi: mem50: type=11, attr=0x8000000000000001, range=[0x00000000f80f8000-0x00000000f80f9000) (0MB)
[    0.000000] efi: mem51: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO 33474HU/33474HU, BIOS GDET95WW (1.55 ) 05/14/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x11e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FE0000000 write-back
[    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
[    0.000000]   6 base 100000000 mask FE0000000 write-back
[    0.000000]   7 base 11F000000 mask FFF000000 uncachable
[    0.000000]   8 base 11E800000 mask FFF800000 uncachable
[    0.000000]   9 base 11E600000 mask FFFE00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fc8000, 0x02fc8fff] PGTABLE
[    0.000000] BRK [0x02fc9000, 0x02fc9fff] PGTABLE
[    0.000000] BRK [0x02fca000, 0x02fcafff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11e400000-0x11e5fffff]
[    0.000000]  [mem 0x11e400000-0x11e5fffff] page 2M
[    0.000000] BRK [0x02fcb000, 0x02fcbfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11c000000-0x11e3fffff]
[    0.000000]  [mem 0x11c000000-0x11e3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
[    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x02fcc000, 0x02fccfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xc7f6cfff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xc7dfffff] page 2M
[    0.000000]  [mem 0xc7e00000-0xc7f6cfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc816f000-0xd6813fff]
[    0.000000]  [mem 0xc816f000-0xc81fffff] page 4k
[    0.000000]  [mem 0xc8200000-0xd67fffff] page 2M
[    0.000000]  [mem 0xd6800000-0xd6813fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdafff000-0xdaffffff]
[    0.000000]  [mem 0xdafff000-0xdaffffff] page 4k
[    0.000000] RAMDISK: [mem 0x35fdc000-0x36fe5fff]
[    0.000000] ACPI: RSDP 00000000daffe014 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000daffe170 000AC (v01 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: FACP 00000000dafec000 0010C (v05 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000dafee000 0C7F4 (v02 LENOVO TP-GD    00001550 INTL 20061109)
[    0.000000] ACPI: FACS 00000000daf59000 00040
[    0.000000] ACPI: TCPA 00000000daffd000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT 00000000daffc000 00651 (v02 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000daffb000 006A5 (v02 LENOVO PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000dafed000 000A5 (v32 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: HPET 00000000dafea000 00038 (v01 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: APIC 00000000dafe9000 00098 (v03 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000dafe8000 0003C (v01 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: FPDT 00000000dafe7000 00064 (v01 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: SSDT 00000000dafe6000 008A2 (v02  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000dafe5000 00B22 (v02  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000dafe4000 0003E (v01 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000dafe3000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: MSDM 00000000daf54000 00055 (v03 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000dafe2000 002BA (v01 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: DBG2 00000000dafe1000 000A5 (v00 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: BGRT 00000000dafe0000 00038 (v00 LENOVO TP-GD    00001550 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011e5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11e5fffff]
[    0.000000]   NODE_DATA [mem 0x11e5f4000-0x11e5f8fff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff880119c00000-ffff88011dbfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11e5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009bfff]
[    0.000000]   node   0: [mem 0x0009d000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xc7f6cfff]
[    0.000000]   node   0: [mem 0xc816f000-0xd6813fff]
[    0.000000]   node   0: [mem 0xdafff000-0xdaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x11e5fffff]
[    0.000000] On node 0 totalpages: 1001902
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 24 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13649 pages used for memmap
[    0.000000]   DMA32 zone: 873490 pages, LIFO batch:31
[    0.000000]   Normal zone: 1944 pages used for memmap
[    0.000000]   Normal zone: 124416 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000c7f6d000 - 00000000c816f000
[    0.000000] PM: Registered nosave memory: 00000000d6814000 - 00000000dae9f000
[    0.000000] PM: Registered nosave memory: 00000000dae9f000 - 00000000daf9f000
[    0.000000] PM: Registered nosave memory: 00000000daf9f000 - 00000000dafff000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f80f8000
[    0.000000] PM: Registered nosave memory: 00000000f80f8000 - 00000000f80f9000
[    0.000000] PM: Registered nosave memory: 00000000f80f9000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 0000000100000000
[    0.000000] e820: [mem 0xdfa00000-0xf80f7fff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88011e200000 s86400 r8192 d24192 u262144
[    0.000000] pcpu-alloc: s86400 r8192 d24192 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 986221
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.10.0-2-generic.efi.signed root=UUID=4ed0903a-c5d2-4b4d-b66c-3970006a769a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3778640k/4691968k available (7044k kernel code, 684360k absent, 228968k reserved, 6253k data, 1340k init)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Experimental no-CBs for all CPUs
[    0.000000]     Experimental no-CBs CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1696.008 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3392.01 BogoMIPS (lpj=6784032)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000023] init_memory_mapping: [mem 0xd6814000-0xd6a13fff]
[    0.000025]  [mem 0xd6814000-0xd6a13fff] page 4k
[    0.000052] init_memory_mapping: [mem 0xd6a14000-0xda659fff]
[    0.000053]  [mem 0xd6a14000-0xd6bfffff] page 4k
[    0.000055]  [mem 0xd6c00000-0xda5fffff] page 2M
[    0.000056]  [mem 0xda600000-0xda659fff] page 4k
[    0.032184] Security Framework initialized
[    0.032198] AppArmor: AppArmor initialized
[    0.032199] Yama: becoming mindful.
[    0.032575] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.034093] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.034781] Mount-cache hash table entries: 256
[    0.035012] Initializing cgroup subsys memory
[    0.035024] Initializing cgroup subsys devices
[    0.035026] Initializing cgroup subsys freezer
[    0.035028] Initializing cgroup subsys blkio
[    0.035030] Initializing cgroup subsys perf_event
[    0.035033] Initializing cgroup subsys hugetlb
[    0.035065] CPU: Physical Processor ID: 0
[    0.035067] CPU: Processor Core ID: 0
[    0.035073] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.035073] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.035650] mce: CPU supports 7 MCE banks
[    0.035666] CPU0: Thermal monitoring enabled (TM1)
[    0.035679] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.035679] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.035679] tlb_flushall_shift: 1
[    0.035847] Freeing SMP alternatives: 28k freed
[    0.038894] ACPI: Core revision 20130328
[    0.050216] ACPI: All ACPI Tables successfully acquired
[    0.057599] ftrace: allocating 27433 entries in 108 pages
[    0.077155] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.116857] smpboot: CPU0: Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz (fam: 06, model: 3a, stepping: 09)
[    0.116867] TSC deadline timer enabled
[    0.116881] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    0.116890] ... version:                3
[    0.116891] ... bit width:              48
[    0.116892] ... generic registers:      4
[    0.116894] ... value mask:             0000ffffffffffff
[    0.116895] ... max period:             000000007fffffff
[    0.116896] ... fixed-purpose events:   3
[    0.116898] ... event mask:             000000070000000f
[    0.132502] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.118584] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.160252] Brought up 4 CPUs
[    0.160256] smpboot: Total of 4 processors activated (13568.06 BogoMIPS)
[    0.164858] devtmpfs: initialized
[    0.165927] EVM: security.selinux
[    0.165929] EVM: security.SMACK64
[    0.165931] EVM: security.capability
[    0.165996] PM: Registering ACPI NVS region [mem 0xdae9f000-0xdaf9efff] (1048576 bytes)
[    0.167192] regulator-dummy: no parameters
[    0.167248] NET: Registered protocol family 16
[    0.167413] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.167416] ACPI: bus type PCI registered
[    0.167418] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.167615] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.167618] PCI: not using MMCONFIG
[    0.167620] PCI: Using configuration type 1 for base access
[    0.168710] bio: create slab <bio-0> at 0
[    0.168891] ACPI: Added _OSI(Module Device)
[    0.168893] ACPI: Added _OSI(Processor Device)
[    0.168895] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.168897] ACPI: Added _OSI(Processor Aggregator Device)
[    0.171292] ACPI: EC: Look up EC in DSDT
[    0.173707] ACPI: Executed 1 blocks of module-level executable AML code
[    0.177759] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.207649] ACPI: SSDT 00000000dae3a018 0083B (v02  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.208267] ACPI: Dynamic OEM Table Load:
[    0.208270] ACPI: SSDT           (null) 0083B (v02  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.214926] ACPI: SSDT 00000000dae3ba98 00303 (v02  PmRef    ApIst 00003000 INTL 20061109)
[    0.215584] ACPI: Dynamic OEM Table Load:
[    0.215587] ACPI: SSDT           (null) 00303 (v02  PmRef    ApIst 00003000 INTL 20061109)
[    0.220790] ACPI: SSDT 00000000dae39d98 00119 (v02  PmRef    ApCst 00003000 INTL 20061109)
[    0.221398] ACPI: Dynamic OEM Table Load:
[    0.221401] ACPI: SSDT           (null) 00119 (v02  PmRef    ApCst 00003000 INTL 20061109)
[    1.045652] ACPI: Interpreter enabled
[    1.045664] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130328/hwxface-568)
[    1.045672] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130328/hwxface-568)
[    1.045693] ACPI: (supports S0 S3 S4 S5)
[    1.045696] ACPI: Using IOAPIC for interrupt routing
[    1.045725] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    1.046298] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    1.056436] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.056600] ACPI: No dock devices found.
[    1.074041] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.074194] \_SB_.PCI0:_OSC invalid UUID
[    1.074195] _OSC request data:1 8 0 
[    1.074643] PCI host bridge to bus 0000:00
[    1.074648] pci_bus 0000:00: root bus resource [bus 00-3e]
[    1.074650] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.074653] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.074655] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.074657] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.074660] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.074662] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.074664] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    1.074666] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.074668] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.074671] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.074673] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.074675] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.074677] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.074679] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    1.074682] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    1.074684] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    1.074686] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    1.074697] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.074808] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    1.074824] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    1.074833] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.074840] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    1.074954] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    1.074987] pci 0000:00:14.0: reg 10: [mem 0xf2700000-0xf270ffff 64bit]
[    1.075090] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.075446] pci 0000:00:14.0: System wakeup disabled by ACPI
[    1.075491] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.075525] pci 0000:00:16.0: reg 10: [mem 0xf2715000-0xf271500f 64bit]
[    1.075626] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.075734] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.075763] pci 0000:00:1a.0: reg 10: [mem 0xf271a000-0xf271a3ff]
[    1.075880] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.076211] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    1.076253] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.076279] pci 0000:00:1b.0: reg 10: [mem 0xf2710000-0xf2713fff 64bit]
[    1.076381] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.076423] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    1.076464] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.076575] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.076621] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    1.076659] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    1.076769] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.076812] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    1.076852] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    1.076961] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.077006] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    1.077056] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.077085] pci 0000:00:1d.0: reg 10: [mem 0xf2719000-0xf27193ff]
[    1.077211] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.077553] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    1.077599] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    1.077798] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.077827] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    1.077839] pci 0000:00:1f.2: reg 14: [io  0x409c-0x409f]
[    1.077853] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    1.077865] pci 0000:00:1f.2: reg 1c: [io  0x4098-0x409b]
[    1.077878] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    1.077890] pci 0000:00:1f.2: reg 24: [mem 0xf2718000-0xf27187ff]
[    1.077953] pci 0000:00:1f.2: PME# supported from D3hot
[    1.078034] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    1.078059] pci 0000:00:1f.3: reg 10: [mem 0xf2714000-0xf27140ff 64bit]
[    1.078093] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    1.078362] pci 0000:02:00.0: [10ec:5229] type 00 class 0xff0000
[    1.078424] pci 0000:02:00.0: reg 10: [mem 0xf2600000-0xf2600fff]
[    1.078925] pci 0000:02:00.0: supports D1 D2
[    1.078927] pci 0000:02:00.0: PME# supported from D1 D2 D3hot
[    1.079016] pci 0000:02:00.0: System wakeup disabled by ACPI
[    1.089684] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.089694] pci 0000:00:1c.0:   bridge window [mem 0xf2600000-0xf26fffff]
[    1.089849] pci 0000:03:00.0: [14e4:4359] type 00 class 0x028000
[    1.089886] pci 0000:03:00.0: reg 10: [mem 0xf1d00000-0xf1d03fff 64bit]
[    1.090088] pci 0000:03:00.0: supports D1 D2
[    1.090090] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.090141] pci 0000:03:00.0: System wakeup disabled by ACPI
[    1.101670] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    1.101676] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.101682] pci 0000:00:1c.1:   bridge window [mem 0xf1d00000-0xf25fffff]
[    1.101690] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    1.101862] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    1.101937] pci 0000:04:00.0: reg 10: [io  0x2000-0x20ff]
[    1.102067] pci 0000:04:00.0: reg 18: [mem 0xf0c04000-0xf0c04fff 64bit pref]
[    1.102148] pci 0000:04:00.0: reg 20: [mem 0xf0c00000-0xf0c03fff 64bit pref]
[    1.102505] pci 0000:04:00.0: supports D1 D2
[    1.102507] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.102939] pci 0000:04:00.0: System wakeup disabled by ACPI
[    1.113692] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.113698] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    1.113703] pci 0000:00:1c.3:   bridge window [mem 0xf1500000-0xf1cfffff]
[    1.113711] pci 0000:00:1c.3:   bridge window [mem 0xf0c00000-0xf14fffff 64bit pref]
[    1.113816] \_SB_.PCI0:_OSC invalid UUID
[    1.113818] _OSC request data:1 1f 0 
[    1.113823] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    1.113825] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    1.114680] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.114750] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.114818] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.114884] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.114954] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.115021] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.115087] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.115153] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.115536] ACPI: Enabled 6 GPEs in block 00 to 3F
[    1.115545] acpi root: \_SB_.PCI0 notify handler is installed
[    1.115625] Found 1 acpi root devices
[    1.115697] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.115863] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.115868] vgaarb: loaded
[    1.115869] vgaarb: bridge control possible 0000:00:02.0
[    1.116062] SCSI subsystem initialized
[    1.116064] ACPI: bus type ATA registered
[    1.116114] libata version 3.00 loaded.
[    1.116131] ACPI: bus type USB registered
[    1.116154] usbcore: registered new interface driver usbfs
[    1.116164] usbcore: registered new interface driver hub
[    1.116194] usbcore: registered new device driver usb
[    1.116327] PCI: Using ACPI for IRQ routing
[    1.118168] PCI: pci_cache_line_size set to 64 bytes
[    1.118317] e820: reserve RAM buffer [mem 0x0009c000-0x0009ffff]
[    1.118319] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    1.118321] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.118323] e820: reserve RAM buffer [mem 0xc7f6d000-0xc7ffffff]
[    1.118325] e820: reserve RAM buffer [mem 0xd6814000-0xd7ffffff]
[    1.118326] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    1.118328] e820: reserve RAM buffer [mem 0x11e600000-0x11fffffff]
[    1.118422] NetLabel: Initializing
[    1.118424] NetLabel:  domain hash size = 128
[    1.118425] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.118436] NetLabel:  unlabeled traffic allowed by default
[    1.118498] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.118505] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.120518] Switching to clocksource hpet
[    1.126298] AppArmor: AppArmor Filesystem Enabled
[    1.126324] pnp: PnP ACPI init
[    1.126338] ACPI: bus type PNP registered
[    1.126380] pnp 00:00: [dma 4]
[    1.126404] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.126427] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    1.126568] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.126602] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.126653] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.126656] system 00:04: [io  0x1000-0x100f] has been reserved
[    1.126659] system 00:04: [io  0xffff] has been reserved
[    1.126661] system 00:04: [io  0xffff] has been reserved
[    1.126666] system 00:04: [io  0x0400-0x0453] has been reserved
[    1.126668] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.126671] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.126673] system 00:04: [io  0x164e-0x164f] has been reserved
[    1.126676] system 00:04: [io  0x06fc-0x06ff] has been reserved
[    1.126678] system 00:04: [io  0x0700-0x0703] has been reserved
[    1.126682] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.126709] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.126764] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.126767] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.126789] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.127099] pnp 00:08: Plug and Play ACPI device, IDs PTL0001 PNP0303 (active)
[    1.127160] pnp 00:09: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    1.127208] pnp 00:0a: Plug and Play ACPI device, IDs LEN0031 PNP0f13 (active)
[    1.127354] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.127357] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.127360] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.127362] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.127366] system 00:0b: [mem 0xf8000000-0xfbffffff] could not be reserved
[    1.127368] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.127371] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.127373] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.127376] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    1.127379] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.127381] system 00:0b: [mem 0xfffff000-0xffffffff] has been reserved
[    1.127385] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.127619] pnp: PnP ACPI: found 12 devices
[    1.127621] ACPI: bus type PNP unregistered
[    1.134224] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.134234] pci 0000:00:1c.0:   bridge window [mem 0xf2600000-0xf26fffff]
[    1.134249] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    1.134254] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.134261] pci 0000:00:1c.1:   bridge window [mem 0xf1d00000-0xf25fffff]
[    1.134267] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    1.134275] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.134279] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    1.134288] pci 0000:00:1c.3:   bridge window [mem 0xf1500000-0xf1cfffff]
[    1.134294] pci 0000:00:1c.3:   bridge window [mem 0xf0c00000-0xf14fffff 64bit pref]
[    1.134584] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.134586] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.134589] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.134591] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.134594] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.134596] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.134598] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    1.134600] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.134603] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.134605] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.134607] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    1.134610] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    1.134612] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    1.134614] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    1.134617] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    1.134619] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    1.134621] pci_bus 0000:00: resource 20 [mem 0xdfa00000-0xfeafffff]
[    1.134624] pci_bus 0000:02: resource 1 [mem 0xf2600000-0xf26fffff]
[    1.134627] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    1.134629] pci_bus 0000:03: resource 1 [mem 0xf1d00000-0xf25fffff]
[    1.134631] pci_bus 0000:03: resource 2 [mem 0xf0400000-0xf0bfffff 64bit pref]
[    1.134634] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    1.134636] pci_bus 0000:04: resource 1 [mem 0xf1500000-0xf1cfffff]
[    1.134639] pci_bus 0000:04: resource 2 [mem 0xf0c00000-0xf14fffff 64bit pref]
[    1.134675] NET: Registered protocol family 2
[    1.134890] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    1.135036] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.135138] TCP: Hash tables configured (established 32768 bind 32768)
[    1.135159] TCP: reno registered
[    1.135169] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.135190] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.135264] NET: Registered protocol family 1
[    1.135278] pci 0000:00:02.0: Boot video device
[    1.135949] PCI: CLS 64 bytes, default 64
[    1.136014] Trying to unpack rootfs image as initramfs...
[    1.508388] Freeing initrd memory: 16424k freed
[    1.511042] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.511048] software IO TLB [mem 0xd2417000-0xd6417000] (64MB) mapped at [ffff8800d2417000-ffff8800d6416fff]
[    1.511299] Scanning for low memory corruption every 60 seconds
[    1.511535] Initialise module verification
[    1.511587] audit: initializing netlink socket (disabled)
[    1.511598] type=2000 audit(1373302497.468:1): initialized
[    1.550257] bounce pool size: 64 pages
[    1.550269] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.551745] VFS: Disk quotas dquot_6.5.2
[    1.551794] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.552328] fuse init (API version 7.22)
[    1.552410] msgmni has been set to 7536
[    1.552977] Key type asymmetric registered
[    1.552980] Asymmetric key parser 'x509' registered
[    1.553015] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.553061] io scheduler noop registered
[    1.553063] io scheduler deadline registered (default)
[    1.553091] io scheduler cfq registered
[    1.553343] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.553358] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.553421] efifb: probing for efifb
[    1.554168] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90004800000, using 4160k, total 4160k
[    1.554170] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    1.554172] efifb: scrolling: redraw
[    1.554174] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.557943] Console: switching to colour frame buffer device 170x48
[    1.561500] fb0: EFI VGA frame buffer device
[    1.561507] intel_idle: MWAIT substates: 0x21120
[    1.561508] intel_idle: v0.4 model 0x3A
[    1.561510] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.562208] ACPI: AC Adapter [AC] (on-line)
[    1.562340] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.562345] ACPI: Power Button [PWRB]
[    1.562420] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.061298] ACPI: Lid Switch [LID0]
[    2.061347] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.061351] ACPI: Power Button [PWRF]
[    2.061468] ACPI: Requesting acpi_cpufreq
[    2.064826] thermal LNXTHERM:00: registered as thermal_zone0
[    2.064829] ACPI: Thermal Zone [TZ01] (30 C)
[    2.064862] GHES: HEST is not enabled!
[    2.064961] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.066787] Linux agpgart interface v0.103
[    2.068275] brd: module loaded
[    2.069072] loop: module loaded
[    2.069408] libphy: Fixed MDIO Bus: probed
[    2.069492] tun: Universal TUN/TAP device driver, 1.6
[    2.069493] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.069542] PPP generic driver version 2.4.2
[    2.069589] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.069591] ehci-pci: EHCI PCI platform driver
[    2.069722] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    2.069731] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.069739] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.069757] ehci-pci 0000:00:1a.0: debug port 2
[    2.073669] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.073690] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf271a000
[    2.084999] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.085022] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.085025] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.085027] usb usb1: Product: EHCI Host Controller
[    2.085029] usb usb1: Manufacturer: Linux 3.10.0-2-generic ehci_hcd
[    2.085031] usb usb1: SerialNumber: 0000:00:1a.0
[    2.085148] hub 1-0:1.0: USB hub found
[    2.085153] hub 1-0:1.0: 3 ports detected
[    2.085417] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    2.085425] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.085430] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.085446] ehci-pci 0000:00:1d.0: debug port 2
[    2.089363] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.089379] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf2719000
[    2.100998] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.101012] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.101015] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.101017] usb usb2: Product: EHCI Host Controller
[    2.101019] usb usb2: Manufacturer: Linux 3.10.0-2-generic ehci_hcd
[    2.101021] usb usb2: SerialNumber: 0000:00:1d.0
[    2.101137] hub 2-0:1.0: USB hub found
[    2.101141] hub 2-0:1.0: 3 ports detected
[    2.101259] ehci-platform: EHCI generic platform driver
[    2.101267] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.101280] uhci_hcd: USB Universal Host Controller Interface driver
[    2.101414] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    2.101418] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.101427] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.101522] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.101552] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    2.101606] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.101608] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.101610] usb usb3: Product: xHCI Host Controller
[    2.101613] usb usb3: Manufacturer: Linux 3.10.0-2-generic xhci_hcd
[    2.101615] usb usb3: SerialNumber: 0000:00:14.0
[    2.101701] xHCI xhci_add_endpoint called for root hub
[    2.101703] xHCI xhci_check_bandwidth called for root hub
[    2.101725] hub 3-0:1.0: USB hub found
[    2.101733] hub 3-0:1.0: 4 ports detected
[    2.102066] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.102070] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.102095] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.102097] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.102100] usb usb4: Product: xHCI Host Controller
[    2.102102] usb usb4: Manufacturer: Linux 3.10.0-2-generic xhci_hcd
[    2.102104] usb usb4: SerialNumber: 0000:00:14.0
[    2.102187] xHCI xhci_add_endpoint called for root hub
[    2.102189] xHCI xhci_check_bandwidth called for root hub
[    2.102208] hub 4-0:1.0: USB hub found
[    2.102216] hub 4-0:1.0: 4 ports detected
[    2.121077] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.134600] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.134719] mousedev: PS/2 mouse device common for all mice
[    2.141492] rtc_cmos 00:05: RTC can wake from S4
[    2.141632] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.141666] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.141736] device-mapper: uevent: version 1.0.3
[    2.141808] device-mapper: ioctl: 4.24.0-ioctl (2013-01-15) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.141815] Intel P-state driver initializing.
[    2.141828] Intel pstate controlling: cpu 0
[    2.141844] Intel pstate controlling: cpu 1
[    2.141862] Intel pstate controlling: cpu 2
[    2.141875] Intel pstate controlling: cpu 3
[    2.141972] cpuidle: using governor ladder
[    2.145040] cpuidle: using governor menu
[    2.145049] ledtrig-cpu: registered to indicate activity on CPUs
[    2.145050] EFI Variables Facility v0.08 2004-May-17
[    2.158504] ashmem: initialized
[    2.158819] TCP: cubic registered
[    2.159022] NET: Registered protocol family 10
[    2.159445] NET: Registered protocol family 17
[    2.159467] Key type dns_resolver registered
[    2.159922] Loading module verification certificates
[    2.161510] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 238e8976ebaee4c78e1f970bca24255fc770c7c4'
[    2.161520] registered taskstats version 1
[    2.164188] Key type trusted registered
[    2.166210] Key type encrypted registered
[    2.168674] rtc_cmos 00:05: setting system clock to 2013-07-08 16:54:58 UTC (1373302498)
[    2.168873] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.168874] EDD information not available.
[    2.178611] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.294787] ACPI: Battery Slot [BAT0] (battery present)
[    2.295447] Freeing unused kernel memory: 1340k freed
[    2.295625] Write protecting the kernel read-only data: 12288k
[    2.297775] Freeing unused kernel memory: 1136k freed
[    2.299630] Freeing unused kernel memory: 1004k freed
[    2.312461] systemd-udevd[125]: starting version 204
[    2.335305] rtsx_pci 0000:02:00.0: irq 41 for MSI/MSI-X
[    2.335340] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 41
[    2.335943] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.336186] r8169 0000:04:00.0: irq 42 for MSI/MSI-X
[    2.336336] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000652000, b8:88:e3:e0:8f:8a, XID 0c900880 IRQ 42
[    2.336338] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.336910] libahci: module verification failed: signature and/or required key missing - tainting kernel
[    2.337500] ahci 0000:00:1f.2: version 3.0
[    2.337643] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    2.353146] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    2.353152] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    2.353160] ahci 0000:00:1f.2: setting latency timer to 64
[    2.361426] scsi0 : ahci
[    2.361501] scsi1 : ahci
[    2.361559] scsi2 : ahci
[    2.361617] scsi3 : ahci
[    2.361669] scsi4 : ahci
[    2.361722] scsi5 : ahci
[    2.361782] ata1: SATA max UDMA/133 abar m2048@0xf2718000 port 0xf2718100 irq 43
[    2.361783] ata2: DUMMY
[    2.361786] ata3: SATA max UDMA/133 abar m2048@0xf2718000 port 0xf2718200 irq 43
[    2.361787] ata4: DUMMY
[    2.361788] ata5: DUMMY
[    2.361789] ata6: DUMMY
[    2.397205] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.509242] tsc: Refined TSC clocksource calibration: 1696.146 MHz
[    2.509247] Switching to clocksource tsc
[    2.529633] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.529656] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.529845] hub 1-1:1.0: USB hub found
[    2.529995] hub 1-1:1.0: 6 ports detected
[    2.641297] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.681333] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.681360] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.693718] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.693727] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.693733] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.693744] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.693751] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.693756] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.694768] ata1.00: ATA-8: HITACHI HTS725050A7E630, GH2ZB390, max UDMA/133
[    2.694773] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.695915] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.695920] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.695924] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.696549] ata3.00: ATA-8: SAMSUNG MZMPA024HMCD-000L1, AXM22L1Q, max UDMA/133
[    2.696553] ata3.00: 46905264 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.696949] ata1.00: configured for UDMA/133
[    2.696969] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.696976] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.696978] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.697205] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72505 GH2Z PQ: 0 ANSI: 5
[    2.697406] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.697410] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.697415] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.697480] sd 0:0:0:0: [sda] Write Protect is off
[    2.697483] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.697519] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.698211] ata3.00: configured for UDMA/133
[    2.698419] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG MZMPA024 AXM2 PQ: 0 ANSI: 5
[    2.698557] sd 2:0:0:0: [sdb] 46905264 512-byte logical blocks: (24.0 GB/22.3 GiB)
[    2.698582] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.698664] sd 2:0:0:0: [sdb] Write Protect is off
[    2.698668] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.698715] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.701019]  sdb: sdb1
[    2.701521] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.773754] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.773760] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.774115] hub 2-1:1.0: USB hub found
[    2.774224] hub 2-1:1.0: 8 ports detected
[    2.776452]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9
[    2.777322] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.845463] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.945326] usb 1-1.1: New USB device found, idVendor=03eb, idProduct=8206
[    2.945349] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.945350] usb 1-1.1: Product: Atmel maXTouch Digitizer
[    2.945352] usb 1-1.1: Manufacturer: Atmel
[    2.951001] hidraw: raw HID events driver (C) Jiri Kosina
[    2.957299] usbcore: registered new interface driver usbhid
[    2.957301] usbhid: USB HID core driver
[    2.960365] hid-generic 0003:03EB:8206.0002: hiddev0,hidraw0: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:1a.0-1.1/input1
[    3.017550] usb 1-1.3: new full-speed USB device number 4 using ehci-pci
[    3.113201] usb 1-1.3: New USB device found, idVendor=0a5c, idProduct=21f3
[    3.113204] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.113206] usb 1-1.3: Product: BCM20702A0
[    3.113207] usb 1-1.3: Manufacturer: Broadcom Corp
[    3.113208] usb 1-1.3: SerialNumber: C0143DBF4BF6
[    3.185613] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    3.279903] usb 2-1.5: New USB device found, idVendor=0483, idProduct=91d1
[    3.279905] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.279907] usb 2-1.5: Product: STM32 eMotion2
[    3.279909] usb 2-1.5: Manufacturer: STMicroelectronics
[    3.279910] usb 2-1.5: SerialNumber: STM32 eMotion2
[    3.353688] usb 2-1.6: new high-speed USB device number 4 using ehci-pci
[    3.509888] usb 2-1.6: New USB device found, idVendor=04f2, idProduct=b315
[    3.509891] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.509894] usb 2-1.6: Product: Integrated Camera
[    3.509896] usb 2-1.6: Manufacturer: SunplusIT INC.
[    3.829603] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    4.638661] init: upstart-dbus-bridge main process (188) terminated with status 1
[    4.638685] init: upstart-dbus-bridge main process ended, respawning
[   11.395356] Adding 3906556k swap on /dev/sda7.  Priority:-1 extents:1 across:3906556k FS
[   11.475395] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.534709] systemd-udevd[309]: starting version 204
[   11.564575] lp: driver loaded but no devices found
[   11.611806] Non-volatile memory driver v1.3
[   11.614578] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   11.614581] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   11.614582] thinkpad_acpi: ThinkPad BIOS GDET95WW (1.55 ), EC unknown
[   11.614583] thinkpad_acpi: Lenovo ThinkPad Twist, model 33474HU
[   11.615639] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   11.615719] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   11.615841] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   11.615843] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   12.099937] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   12.231436] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   12.599437] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   12.599516] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   12.603331] wmi: Mapper loaded
[   12.606881] tpm_tis 00:09: 1.2 TPM (device-id 0x0, rev-id 78)
[   12.607553] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input4
[   12.630611] mei_me 0000:00:16.0: setting latency timer to 64
[   12.630656] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   12.641293] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130328/utaddress-251)
[   12.641301] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.641307] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130328/utaddress-251)
[   12.641310] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.641311] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130328/utaddress-251)
[   12.641315] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.641316] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.645740] cfg80211: Calling CRDA to update world regulatory domain
[   12.647399] lib80211: common routines for IEEE802.11 drivers
[   12.647402] lib80211_crypt: registered algorithm 'NULL'
[   12.648822] [drm] Initialized drm 1.1.0 20060810
[   12.658377] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.658380] Disabling lock debugging due to kernel taint
[   12.659756] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.685647] SKU: Nid=0x1d sku_cfg=0x40148605
[   12.685651] SKU: port_connectivity=0x1
[   12.685652] SKU: enable_pcbeep=0x1
[   12.685654] SKU: check_sum=0x00000004
[   12.685655] SKU: customization=0x00000086
[   12.685657] SKU: external_amp=0x0
[   12.685658] SKU: platform_type=0x1
[   12.685659] SKU: swap=0x0
[   12.685660] SKU: override=0x1
[   12.685833] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   12.685836]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.685837]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   12.685839]    mono: mono_out=0x0
[   12.685840]    inputs:
[   12.685842]      Mic=0x18
[   12.685844]      Internal Mic=0x12
[   12.685846] realtek: No valid SSID, checking pincfg 0x40148605 for NID 0x1d
[   12.685848] realtek: Enabling init ASM_ID=0x8605 CODEC_ID=10ec0269
[   12.691550] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x17
[   12.699603] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.701896] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   12.701990] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   12.702124] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.702235] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.703854] lib80211_crypt: registered algorithm 'TKIP'
[   12.705420] [drm] Memory usable by graphics device = 2048M
[   12.705424] checking generic (e0000000 410000) vs hw (e0000000 10000000)
[   12.705426] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   12.705445] Console: switching to colour dummy device 80x25
[   12.708138] i915 0000:00:02.0: setting latency timer to 64
[   12.749029] eth1: Broadcom BCM4359 802.11 Hybrid Wireless Controller 6.30.223.30 (r390414)
[   12.751623] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   12.751635] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.751637] [drm] Driver supports precise vblank timestamp query.
[   12.751703] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.864003] input: Atmel Atmel maXTouch Digitizer as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input9
[   12.864360] hid-multitouch 0003:03EB:8206.0001: input,hidraw1: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:1a.0-1.1/input0
[   12.902264] cfg80211: World regulatory domain updated:
[   12.902271] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.902273] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.902275] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.902276] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.902278] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.902279] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.918018] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   12.922939] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x17
[   12.924594] type=1400 audit(1373316909.246:2): apparmor="STATUS" operation="profile_load" parent=534 profile="unconfined" name="/sbin/dhclient" pid=572 comm="apparmor_parser"
[   12.924603] type=1400 audit(1373316909.246:3): apparmor="STATUS" operation="profile_load" parent=534 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[   12.924610] type=1400 audit(1373316909.246:4): apparmor="STATUS" operation="profile_load" parent=534 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=572 comm="apparmor_parser"
[   12.925070] type=1400 audit(1373316909.246:5): apparmor="STATUS" operation="profile_replace" parent=534 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[   12.925077] type=1400 audit(1373316909.246:6): apparmor="STATUS" operation="profile_replace" parent=534 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=572 comm="apparmor_parser"
[   12.925125] type=1400 audit(1373316909.246:7): apparmor="STATUS" operation="profile_replace" parent=504 profile="unconfined" name="/sbin/dhclient" pid=571 comm="apparmor_parser"
[   12.925132] type=1400 audit(1373316909.246:8): apparmor="STATUS" operation="profile_replace" parent=504 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=571 comm="apparmor_parser"
[   12.925137] type=1400 audit(1373316909.246:9): apparmor="STATUS" operation="profile_replace" parent=504 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=571 comm="apparmor_parser"
[   12.925334] type=1400 audit(1373316909.246:10): apparmor="STATUS" operation="profile_replace" parent=534 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=572 comm="apparmor_parser"
[   12.925839] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x17
[   12.926476] type=1400 audit(1373316909.250:11): apparmor="STATUS" operation="profile_replace" parent=557 profile="unconfined" name="/sbin/dhclient" pid=573 comm="apparmor_parser"
[   12.927368] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x17
[   12.928280] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.950270] kvm: disabled by bios
[   12.950865] fbcon: inteldrmfb (fb0) is primary device
[   13.012265] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[   13.041540] Bluetooth: Core ver 2.16
[   13.041560] NET: Registered protocol family 31
[   13.041561] Bluetooth: HCI device and connection manager initialized
[   13.041624] Bluetooth: HCI socket layer initialized
[   13.041626] Bluetooth: L2CAP socket layer initialized
[   13.041631] Bluetooth: SCO socket layer initialized
[   13.046148] usbcore: registered new interface driver btusb
[   13.046699] Linux video capture interface: v2.00
[   13.052779] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b315)
[   13.061086] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input10
[   13.061177] usbcore: registered new interface driver uvcvideo
[   13.061178] USB Video Class driver (1.1.1)
[   13.622471] Console: switching to colour frame buffer device 170x48
[   13.624765] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.624767] i915 0000:00:02.0: registered panic notifier
[   13.750901] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x000000066) is beyond end of object (length 0x16) (20130328/exoparg2-421)
[   13.750912] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BRNS] (Node ffff880118246aa0), AE_AML_PACKAGE_LIMIT (20130328/psparse-537)
[   13.750920] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VID_.LCD0._BCM] (Node ffff880118248ed8), AE_AML_PACKAGE_LIMIT (20130328/psparse-537)
[   13.750930] ACPI Error: Evaluating _BCM failed (20130328/video-373)
[   13.751080] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   13.751155] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input11
[   13.751363] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.850770] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   14.750628] init: failsafe main process (736) killed by TERM signal
[   15.177943] Bluetooth: RFCOMM TTY layer initialized
[   15.177957] Bluetooth: RFCOMM socket layer initialized
[   15.177959] Bluetooth: RFCOMM ver 1.11
[   15.178619] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.178622] Bluetooth: BNEP filters: protocol multicast
[   15.178630] Bluetooth: BNEP socket layer initialized
[   15.416632] init: avahi-cups-reload main process (813) terminated with status 1
[   15.542391] ppdev: user-space parallel port driver
[   16.525741] r8169 0000:04:00.0 eth0: link down
[   16.525794] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.526130] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.431557] Unsafe core_pattern used with suid_dumpable=2. Pipe handler or fully qualified core dump path required.
[   24.475715] cfg80211: Calling CRDA for country: US
[   24.478535] cfg80211: Regulatory domain changed to country: US
[   24.478539] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.478540] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   24.478542] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   24.478543] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.478544] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.478545] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.478546] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   24.478547] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
```

---

### Post by EricKit on 2013-07-15
I can confirm that the touchpad is always broken after a shutdown and power up, always works after a reboot.

---

