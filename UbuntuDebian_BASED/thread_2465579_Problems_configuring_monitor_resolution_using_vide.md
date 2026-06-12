---
title: "Problems configuring monitor resolution using video splitter"
date: 2021-08-05
forum: Ubuntu/Debian BASED
---

### Post by ddvo on 2021-08-05
Hello,

I am facing problems to declare a specific video resolution using an video spiltter with following characteristics:

Brand: ATEN
Model: VS134A

Basically the problem is, when connect the video to the splitter I get only 1024x768 resolution and need 1920x1080. I already tried to change it using xrandr but received the error xrandr: configure crtc 0 failed.

Then I tried connecting the monitor directly to pc, although the auto resolution is 1920x1080, when I try to create, add and then select the new mode in the output using xrandr, I keep getting the failed crtc configuration error and resolution do not change.

We already have an script for resolution with some monitors made usig xandr command and is working.

I need to solve this issue for different brands PCs on VGA video output (working with HDMI splitters not experience this issue).

I already tried to force resolution in grub, with no results.

I am using a propietary OS based on Ubuntu, runnig a propietary application. 

**lsb_release:**
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.2 LTS
Release: 16.04
Codename: xenial

**lspci -v:**
00:02.0 VGA compatible controller: Intel Corporation Device 3e91 (prog-if 00 [VGA controller])
    DeviceName: Onboard - Video
    Subsystem: Hewlett-Packard Company Device 86e9
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at de000000 (64-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] #1b
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] #13

**lshw -c video:**
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)

**Grub:**

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR="Terabuntu 2.01"
GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="net.ifnames=0"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640X480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


GRUB_BACKGROUND="/etc/PinguyBuilder/grub.png"

[B]Xorg.0.log:
[/B][    15.444]    Module class: X.Org Video Driver
[    15.444]    ABI class: X.Org Video Driver, version 20.0
[    15.444] (II) LoadModule: "vesa"
[    15.445] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.445] (II) Module vesa: vendor="X.Org Foundation"
[    15.445]    compiled for 1.18.1, module version = 2.3.4
[    15.445]    Module class: X.Org Video Driver
[    15.445]    ABI class: X.Org Video Driver, version 20.0
[    15.445] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    15.445] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    15.445] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    15.445] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    15.445] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    15.445] (II) FBDEV: driver for framebuffer: fbdev
[    15.445] (II) VESA: driver for VESA chipsets: vesa
[    15.485] (EE) open /dev/dri/card0: No such file or directory
[    15.485] (WW) Falling back to old probe method for modesetting
[    15.485] (EE) open /dev/dri/card0: No such file or directory
[    15.485] (II) Loading sub module "fbdevhw"
[    15.485] (II) LoadModule: "fbdevhw"
[    15.485] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.485] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.485]    compiled for 1.18.4, module version = 0.0.2
[    15.485]    ABI class: X.Org Video Driver, version 20.0
[    15.485] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    15.485] (II) FBDEV(1): using default device
[    15.485] (WW) Falling back to old probe method for vesa
[    15.485] (EE) Screen 0 deleted because of no matching config section.
[    15.485] (II) UnloadModule: "modesetting"
[    15.485] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    15.485] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    15.485] (==) FBDEV(0): RGB weight 888
[    15.485] (==) FBDEV(0): Default visual is TrueColor
[    15.485] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.485] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[    15.485] (II) FBDEV(0): checking modes against framebuffer device...
[    15.485] (II) FBDEV(0): checking modes against monitor...
[    15.485] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    15.485] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    15.485] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104$
[    15.485] (==) FBDEV(0): DPI set to (96, 96)

Thanks in advance.

---

### Post by QIII on 2021-08-05
> I am using a propietary OS based on Ubuntu

Moved to **Ubuntu/Debian BASED**

---

### Post by tea for one on 2021-08-05
> **ddvo said:**
> 

I am using a propietary OS based on Ubuntu, runnig a propietary application. 

**lsb_release:**
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.2 LTS
Release: 16.04
Codename: xenial

GRUB_DISTRIBUTOR="Terabuntu 2.01"

Ubuntu 16.04 has reached end of life and is now unsupported.

What is Terabuntu 2.01?

If this is a proprietary OS with a proprietary application, then you should contact the supplier/developer?

---

### Post by ddvo on 2021-08-05
Thanks for the quick answer, I am part of the team for this vendor, I am just stuck on this right now and asking if any one have some idea to solve it. We know about Ubuntu is 16.04 is already unsupported, but this is and old installation present in some old clients, that are not able to migrate to the new OS version.

Thanks again

---

