---
title: "*-network Unclaimed (after nvidia driver install)"
date: 2021-11-10
forum: Ubuntu/Debian BASED
---

### Post by silicon-void on 2021-11-10
Need help.

I am running Elementary OS (Ubuntu 20.4 with Pantheon GUI) and I was getting some errors with the software app regarding uodating the exiting 470.79? driver to 470.82, so I manually downloaded and installed the current driver through terminal. As far as the driver, everything is working - however when I rebooted, the network adapter doesn't show to be enabled, and lshw says it is unclaimed:

sudo lshw -C network
  *-network UNCLAIMED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Network Connection
       vendor: Realtek Semiconductor Co., Ltd
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:f2204000-f2204fff memory:f2200000-f2203fff

I forgot what else I ran (after 30 pages of other threads) but the physical driver looks to be {8139cp} as the driver is already on the system and was working before.

As I have no access to the internet I cannot download anything, including some of the terminal commands I saw in other pages - but I shouldn't have to download anything...
How do I get the os to load the friggin driver that is already there to claim the adapter???

Thank in advance for the assistance.
SV

---

### Post by howefield on 2021-11-10
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

