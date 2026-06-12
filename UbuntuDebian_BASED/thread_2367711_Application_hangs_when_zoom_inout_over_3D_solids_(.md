---
title: "Application hangs when zoom in/out over 3D solids (Radeon HD 3000)"
date: 2017-08-02
forum: Ubuntu/Debian BASED
---

### Post by luispa on 2017-08-02
Hi Folks,
I'm using KDE Neon which is based on Ubuntu 16.04. I recently upgraded my desktop and I bought an Asus motherboard (M5A78L-M/USB3) with integrated graphic card (Radeon HD 3000) with a FX-8300 AMD processor. I use Heekscad a lot for CAM work. I realized Heekscad hangs for more than a couple minutes when doing a simple task like a zoom in/out over 3D solids. I tested it with a dedicated graphic card, an old GEFORCE and it worked flawlessly. Is there some way to tweak the HD 3000 to deal with that kind of tasks?

The screenshots were taked right after doing a zoom in and right after the operation was completed, take a look at the clock for an idea of the elapsed time.
[ATTACH=CONFIG]276229[/ATTACH]
[ATTACH=CONFIG]276230[/ATTACH]

The output of:
```
dmesg | grep radeon
```

is

```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-28-generic root=UUID=91fda081-e66d-4f96-8739-239027053466 ro quiet splash vt.handoff=7 radeon.gartsize=512 radeon.pcie_gen2=1 radeon.agpmode=4 radeon.disp_priority=2 radeon.vm_size=1 radeon.fastfb=1 radeon.dpm=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-28-generic root=UUID=91fda081-e66d-4f96-8739-239027053466 ro quiet splash vt.handoff=7 radeon.gartsize=512 radeon.pcie_gen2=1 radeon.agpmode=4 radeon.disp_priority=2 radeon.vm_size=1 radeon.fastfb=1 radeon.dpm=1
[    2.172370] [drm] radeon kernel modesetting enabled.
[    2.177870] fb: switching to radeondrmfb from VESA VGA
[    2.179034] radeon 0000:01:05.0: VRAM: 1024M 0x00000000C0000000 - 0x00000000FFFFFFFF (1024M used)
[    2.179035] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    2.179252] [drm] radeon: 1024M of VRAM memory ready
[    2.179253] [drm] radeon: 512M of GTT memory ready.
[    2.184310] [drm] radeon: dpm initialized
[    2.213042] radeon 0000:01:05.0: WB enabled
[    2.213043] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff96a7dcbdfc00
[    2.213046] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
[    2.213257] [drm] radeon: irq initialized.
[    2.338955] fbcon: radeondrmfb (fb0) is primary device
[    2.339041] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    2.393649] [drm] Initialized radeon 2.49.0 20080528 for 0000:01:05.0 on minor 0
[   20.654626] radeon 0000:01:05.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
```

The output of

```
systool -v -m radeon
```

is

```
Module = "radeon"

  Attributes:
    coresize            = "1507328"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "21"
    srcversion          = "E3A714F6EF43112B4F27E7B"
    taint               = ""
    uevent              = <store method only>

  Parameters:
    agpmode             = "4"
    aspm                = "-1"
    audio               = "-1"
    auxch               = "-1"
    backlight           = "-1"
    bapm                = "-1"
    benchmark           = "0"                                                                                                                                                                             
    connector_table     = "0"                                                                                                                                                                             
    deep_color          = "0"                                                                                                                                                                             
    disp_priority       = "2"                                                                                                                                                                             
    dpm                 = "1"                                                                                                                                                                             
    dynclks             = "-1"                                                                                                                                                                            
    fastfb              = "1"                                                                                                                                                                             
    hard_reset          = "0"                                                                                                                                                                             
    hw_i2c              = "0"                                                                                                                                                                             
    lockup_timeout      = "10000"                                                                                                                                                                         
    msi                 = "-1"                                                                                                                                                                            
    mst                 = "0"                                                                                                                                                                             
    no_wb               = "0"                                                                                                                                                                             
    pcie_gen2           = "1"                                                                                                                                                                             
    r4xx_atom           = "0"                                                                                                                                                                             
    runpm               = "-1"
    test                = "0"
    tv                  = "1"
    use_pflipirq        = "2"
    uvd                 = "1"
    vce                 = "1"
    vm_block_size       = "9"
    vm_size             = "1"

  Sections:
    .altinstr_replacement= "0x0000000000000000"
    .altinstructions    = "0x0000000000000000"
    .bss                = "0x0000000000000000"
    .data.unlikely      = "0x0000000000000000"
    .data               = "0x0000000000000000"
    .exit.text          = "0x0000000000000000"
    .fixup              = "0x0000000000000000"
    .gnu.linkonce.this_module= "0x0000000000000000"
    .init.text          = "0x0000000000000000"
    .note.gnu.build-id  = "0x0000000000000000"
    .parainstructions   = "0x0000000000000000"
    .ref.data           = "0x0000000000000000"
    .rodata.str1.1      = "0x0000000000000000"
    .rodata.str1.8      = "0x0000000000000000"
    .rodata             = "0x0000000000000000"
    .smp_locks          = "0x0000000000000000"
    .strtab             = "0x0000000000000000"
    .symtab             = "0x0000000000000000"
    .text               = "0x0000000000000000"
    .text.unlikely      = "0x0000000000000000"
    __bug_table         = "0x0000000000000000"
    __ex_table          = "0x0000000000000000"
    __jump_table        = "0x0000000000000000"
    __mcount_loc        = "0x0000000000000000"
    __param             = "0x0000000000000000"
    __tracepoints_ptrs  = "0x0000000000000000"
    __tracepoints       = "0x0000000000000000"
    __tracepoints_strings= "0x0000000000000000"
    __verbose           = "0x0000000000000000"
    _ftrace_events      = "0x0000000000000000"
```

I'd prefer to keep using the integrated graphic chipset. Any idea about how to tweak it?

Thank you very much in advance.

---

### Post by slickymaster on 2017-08-02
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by luispa on 2017-08-02
I'm sorry for posting this thread in the wrong forum.

---

