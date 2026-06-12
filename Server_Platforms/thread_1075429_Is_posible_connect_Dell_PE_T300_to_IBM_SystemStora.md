---
title: "Is posible connect Dell PE T300 to IBM SystemStorage DS3200 external min-SAS"
date: 2009-02-20
forum: Server Platforms
---

### Post by Meskis on 2009-02-20
Hi,
I have Dell Power Edge T300 with hardware RAID1, I want to connect IBM external HDD storage to that server. I inserted IBM sas hba controller and connected storage thru external mini-SAS cable.
Im very new in Linux and Ubuntu, so I cant understand does Ubuntu correcly recognized that IBM card and if it recognized the card, how can I format and mount that external storage. I want to set up RAID5 on that storage.
Thats how Ubuntu 8.04 sees IBM hardware:

*-pci:0
             description: PCI bridge
             product: 5100 Chipset PCI Express x8 Port 2-3
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-scsi
                description: SCSI storage controller
                product: SAS1068E PCI-Express Fusion-MPT SAS
                vendor: LSI Logic / Symbios Logic
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: scsi0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: scsi pm pciexpress msi msix bus_master cap_list scsi-host
                configuration: driver=mptsas latency=0 module=mptsas
              *-disk:0 UNCLAIMED
                   description: SCSI Disk
                   product: 1726-2xx  FAStT
                   vendor: IBM
                   physical id: 0.0.0
                   bus info: scsi@0:0.0.0
                   version: 0617
                   serial: SX82128299
                   configuration: ansiversion=5
              *-disk:1 UNCLAIMED
                   description: SCSI Disk
                   product: Universal Xport
                   vendor: IBM
                   physical id: 0.0.1f
                   bus info: scsi@0:0.0.31
                   version: 0617
                   serial: SX82128299
                   capacity: 20MiB (20MB)
                   capabilities: 7200rpm
                   configuration: ansiversion=5

With fdisk I can see only servers hdd, no other device are visible:

Disk /dev/sda: 248.9 GB, 248999051264 bytes
255 heads, 63 sectors/track, 30272 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b312e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29517   237095271   83  Linux
/dev/sda2           29518       30272     6064537+   5  Extended
/dev/sda5           29518       30272     6064506   82  Linux swap / Solaris

All help is appreciable and if You need any other info please ask.
Does it posible at all to connect external IBM storage to server on Ubuntu?
Thank You (A&#269;i&#363;)

---

