---
title: "3ware 9650SE RAID kills network adaptor"
date: 2008-07-18
forum: Server Platforms
---

### Post by newenden on 2008-07-18
I've got an HP ML150 G5 server, which I originally configured using mirrored SATA drives under 8.04 Server 64 bit as a VMware host. It was fine, but disk performance was slow under load.

I decided to buy a 3ware 9650SE RAID controller (ML150 has PCI Express bus) as feedback on 3ware with Linux/Ubuntu is good. But I have a problem.

Without the 9650SE installed, 8.04 Server installed fine and detected all devices etc.

With the 9650 installed, 8.04 detects the 3ware card OK but can't then detect the onboard LAN adapter. Same story trying to install earlier versions of Ubuntu as well. I get a red window popping up during install telling me that there's no network adapter detected.

I've now installed Windows 2003 R2, and have both 9650SE and onboard LAN installed and working perfectly. So the problem isn't a fundamental hardware conflict between 9650SE and ML150 server as both devices work together fine under Windows with the same BIOS config.

Is there any way of manually loading the network driver under Ubuntu Server? 'sudo lshw' shows the existence of the network adapter but lists it as 'UNCLAIMED'. My gut feeling is that the problem is an installation issue, ad that if I could only re-run the network installation once Ubuntu has booted then I should be OK. But how?

Many thanks,

Chris

---

### Post by newenden on 2008-07-19
Hi,

Some more info on this issue.

The ML150 has a Broadcom 5722 onboard NIC, and I'm now convinced that the problem is a conflict between the Broadcom tg3 driver and the 3ware driver in Ubuntu 8.04. I tried installing 8.04 server on a plain SATA drive without the 3ware card installed, and then reinstalling the 3ware card. Whenever the 3ware card is installed in the server the Broadcom driver fails to load.

I googled around and downloaded BCM5700-source (and its dependencies) via Aptitude. Even installing dpatch (referred to in a forum post) I couldn't get the wretched thing to build. There seem to be a load of people on the forums who want to try the BCM5700 driver for various reasons but are unable to build it. My knowledge has run out at this point - I'm not the right person to be debugging compile scripts for device drivers! Have to say I've never been an issue like this installing hundreds of Windows servers :-)

So 3 very straightforward questions if anyone can help please:

- does anyone have a pointer to a solution for building and installing BCM5700 drivers? I'd like to try that if I could.

- what alternative NICs have absolutely bombproof 8.04 server support and are known to work with the inbuilt 3ware driver? I need a PCI Express gigabit server card, Intel would seem to be a pretty safe choice I'd have thought, what experience do people have?

- how do I raise a formal Ubuntu bug report? As I said, I'm convinced now that the issue is a conflict between the tg3 and 3ware drivers in Ubuntu kernel and believe the issue needs escalating.

Many thanks in advance,

Chris

---

### Post by windependence on 2008-07-19
Just throw a cheap gigE 3com card in there and you'll be fine. must be some weird hardware on that board.

-Tim

---

### Post by newenden on 2008-07-23
> **windependence said:**
> Just throw a cheap gigE 3com card in there and you'll be fine. must be some weird hardware on that board.

-Tim

Tim,

I couldn't easily get hold of a 3com card but I've tried a PCIE gigE Intel card, a PCI gigE Realtek-based card and a PCI 100Mbit Realtek card. All are detected and work perfectly without the 3ware controller installed, none of them load their drivers when the 3ware card is installed. In all cases, lshw shows the devices but as UNCLAIMED. Error messages flash by at bootup referencing the driver name (eg tg3, e1000) and comments like 'unable to indentify chipset features'. Are these logged anywhere? I could provide fuller info if so but they disappear quickly off the top of the console.

Any more ideas anyone?

Cheers

Chris

---

### Post by windependence on 2008-07-23
Do a:

```
dmesg | less
```

and you can see the bootup messages.

-Tim

---

### Post by newenden on 2008-07-24
> **windependence said:**
> Do a:

```
dmesg | less
```

and you can see the bootup messages.

-Tim

Tim,

I don't know how much of dmesg is useful - I've extracted the section where ethernet and 3ware cards are installed, both in the case (1) where the 3ware card is NOT installed and the ethernet adaptor installs OK, and (2) where the 3ware card is installed and ethernet fails. The key lines in (2) are at 79.799 it seems to me. Also, both the 3ware and ethernet seem to be fighting over IRQ 23 - I don't know if this an issue.

Please bear with me if I've posted too much or too little...

Cheers

Chris

```
 (1)

[   56.113414] PNP: No PS/2 controller found. Probing ports directly.
[   69.150235] serio: i8042 KBD port at 0x60,0x64 irq 1
[   69.196202] mice: PS/2 mouse device common for all mice
[   69.196243] cpuidle: using governor ladder
[   69.196245] cpuidle: using governor menu
[   69.198637] NET: Registered protocol family 1
[   69.198731] registered taskstats version 1
[   69.198826]   Magic number: 0:582:473
[   69.198852] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   69.198854] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   69.199081] Freeing unused kernel memory: 328k freed
[   69.330812] fuse init (API version 7.9)
[   69.345499] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   69.345509] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   69.345520] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   69.345529] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   69.561303] SCSI subsystem initialized
[   69.567364] tg3.c:v3.86 (November 9, 2007)
[   69.567392] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   69.567401] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   69.572084] libata version 3.00 loaded.
[   69.572155] usbcore: registered new interface driver usbfs
[   69.572180] usbcore: registered new interface driver hub
[   69.572282] usbcore: registered new device driver usb
[   69.574584] USB Universal Host Controller Interface driver v3.0
[   69.609758] eth0: Tigon3 [partno(N/A) rev a200 PHY(5722/5756)] (PCI Express) 10/100/1000Base-T Ethernet 00:1e:0b:fc:ea:55
[   69.609765] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   69.609768] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   69.610032] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   69.610044] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   69.610047] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   69.610260] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   69.610285] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ec00
[   69.610408] usb usb1: configuration #1 chosen from 1 choice
[   69.610427] hub 1-0:1.0: USB hub found
[   69.610433] hub 1-0:1.0: 2 ports detected
[   69.714131] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   69.716048] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   69.716055] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   69.716109] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   69.720017] ehci_hcd 0000:00:1d.7: debug port 1
[   69.720022] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   69.720028] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfceffc00
[   69.734579] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   69.734662] usb usb2: configuration #1 chosen from 1 choice
[   69.734681] hub 2-0:1.0: USB hub found
[   69.734687] hub 2-0:1.0: 2 ports detected
[   69.844588] ata_piix 0000:00:1f.2: version 2.12
[   69.844596] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   69.844633] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   69.844660] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   69.844780] scsi0 : ata_piix
[   69.844832] scsi1 : ata_piix
[   69.845835] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[   69.845838] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[   70.024766] ata1.00: ATA-7: HDS728080PLA380, PF2OA6BA, max UDMA/133
[   70.024769] ata1.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   70.064753] ata1.00: configured for UDMA/133
[   70.235143] scsi 0:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
[   70.235206] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   70.235233] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   70.235259] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   70.235305] scsi2 : ata_piix
[   70.235347] scsi3 : ata_piix
[   70.236317] ata3: SATA max UDMA/133 cmd 0xe880 ctl 0xe800 bmdma 0xe080 irq 19
[   70.236320] ata4: SATA max UDMA/133 cmd 0xe480 ctl 0xe400 bmdma 0xe088 irq 19
[   70.503519] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   70.677805] usb 1-1: configuration #1 chosen from 1 choice
[   70.689771] usbcore: registered new interface driver hiddev
[   70.694800] input: ServerEngines SE USB Device as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   70.744196] ata4.00: ATAPI: HL-DT-STDVD-ROM GDRH20N, D8E4, max UDMA/100
[   70.744654] input,hidraw0: USB HID v1.11 Keyboard [ServerEngines SE USB Device] on usb-0000:00:1d.0-1
[   70.748739] input: ServerEngines SE USB Device as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input2
[   70.824609] input,hidraw1: USB HID v1.11 Mouse [ServerEngines SE USB Device] on usb-0000:00:1d.0-1
[   70.824617] usbcore: registered new interface driver usbhid
[   70.824619] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   70.944087] ata4.00: configured for UDMA/100
[   70.945604] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDRH20N  D8E4 PQ: 0 ANSI: 5
[   70.952578] Driver 'sd' needs updating - please use bus_type methods


```

```
 (2)

[   66.245247] PNP: No PS/2 controller found. Probing ports directly.
[   79.283074] serio: i8042 KBD port at 0x60,0x64 irq 1
[   79.329048] mice: PS/2 mouse device common for all mice
[   79.329088] cpuidle: using governor ladder
[   79.329090] cpuidle: using governor menu
[   79.331198] NET: Registered protocol family 1
[   79.331289] registered taskstats version 1
[   79.331389]   Magic number: 0:453:530
[   79.331415] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   79.331417] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   79.331651] Freeing unused kernel memory: 328k freed
[   79.463449] fuse init (API version 7.9)
[   79.477571] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   79.477581] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   79.477592] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   79.477601] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   79.678998] usbcore: registered new interface driver usbfs
[   79.679019] usbcore: registered new interface driver hub
[   79.679041] usbcore: registered new device driver usb
[   79.679707] USB Universal Host Controller Interface driver v3.0
[   79.679760] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   79.679770] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   79.679773] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   79.679981] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   79.680007] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[   79.680111] usb usb1: configuration #1 chosen from 1 choice
[   79.680129] hub 1-0:1.0: USB hub found
[   79.680133] hub 1-0:1.0: 2 ports detected
[   79.689986] SCSI subsystem initialized
[   79.690593] 3ware 9000 Storage Controller device driver for Linux v2.26.02.010.
[   79.708243] libata version 3.00 loaded.
[   79.796990] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   79.798983] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   79.798989] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   79.799040] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   79.799076] ehci_hcd 0000:00:1d.7: debug port 15 IN USE
[   79.799081] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   79.799088] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcdffc00
[   79.799096] ehci_hcd 0000:00:1d.7: startup error -19
[   79.799167] ehci_hcd 0000:00:1d.7: USB bus 2 deregistered
[   79.800933] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[   79.800939] ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -19
[   79.801246] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   79.801253] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   80.046701] scsi0 : 3ware 9000 Storage Controller
[   80.046743] 3w-9xxx: scsi0: Found a 3ware 9000 Storage Controller at 0xfceff000, IRQ: 16.
[   80.067307] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   80.240813] usb 1-1: configuration #1 chosen from 1 choice
[   80.252706] usbcore: registered new interface driver hiddev
[   80.257823] input: ServerEngines SE USB Device as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   80.318443] input,hidraw0: USB HID v1.11 Keyboard [ServerEngines SE USB Device] on usb-0000:00:1d.0-1
[   80.322736] input: ServerEngines SE USB Device as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input2
[   80.347804] input,hidraw1: USB HID v1.11 Mouse [ServerEngines SE USB Device] on usb-0000:00:1d.0-1
[   80.347815] usbcore: registered new interface driver usbhid
[   80.347818] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   80.407736] 3w-9xxx: scsi0: Firmware FE9X 3.08.00.022, BIOS BE9X 3.08.00.004, Ports: 4.
[   80.407794] tg3.c:v3.86 (November 9, 2007)
[   80.407825] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   80.407836] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   80.408887] scsi 0:0:0:0: Direct-Access     AMCC     9650SE-4LP DISK  3.08 PQ: 0 ANSI: 5
[   80.409688] scsi 0:0:0:1: Direct-Access     AMCC     9650SE-4LP DISK  3.08 PQ: 0 ANSI: 5
[   80.422849] Driver 'sd' needs updating - please use bus_type methods


```

---

### Post by newenden on 2008-07-24
On the suggestion of 3ware support, I tried downloading and booting from the latest Knoppix live CD. 

Knoppix works perfectly, it installs drivers for both the 3ware card and onboard Broadcom LAN. I can browse the web and my 3ware RAID array. So the problem can only be with Ubuntu, most probably its 3ware driver.

I however need Ubuntu to run VMware server. How can I escalate this beyond the forums to Ubuntu?

Many thanks,

Chris

---

### Post by dean123 on 2008-07-24
> **newenden said:**
> Hi,

Some more info on this issue.

The ML150 has a Broadcom 5722 onboard NIC, and I'm now convinced that the problem is a conflict between the Broadcom tg3 driver and the 3ware driver in Ubuntu 8.04. I tried installing 8.04 server on a plain SATA drive without the 3ware card installed, and then reinstalling the 3ware card. Whenever the 3ware card is installed in the server the Broadcom driver fails to load.

I googled around and downloaded BCM5700-source (and its dependencies) via Aptitude. Even installing dpatch (referred to in a forum post) I couldn't get the wretched thing to build. There seem to be a load of people on the forums who want to try the BCM5700 driver for various reasons but are unable to build it. My knowledge has run out at this point - I'm not the right person to be debugging compile scripts for device drivers! Have to say I've never been an issue like this installing hundreds of Windows servers :-)

So 3 very straightforward questions if anyone can help please:

- does anyone have a pointer to a solution for building and installing BCM5700 drivers? I'd like to try that if I could.

- what alternative NICs have absolutely bombproof 8.04 server support and are known to work with the inbuilt 3ware driver? I need a PCI Express gigabit server card, Intel would seem to be a pretty safe choice I'd have thought, what experience do people have?

- how do I raise a formal Ubuntu bug report? As I said, I'm convinced now that the issue is a conflict between the tg3 and 3ware drivers in Ubuntu kernel and believe the issue needs escalating.

Many thanks in advance,

Chris


>>> does anyone have a pointer to a solution for building and installing BCM5700 drivers?

If your NIC source is good, you need to install gcc, etc..

# apt-get install build-essential
# apt-get install libncurses5-dev 
# apt-get install linux-headers-`uname -r` 

( uname -r is your current kernel ver. )

# cd /usr/src ; ln -s /usr/src/linux-headers-`uname -r` linux

now recompile your source. 

# insmod <your-compiled-nic-module> eg tg3.ko or whatever it is..

the existing tg3 module should be under 

/lib/modules/`uname -r`/kernel/drivers/net

..hope that helps. 

I doubt that the problem is caused by 3ware driver....OEM systems are tough to debug...Hope that helps.

---

### Post by windependence on 2008-07-24
> **newenden said:**
> On the suggestion of 3ware support, I tried downloading and booting from the latest Knoppix live CD. 

Knoppix works perfectly, it installs drivers for both the 3ware card and onboard Broadcom LAN. I can browse the web and my 3ware RAID array. So the problem can only be with Ubuntu, most probably its 3ware driver.

I however need Ubuntu to run VMware server. How can I escalate this beyond the forums to Ubuntu?

Many thanks,

Chris

If this IS a bug, it could take a while to fix. I would try CentOS or OpenSuSE. They both work very well for me with VMware.

FYI, on Monday the 28th you will be able to download VMware ESXi for FREE. There is no host OS needed with that.

-Tim

---

### Post by newenden on 2008-07-25
> **windependence said:**
> If this IS a bug, it could take a while to fix. I would try CentOS or OpenSuSE. They both work very well for me with VMware.

FYI, on Monday the 28th you will be able to download VMware ESXi for FREE. There is no host OS needed with that.

-Tim

Tim,

Many thanks for your suggested alternatives - I agree that the immediate way forward for me now is to move away from Ubuntu.

I hadn't seen the news about ESXi, I think that's the route I'll be taking. A smart move by VMware, in my view, as well as excellent news for SMEs.

---

### Post by boblogic on 2009-05-18
I have the same problem with 9.04 Jaunty on an Asus A9N32-SLI Deluxe mother board.
It comes with two GigE NICs, so I disabled the first one, and enabled the second one.
The network problems went away. I also keep some D-Link DFE-530TX+ network cards around to help troubleshoot network problems. They are cheap and well supported

---

