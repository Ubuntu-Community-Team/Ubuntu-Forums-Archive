---
title: "xen 8.04 kernel boot failure on loading ahci module"
date: 2008-06-12
forum: Virtualisation
---

### Post by ralic on 2008-06-12
My SATA disks are identified fine when booting with the stock 8.04 kernel (2.6.24-18-server), but when booting with the stock 8.04 xen kernel, I get a Call Trace and no disks are found.

I have attached the dmesg output from a boot up using the server kernel and one from the xen kernel. Had to zip them to beat the filesize limit.

I have managed to trace the failure to the ahci.ko kernel module:
```

[    3.422] ahci 00:0:0e.0: AHCI 00.00 3 slots 4 ports 3 Gbps 0xf impl IDE mode
[    3.424] ahci 00:0:0e.0: flags: 6bit sntf led clo pmp pio 
[    3.423] PCI: Setting latency timer of device 00:0:0e.0 to 6
[    3.437] WARNING: at /build/buildd/linux-2.6.2/debian/build/custom-source-xen/drivers/ata/libata-core.c:73 ata_host_activate()
[    3.438] Pid: 19, comm: modprobe Not tainted 2.6.2-1-xen #1
[    3.436] 
[    3.436] Call Trace:
[    3.434]  [<ffffffff80ba4e>] :libata:ata_host_activate+0x1e/0x10
[    3.432]  [<ffffffff80f8b9f>] :ahci:ahci_init_one+0x9f/0xb5
[    3.431]  [<ffffffff83aed6] pci_device_probe+0x7/0xa0
[    3.430]  [<ffffffff83c8cac>] driver_probe_device+0x9c/0x1b0
[    3.438]  [<ffffffff83c8f7>] __driver_attach+0xc9/0xd0
[    3.446]  [<ffffffff83c8eb0] __driver_attach+0x0/0xd0
[    3.444]  [<ffffffff83c7eed>] bus_for_each_dev+0x4d/0x8
[    3.442]  [<ffffffff83c8fc>] bus_add_driver+0xac/0x20
[    3.440]  [<ffffffff83b19] __pci_register_driver+0x6/0xb0
[    3.448]  [<ffffffff82a3e>] sys_init_module+0x1e/0x1a9
[    3.447]  [<ffffffff82a13>] cp_new_stat+0xe5/0x10
[    3.445]  [<ffffffff82c68] system_call+0x6/0x6d
[    3.443]  [<ffffffff82c60] system_call+0x0/0x6d
[    3.441] 
[    3.448] scsi0 : ahci
[    3.457] scsi1 : ahci
[    3.457] scsi2 : ahci
[    3.457] scsi3 : ahci
[    3.464] ata1: SATA max UDMA/13 abar m89@0xfe240 port 0xfe240
[    3.463] ata2: SATA max UDMA/13 abar m89@0xfe240 port 0xfe248
[    3.461] ata3: SATA max UDMA/13 abar m89@0xfe240 port 0xfe240
[    3.469] ata4: SATA max UDMA/13 abar m89@0xfe240 port 0xfe248
[    4.163] ata1: SATA link up 3.0 Gbps (SStatus 13 SControl 30)
[   3.195] ata1.0: qc timeout (cmd 0xec)
[   3.107] ata1.0: failed to IDENTIFY (I/O error, err_mask=0x4)
[   3.105] ata1: failed to recover some devices, retrying in 5 secs
[   3.720] ata1: SATA link up 3.0 Gbps (SStatus 13 SControl 30)
[   6.761] ata1.0: qc timeout (cmd 0xec)
[   6.762] ata1.0: failed to IDENTIFY (I/O error, err_mask=0x4)
[   6.760] ata1: failed to recover some devices, retrying in 5 secs
[   7.499] ata1: SATA link up 3.0 Gbps (SStatus 13 SControl 30)
[  15.437] ata1.0: qc timeout (cmd 0xec)
[  15.438] ata1.0: failed to IDENTIFY (I/O error, err_mask=0x4)
[  15.436] ata1: failed to recover some devices, retrying in 5 secs
[  11.054] ata1: SATA link up 3.0 Gbps (SStatus 13 SControl 30)
[  11.652] ata2: SATA link up 1.5 Gbps (SStatus 13 SControl 30)
[  11.695] ata2.0: qc timeout (cmd 0xec)
[  11.696] ata2.0: failed to IDENTIFY (I/O error, err_mask=0x5)
[  11.695] ata2: failed to recover some devices, retrying in 5 secs
.
.
.
```

The module is different between versions as can be seen here:
```
xen@xenman:~$ ls -l /lib/modules/2.6.24-18-xen/kernel/drivers/ata/ahci.ko
-rw-r--r-- 1 root root 49072 2008-05-29 02:10 /lib/modules/2.6.24-18-xen/kernel/drivers/ata/ahci.ko
xen@xenman:~$ ls -l /lib/modules/2.6.24-18-server/kernel/drivers/ata/ahci.ko
-rw-r--r-- 1 root root 56432 2008-05-29 02:02 /lib/modules/2.6.24-18-server/kernel/drivers/ata/ahci.ko
```

The failure with the xen boot eventually drops me into an initramfs prompt and if I try and insmod the ahci.ko the problem repeats.

I would like to know if someone could assist me by indicating how I can determine the differences between these modules, so that I can apply whatever is working in the stock server one to the xen one.

If it helps, here is the lspci output from the box after booting the server kernel:
```
xen@xenman:~$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation Unknown device 07e2 (rev a2)
```

TIA

---

