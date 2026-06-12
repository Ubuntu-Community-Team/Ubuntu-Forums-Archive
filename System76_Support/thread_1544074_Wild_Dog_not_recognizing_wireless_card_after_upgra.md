---
title: "Wild Dog not recognizing wireless card after upgrade"
date: 2010-08-02
forum: System76 Support
---

### Post by pbelmonte on 2010-08-02
I have a Wild Dog (model wldp5) that I recently upgraded from Intrepid all the way to Lucid (10.04).  However, after upgrading through 9.10, the system stopped seeing my wireless card, and I do not even have an option available to me to enable wireless networking.  However, the live CD can see the wireless card.

Reinstalling network-manager (sudo apt-get --reinstall install network-manager) has been ineffective, and this is the relevant information about the wireless card I see upon using lspci -v | less:

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
 (rev 02)
        Subsystem: Intel Corporation Device 5044
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root
 Port (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e0200000-e02fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express ME
I Controller (rev 02)
        Subsystem: Intel Corporation Device 5044
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e0325900 (64-bit, non-prefetchable) [size=16]

```When using lspci | grep Wireless:

```
lspci | grep Wireless
07:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```Any advice that can help me avoid having to make a clean reinstall would be much appreciated!

EDIT: I just reinstalled, and the new configuration detects the wireless card all right.

---

### Post by jbelmonte on 2010-08-02
Didn't you select the Atheros driver in Jaunty to get wireless performance to improve? Since you have an Intel Wireless card, maybe you need to get rid of the Atheros selection. If this could help, does anyone know how to accomplish this?

---

### Post by jbelmonte on 2010-08-02
This sounds like a borked upgrade, but does anybody have any ideas for getting the Wild Dog to see the Wireless Card? I know a complete system install is an option, but that is a pain in the butt when it is only the wireless card that needs finding.

---

### Post by isantop on 2010-08-03
I'd have to agree on that; it sounds like a bad upgrade.

We can (and should) test first, just to make sure. Try creating an Ubuntu Live CD to boot off of. If the wireless works in the LiveCD, a fresh install will fix the problem right up, and may end up being less of a pain in the butt than fixing this.

---

### Post by jbelmonte on 2010-08-04
> **isantop said:**
> I'd have to agree on that; it sounds like a bad upgrade.

We can (and should) test first, just to make sure. Try creating an Ubuntu Live CD to boot off of. If the wireless works in the LiveCD, a fresh install will fix the problem right up, and may end up being less of a pain in the butt than fixing this.

Hi isantop,

My son did a clean install yesterday. Although wireless shows up and he can connect, performance is not as good as under Intrepid. The connection is not as strong and it keeps dropping on him. We have rebooted the router a couple of times, but that didn't help. That being said, we can't rule out a flaky router because a laptop he has is also having connection problems. We'll open a new ticket if we can't figure it out.

Thanks,
John

---

