---
title: "Can't connect to the net!"
date: 2010-09-27
forum: Ubuntu Cloud and Juju
---

### Post by houshdaran on 2010-09-27
Hello.I cannot connect to the internet under ubuntu;under windows xp I can.and I could connect under ubuntu before
 
 
 
Please tell me what's getting wrong here?
 
I am connecting to the internet through a wireless network.
 
I suspect having a malware.What about you

---

### Post by Joe of loath on 2010-09-27
More info needed ;) What wifi chip are you using, has it worked before?

And it's almost certainly not malware, there's close to none for Linux :)

---

### Post by houshdaran on 2010-09-27
D-Link wireless Network adapter..........(not sure about the actual name but it is D-link wireless NIC)

---

### Post by Joe of loath on 2010-09-27
USB or PCI? If it's USB, post the output of lsusb, if it's PCI, post the output of lspci.

---

### Post by houshdaran on 2010-09-28
It's PCI

here is lspci output:

> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g


---

### Post by Joe of loath on 2010-09-28
Apparently it's supported. Have you tried moving it to a different PCI slot or reseated it?

---

### Post by houshdaran on 2010-09-28
I restarted my PC and now am able to connect via ubuntu.So do I need any anti-virus?

---

### Post by Joe of loath on 2010-09-28
Nope, none at all, unless you want to share lots of files with a Windows installation/partition/friend with Windows, as you might accidentally transfer over a Windows virus.

---

### Post by houshdaran on 2010-09-29
I transfer files from windows computers on my USB flash memory

---

### Post by sdowney717 on 2010-10-01
[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

Avast has a free linux version and there is ClamAV

I just tested it and it works using my windows registration
You dont need it for linux.
It could still be useful to scan windows files.

---

