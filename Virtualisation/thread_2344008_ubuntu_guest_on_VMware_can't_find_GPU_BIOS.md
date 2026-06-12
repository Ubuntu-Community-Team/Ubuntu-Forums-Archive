---
title: "ubuntu guest on VMware: can't find GPU BIOS"
date: 2016-11-21
forum: Virtualisation
---

### Post by patpro on 2016-11-21
Hi,

I've got a multi-OS workstation running ESXi 5.5 for now, 6.x soon. On top I'm running an OSX VM and a Windows VM, with GPU passthrough. Everything works great. But when I try to run a Ubuntu VM (guest) on top of ESXi, with GPU passthrough, it fails using the GPU (a MSI Radeon R9 270X GAMING 2G).

I've tried Ubuntu 14.x LTS, and 16.x LTS. I've tried BIOS and EFI. Everything ends with the same non-functioning GPU. 
I've also read this thread [https://ubuntuforums.org/showthread.php?t=2235405](https://ubuntuforums.org/showthread.php?t=2235405) , but no luck. It's not clear to me whether I need to path my kernel, or not (and that's not something I'm comfortable with).
I've tried to put BIOS files from [www.techpowerup.com]("http://www.techpowerup.com") into /lib/firmware/radeon, but it did not help.

dmesg shows those lines:

```
[   26.286898] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:16.0/0000:0b:00.1/sound/card0/input11
[   26.286964] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:16.0/0000:0b:00.1/sound/card0/input12
[   26.590602] [drm] radeon kernel modesetting enabled.
[   26.592270] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[   26.592272] AMD IOMMUv2 functionality not available on this system
```

and

```
[   26.643816] Finished initializing topology ret=0
[   26.643854] kfd kfd: Initialized module
[   26.644113] radeon 0000:0b:00.0: enabling device (0000 -> 0003)
[   26.645177] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6810 0x1462:0x3030).
[   26.645192] [drm] register mmio base: 0xFD380000
[   26.645193] [drm] register mmio size: 262144
[   26.645201] radeon 0000:0b:00.0: BAR 6: can't assign [??? 0x00000000 flags 0x20000000] (bogus alignment)
[   26.645216] radeon 0000:0b:00.0: BAR 6: can't assign [??? 0x00000000 flags 0x20000000] (bogus alignment)
[   26.645246] [drm:radeon_get_bios [radeon]] *ERROR* Unable to locate a BIOS ROM
[   26.645270] radeon 0000:0b:00.0: Fatal error during GPU init
[   26.645286] [drm] radeon: finishing device.
[   26.645287] [TTM] Memory type 2 has not been initialized
[   26.685269] radeon: probe of 0000:0b:00.0 failed with error -22
```

lspci -v shows this:

```
0b:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT [Radeon R7 370 / R9 270X/370 OEM] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3030
    Physical Slot: 192
    Flags: fast devsel, IRQ 19
    Memory at <ignored> (64-bit, prefetchable)
    Memory at d3700000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 4000 [size=256]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [200] #15
    Capabilities: [270] #19
    Capabilities: [2b0] Address Translation Service (ATS)
    Capabilities: [2c0] #13
    Capabilities: [2d0] #1b

0b:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device aab0
    Physical Slot: 192
    Flags: bus master, fast devsel, latency 64, IRQ 73
    Memory at d3740000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: snd_hda_intel

```

Any help would be greatly appreciated!

---

### Post by virtmm on 2016-11-22
I also have this same problem on ESXi 6.  I also have tried various  versions of Ubuntu with no luck.  I tried setting up and modifying  appropriate *.conf file in /usr/share/X11/xorg.conf.d, also without any luck.  I of course have the:

```
[drm:radeon_get_bios [radeon]] *ERROR* Unable to locate a BIOS ROM

```
After setting up a 20-radeon.conf file I get:

```
Screen 1 deleted because of no matching config section
```

I have seen a lot of posts over the last several years from people having this issue.  So far the only "solution" I have seen is the same one you reference regarding patching the kernel radeon driver to get the settings from a file instead of reading the video BIOS.  Unfortunately, I don't have experience doing that and I don't know if the code is still valid, or how to patch the kernel.  If I can figure out how to do it, it will be worth a try.  Figuring out how to patch the kernel is my next project.

---

### Post by patpro on 2016-11-25
Damn, looks like nobody but us cares about this problem&#8230; thanks for your reply. I'll post here if I found something.

---

### Post by virtmm on 2016-11-26
It looks like this issue has been around for a number of years so I am not real hopeful of a fix.  One thing I realized is that my MB defaulted to CMS/legacy BIOS only (not UEFI) and my ESXi install was under that condition.  While I tried the BIOS/EFI boot option in ESXi with no impact, that was still with ESXi installed and running under BIOS at the system level.  This may not matter (it is not supposed to matter).  But since the issue is that the Linux VM is not seeing the vidio BIOS, it is possible that ESXi is not seeing it either winch could be why it is not passing it along.  I have since changed the MB/system BIOS to UEFI but I need to re-install ESXI under that condition.  I am not particularly hopeful, but worth a try.

If I figure out a fix, I will post back here too.  

I am also now looking at KVM on top of Ubuntu.

---

### Post by patpro on 2016-11-26
Not sure the problem is here (BIOS vs EFI), I've found posts that suggest something changed around Ubuntu 13.10 release and that GPU passthrough was working before that.
And it looks like no guest OS can reach the graphics card BIOS. I've tried to extract the BIOS of my MSI card from inside my Windows VM, and while the utility (GPU-Z) provided hardware info for the card, it was unable to access its BIOS.

---

### Post by virtmm on 2016-11-27
Yes, I have been unsuccessful with the UFEI route.  Switched my BIOS to UEFI, re-installed ESXi etc, Ubuntu VM still can't read the video BIOS so I can't get the radeon driver to install.

I even tried the new ESXI 6.5.  A note here.  If you need to passthrough AMD GPU of the R9 270x, HD7950, R9 280x vintage to a windows machine, DO NOT switch to ESXi 6.5.  Vmware has removed those cards as supported for passthrough.  You can't even select them (they are greyed out) at the host level, to make them available for passthrough anymore. Unless you want to cook your own drivers and add them back in they are no longer supported for passthrough starting with ESXi 6.5.  I should qualify this that it is at least true using the ESXi 6.5 included web client.  I did not try using vCenter, but I suspect it would make no difference.

---

### Post by patpro on 2016-12-04
ESXi 6.5 is a very bad news then :/
I'm still running 5.5 for now, and plan to switch to 6.0 soon.

I've worked on the custom kernel solution, but it did not work as expected. Following steps from [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) I've been able to create a custom kernel including the patch from [https://lists.freedesktop.org/archives/dri-devel/2014-November/072701.html](https://lists.freedesktop.org/archives/dri-devel/2014-November/072701.html)
Now at boot time I see: 

```
# dmesg | egrep -i 'pitcairn|radeon|verde|curacao'
[    2.924346] [drm] radeon kernel modesetting enabled.
[    2.926908] radeon 0000:0b:00.0: enabling device (0000 -> 0003)
[    2.927582] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6810 0x1462:0x3030).
[    2.927618] radeon 0000:0b:00.0: BAR 6: can't assign [??? 0x00000000 flags 0x20000000] (bogus alignment)
[    2.927629] radeon 0000:0b:00.0: BAR 6: can't assign [??? 0x00000000 flags 0x20000000] (bogus alignment)
[    2.927639] radeon 0000:0b:00.0: Direct firmware load for radeon/vbios.bin failed with error -2
[    2.927665] [drm:radeon_get_bios [radeon]] *ERROR* firmware request returned NULL
[    2.927682] [drm:radeon_get_bios [radeon]] *ERROR* Unable to locate a BIOS ROM
[    2.927684] radeon 0000:0b:00.0: Fatal error during GPU init
[    2.927686] [drm] radeon: finishing device.
[    2.935612] radeon: probe of 0000:0b:00.0 failed with error -22
```

The line "radeon 0000:0b:00.0: Direct firmware load for radeon/vbios.bin failed with error -2" proves that the patch is effective (added code is executed), but unfortunately it fails loading the BIOS from the file. I have absolutely no clue why it fails. May be the BIOS file is not good, may be the code needs to be fixed for current kernel…

```
# file /lib/firmware/radeon/vbios.bin 
/lib/firmware/radeon/vbios.bin: BIOS (ia32) ROM Ext. IBM comp. Video (128*512)
```

I've tried 2 different BIOS files, from [www.techpowerup.com]("http://www.techpowerup.com") without luck. I would probably need to boot the box from windows instead of ESXi to be able to dump the BIOS from the graphics card, unless someone knows how to do this from ESXi.

Any idea is welcome.

---

### Post by patpro on 2016-12-14
Ok, latest news:

I've tried :
- CentOS 7
- OpenSuse 42
- elementaryos 0.4

They all failed me when I attempted to install fglrx drivers for the same reason: no longer supported / get lost / use crapy opensource radeon driver.

After more research I've been able to install ubuntu-15.04-desktop-amd64 and to add fglrx drivers.

BUT.

even if I don't get the BIOS error ([drm:radeon_get_bios [radeon]] *ERROR* Unable to locate a BIOS ROM), the Xorg config is broken, and I can't log into GUI. I don't have a proof that my setup is working, as the display pluged in to the radeon graphics card stays black. But lspci and dmesg let me think I'm on the way to make it work.

Nevertheless I'm not so confident about this issue: a story that starts with a non-upgradable linux release can't end well. 
I see only 2 happy ending here: either fglrx comes back with full support from AMD and the Linux/Xorg community, or the opensource radeon driver supports BIOS-as-a-file (you dump your graphics card BIOS into a file that can be loaded by the kernel or the driver).

---

