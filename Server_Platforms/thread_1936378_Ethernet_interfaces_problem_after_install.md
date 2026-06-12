---
title: "Ethernet interfaces problem after install"
date: 2012-03-05
forum: Server Platforms
---

### Post by jihlava on 2012-03-05
Hello,

Installing ubuntu 11.10 server on two HP Proliant DL 360 G5 boxes.   One works without issue, one doesn't.  As far as I can see all the settings in the bios (including its version), the Broadcom Boot Agent configuration, and the Lights Out management are the same between the two hosts.

From a cd I run the installer on the problematic box and the install process works without any argument.  Early in the install process when it configures the network it asks to select the primary ethernet interface and shows eth0 and eth1 identifying both of them as Broadcom Net Extreme II BCM5708 Gigabit Ethernet. I choose eth0.  The card is configured in the expected way via DHCP and is clearly working (time server is set, packages are downloaded, I can reach the address remotely while the install is proceeding).  

When the install finishes the reboot fails to start eth0.  /etc/network/interfaces shows 'auto inet dhcp' for eth0 as expected.   ifconfig -a only shows eth1 but as its not configured its not up.  ifconfig eth0 returns no such device.
dmesg shows several entries for bnx2 where the card is identified:
bnx2: Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.1.6 (Mar 7, 2011)
bnx2 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
bnx2 0000:03:00.0: eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem f8000000, IRQ 18, node addr 00:1e:0b:5e:85:ee
bnx2 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
bnx2: Can't load firmware file "bnx2/bnx2-mips-06-6.2.1.fw"
bnx2 0000:05:00.0: PCI INT A disabled
bnx2: probe of 0000:05:00.0 failed with error -2

At  this point udevd starts up and renames eth0 to eth1.  I cannot work out what the kernel is discovering to cause this to happen.  I tried deleting /etc/udevd/rules.d/70-persistent-net.rules but its simply re-created with no change to the behaviour.

On the second box doing exactly the same install process, the same messages appear in demsg followed by udevd starting up but with no further activity, then followed by

bnx2 0000:03:00.0: irq 68 for MSI/MSI-X
bnx2 0000:03:00.0: eth0: using MSI
bnx2 0000:03:00.0: eth0: NIC Copper Link is Up, 1000 Mbps full duplex, receive & transmit flow control ON

And the interface is fine.  eth1 also exists (but I'm not configuring that at this stage).

Even though the module loading reports some errors as above, they are the same on both boxes, so I doubt that's the key.

Various posts on forums suggest a bug (some sort of udev race condition during boot) and a workaround to edit the udev script in/usr/share/initramfs-tools/scripts/init-bottom/ to enable a wait function.
Curiously ubuntu's busybox seems to have no editor available so I couldn't edit this file at the completion of the install.

But the point is that two seemingly identical hardware boxes behave differently.  I've run out of places to look and would appreciate any suggestions, especially if you've seen this problem.

Many thanks.

---

