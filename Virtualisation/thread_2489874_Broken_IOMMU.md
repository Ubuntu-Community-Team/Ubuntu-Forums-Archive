---
title: "Broken IOMMU ?"
date: 2023-08-12
forum: Virtualisation
---

### Post by tryphon2 on 2023-08-12
Hello,

I was very happy with my fully working Windows 10 VM under KVM using a dedicated Radeon graphic card (PCI passthrough) since months. Yesterday, I was playing a game then I normally shut down Windows 10. After 20 minutes, the shut down process was stuck. Anyway I forced the VM to shut down, then I shut down Ubuntu. Today, I turn on my computer and I am surprised to see my second graphic card up on Ubuntu (22.04, kernel 5.19) since it is reserved for my VM (I did not process any update at that time).

I checked the vfio-pci drivers in use :

```
lspci -nnv | grep vfio
```

but no output.

Also in the grub file:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on kvm.ignore_msrs=1 vfio-pci.ids=1002:6985,1002:aae0"
```

the parameters are ok.

```
sudo dmesg | grep "Virtualization Technology for Directed I/O"
[    2.253556] DMAR: Intel(R) Virtualization Technology for Directed I/O
```

```
sudo dmesg | grep -i iommu
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=d4f0846c-16f0-4562-b0fc-232b42ec0005 ro quiet splash intel_iommu=on kvm.ignore_msrs=1 vfio-pci.ids=10de:102d vt.handoff=7
[    0.710282] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=d4f0846c-16f0-4562-b0fc-232b42ec0005 ro quiet splash intel_iommu=on kvm.ignore_msrs=1 vfio-pci.ids=10de:102d vt.handoff=7
[    0.710386] DMAR: IOMMU enabled
[    1.637402] DMAR-IR: IOAPIC id 3 under DRHD base  0xf7ffc000 IOMMU 0
[    1.637404] DMAR-IR: IOAPIC id 1 under DRHD base  0xf3ffc000 IOMMU 2
[    1.637405] DMAR-IR: IOAPIC id 2 under DRHD base  0xf3ffc000 IOMMU 2
[    2.135408] iommu: Default domain type: Translated 
[    2.135408] iommu: DMA domain TLB invalidation policy: lazy mode 
[    2.214090] DMAR: **IOMMU feature sc_support inconsistent**
[    2.214092] DMAR: **IOMMU feature dev_iotlb_support inconsistent**
[    2.214216] pci 0000:00:1b.0: Adding to iommu group 0
...
```

I do not know if the lines in bold were there before the trouble.

I tried again :
```
sudo update-grub
```
then reboot.
But vfio-pci drivers do not show up anymore.

Finally, I updated Ubuntu loading kernel 6.2. Reboot. But same issue.
I tried to declare another device using the grub, but same issue.
Something is broken, but I did not get clue to understand where.

Any idea ?

Thank you.

Dell Precision T7810
nVidia Quadro K6000 (main)
AMD Radeon WX3100 (for VM)
Ubuntu 22.04
KVM
Windows 10

---

### Post by ajgreeny on 2023-08-12
That 6.2.0-26 kernel version has caused many users problems with their systems, so assuming you still have the 5.19.0-50 (or other 5.19 kernel) try booting to that from the grub menu to see if that overcomes the problem you are getting at the moment.

If that works properly we can then try to sort out where you go from here.

---

### Post by tryphon2 on 2023-08-13
Thank you for reading.

Trouble started under 5.19 kernel : vfio-pci drivers do not show up anymore. I use this kernel with Ubuntu. After many unsuccessful tries to sort out the issue under this kernel, I decided to upgrade and kernel 6.2 came up automatically.

However, going back to kernel 5.19 revived the vfio-pci drivers as you said.

Nonetheless, the graphic card dedicated to the VM is now unstable and Windows deactivates it in some circumstances (games). Starting the VM, KVM often states "Unknown PCI header type 127 for device nnnnn". Installing again the AMD drivers did not help.

Something remains broken.

---

### Post by mIk3_08 on 2023-08-13
The error message "Unknown PCI header type 127 for device nnnnn"  indicates that the system unit is unable to identify the PCI device with  the device ID nnnnn. This can happen for a number of reasons,  including: maybe the PCI device is not properly seated in its slot or the PCI  device is incompatible with the system unit, the system unit's BIOS is not up to date. Regards and cheers

---

### Post by tryphon2 on 2023-08-15
I seated again the graphic card. The VM can start but the display is unstable and Windows deactivates the graphic driver (code 43). Before the trouble, the VM + graphic card worked for months. From your explanations, is it possible a damaged VM could generate the unknown PCI header error or unstable graphic driver ?

I plan to go back to Ubuntu 20.04 ...

---

### Post by MAFoElffen on 2023-08-15
I am not having any troubles with
```

mafoelffen@msi-ubuntu:~$ lsb_release -d
Description:    Ubuntu 22.04.3 LTS
mafoelffen@msi-ubuntu:~$ uname -r
6.2.0-26-generic
mafoelffen@msi-ubuntu:~$ kvm -version
QEMU emulator version 6.2.0 (Debian 1:6.2+dfsg-2ubuntu6.12)
Copyright (c) 2003-2021 Fabrice Bellard and the QEMU Project developers
mafoelffen@msi-ubuntu:~$ libvirtd --version
libvirtd (libvirt) 8.0.0

```
But I was one of the beta testers for KVM 6.0 & 6.2... And I do hardware pass-throughs with scripts in /etc/libvirt/hooks/...

---

### Post by MAFoElffen on 2023-08-15
I reread my own post, and I have to back up for a second. That post made it sound like it was easy to do and stable, once you have it set up. Far from that. I consider myself having a few advanced skills, and some Linux experience. Heck, I support the Linux Graphics layer, right? It humbled me. I learned a lot about what does not work. LOL

It is neither. It is not easy, and it is not consistent. I can usually explain things to others, but I do not know if I can explain how to do this to others... My hat is off to you if you find a way that works for out of the gate, and stays that way from release to release.

I loosely used these 6 guides for inspiration. I'm not saying that any of these covered everything. I used pieces of each for reference. I had to use information from all 6 and do a lot of trial and error. And personally, I can say I did it, it worked, but... LOL. I went back to dual booting and just doing it on straight on hardware.

RE:
[https://libvirt.org/hooks.html](https://libvirt.org/hooks.html)
[https://passthroughpo.st/simple-per-vm-libvirt-hooks-with-the-vfio-tools-hook-helper/](https://passthroughpo.st/simple-per-vm-libvirt-hooks-with-the-vfio-tools-hook-helper/)
[https://github.com/jkhsjdhjs/gpu-passthrough/blob/master/etc/libvirt/hooks/qemu](https://github.com/jkhsjdhjs/gpu-passthrough/blob/master/etc/libvirt/hooks/qemu)
[https://github.com/BigAnteater/KVM-GPU-Passthrough](https://github.com/BigAnteater/KVM-GPU-Passthrough)
[https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF](https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF)
[https://www.pugetsystems.com/labs/articles/multiheaded-nvidia-gaming-using-ubuntu-14-04-kvm-585/](https://www.pugetsystems.com/labs/articles/multiheaded-nvidia-gaming-using-ubuntu-14-04-kvm-585/)

For me, it was not STABLE and I didn't like the lag... Lately I have played with the thought of trying it again on my new workstation, iCore 9 13th Gen that is on ZFS-on-Root with NVMe RAIDz storage pools and loads of DDR5 RAM... Because VM's on that snap and pop, better than being on straight hardware, but I haven't had the time or patience saved up yet for that challenge. LOL I would hope that if I did, that it would go smoother than last time.

---

### Post by tryphon2 on 2023-08-28
Happy to read your feeling and experience. I have not real skills on VM configuration. The destination of the VM I built is not for a unique user. As I have plenty of room to plug 16X graphic cards on 2 workstations and 1 server with an orgy of memory modules, VMs are a flexible solution easy to maintain. Also, multi-user Windows OS for servers is strongly beyond my means.

The solution to modify quickly the grub file is not so bad for me when I want to add or free graphic hardware for a VM. I would prefer all this operation integrated in KVM/QEMU. Maybe in the future ...

Thank you for the links. I may consider scripting for a while: I would prefer this solution than coming back to dual-boot (not really convenient and usable on servers).

I tasted the possibility to run in parallel Ubuntu and Windows VM with graphic card and it appeared really convincing :

> I can usually explain things to others, but I do not know if I can explain how to do this to others

You may try to invite people to cooperate with you to write a dedicated thread and present some generalities/details to practically get a working VM+graphic card ... what works and what does not.

If I find something stable from release to release, sure I will post it.

---

### Post by MAFoElffen on 2023-09-16
I can report that with kernel 6.3.0-32, that IMMOU is working:
```

mafoelffen@msi-ubuntu:~$ uname -r
6.2.0-32-generic

mafoelffen@msi-ubuntu:~$ sudo dmesg | grep -i -e IOMMU -e 'adding to'
[sudo] password for mafoelffen: 
[    0.000000] Command line: BOOT_IMAGE=/BOOT/ubuntu_2204@/vmlinuz-6.2.0-32-generic root=ZFS=rpool/ROOT/ubuntu_2204 ro cgroup_memory=1 cgroup_enable=memory swapaccount=1 systemd.unified_cgroup_hierarchy=0 [COLOR=#FF0000]intel_iommu=on[/COLOR] -- video=uvesa:1920x1080-32@60,mtrr:3,ywrap,noblank consoleblank=0 init_on_alloc=0 intel_iommu=on kvm.ignore_msrs=1 [COLOR=#FF0000]vfio-pci.ids=8086:a780[/COLOR] igb.max_vfs=7
[    0.143996] Kernel command line: BOOT_IMAGE=/BOOT/ubuntu_2204@/vmlinuz-6.2.0-32-generic root=ZFS=rpool/ROOT/ubuntu_2204 ro cgroup_memory=1 cgroup_enable=memory swapaccount=1 systemd.unified_cgroup_hierarchy=0 [COLOR=#FF0000]intel_iommu=on[/COLOR] -- video=uvesa:1920x1080-32@60,mtrr:3,ywrap,noblank consoleblank=0 init_on_alloc=0 intel_iommu=on kvm.ignore_msrs=1 [COLOR=#FF0000]vfio-pci.ids=8086:a780[/COLOR] igb.max_vfs=7
[COLOR=#ff0000][    0.144048] DMAR: IOMMU enabled[/COLOR]
[    0.308856] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.588897] pci 0000:00:02.0: DMAR: Skip IOMMU disabling for graphics
[    0.614793] iommu: Default domain type: Translated 
[    0.614793] iommu: DMA domain TLB invalidation policy: lazy mode 
[    0.657384] DMAR: IOMMU feature fl1gp_support inconsistent
[    0.657385] DMAR: IOMMU feature pgsel_inv inconsistent
[    0.657386] DMAR: IOMMU feature nwfs inconsistent
[    0.657387] DMAR: IOMMU feature dit inconsistent
[    0.657388] DMAR: IOMMU feature sc_support inconsistent
[    0.657389] DMAR: IOMMU feature dev_iotlb_support inconsistent
[COLOR=#ff0000][    0.657621] pci 0000:00:02.0: Adding to iommu group 0[/COLOR]
[    0.658049] pci 0000:00:00.0: Adding to iommu group 1
[    0.658060] pci 0000:00:01.0: Adding to iommu group 2
[    0.658069] pci 0000:00:06.0: Adding to iommu group 3
[    0.658077] pci 0000:00:08.0: Adding to iommu group 4
[    0.658084] pci 0000:00:0a.0: Adding to iommu group 5
[    0.658099] pci 0000:00:14.0: Adding to iommu group 6
[    0.658107] pci 0000:00:14.2: Adding to iommu group 6
[    0.658116] pci 0000:00:14.3: Adding to iommu group 7
[    0.658128] pci 0000:00:16.0: Adding to iommu group 8
[    0.658135] pci 0000:00:17.0: Adding to iommu group 9
[    0.658152] pci 0000:00:1a.0: Adding to iommu group 10
[    0.658174] pci 0000:00:1b.0: Adding to iommu group 11
[    0.658184] pci 0000:00:1b.4: Adding to iommu group 12
[    0.658206] pci 0000:00:1c.0: Adding to iommu group 13
[    0.658216] pci 0000:00:1c.1: Adding to iommu group 14
[    0.658226] pci 0000:00:1c.3: Adding to iommu group 15
[    0.658235] pci 0000:00:1d.0: Adding to iommu group 16
[    0.658245] pci 0000:00:1d.4: Adding to iommu group 17
[    0.658268] pci 0000:00:1f.0: Adding to iommu group 18
[    0.658277] pci 0000:00:1f.3: Adding to iommu group 18
[    0.658286] pci 0000:00:1f.4: Adding to iommu group 18
[    0.658294] pci 0000:00:1f.5: Adding to iommu group 18
[    0.658317] pci 0000:01:00.0: Adding to iommu group 19
[    0.658326] pci 0000:01:00.1: Adding to iommu group 19
[    0.658336] pci 0000:01:00.2: Adding to iommu group 19
[    0.658344] pci 0000:01:00.3: Adding to iommu group 19
[    0.658354] pci 0000:02:00.0: Adding to iommu group 20
[    0.658371] pci 0000:03:00.0: Adding to iommu group 21
[    0.658380] pci 0000:05:00.0: Adding to iommu group 22
[    0.658390] pci 0000:06:00.0: Adding to iommu group 23
[    0.658401] pci 0000:07:00.0: Adding to iommu group 24
[    0.658411] pci 0000:07:00.1: Adding to iommu group 25
[    0.658421] pci 0000:08:00.0: Adding to iommu group 26
[    0.658431] pci 0000:09:00.0: Adding to iommu group 27
[    0.658442] pci 0000:0a:08.0: Adding to iommu group 28
[    0.658461] pci 0000:0a:09.0: Adding to iommu group 29
[    0.658471] pci 0000:0a:0a.0: Adding to iommu group 30
[    0.658480] pci 0000:0a:0b.0: Adding to iommu group 31
[    0.658492] pci 0000:0a:10.0: Adding to iommu group 32
[    0.658508] pci 0000:0a:11.0: Adding to iommu group 33
[    0.658517] pci 0000:0a:12.0: Adding to iommu group 34
[    0.658528] pci 0000:0a:13.0: Adding to iommu group 35
[    0.658538] pci 0000:13:00.0: Adding to iommu group 36
[    1.188487]     intel_iommu=on
[    1.647864] pci 0000:07:10.0: Adding to iommu group 37
[    1.654228] pci 0000:07:10.2: Adding to iommu group 38
[    1.660360] pci 0000:07:10.4: Adding to iommu group 39
[    1.669007] pci 0000:07:10.6: Adding to iommu group 40
[    1.708129] pci 0000:07:11.0: Adding to iommu group 41
[    1.746014] pci 0000:07:11.2: Adding to iommu group 42
[    1.768401] pci 0000:07:11.4: Adding to iommu group 43
[    2.124003] pci 0000:07:10.1: Adding to iommu group 44
[    2.158066] pci 0000:07:10.3: Adding to iommu group 45
[    2.210899] pci 0000:07:10.5: Adding to iommu group 46
[    2.243678] pci 0000:07:10.7: Adding to iommu group 47
[    2.279438] pci 0000:07:11.1: Adding to iommu group 48
[    2.343557] pci 0000:07:11.3: Adding to iommu group 49
[    2.378893] pci 0000:07:11.5: Adding to iommu group 50


mafoelffen@msi-ubuntu:~$ for d in /sys/kernel/iommu_groups/*/devices/*; do n=${d#*/iommu_groups/*}; n=${n%%/*}; printf 'IOMMU group %s ' "$n"; lspci -nns "${d##*/}"; done
[COLOR=#ff0000]IOMMU group 0 00:02.0 Display controller [0380]: Intel Corporation Device [8086:a780] (rev 04)[/COLOR]
IOMMU group 10 00:1a.0 PCI bridge [0604]: Intel Corporation Device [8086:7a48] (rev 11)
IOMMU group 11 00:1b.0 PCI bridge [0604]: Intel Corporation Device [8086:7a40] (rev 11)
IOMMU group 12 00:1b.4 PCI bridge [0604]: Intel Corporation Device [8086:7a44] (rev 11)
IOMMU group 13 00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:7a38] (rev 11)
IOMMU group 14 00:1c.1 PCI bridge [0604]: Intel Corporation Device [8086:7a39] (rev 11)
IOMMU group 15 00:1c.3 PCI bridge [0604]: Intel Corporation Device [8086:7a3b] (rev 11)
IOMMU group 16 00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:7a30] (rev 11)
IOMMU group 17 00:1d.4 PCI bridge [0604]: Intel Corporation Device [8086:7a34] (rev 11)
IOMMU group 18 00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:7a04] (rev 11)
IOMMU group 18 00:1f.3 Audio device [0403]: Intel Corporation Device [8086:7a50] (rev 11)
IOMMU group 18 00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:7a23] (rev 11)
IOMMU group 18 00:1f.5 Serial bus controller [0c80]: Intel Corporation Device [8086:7a24] (rev 11)
IOMMU group 19 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU116 [GeForce GTX 1660 Ti] [10de:2182] (rev a1)
IOMMU group 19 01:00.1 Audio device [0403]: NVIDIA Corporation TU116 High Definition Audio Controller [10de:1aeb] (rev a1)
IOMMU group 19 01:00.2 USB controller [0c03]: NVIDIA Corporation TU116 USB 3.1 Host Controller [10de:1aec] (rev a1)
IOMMU group 19 01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU116 USB Type-C UCSI Controller [10de:1aed] (rev a1)
IOMMU group 1 00:00.0 Host bridge [0600]: Intel Corporation Device [8086:a700] (rev 01)
IOMMU group 20 02:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd Device [144d:a80c]
IOMMU group 21 03:00.0 Non-Volatile memory controller [0108]: Phison Electronics Corporation PS5013 E13 NVMe Controller [1987:5013] (rev 01)
IOMMU group 22 05:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd Device [144d:a80c]
IOMMU group 23 06:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:125c] (rev 04)
IOMMU group 24 07:00.0 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [8086:10c9] (rev 01)
IOMMU group 25 07:00.1 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [8086:10c9] (rev 01)
IOMMU group 26 08:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 02)
IOMMU group 27 09:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 28 0a:08.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 29 0a:09.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 2 00:01.0 PCI bridge [0604]: Intel Corporation Device [8086:a70d] (rev 01)
IOMMU group 30 0a:0a.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 31 0a:0b.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 32 0a:10.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 33 0a:11.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 34 0a:12.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 35 0a:13.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8748 48-Lane, 12-Port PCI Express Gen 3 (8 GT/s) Switch, 27 x 27mm FCBGA [10b5:8748] (rev ca)
IOMMU group 36 13:00.0 Non-Volatile memory controller [0108]: Phison Electronics Corporation PS5013 E13 NVMe Controller [1987:5013] (rev 01)
IOMMU group 37 07:10.0 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 38 07:10.2 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 39 07:10.4 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 3 00:06.0 PCI bridge [0604]: Intel Corporation Device [8086:a74d] (rev 01)
IOMMU group 40 07:10.6 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 41 07:11.0 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 42 07:11.2 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 43 07:11.4 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 44 07:10.1 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 45 07:10.3 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 46 07:10.5 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 47 07:10.7 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 48 07:11.1 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 49 07:11.3 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 4 00:08.0 System peripheral [0880]: Intel Corporation Device [8086:a74f] (rev 01)
IOMMU group 50 07:11.5 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 5 00:0a.0 Signal processing controller [1180]: Intel Corporation Device [8086:a77d] (rev 01)
IOMMU group 6 00:14.0 USB controller [0c03]: Intel Corporation Device [8086:7a60] (rev 11)
IOMMU group 6 00:14.2 RAM memory [0500]: Intel Corporation Device [8086:7a27] (rev 11)
IOMMU group 7 00:14.3 Network controller [0280]: Intel Corporation Device [8086:7a70] (rev 11)
IOMMU group 8 00:16.0 Communication controller [0780]: Intel Corporation Device [8086:7a68] (rev 11)
IOMMU group 9 00:17.0 SATA controller [0106]: Intel Corporation Device [8086:7a62] (rev 11)

# Reported from the Host:
mafoelffen@msi-ubuntu:~$ lspci -nnk | grep -A 3 -Ei 'VGA|DISPLAY' 
00:02.0 Display controller [0380]: Intel Corporation Device [8086:a780] (rev 04)
    DeviceName: Onboard - Video
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7d91]
    Kernel driver in use: [COLOR=#ff0000]vfio-pci[/COLOR]
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU116 [GeForce GTX 1660 Ti] [10de:2182] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] TU116 [GeForce GTX 1660 Ti] [1462:375a]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

# Reported from the VM:
mafoelffen@ubuntu-igpu:~$ clinfo | grep "Device Name"
  Device Name                                     Intel(R) UHD Graphics 770
    Device Name                                   Intel(R) UHD Graphics 770
    Device Name                                   Intel(R) UHD Graphics 770
    Device Name                                   Intel(R) UHD Graphics 770

```
Running the Intel Iris XE drivers on the host and VM... It works, but in benchmarks, it still has the lag that I know is there, compared to running it as native in dual-boot.  That is why I dual-boot. With mine, I know it's that the Intel XE drivers are still in an experimental stage for pass-throughs... But I understand that I have the time, skills, and hardware to reconfigure it different ways, to do different scenarios.

---

### Post by #&amp;thj^% on 2023-09-16
I as well have no problems:
```
uname -r && cat /etc/os-release
6.2.0-32-generic
PRETTY_NAME="Linux Lite 6.4"
NAME="Ubuntu"
VERSION_ID="23.04"
VERSION="23.04 (Lunar Lobster)"
VERSION_CODENAME=lunar
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=lunar
LOGO=ubuntu-logo
####
sudo dmesg | grep -i -e IOMMU -e 'IOMMU enabled'
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-32-generic root=/dev/mapper/vglinux-root ro quiet iommu=pt splash
[    0.033585] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-32-generic root=/dev/mapper/vglinux-root ro quiet iommu=pt splash
[    0.339836] iommu: Default domain type: Passthrough (set via kernel command line)
[    0.604366] pci 0000:00:00.2: AMD-Vi: IOMMU performance counters supported
[    0.604415] pci 0000:00:01.0: Adding to iommu group 0
[    0.604423] pci 0000:00:01.1: Adding to iommu group 1
[    0.604430] pci 0000:00:01.2: Adding to iommu group 2
[    0.604441] pci 0000:00:02.0: Adding to iommu group 3
[    0.604449] pci 0000:00:02.1: Adding to iommu group 4
[    0.604456] pci 0000:00:02.4: Adding to iommu group 5
[    0.604469] pci 0000:00:08.0: Adding to iommu group 6
[    0.604476] pci 0000:00:08.1: Adding to iommu group 6
[    0.604482] pci 0000:00:08.2: Adding to iommu group 6
[    0.604493] pci 0000:00:14.0: Adding to iommu group 7
[    0.604500] pci 0000:00:14.3: Adding to iommu group 7
[    0.604525] pci 0000:00:18.0: Adding to iommu group 8
[    0.604531] pci 0000:00:18.1: Adding to iommu group 8
[    0.604538] pci 0000:00:18.2: Adding to iommu group 8
[    0.604544] pci 0000:00:18.3: Adding to iommu group 8
[    0.604551] pci 0000:00:18.4: Adding to iommu group 8
[    0.604558] pci 0000:00:18.5: Adding to iommu group 8
[    0.604564] pci 0000:00:18.6: Adding to iommu group 8
[    0.604571] pci 0000:00:18.7: Adding to iommu group 8
[    0.604582] pci 0000:01:00.0: Adding to iommu group 9
[    0.604589] pci 0000:01:00.1: Adding to iommu group 9
[    0.604596] pci 0000:02:00.0: Adding to iommu group 10
[    0.604604] pci 0000:03:00.0: Adding to iommu group 11
[    0.604612] pci 0000:04:00.0: Adding to iommu group 12
[    0.604625] pci 0000:05:00.0: Adding to iommu group 6
[    0.604629] pci 0000:05:00.2: Adding to iommu group 6
[    0.604633] pci 0000:05:00.3: Adding to iommu group 6
[    0.604637] pci 0000:05:00.4: Adding to iommu group 6
[    0.604642] pci 0000:05:00.5: Adding to iommu group 6
[    0.604645] pci 0000:05:00.6: Adding to iommu group 6
[    0.604650] pci 0000:06:00.0: Adding to iommu group 6
[    0.604653] pci 0000:06:00.1: Adding to iommu group 6
[    0.605094] pci 0000:00:00.2: AMD-Vi: Found IOMMU cap 0x40
[    0.612547] perf/amd_iommu: Detected AMD IOMMU #0 (2 banks, 4 counters/bank).
[    1.915800] **_AMD-Vi: AMD IOMMUv2 loaded and initialized_**

```

---

### Post by tryphon2 on 2023-09-23
Thank you to give me these config outputs.

After the last update, I have:

```

uname -r6.2.0-33-generic

```

```
sudo dmesg | grep -i -e IOMMU -e 'IOMMU enabled'
[sudo] password for isis: 
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-33-generic root=UUID=d4f0846c-16f0-4562-b0fc-232b42ec0005 ro quiet splash intel_iommu=on kvm.ignore_msrs=1 vfio-pci.ids=1002:6985,1002:aae0 vt.handoff=7
[    0.710935] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-33-generic root=UUID=d4f0846c-16f0-4562-b0fc-232b42ec0005 ro quiet splash intel_iommu=on kvm.ignore_msrs=1 vfio-pci.ids=[COLOR=#ff0000]1002:6985[/COLOR],1002:aae0 vt.handoff=7
[    0.711036] DMAR: [COLOR=#008000]IOMMU enabled[/COLOR]
[    1.635303] DMAR-IR: IOAPIC id 3 under DRHD base  0xf7ffc000 IOMMU 0
[    1.635305] DMAR-IR: IOAPIC id 1 under DRHD base  0xf3ffc000 IOMMU 2
[    1.635306] DMAR-IR: IOAPIC id 2 under DRHD base  0xf3ffc000 IOMMU 2
[    2.827995] iommu: Default domain type: Translated 
[    2.827995] iommu: DMA domain TLB invalidation policy: lazy mode 
[    2.925321] DMAR: IOMMU feature sc_support inconsistent
[    2.925323] DMAR: IOMMU feature dev_iotlb_support inconsistent
[    2.925448] pci 0000:00:1b.0: Adding to iommu group 0
[    2.925895] pci 0000:ff:08.0: Adding to iommu group 1
[    2.925928] pci 0000:ff:08.2: Adding to iommu group 1
[    2.925963] pci 0000:ff:08.3: Adding to iommu group 2
[    2.926050] pci 0000:ff:09.0: Adding to iommu group 3
[    2.926082] pci 0000:ff:09.2: Adding to iommu group 3
[    2.926117] pci 0000:ff:09.3: Adding to iommu group 4
[    2.926256] pci 0000:ff:0b.0: Adding to iommu group 5
[    2.926291] pci 0000:ff:0b.1: Adding to iommu group 5
[    2.926324] pci 0000:ff:0b.2: Adding to iommu group 5
[    2.926357] pci 0000:ff:0b.3: Adding to iommu group 5
[    2.926603] pci 0000:ff:0c.0: Adding to iommu group 6
[    2.926637] pci 0000:ff:0c.1: Adding to iommu group 6
[    2.926670] pci 0000:ff:0c.2: Adding to iommu group 6
[    2.926704] pci 0000:ff:0c.3: Adding to iommu group 6
[    2.926741] pci 0000:ff:0c.4: Adding to iommu group 6
[    2.926775] pci 0000:ff:0c.5: Adding to iommu group 6
[    2.926808] pci 0000:ff:0c.6: Adding to iommu group 6
[    2.926841] pci 0000:ff:0c.7: Adding to iommu group 6
[    2.927034] pci 0000:ff:0d.0: Adding to iommu group 7
[    2.927071] pci 0000:ff:0d.1: Adding to iommu group 7
[    2.927105] pci 0000:ff:0d.2: Adding to iommu group 7
[    2.927142] pci 0000:ff:0d.3: Adding to iommu group 7
[    2.927176] pci 0000:ff:0d.4: Adding to iommu group 7
[    2.927210] pci 0000:ff:0d.5: Adding to iommu group 7
[    2.927430] pci 0000:ff:0f.0: Adding to iommu group 8
[    2.927465] pci 0000:ff:0f.1: Adding to iommu group 8
[    2.927501] pci 0000:ff:0f.2: Adding to iommu group 8
[    2.927535] pci 0000:ff:0f.3: Adding to iommu group 8
[    2.927572] pci 0000:ff:0f.4: Adding to iommu group 8
[    2.927607] pci 0000:ff:0f.5: Adding to iommu group 8
[    2.927643] pci 0000:ff:0f.6: Adding to iommu group 8
[    2.927811] pci 0000:ff:10.0: Adding to iommu group 9
[    2.927847] pci 0000:ff:10.1: Adding to iommu group 9
[    2.927883] pci 0000:ff:10.5: Adding to iommu group 9
[    2.927919] pci 0000:ff:10.6: Adding to iommu group 9
[    2.927957] pci 0000:ff:10.7: Adding to iommu group 9
[    2.928096] pci 0000:ff:12.0: Adding to iommu group 10
[    2.928133] pci 0000:ff:12.1: Adding to iommu group 10
[    2.928170] pci 0000:ff:12.4: Adding to iommu group 10
[    2.928206] pci 0000:ff:12.5: Adding to iommu group 10
[    2.928240] pci 0000:ff:13.0: Adding to iommu group 11
[    2.928276] pci 0000:ff:13.1: Adding to iommu group 12
[    2.928310] pci 0000:ff:13.2: Adding to iommu group 13
[    2.928344] pci 0000:ff:13.3: Adding to iommu group 14
[    2.928431] pci 0000:ff:13.6: Adding to iommu group 15
[    2.928471] pci 0000:ff:13.7: Adding to iommu group 15
[    2.928514] pci 0000:ff:14.0: Adding to iommu group 16
[    2.928548] pci 0000:ff:14.1: Adding to iommu group 17
[    2.928582] pci 0000:ff:14.2: Adding to iommu group 18
[    2.928620] pci 0000:ff:14.3: Adding to iommu group 19
[    2.928768] pci 0000:ff:14.4: Adding to iommu group 20
[    2.928807] pci 0000:ff:14.5: Adding to iommu group 20
[    2.928846] pci 0000:ff:14.6: Adding to iommu group 20
[    2.928884] pci 0000:ff:14.7: Adding to iommu group 20
[    2.928917] pci 0000:ff:16.0: Adding to iommu group 21
[    2.928952] pci 0000:ff:16.1: Adding to iommu group 22
[    2.928985] pci 0000:ff:16.2: Adding to iommu group 23
[    2.929019] pci 0000:ff:16.3: Adding to iommu group 24
[    2.929105] pci 0000:ff:16.6: Adding to iommu group 25
[    2.929146] pci 0000:ff:16.7: Adding to iommu group 25
[    2.929179] pci 0000:ff:17.0: Adding to iommu group 26
[    2.929214] pci 0000:ff:17.1: Adding to iommu group 27
[    2.929247] pci 0000:ff:17.2: Adding to iommu group 28
[    2.929286] pci 0000:ff:17.3: Adding to iommu group 29
[    2.929426] pci 0000:ff:17.4: Adding to iommu group 30
[    2.929467] pci 0000:ff:17.5: Adding to iommu group 30
[    2.929507] pci 0000:ff:17.6: Adding to iommu group 30
[    2.929547] pci 0000:ff:17.7: Adding to iommu group 30
[    2.929712] pci 0000:ff:1e.0: Adding to iommu group 31
[    2.929755] pci 0000:ff:1e.1: Adding to iommu group 31
[    2.929795] pci 0000:ff:1e.2: Adding to iommu group 31
[    2.929836] pci 0000:ff:1e.3: Adding to iommu group 31
[    2.929877] pci 0000:ff:1e.4: Adding to iommu group 31
[    2.929962] pci 0000:ff:1f.0: Adding to iommu group 32
[    2.930004] pci 0000:ff:1f.2: Adding to iommu group 32
[    2.930092] pci 0000:df:08.0: Adding to iommu group 33
[    2.930133] pci 0000:df:08.2: Adding to iommu group 33
[    2.930166] pci 0000:df:08.3: Adding to iommu group 34
[    2.930252] pci 0000:df:09.0: Adding to iommu group 35
[    2.930294] pci 0000:df:09.2: Adding to iommu group 35
[    2.930329] pci 0000:df:09.3: Adding to iommu group 36
[    2.930468] pci 0000:df:0b.0: Adding to iommu group 37
[    2.930510] pci 0000:df:0b.1: Adding to iommu group 37
[    2.930559] pci 0000:df:0b.2: Adding to iommu group 37
[    2.930601] pci 0000:df:0b.3: Adding to iommu group 37
[    2.930847] pci 0000:df:0c.0: Adding to iommu group 38
[    2.930891] pci 0000:df:0c.1: Adding to iommu group 38
[    2.930934] pci 0000:df:0c.2: Adding to iommu group 38
[    2.930978] pci 0000:df:0c.3: Adding to iommu group 38
[    2.931021] pci 0000:df:0c.4: Adding to iommu group 38
[    2.931063] pci 0000:df:0c.5: Adding to iommu group 38
[    2.931106] pci 0000:df:0c.6: Adding to iommu group 38
[    2.931149] pci 0000:df:0c.7: Adding to iommu group 38
[    2.931343] pci 0000:df:0d.0: Adding to iommu group 39
[    2.931388] pci 0000:df:0d.1: Adding to iommu group 39
[    2.931432] pci 0000:df:0d.2: Adding to iommu group 39
[    2.931476] pci 0000:df:0d.3: Adding to iommu group 39
[    2.931520] pci 0000:df:0d.4: Adding to iommu group 39
[    2.931564] pci 0000:df:0d.5: Adding to iommu group 39
[    2.931783] pci 0000:df:0f.0: Adding to iommu group 40
[    2.931832] pci 0000:df:0f.1: Adding to iommu group 40
[    2.931877] pci 0000:df:0f.2: Adding to iommu group 40
[    2.931921] pci 0000:df:0f.3: Adding to iommu group 40
[    2.931968] pci 0000:df:0f.4: Adding to iommu group 40
[    2.932013] pci 0000:df:0f.5: Adding to iommu group 40
[    2.932057] pci 0000:df:0f.6: Adding to iommu group 40
[    2.932223] pci 0000:df:10.0: Adding to iommu group 41
[    2.932270] pci 0000:df:10.1: Adding to iommu group 41
[    2.932316] pci 0000:df:10.5: Adding to iommu group 41
[    2.932362] pci 0000:df:10.6: Adding to iommu group 41
[    2.932408] pci 0000:df:10.7: Adding to iommu group 41
[    2.932555] pci 0000:df:12.0: Adding to iommu group 42
[    2.932602] pci 0000:df:12.1: Adding to iommu group 42
[    2.932649] pci 0000:df:12.4: Adding to iommu group 42
[    2.932698] pci 0000:df:12.5: Adding to iommu group 42
[    2.932731] pci 0000:df:13.0: Adding to iommu group 43
[    2.932764] pci 0000:df:13.1: Adding to iommu group 44
[    2.932798] pci 0000:df:13.2: Adding to iommu group 45
[    2.932832] pci 0000:df:13.3: Adding to iommu group 46
[    2.932918] pci 0000:df:13.6: Adding to iommu group 47
[    2.932966] pci 0000:df:13.7: Adding to iommu group 47
[    2.932999] pci 0000:df:14.0: Adding to iommu group 48
[    2.933032] pci 0000:df:14.1: Adding to iommu group 49
[    2.933066] pci 0000:df:14.2: Adding to iommu group 50
[    2.933102] pci 0000:df:14.3: Adding to iommu group 51
[    2.933241] pci 0000:df:14.4: Adding to iommu group 52
[    2.933290] pci 0000:df:14.5: Adding to iommu group 52
[    2.933338] pci 0000:df:14.6: Adding to iommu group 52
[    2.933389] pci 0000:df:14.7: Adding to iommu group 52
[    2.933422] pci 0000:df:16.0: Adding to iommu group 53
[    2.933455] pci 0000:df:16.1: Adding to iommu group 54
[    2.933488] pci 0000:df:16.2: Adding to iommu group 55
[    2.933522] pci 0000:df:16.3: Adding to iommu group 56
[    2.933608] pci 0000:df:16.6: Adding to iommu group 57
[    2.933658] pci 0000:df:16.7: Adding to iommu group 57
[    2.933691] pci 0000:df:17.0: Adding to iommu group 58
[    2.933724] pci 0000:df:17.1: Adding to iommu group 59
[    2.933758] pci 0000:df:17.2: Adding to iommu group 60
[    2.933792] pci 0000:df:17.3: Adding to iommu group 61
[    2.933931] pci 0000:df:17.4: Adding to iommu group 62
[    2.933982] pci 0000:df:17.5: Adding to iommu group 62
[    2.934032] pci 0000:df:17.6: Adding to iommu group 62
[    2.934084] pci 0000:df:17.7: Adding to iommu group 62
[    2.934250] pci 0000:df:1e.0: Adding to iommu group 63
[    2.934301] pci 0000:df:1e.1: Adding to iommu group 63
[    2.934353] pci 0000:df:1e.2: Adding to iommu group 63
[    2.934404] pci 0000:df:1e.3: Adding to iommu group 63
[    2.934455] pci 0000:df:1e.4: Adding to iommu group 63
[    2.934541] pci 0000:df:1f.0: Adding to iommu group 64
[    2.934593] pci 0000:df:1f.2: Adding to iommu group 64
[    2.934626] pci 0000:00:00.0: Adding to iommu group 65
[    2.934659] pci 0000:00:01.0: Adding to iommu group 66
[    2.934692] pci 0000:00:02.0: Adding to iommu group 67
[    2.934728] pci 0000:00:03.0: Adding to iommu group 68
[    2.934761] pci 0000:00:05.0: Adding to iommu group 69
[    2.934793] pci 0000:00:05.1: Adding to iommu group 70
[    2.934826] pci 0000:00:05.2: Adding to iommu group 71
[    2.934861] pci 0000:00:05.4: Adding to iommu group 72
[    2.934893] pci 0000:00:11.0: Adding to iommu group 73
[    2.934955] pci 0000:00:11.4: Adding to iommu group 74
[    2.934988] pci 0000:00:14.0: Adding to iommu group 75
[    2.935100] pci 0000:00:16.0: Adding to iommu group 76
[    2.935153] pci 0000:00:16.2: Adding to iommu group 76
[    2.935207] pci 0000:00:16.3: Adding to iommu group 76
[    2.935240] pci 0000:00:19.0: Adding to iommu group 77
[    2.935273] pci 0000:00:1a.0: Adding to iommu group 78
[    2.935307] pci 0000:00:1c.0: Adding to iommu group 79
[    2.935341] pci 0000:00:1c.4: Adding to iommu group 80
[    2.935375] pci 0000:00:1d.0: Adding to iommu group 81
[    2.935486] pci 0000:00:1f.0: Adding to iommu group 82
[    2.935542] pci 0000:00:1f.2: Adding to iommu group 82
[    2.935597] pci 0000:00:1f.3: Adding to iommu group 82
[    2.935636] pci 0000:01:00.0: Adding to iommu group 83
[    2.935670] pci 0000:02:01.0: Adding to iommu group 84
[    2.935704] pci 0000:02:02.0: Adding to iommu group 85
[    2.935740] pci 0000:02:08.0: Adding to iommu group 86
[    2.935775] pci 0000:02:09.0: Adding to iommu group 87
[    2.935809] pci 0000:02:0a.0: Adding to iommu group 88
[    2.935844] pci 0000:03:00.0: Adding to iommu group 89
[    2.935881] pci 0000:04:00.0: Adding to iommu group 90
[    2.935916] pci 0000:06:00.0: Adding to iommu group 91
[    2.935952] pci 0000:07:00.0: Adding to iommu group 92
[    2.936038] pci 0000:08:00.0: Adding to iommu group 93
[    2.936095] pci 0000:08:00.1: Adding to iommu group 93
[    2.936129] pci 0000:09:00.0: Adding to iommu group 94
[    2.936166] pci 0000:0a:08.0: Adding to iommu group 95
[    2.936199] pci 0000:0a:10.0: Adding to iommu group 96
[    2.936240] pci 0000:0b:00.0: Adding to iommu group 97
[    2.936275] pci 0000:0c:00.0: Adding to iommu group 98
[    2.936362] pci 0000:0e:00.0: Adding to iommu group 99
[    2.936419] pci 0000:0e:00.1: Adding to iommu group 99
[    2.936452] pci 0000:e0:05.0: Adding to iommu group 100
[    2.936495] pci 0000:e0:05.1: Adding to iommu group 101
[    2.936528] pci 0000:e0:05.2: Adding to iommu group 102
[    2.936561] pci 0000:e0:05.4: Adding to iommu group 103
[    6.955179] AMD-Vi: AMD IOMMUv2 functionality not available on this system - This is not a bug.

```

The last line should not have impact on my system.

However :

```
lspci -nnk | grep -A 3 -Ei 'VGA|DISPLAY' 
08:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK110GL [Quadro K6000] [10de:103a] (rev a1)
    Subsystem: NVIDIA Corporation GK110GL [Quadro K6000] [10de:1036]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
--
0e:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Lexa XT [Radeon PRO WX 3100] [[COLOR=#ff0000]1002:6985[/COLOR]]
    Subsystem: Dell Lexa XT [Radeon PRO WX 3100] [1028:0b0c]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

```

The reserved AMD graphic card did not get the vfio-pci driver as expected.

---

### Post by tryphon2 on 2023-09-23
[COLOR=#008000]Ignore[/COLOR]

---

### Post by MAFoElffen on 2023-09-24
Can you show me the contents of your /etc/modprobe.d/vfio.conf file?

For example, my old one was:
```

# File /etc/modprobe.d/vfio.conf
# Pass Through the iGPU and sr-iov NIC
# driver used
#
blacklist i915
blacklist igbvf
# where it is located
#vfio-pci.ids=8086:a780,10b5:8748
options vfio-pci ids=8086:a780,10b5:8748

```
 << I do both those differently now, but for vfio-pci, that is an example of how you do that. That is how they were removed from the host and the vfio-pci drivers added to them. >>

Once I did that, and did
```

sudo update-initramfs -c -k all
reboot

```
Then in lshw, the drivers for those two devices would show up as 'vfio-pci'... Just saying. There is a bit more to it than you posted.

---

### Post by tryphon2 on 2023-09-25
The file /etc/modprobe.d/vfio.conf does not exist on my system (I did not check if it existed the case before my issue).

Also I tried this :

```

sudo su
sudo echo "vfio-pci" >>/etc/initramfs-tools/modules
exit
sudo update-initramfs -u -k $(uname -r)
sudo update-grub
reboot

```

vfio-pci came alive for the passthrough graphic card.

However the hdmi audio part is often missing :
```
virsh nodedev-dumpxml pci_0000_0e_00_1
```
returns:
```
error: Could not find matching device 'pci_0000_0e_00_1'
error: Node device not found: no node device with matching name 'pci_0000_0e_00_1'
```

I will try your suggestion ...

---

### Post by MAFoElffen on 2023-09-26
I had to create my /etc/modprobe.d/vfio.conf file from scratch. Look at the content s of while I explain this...

What you do in that file is to blacklist the driver that usually loads as a driver for that device, so it it goes unclaimed by the system. Then tell vfio-pci to load to the pciid. You can find both in the output of lspci, using grep filter similar to what I used in Post #9.

As an example, to hopefully answer you new issue on audio, changing that filter to 'Audio'
```

mafoelffen@msi-ubuntu:~$ sudo lspci -nnk | grep -A 3 -Ei 'Audio'
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:7a50] (rev 11)
    DeviceName: Onboard - Sound
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7d91]
    Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: NVIDIA Corporation TU116 High Definition Audio Controller [10de:1aeb] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] TU116 High Definition Audio Controller [1462:375a]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```
And looking at that output, then lines to do it for Audio would would be
```

blacklist snd_hda_intel
# For the NVIDIA TU116 device there
options vfio-pci ids=1462:375a

```
Then after updating the initramfs image and rebooting, then that device would be using the vfio-pci driver...

BUT-- Notice this while doing a reverse lookup, by using the proposed blacklisted module 'snd_hda_intel' as the filter on that...
```

mafoelffen@msi-ubuntu:~$ sudo lspci -nnk | grep -B 3 -Ei 'snd_hda_intel'
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:7a50] (rev 11)
    DeviceName: Onboard - Sound
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7d91]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
--
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation TU116 High Definition Audio Controller [10de:1aeb] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] TU116 High Definition Audio Controller [1462:375a]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```
Do you understand what that means? It means that if I blacklist module 'snd_hda_intel' there is more than that one Audio device present that uses that driver (the onboard Intel sound controller) and blacklisting that module is going to break that on the Host... Because the module would not be loading to that device (blacklisted) and that device would change to unclaimed.

That is something you have to watch out for. Or at least understand that other things may be affected by that.

---

### Post by tryphon2 on 2023-09-26
Thank you MAFoElffen. I am now able to start again my Windows VM with my dedicated Radeon graphic card. It makes sense that without blacklisting some devices may be claimed by the host before they are associated with the vfio-pci driver. For the audio device, this situation was intermittent and was confusing me.

My Ubuntu 22.04 system came from updated 20.04 one. Does it explain why I got this apparent broken IOMMU ?

I will report the stability of the passthrough mechanism after some days using the VM.

Thank you for this great help.

---

### Post by MAFoElffen on 2023-09-26
You are welcome. Glad that is is working for you now.

On do-release-upgrade... Yes. It might have replaced the modules folder during the release upgrade. It usually leaves User conf files, but those are usually in common places. LOL. We are doing advanced things beyond what is usually "Normal". So things might break during that.

If you work out the audio, please update this so that the thread is updated.

If after a few days, it passes your Litmus Shakedown Test, and is resolve to your satisfaction, then visit the "Thread Tools" link in the upper right of this thread and mark the thread as "Solved". That way others can see what worked for you, to solve their own similar issues.

---

### Post by tryphon2 on 2023-10-02
The issue is circumscribed but resistant.
```
0e:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Lexa XT [Radeon PRO WX 3100] [1002:6985] (rev ff)
    Kernel driver in use: [COLOR=#b22222]vfio-pci[/COLOR]
    Kernel modules: amdgpu
0e:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X] [1002:aae0] (rev ff)
    Kernel driver in use: [COLOR=#b22222]vfio-pci[/COLOR]
    Kernel modules: snd_hda_intel

```
and /etc/modprobe.d/vfio.conf
```
blacklist amdgpu
# Give vfio driver for the Radeon WX 3100 hardware
options vfio-pci ids=1002:6985,1002:aae0

```
but :

```
virsh nodedev-dumpxml pci_0000_0e_00_1
error: Could not find matching device 'pci_0000_0e_00_1'
error: Node device not found: no node device with matching name 'pci_0000_0e_00_1'
```

When the amd audio device is not passed, the passthrough mechanism is not working . In fact the AMD audio device usually uses the snd_hda_intel driver that is also used by a nVidia graphic card and an integrated audio chip on the motherboard. I presume I cannot blacklist this driver.

Inextricable situation ?

---

### Post by MAFoElffen on 2023-10-06
Like I said with mine. I can't pass-through the audio, because mine also uses driver snd_hda-intel for both my Intel iGPU and my NVidia GPU... Just because if I blacklist, it then I lose audio for the main active GPU on the host.

It's not a problem for me, because I just use the virtio audio. I still get sound on the VM that way. I just do that because "I can."

Most my gaming is native, because I dual boot. No lag. No video or audio problems.

---

