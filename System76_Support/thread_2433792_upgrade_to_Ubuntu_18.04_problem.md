---
title: "upgrade to Ubuntu 18.04 problem"
date: 2019-12-25
forum: System76 Support
---

### Post by sviginak on 2019-12-25
Big problem for me, hope the fix is easy. A year ago in 16.04, I followed some bad advice and could not boot. I ended up using the terminal to install Lubuntu, and after that the Lubuntu icon would appear during boot, but Ubuntu always came up as before. I was hoping when I upgraded that this problem would disappear, but alas it has not. I cannot start up unless I select lubuntu at the password sign in. I am in Lubuntu right now. After upgrading to 18.04.3 I was using ubuntu, but now it is the next day and when I restarted, my password will only boot if I select lubuntu. (which I have never used). So wondering if I can use terminal to install ubuntu boot command and delete lubuntu boot command. Thanks in advance if someone can help.

---

### Post by crip720 on 2019-12-25
Can you confirm that you installed lubuntu desktop and not lubuntu system.  18.04 uses the gnome desktop instead of the unity desktop found with 16.04.  Can you backup your important data and/or data you want to keep?

---

### Post by sviginak on 2019-12-25
I did a back up to a portable drive before I upgraded. It said it went ok, but it doesn't look recognizable to me, but I am not sure. I am backing up my home folder on same drive so I have another copy. I am not sure how to tell if I have Lub desktop or whole system.

---

### Post by sviginak on 2019-12-25
I can log into lubunt or unity from the 18.04 screen if I select them from the button next to password. If I select ubuntu it circles me back to select user screen after I enter my password.

---

### Post by crip720 on 2019-12-26
Not sure if it has changed in 18.04, but have found in 19.10 that the login screen asks for user name first, before asking for password, instead of just asking for password.  Confusing for first time you put in password as usual, but it keeps going back.  Check if it asking for user name first, might not be clear.

---

### Post by sviginak on 2019-12-26
Thanks to all that commented. I finally back  up my personal data and did a clean install of Ubuntu, everything seems to be working fine. Thanks again...

---

### Post by sviginak on 2020-01-03
I have been running ok for a week. Today I got the update software notice where I had to reboot. When I came back up, the screen is very much zoomed in, and the background has changed to a pattern of sorts instead of the bionic beaver orangeish. Looking at displays it says unknown display. Any thoughts?

I should add I did some sudo stuff that was supposed to help me view videos on the web. I have an invidia card and system 76 Gazelle Pro 6.

---

### Post by mörgæs on 2020-01-04
> **sviginak said:**
> 
I did some sudo stuff that was supposed to help me view videos on the web. 

You need to be much more specific, perferrably by posting the exact commands and their output.

We also need to know the exact hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by sviginak on 2020-01-07
```
computer
    description: Notebook
    product: Gazelle Professional (Not Applicable)
    vendor: System76, Inc.
    version: gazp6
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=Not Applicable sku=Not Applicable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Gazelle Professional
       vendor: System76, Inc.
       physical id: 0
       version: gazp6
       serial: [REMOVED]
       slot: Not Applicable
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.4
          date: 08/09/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: 4
          size: 128KiB
          capacity: 128KiB
          capabilities: internal varies
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 5
          size: 512KiB
          capacity: 512KiB
          capabilities: internal varies unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 6
          size: 3MiB
          capacity: 3MiB
          capabilities: internal varies unified
          configuration: level=3
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [REMOVED]
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [REMOVED]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4f
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          slot: SOCKET 0
          size: 1126MHz
          capacity: 2900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f4000000-f60fffff ioport:e8000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF116M [GeForce GT 560M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:31 memory:f4000000-f5ffffff memory:e8000000-efffffff memory:f0000000-f3ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GF116 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f6080000-f6083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:30 memory:f650a000-f650a00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f6508000-f65083ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-37-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:f6500000-f6503fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f6400000-f64fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:f6400000-f6401fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.0.0-37-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 5.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.0.0-37-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 5.00
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:f6300000-f63fffff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0f0
                version: 05
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:33 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 90
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:f6326000-f63260ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 90
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f6325000-f63250ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 90
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:f6324000-f63240ff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) memory:f6200000-f62fffff
           *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=5.0.0-37-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:18 ioport:c000(size=256) memory:f6200000-f6203fff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f6100000-f61fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:f6101000-f61017ff memory:f6100000-f61000ff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f6507000-f65073ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-37-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: BisonCam, NB Pro
                      vendor: BisonCam, NB Pro
                      physical id: 6
                      bus info: usb@2:1.6
                      version: 6.04
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f6506000-f65067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6505000-f65050ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9320423AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SDM1
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=7a87842e
           *-volume
                description: Linux LVM Physical Volume partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                serial: [REMOVED]
                size: 298GiB
                capacity: 298GiB
                capabilities: primary bootable multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633F
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: TM00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh
```

Since I had just upgraded from 16.04 to 18.04 I upgraded from my usb drive again. I posted my hardware list so it will be in this thread for future. I just installed the System 76 driver and am going to reboot so I thought I should do it now. I did notice in terminal that somehow I had downgraded to 18.04.1 when the zoomed in screen showed up.

---

### Post by sviginak on 2020-01-07
Obviously my use of code window did not work as planned. ;) I used adv reply, clicked on # and pasted my txt between the codes where the cursor was? I thought the window would be smaller and scroll bar in window.  

Edt;On reboot the window was resized so I guess it worked. When booting I don't get my user to come up on password sign in. Instead I get a message **"An application wants to access the keyring "Default keyring" but it is locked.** I enter my password and click unlock, but the same message comes back when I reboot again. Can I unlock this somewhere?

Edit2: I had auto login selected when I upgraded the last time. I went to Users and turned this off and rebooted. After I selected myself as the user and entered my password, I was again given the keyring message, but had a checkbox to select "Unlock whenever I sign in" and this appears to have solved that issue. I had selected auto login because I hate having to sign in every time my computer goes to sleep, and can't find a place to change that.

---

