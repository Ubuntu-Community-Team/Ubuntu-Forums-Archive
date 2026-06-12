---
title: "tigon firmware/drivers"
date: 2013-02-24
forum: Server Platforms
---

### Post by MakOwner on 2013-02-24
I'm loading a 12.04 install onto a hand-me-down server.
the 12.04 minimal install ddisk stops and asks for a firmware/driver disk, but if you ignore that the install procedes - over the network - and completes successfully.  Upon reboot after the installatio is complete, there is no network connectivity.  

So, the installer can load the needed stuff to run the installation, but the drivers that are used during the install can't be used on the installed server?


I see several posts about this when searching, but I don't see any conclusive answers on how to get the appropriate driver (re) loaded.

Sadly, these NIC ports are the only option for this server - there are no more slots available to lod additional NICs -- and the best part is the 10.04 installation worked just fine.

Is the only option to use the 10.04 install and then dist-upgrade rather than a fresh install?

---

### Post by cariboo on 2013-02-24
Could you paste the output of:

```
sudo lshw -C network
```

in your next post?

---

### Post by MakOwner on 2013-02-24
> **cariboo907 said:**
> Could you paste the output of:

```
sudo lshw -C network
```

in your next post?

```

        *-network:0
             description: Ethernet interface
             product: NetXtreme BCM5702X Gigabit Ethernet
             vendor: Broadcom Corporation
             physical id: 3
             bus info: pci@0000:02:03.0
             logical name: eth0
             version: 02
             serial: 00:50:45:5c:2d:d6
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 64 bits
             clock: 66MHz
             capabilities: pcix pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5702-v2.37 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:27 memory:fe000000-fe00ffff memory:fe300000-fe30ffff
        *-network:1 DISABLED
             description: Ethernet interface
             product: NetXtreme BCM5702X Gigabit Ethernet
             vendor: Broadcom Corporation
             physical id: 4
             bus info: pci@0000:02:04.0
             logical name: eth1
             version: 02
             serial: 00:50:45:5c:2d:d7
             capacity: 1Gbit/s
             width: 64 bits
             clock: 66MHz
             capabilities: pcix pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5702-v2.37 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
             resources: irq:27 memory:fe010000-fe01ffff memory:fe310000-fe31ffff

```

---

### Post by MakOwner on 2013-04-02
I loaded the firmware from another server onto a floppy -- the install hist it during the install process and _somtimes_ you get functioning networking.  No idea what the differences between the times it works and when it doens't might be.
the firmware bin files are in /lib/firmware/tigon - tg3.bin, tg3_ts05.bin and tg3_tso.bin.  

Just freaking great.

---

### Post by MakOwner on 2013-04-02
The server installation for 12.04 loads the drivers for the installation over the network, but then fails to load them on first boot. 

I could understand that on the mini installation, but the server install?  The part about it loading the drivers for the install then not loading at boot time is the really impressive part.  At least the mini install sort of warns you by asking for a floppy for the driver...

---

