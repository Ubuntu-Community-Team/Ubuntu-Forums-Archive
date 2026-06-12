---
title: "Broadcom BCM5708 on Dell Poweredge R200"
date: 2010-03-16
forum: Server Platforms
---

### Post by JamesPullman on 2010-03-16
Good day,

Have Ubuntu 9.10 installed on a new Dell PowerEdge R200.  There is a dual-port onboard NIC and I have two BCM5708 cards on PCI-Express.

The on-board ports are working, the other two are not.

Output from dmesg:

```
[    2.865207] eth0: Tigon3 [partno(BCM95721) rev 4201] (PCI Express) MAC address 00:25:64:3d:04:47
[    2.865209] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.865211] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    2.865213] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.865231] tg3 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.865238] tg3 0000:06:00.0: setting latency timer to 64
[    2.915287] eth1: Tigon3 [partno(BCM95721) rev 4201] (PCI Express) MAC address 00:25:64:3d:04:48
[    2.915290] eth1: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.915292] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    2.915293] eth1: dma_rwctrl[76180000] dma_mask[64-bit]
[    7.867249] Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.0.2 (Aug 21, 2009)
[    7.867268] bnx2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.886578] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    8.080985]   alloc irq_desc for 28 on node -1
[    8.080988]   alloc kstat_irqs on node -1
[    8.081002] tg3 0000:06:00.0: irq 28 for MSI/MSI-X
[    8.115636] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    8.115706]   alloc irq_desc for 29 on node -1
[    8.115709]   alloc kstat_irqs on node -1
[    8.115721] tg3 0000:05:00.0: irq 29 for MSI/MSI-X
[    8.150260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.462518] bnx2 0000:02:00.0: firmware: requesting bnx2/bnx2-mips-06-5.0.0.j3.fw
[    8.689919] bnx2 0000:02:00.0: firmware: requesting bnx2/bnx2-rv2p-06-5.0.0.j3.fw
[    8.762063] eth2: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem da000000, IRQ 16, node addr 00:10:18:3c:ec:84
[    8.762087] bnx2 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.362520] bnx2 0000:04:00.0: firmware: requesting bnx2/bnx2-mips-06-5.0.0.j3.fw
[    9.365143] bnx2 0000:04:00.0: firmware: requesting bnx2/bnx2-rv2p-06-5.0.0.j3.fw
[    9.368133] eth3: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem dc000000, IRQ 16, node addr 00:10:18:3c:ec:7c
[    9.371299] udev: renamed network interface eth2 to eth3
[    9.378519]   alloc irq_desc for 30 on node -1
[    9.378521]   alloc kstat_irqs on node -1
[    9.378531] bnx2 0000:02:00.0: irq 30 for MSI/MSI-X
[    9.733276] tg3: eth0: Link is up at 100 Mbps, full duplex.
[    9.733278] tg3: eth0: Flow control is on for TX and on for RX.
[    9.810547] tg3: eth1: Link is up at 100 Mbps, full duplex.
[    9.810549] tg3: eth1: Flow control is on for TX and on for RX.
_***[   13.450007] bnx2: fw sync timeout, reset code = 1030003***_
[   13.451142] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   13.452152] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.453770] udev: renamed network interface eth3_rename to eth2
[   13.453839] bnx2 0000:02:00.0: irq 30 for MSI/MSI-X
_***[   17.520008] bnx2: fw sync timeout, reset code = 1030006***_
[   23.761255] eth0: no IPv6 routers present
[   23.771255] eth1: no IPv6 routers present

```Every time I try to ifup the interface the reset code climbs by 3 more.

Being the too-eager-to-fix person I am I have tried a few things with none fixing the problem so far.  Here's what I've done:

1.  Upgraded kernel to 2.6.32.9

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.9/")

2.  Installed the Broadcom provided driver

[http://www.broadcom.com/docs/driver_download/NXII/linux-2.0.8b_1.52.12.zip](http://www.broadcom.com/docs/driver_download/NXII/linux-2.0.8b_1.52.12.zip)

Ethtool -i output:

```
snip@snip:~$ sudo ethtool -i eth0
driver: tg3
version: 3.102
firmware-version: 5721-v3.65, ASFIPMI v6.25
bus-info: 0000:05:00.0
snip@snip:~$ sudo ethtool -i eth1
driver: tg3
version: 3.102
firmware-version: 5721-v3.65, ASFIPMI v6.25
bus-info: 0000:06:00.0
snip@snip:~$ sudo ethtool -i eth2
driver: bnx2
version: 2.0.8b
firmware-version: 5.0.9 bc 5.0.4
bus-info: 0000:04:00.0
snip@snip:~$ sudo ethtool -i eth3
driver: bnx2
version: 2.0.8b
firmware-version: 5.0.9 bc 5.0.4
bus-info: 0000:02:00.0

```When I was on the Ubuntu kernel the bnx2 driver version was 2.0.2.  I am really at a loss to understand what's going on here, this isn't a really new/fancy NIC.

```
snip@snip:~$ uname -a
Linux snip 2.6.32-02063209-generic #02063209 SMP Wed Feb 24 10:09:53 UTC 2010 x86_64 GNU/Linux
``````
snip@snip:/proc/bus/pci$ cat devices
0000    808629f0        0                      0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0
0008    808629f1        18                     0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0        pcieport
00e0    80862940        19                     0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0        pcieport
00e4    80862948        1a                     0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0        pcieport
00e5    8086294a        1b                     0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0        pcieport
00e8    80862934        15                     0                       0                       0                       0                    dc61                       0                     0                       0                       0                       0                       0                      20                    0                0        uhci_hcd
00e9    80862935        14                     0                       0                       0                       0                    dc81                       0                     0                       0                       0                       0                       0                      20                    0                0        uhci_hcd
00ea    80862936        15                     0                       0                       0                       0                    dca1                       0                     0                       0                       0                       0                       0                      20                    0                0        uhci_hcd
00ef    8086293a        15              de0ffc00                       0                       0                       0                       0                       0                     0                     400                       0                       0                       0                       0                    0                0        ehci_hcd
00f0    8086244e        0                      0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0
00f8    80862916        0                      0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0
00fa    80862920        17                  dc31                    dc29                    dc39                    dc2d                    dc41                    dc51                     0                       8                       4                       8                       4                      10                   10                0        ata_piix
0100    11660103        0                      0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0
0200    14e4164c        10              da000004                       0                       0                       0                       0                       0                     0                 2000000                       0                       0                       0                       0                    0                0        bnx2
0300    11660103        0                      0                       0                       0                       0                       0                       0                     0                       0                       0                       0                       0                       0                    0                0
0400    14e4164c        10              dc000004                       0                       0                       0                       0                       0                     0                 2000000                       0                       0                       0                       0                    0                0        bnx2
0500    14e41659        1d              de1f0004                       0                       0                       0                       0                       0                     0                   10000                       0                       0                       0                       0                    0                0        tg3
0600    14e41659        1c              de2f0004                       0                       0                       0                       0                       0                     0                   10000                       0                       0                       0                       0                    0                0        tg3
0728    1002515e        5               d0000008                    ec01                de3f0000                       0                       0                       0              de300002                 8000000                     100                   10000                       0                       0                    0            20000

```Please let me know what other information I can provide or where my request would be better handled.  I've spent some time with Google on this topic and the majority of my hits are from over a year ago with fixes that have been in kernels for a while now.

---

### Post by tgalati4 on 2010-03-16
Try one broadcom card first.  Modern cards use quite a bit of power to sustain the high throughput speeds.  It's possible that the pci-e bus is sagging with 2 high-powered cards in it.

If it works with one card, then try the other card solo.  If you determine that each card works by itself, but both cards don't work, then that would be indicative.

What kind of services are you running on this machine that require 4 network cards?

---

### Post by JamesPullman on 2010-03-16
Thanks for the suggestion, I will have to pull the cards on that machine and bring the troublesome cards over to a machine that I can be more disruptive on.  Fortunately it's an identical built R200 so I'll be able to keep beating my head against it.

The machine is an application server.

1 NIC for Gig DB requests to the database backend
1 NIC for LAN
2 NICs on two different ISPs

Right now the redundant ISP connection and Gig DB interface are dark.  I clearly should have tested more instead of assuming that modprobe recognizing the NIC meant it was working.

I doubt it's about power usage as these are single port NICs but I will have to wait and see.

Should I be cross-posting this anywhere else?  I see there's a Dell-centric area in these forums as well.

---

### Post by JamesPullman on 2010-04-09
Alright it's been 3 weeks but I have a free hand to work on this.  The NICs are now here with me and a second R200 is acting the same as the first.

To start, I'm down to just one of these NICs and the problem is still present.  So I doubt it has to do with power to the bus.

The software is now closer to 'stock' Ubuntu 9.10, I haven't done all those kernel / driver updates as above.

I found this:

[http://article.gmane.org/gmane.linux.network/156619/](http://article.gmane.org/gmane.linux.network/156619/)

Which shows some similar errors to mine, except the scenario posed is different, bonding is in use.  I've tried 2.6.30.10-generic from Mainline with no success.

I also found this:

[http://lopsa.org/node/1836](http://lopsa.org/node/1836)

Which suggests disabling MSI on the bnx2 driver.  I tried that with no success.

So .. two things.

#1 - What can I do next here to diagnose?  What information can I provide?

#2 - Can anyone recommend a single or dual port PCI-Express gigabit copper NIC?

---

### Post by jrohan on 2010-04-29
Hi James,
 
I think you have hit the same problem I just did.
I've got a Broadcom BCM5708 in a server running Xenserver and had issues with it.
Have a look at your dmesg output above - it's not a PCI-E card ;)
Probably not the answer you wanted to hear, but at least it's an answer.....
Cheers,
 
Justin

---

### Post by JamesPullman on 2010-04-29
Yeah, dmesg calls it a 64 bit PCI-X card but having pulled it out of the system and replaced it with a PCI-E card I'm pretty sure what kind of card it is ;)

From the PCB:  BCM95708A0804F
From the chip:  BCM5708CKFBG

I have replaced the cards with Intel offerings but am not going to give up on these cards - I paid for them after all.

Now to go Google those numbers ...

---

### Post by tgalati4 on 2010-04-29
Try 32-bit Live CD and see the network cards work.  It may be a 32-bit/64-bit problem.

---

### Post by iissmart on 2010-04-29
> **JamesPullman said:**
> #2 - Can anyone recommend a single or dual port PCI-Express gigabit copper NIC?

Intel Pro/1000 Server NICs. There's simply nothing that compares to those. You can get single port, dual, or quads on a single card.

---

