---
title: "amd64bit displays weird  user name"
date: 2013-03-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-04
Just did an install of the daily build on:

```

ventrical@ventrical-System-Product-Name:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
ventrical@ventrical-System-Product-Name:~$ 


```

and got that funny product name. Does that mean Ubuntu now owns me !? :) lol

---

### Post by cariboo on 2013-03-04
Did you file a bug report?

I can't understand why people leave the default host name, when doing an install, changing the host name to reflect what the install is, is a great way to differentiate between installs, when you have multiples, or even to tell you what system you are using, and it usually takes up a lot less room on the command line. :-D We lobbied hard to have this ability, and it's kind of disappointing to see people don't use it.

---

### Post by ventrical on 2013-03-05
> **cariboo907 said:**
> Did you file a bug report?

I can't understand why people leave the default host name, when doing an install, changing the host name to reflect what the install is, is a great way to differentiate between installs, when you have multiples, or even to tell you what system you are using, and it usually takes up a lot less room on the command line. :-D We lobbied hard to have this ability, and it's kind of disappointing to see people don't use it.


This is a *new* one for me. First time I ever saw it. (There are a lot of firsts these days). Usually during install it gets the Mobo information from BIOS and assigns that name and code, which is perfectly ok for me and how I differentiate between computers. This time , however, it seems that  this option was not available so I really do not follow your thread.


ahhh... nevertheless.. I will file a bug on this.

Thanks for your help.

---

### Post by ventrical on 2013-03-05
I filed the bug against Ubiquity but it is reported that 'ubiquity is not installed' so am I to assume that I have to file this bug from the live USB?

---

### Post by ventrical on 2013-03-05
SOLVED

Easier fix is to just edit the hosts and hostnames files.

ventrical@ventrical-Mir-WaylandStation:~$

---

