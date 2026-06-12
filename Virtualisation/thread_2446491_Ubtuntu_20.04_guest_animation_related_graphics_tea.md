---
title: "Ubtuntu 20.04 guest animation related graphics tearing"
date: 2020-07-01
forum: Virtualisation
---

### Post by jordandev on 2020-07-01
Hey everyone, having weird graphics tearing issues with animations on 20.04. The applications menu is particularly affected with very visible tearing during the animations.
Actually, it's pretty much the same issue described [here]("https://forums.virtualbox.org/viewtopic.php?f=3&t=98233") (including [video]("https://youtu.be/kh0z48qNIDA?t=37")) so I'm not the only person with the issue. I'm posting it here because using the Wayland session the animations work and with the default X11 they don't so it's potentially a configuration issue rather than a VirtualBox issue?

Setup
host: Windows 10 (16GB ram, AMD Radeon R9 GPU, VirtualBox 3d acceleration enabled)
guest: Fresh Ubuntu 20.04 LTS install, updated to be current as of today (4GB ram, 4vCPUs)
Virtualbox: 6.0.22 (check for updates reports nothing)
Guest additions: 6.0.22 from CD image; also tested version in apt both show the issue

Other info:
```
ordan@vm:~$ uname -a
Linux vm 5.4.0-39-generic #43-Ubuntu SMP Fri Jun 19 10:28:31 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
jordan@vm:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: VMware SVGA II Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
ordan@vm:~$ dmesg | grep drm
[    7.132323] systemd[1]: Starting Load Kernel Module drm...
[    7.636205] systemd[1]: modprobe@drm.service: Succeeded.
[    7.636585] systemd[1]: Finished Load Kernel Module drm.
[    8.422524] [drm] DMA map mode: Caching DMA mappings.
[    8.422579] [drm] Capabilities:
[    8.422579] [drm]   Cursor.
[    8.422580] [drm]   Cursor bypass 2.
[    8.422580] [drm]   Alpha cursor.
[    8.422581] [drm]   3D.
[    8.422581] [drm]   Extended Fifo.
[    8.422581] [drm]   Pitchlock.
[    8.422582] [drm]   Irq mask.
[    8.422582] [drm]   GMR.
[    8.422582] [drm]   Traces.
[    8.422583] [drm]   GMR2.
[    8.422583] [drm]   Screen Object 2.
[    8.422584] [drm] Max GMR ids is 8192
[    8.422585] [drm] Max number of GMR pages is 1048576
[    8.422585] [drm] Max dedicated hypervisor surface memory is 491520 kiB
[    8.422586] [drm] Maximum display memory size is 32768 kiB
[    8.422587] [drm] VRAM at 0xf0000000 size is 32768 kiB
[    8.422587] [drm] MMIO at 0xf2000000 size is 2048 kiB
[    8.423031] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    8.423032] [drm] No driver support for vblank timestamp query.
[    8.423343] [drm] Screen Objects Display Unit initialized
[    8.423525] [drm] width 720
[    8.423541] [drm] height 400
[    8.423558] [drm] bpp 32
[    8.424049] [drm] Fifo max 0x00200000 min 0x00001000 cap 0x00000355
[    8.424060] [drm] DX: no.
[    8.424060] [drm] Atomic: yes.
[    8.424061] [drm] SM4_1: no.
[    8.424078] [drm:vmw_host_log [vmwgfx]] *ERROR* Failed to send host log message.
[    8.425765] [drm:vmw_host_log [vmwgfx]] *ERROR* Failed to send host log message.
[    8.431103] fbcon: svgadrmfb (fb0) is primary device
[    8.435100] [drm] Initialized vmwgfx 2.15.0 20180704 for 0000:00:02.0 on minor 0


```

I've tried varying amounts of GPU memory assigned in VirtualBox from the default to max with no noticeable difference.
Any suggestions for further debugging this?

---

### Post by &amp;KyT$0P# on 2020-07-01
> **jordandev said:**
> VirtualBox 3d acceleration enabled

Does disabling this make any difference?

> guest: ... 4vCPUs

Does your host have at least 8 *physical* CPU cores?

---

### Post by jordandev on 2020-07-01
Disabling 3d acceleration more works around the problem than fixes it in that they just appear in the menu there's no animation. I'm assuming there's an intelligent "only animate with acceleration" switch that's on somewhere.

There's 4 physical cores but the host is completely idle. Lowering or increasing the vCPU count has no affect on the issue.

---

### Post by jordandev on 2020-07-08
Any additional suggestions for debugging this further?

---

### Post by lammert-nijhof on 2020-08-05
You have exactly the same settings as I have, only I always use 128 MB as video memory in 3D mode. I only use the X session. The other difference is the Host. My Host is Ubuntu 20.04 on a Ryzen 3 2200G.

---

