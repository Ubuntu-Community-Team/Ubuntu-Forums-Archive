---
title: "Cant dual boot windows and Elementary"
date: 2018-12-02
forum: Ubuntu/Debian BASED
---

### Post by patricia.p on 2018-12-02
Hi, I'm currently on W10 and tried the elementary OS (Juno) and love it as a liveUSB. My BIOS is not able to see my PCI-E SATA drive 1, but it is visible in Device manager and Disk Creation tool in Windows system tools. 
I installed the eOS on drive 1 with secure boot with password enabled (and physically disconnected my Windows drive 0) and it installed and I rebooted. The USB installer started to reinstall so I closed this as soon as I was able.
I removed the USB drive and rebooted. 
I got the black screen, unbootable.
. I checked the BIOS settings (HP Prodesk 400 G4,) and the drive was not in the Uefi boot order list. Settings are Legacy disabled, Secure boot enabled, UEFI. I re-connected the windows drive and booted into windows after confirming that the PCI-E drive does not appear on the boot list. 
In windows I can see drive 1 and elementary has split it into 2r volumes, one EFI.
Should I repair the boot with a Linux tool, or is this a special PCI-E issue?

Marvell 92xx Storage Space Controller driver installed in windows 10 - is there one for Linux, or is this assumed by the fact that the OS is installed on the drive.

---

### Post by yancek on 2018-12-02
I would suggest that you get more detailed information to post here.  That is best done by using boot repair software which is explained and can be downloaded and run from the site at the link below.  Use the 2nd option, the ppa and after downloading select the Create Boot Info Summary option and definitely do NOT try to make any repairs.  When it finishes, you can post the link you get here at the forums and members will be able to suggest possible solutions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by patricia.p on 2018-12-03
Thanks for your reply.
I swapped the SATA drive from PCI-E to the motherboard, and when I confirmed that Windows could boot both drives, I turned off secure boot and unticked the secure options on HP bios for business machines. 
I used the USB installer to delete the previous install and created three partitions as advised by itsfoss.com, root, swap and home. I installed elementary on the drive and rebooted to grub.
I have restarted a few times now and it seems stable dual booting elementary and W10. 
The PCI-E issue may not be a problem as the Marvell driver must have been installed 
[section of sudo lshw]
cea03fff
        *-pci:1
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:3000(size=4096) memory:ce900000-ce9fffff
           *-storage
                description: SATA controller
                product: 88SE9235 PCIe 2.0 x2 4-port SATA 6 Gb/s Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:125 ioport:3028(size=8) ioport:3034(size=4) ioport:3020(size=8)

---

