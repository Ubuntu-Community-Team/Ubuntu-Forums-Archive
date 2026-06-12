---
title: "Amd Vega 8 (ryzen 3 2200G) passthrough to ubuntu VM on Hyper V 2016"
date: 2018-08-04
forum: Virtualisation
---

### Post by aseemduggal on 2018-08-04
Hi Guys,

I have Ubuntu Server 16.04 running as Virtual machine (Gen 2, secure boot : off) on Hyper v 2016.

Processor: Ryzen 3 2200G

Doing GPU passthrough through DDA and getting below errors in dmesg.

```
hv_vmbus: registering driver hv_pci
[    9.549011] hv_pci 4ac7370c-4134-41df-9876-e9efd1e37292: PCI VMBus probing: Using version 0x10002
[    9.570035] hv_pci 4ac7370c-4134-41df-9876-e9efd1e37292: PCI host bridge to bus 9876:00
[    9.570040] pci_bus 9876:00: root bus resource [mem 0xf8880000-0xf88fffff window]
[    9.570043] pci_bus 9876:00: root bus resource [mem 0xfe0000000-0xff01fffff window]
[    9.596036] pci 9876:00:00.0: [1002:15dd] type 00 class 0x030000
[    9.626334] pci 9876:00:00.0: reg 0x10: [mem 0xfe0000000-0xfefffffff 64bit pref]
[    9.651466] pci 9876:00:00.0: reg 0x18: [mem 0xff0000000-0xff01fffff 64bit pref]
[    9.702857] pci 9876:00:00.0: reg 0x24: [mem 0xf8880000-0xf88fffff]
[    9.726046] hv_vmbus: registering driver hv_balloon
[    9.732092] hv_balloon: Using Dynamic Memory protocol version 2.0
[    9.750493] pci 9876:00:00.0: PME# supported from D1 D2 D3hot D3cold
[    9.761513] hv_vmbus: registering driver hyperv_fb
[    9.764571] checking generic (f8000000 300000) vs hw (f8000000 300000)
[    9.764573] fb: switching to hyperv_fb from EFI VGA
[    9.764684] Console: switching to colour dummy device 80x25
[    9.764869] hyperv_fb: Screen resolution: 1152x864, Color depth: 32
[    9.766084] Console: switching to colour frame buffer device 144x54
[    9.766635] pci 9876:00:00.0: vgaarb: VGA device added: decodes=io+mem,owns=mem,locks=none
[    9.776232] pci 9876:00:00.0: BAR 0: assigned [mem 0xfe0000000-0xfefffffff 64bit pref]
[    9.799822] pci 9876:00:00.0: BAR 2: assigned [mem 0xff0000000-0xff01fffff 64bit pref]
[    9.823526] pci 9876:00:00.0: BAR 5: assigned [mem 0xf8880000-0xf88fffff]
[    9.824652] pci 9876:00:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    9.923655] **Decoding supported only on Scalable MCA processors.**
[    9.956565] amd64_edac_mod**: Unknown symbol amd_unregister_ecc_decoder (err 0)**
[    9.956611] amd64_edac_mod**: Unknown symbol amd_register_ecc_decoder (err 0)**
[    9.956630] amd64_edac_mod**: Unknown symbol amd_report_gart_errors (err 0)**
[   10.857762] [drm] amdgpu kernel modesetting enabled.
[   10.911205] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[   10.911207] AMD IOMMUv2 functionality not available on this system
[   10.924573] **CRAT table not found**
[   10.924576] Virtual CRAT table created for CPU
[   10.924577] Parsing CRAT table with 1 nodes
[   10.924579] Creating topology SYSFS entries
[   10.924592] Topology: Add CPU node
[   10.924592] Finished initializing topology
[   10.924750] kfd kfd: Initialized module
[   10.926645] amdgpu 9876:00:00.0**: can't derive routing for PCI INT A**
[   10.926647] amdgpu 9876:00:00.0**: PCI INT A: no GSI**
[   10.927596] [drm] initializing kernel modesetting (RAVEN 0x1002:0x15DD 0x1462:0x7B38 0xC8).
[   10.927614] [drm] register mmio base: 0xF8880000
[   10.927615] [drm] register mmio size: 524288
[   10.927621] [drm] PCI I/O BAR is not found.
[   10.927624] [drm] add ip block number 0 <soc15_common>
[   10.927625] [drm] add ip block number 1 <gmc_v9_0>
[   10.927626] [drm] add ip block number 2 <vega10_ih>
[   10.927627] [drm] add ip block number 3 <psp>
[   10.927628] [drm] add ip block number 4 <powerplay>
[   10.927630] [drm] add ip block number 5 <dm>
[   10.927631] [drm] add ip block number 6 <gfx_v9_0>
[   10.927632] [drm] add ip block number 7 <sdma_v4_0>
[   10.927633] [drm] add ip block number 8 <vcn_v1_0>
[   11.036401] kfd kfd**: DID 15dd is missing in supported_devices**
[COLOR=#ff0000][   11.036404] kfd kfd: kgd2kfd_probe failed[/COLOR]
[   11.036451] [drm] VCN decode is enabled in VM mode
[   11.036452] [drm] VCN encode is enabled in VM mode
[   11.068253] [drm] BIOS signature incorrect ff ff
[COLOR=#ff0000][   11.068272] amdgpu 9876:00:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
[   11.102075] [drm] BIOS signature incorrect ff ff
[   11.102173] [drm:amdgpu_get_bios [amdgpu]] *ERROR* Unable to locate a BIOS ROM
[   11.102226] amdgpu 9876:00:00.0: Fatal error during GPU init[/COLOR]
[   11.102261] [drm] amdgpu: finishing device.
[   11.104128] amdgpu**: probe of 9876:00:00.0 failed with error -22**

```

I tried upgrading to kernel 4.17.12 and now at 4.18 rc7, still the same error.

lshw

```
*-display UNCLAIMED
          description: VGA compatible controller
          product: Advanced Micro Devices, Inc. [AMD/ATI]
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 1
          bus info: pci@9876:00:00.0
          version: c8
          width: 64 bits
          clock: 33MHz
          capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
          configuration: latency=0
          resources: iomemory:f0-ef iomemory:f0-ef memory:fe0000000-fefffffff memory:ff0000000-ff01fffff memory:f8880000-f88fffff memory:c0000-dffff

```

any help is greatly appreciated.

Thanks

---

