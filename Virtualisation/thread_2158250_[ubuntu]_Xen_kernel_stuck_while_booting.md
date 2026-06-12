---
title: "[ubuntu] Xen kernel stuck while booting"
date: 2013-06-28
forum: Virtualisation
---

### Post by Twonky on 2013-06-28
Dear Xen experts,


I'm trying to get Ubuntu's Xen to work on my desktop, following [Ubuntu's Xen guide]("https://help.ubuntu.com/community/Xen"). Unfortunately, the Xen kernel hangs up while booting - -at different steps. It does not recognize Ctrl+Alt+Delete but requires the reset button to be used.

[B][U]Details
[/U][/B]
Installing the plain Ubuntu 12.04 worked well, installation of[FONT=courier new] xen-hypervisor-4.1-amd64[/FONT] which pulls Xen 4.1 was fine, grub and toolstack were changed as explained.

Console output ends at:
```
(XEN) HVM: ASIDs enabled.
(XEN) HVM: VMX enabled
(XEN) HVM: Hardware Assisted Paging detected.
(XEN) revised cpuid_level = 13
(XEN) revised cpuid_level = 13
(XEN) revised cpuid_level = 13
(XEN) revised cpuid_level = 13
```
Intriguing, since I would have assumed that this message, if repeated a few times, would be printed for each CPU core found, but there are six cores in this CPU. The message revised [FONT=courier new]cpuid_level = 13 [/FONT]can be removed if the BIOS setting "Limit CPUID Maximum".

Another time, it ends at:
```

(XEN) Xen version 4.1.2 (Ubuntu 4.1.2-2ubuntu2.10) [...]
(XEN) Bootloader: GRUB 1.99-21ubuntu3.9
(XEN) Command line: placeholder
[...]
(XEN) Disc information:
(XEN)  Found 0 MBR signatures
(XEN)  Found 0 EDD information structures
(XEN)
(XEN)
(XEN) Xen-e801 RAM map:
(XEN)  0000000000000000 - 000000000009e800 (usable)
(XEN)  0000000000100000 - 00000000dca00000 (usable)
```
The BIOS setting "CPU Intel Virtualization Technology" (VMM may utilize VT hardware capabilities) and "VT-d" are activated.

**_Hardware_**

[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]CPU[/TD]
[TD]Intel Core i7-3970X @ 3.50GHz[/TD]
[/TR]
[TR]
[TD]Mainboard[/TD]
[TD]ATI Rampage IV Extreme[/TD]
[/TR]
[TR]
[TD]Memory[/TD]
[TD]16 GByte DDR3-1600[/TD]
[/TR]
[TR]
[TD]BIOS[/TD]
[TD]Asus Rampage IV Extreme ACPI BIOS Revision 3602[/TD]
[/TR]
[TR]
[TD]Chipset[/TD]
[TD]Intel X79 Express[/TD]
[/TR]
[/TABLE]
[B][U]
Software[/U][/B]

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]Ubuntu[/TD]
[TD]12.04 server[/TD]
[TD]12.10 server[/TD]
[/TR]
[TR]
[TD]Kernel[/TD]
[TD]3.5.0-34[/TD]
[TD]3.5.0-34
[/TD]
[/TR]
[TR]
[TD]xen-hypervisor-amd64[/TD]
[TD]4.1.2-2ubuntu2.10[/TD]
[TD]4.1.3-3ubuntu1.7[/TD]
[/TR]
[/TABLE]

Can anybody give advice?

_**Update (Edit)**_

Upgraded to Ubuntu 12.10. Xen fails to boot but does no longer hang up at some recognizable step, but reboots after too many lines scrolling too fast. Thus, the problem still exists. Trying upgrade to 13.04.

_**Update (Edit)**_

Upgraded to Ubuntu 13.04 server, kernel 3.8.0-25, xen-hypervisor 4.2.1-0ubuntu3.3. **Works** (I guess). **Problem solved**.

---

### Post by heiko_s on 2013-06-28
Try booting into a regular kernel (non-Xen) and check the logs under /var/log/xen as well as /var/log/dmesg.0. In the latter see where exactly it hangs. What's your graphics card for dom0? And what's the driver for it?

---

