---
title: "How do I compile a kernel module (just one) from linux headers?"
date: 2009-04-04
forum: Server Platforms
---

### Post by shinobitux on 2009-04-04
Hey, I'm not exactly NEW to ubuntu, but I don't have a lot of experience compiling my own kernel or drivers.

I'm helping an associate of mine who has 8.10 Server 64-bit (2.6.27-11-server). After install from IDE cdrom (server install) ubuntu doesn't recognize the cdrom.

The cdrom appears to still be working, as he can run windows boot cd's from it. I've read a couple forums and some people claimed that you need to load the ide-generic kernel module which doesn't come with 8.10 server.

I have all these headers:

/usr/src/linux-headers-2.6.27-11
/usr/src/linux-headers-2.6.27-11-generic (I downloaded these)
/usr/src/linux-headers-2.6.27-11-server

In each directory ie: /usr/src/linux-headers-2.6.27-11/drivers/ide there is a Makefile with line 36 

```
obj-$(CONFIG_IDE_GENERIC)               += ide-generic.o
```

but when I tried to run make I realized that there were no targets.

What do I do? Is it possible to compile my own ide-generic.ko?

I even tried copying the ide-generic.ko from an ubuntu 8.04 Server live cd and migrating it to my associates computer.

```

sudo mkdir /lib/modules/$(uname -r)/kernel/drivers/ide
sudo cp ~/ide-generic.ko /lib/modules/$(uname -r)/kernel/drivers/ide/
sudo depmod
sudo update-initramfs -u

```

But it gave me an error, something about the module being the incorrect format or wrongly formed.

Please, let me know what I can do. We're using all the SATA ports and my associate is reluctant to use an external cdrom or installing a SATA expansion card.

Any advice you can give me would be welcome. I look upon this not only as an issue to be resolved, but a learning experience.

~shinobitux

For your critique...

```
ls -1 /dev
```

```

adsp
audio
block
bus
char
console
core
cpu_dma_latency
disk
dsp
fd
full
fuse
hidraw0
hpet
initctl
input
kmem
kmsg
log
loop0
loop1
loop2
loop3
loop4
loop5
loop6
loop7
MAKEDEV
mapper
mcelog
mem
mixer
mixer1
net
network_latency
network_throughput
null
oldmem
port
ppp
psaux
ptmx
pts
ptya0
ptya1
ptya2
ptya3
ptya4
ptya5
ptya6
ptya7
ptya8
ptya9
ptyaa
ptyab
ptyac
ptyad
ptyae
ptyaf
ptyb0
ptyb1
ptyb2
ptyb3
ptyb4
ptyb5
ptyb6
ptyb7
ptyb8
ptyb9
ptyba
ptybb
ptybc
ptybd
ptybe
ptybf
ptyc0
ptyc1
ptyc2
ptyc3
ptyc4
ptyc5
ptyc6
ptyc7
ptyc8
ptyc9
ptyca
ptycb
ptycc
ptycd
ptyce
ptycf
ptyd0
ptyd1
ptyd2
ptyd3
ptyd4
ptyd5
ptyd6
ptyd7
ptyd8
ptyd9
ptyda
ptydb
ptydc
ptydd
ptyde
ptydf
ptye0
ptye1
ptye2
ptye3
ptye4
ptye5
ptye6
ptye7
ptye8
ptye9
ptyea
ptyeb
ptyec
ptyed
ptyee
ptyef
ptyp0
ptyp1
ptyp2
ptyp3
ptyp4
ptyp5
ptyp6
ptyp7
ptyp8
ptyp9
ptypa
ptypb
ptypc
ptypd
ptype
ptypf
ptyq0
ptyq1
ptyq2
ptyq3
ptyq4
ptyq5
ptyq6
ptyq7
ptyq8
ptyq9
ptyqa
ptyqb
ptyqc
ptyqd
ptyqe
ptyqf
ptyr0
ptyr1
ptyr2
ptyr3
ptyr4
ptyr5
ptyr6
ptyr7
ptyr8
ptyr9
ptyra
ptyrb
ptyrc
ptyrd
ptyre
ptyrf
ptys0
ptys1
ptys2
ptys3
ptys4
ptys5
ptys6
ptys7
ptys8
ptys9
ptysa
ptysb
ptysc
ptysd
ptyse
ptysf
ptyt0
ptyt1
ptyt2
ptyt3
ptyt4
ptyt5
ptyt6
ptyt7
ptyt8
ptyt9
ptyta
ptytb
ptytc
ptytd
ptyte
ptytf
ptyu0
ptyu1
ptyu2
ptyu3
ptyu4
ptyu5
ptyu6
ptyu7
ptyu8
ptyu9
ptyua
ptyub
ptyuc
ptyud
ptyue
ptyuf
ptyv0
ptyv1
ptyv2
ptyv3
ptyv4
ptyv5
ptyv6
ptyv7
ptyv8
ptyv9
ptyva
ptyvb
ptyvc
ptyvd
ptyve
ptyvf
ptyw0
ptyw1
ptyw2
ptyw3
ptyw4
ptyw5
ptyw6
ptyw7
ptyw8
ptyw9
ptywa
ptywb
ptywc
ptywd
ptywe
ptywf
ptyx0
ptyx1
ptyx2
ptyx3
ptyx4
ptyx5
ptyx6
ptyx7
ptyx8
ptyx9
ptyxa
ptyxb
ptyxc
ptyxd
ptyxe
ptyxf
ptyy0
ptyy1
ptyy2
ptyy3
ptyy4
ptyy5
ptyy6
ptyy7
ptyy8
ptyy9
ptyya
ptyyb
ptyyc
ptyyd
ptyye
ptyyf
ptyz0
ptyz1
ptyz2
ptyz3
ptyz4
ptyz5
ptyz6
ptyz7
ptyz8
ptyz9
ptyza
ptyzb
ptyzc
ptyzd
ptyze
ptyzf
ram0
ram1
ram10
ram11
ram12
ram13
ram14
ram15
ram2
ram3
ram4
ram5
ram6
ram7
ram8
ram9
random
rtc
rtc0
sda
sda1
sda2
sda5
sdb
sdc
sdc1
sdc2
sdc5
sdd
sde
sdf
sdf1
sdf3
sequencer
sequencer2
sg0
sg1
sg2
sg3
sg4
sg5
shm
snapshot
snd
sndstat
stderr
stdin
stdout
tty
tty0
tty1
tty10
tty11
tty12
tty13
tty14
tty15
tty16
tty17
tty18
tty19
tty2
tty20
tty21
tty22
tty23
tty24
tty25
tty26
tty27
tty28
tty29
tty3
tty30
tty31
tty32
tty33
tty34
tty35
tty36
tty37
tty38
tty39
tty4
tty40
tty41
tty42
tty43
tty44
tty45
tty46
tty47
tty48
tty49
tty5
tty50
tty51
tty52
tty53
tty54
tty55
tty56
tty57
tty58
tty59
tty6
tty60
tty61
tty62
tty63
tty7
tty8
tty9
ttya0
ttya1
ttya2
ttya3
ttya4
ttya5
ttya6
ttya7
ttya8
ttya9
ttyaa
ttyab
ttyac
ttyad
ttyae
ttyaf
ttyb0
ttyb1
ttyb2
ttyb3
ttyb4
ttyb5
ttyb6
ttyb7
ttyb8
ttyb9
ttyba
ttybb
ttybc
ttybd
ttybe
ttybf
ttyc0
ttyc1
ttyc2
ttyc3
ttyc4
ttyc5
ttyc6
ttyc7
ttyc8
ttyc9
ttyca
ttycb
ttycc
ttycd
ttyce
ttycf
ttyd0
ttyd1
ttyd2
ttyd3
ttyd4
ttyd5
ttyd6
ttyd7
ttyd8
ttyd9
ttyda
ttydb
ttydc
ttydd
ttyde
ttydf
ttye0
ttye1
ttye2
ttye3
ttye4
ttye5
ttye6
ttye7
ttye8
ttye9
ttyea
ttyeb
ttyec
ttyed
ttyee
ttyef
ttyp0
ttyp1
ttyp2
ttyp3
ttyp4
ttyp5
ttyp6
ttyp7
ttyp8
ttyp9
ttypa
ttypb
ttypc
ttypd
ttype
ttypf
ttyq0
ttyq1
ttyq2
ttyq3
ttyq4
ttyq5
ttyq6
ttyq7
ttyq8
ttyq9
ttyqa
ttyqb
ttyqc
ttyqd
ttyqe
ttyqf
ttyr0
ttyr1
ttyr2
ttyr3
ttyr4
ttyr5
ttyr6
ttyr7
ttyr8
ttyr9
ttyra
ttyrb
ttyrc
ttyrd
ttyre
ttyrf
ttys0
ttyS0
ttys1
ttyS1
ttys2
ttyS2
ttys3
ttyS3
ttys4
ttys5
ttys6
ttys7
ttys8
ttys9
ttysa
ttysb
ttysc
ttysd
ttyse
ttysf
ttyt0
ttyt1
ttyt2
ttyt3
ttyt4
ttyt5
ttyt6
ttyt7
ttyt8
ttyt9
ttyta
ttytb
ttytc
ttytd
ttyte
ttytf
ttyu0
ttyu1
ttyu2
ttyu3
ttyu4
ttyu5
ttyu6
ttyu7
ttyu8
ttyu9
ttyua
ttyub
ttyuc
ttyud
ttyue
ttyuf
ttyv0
ttyv1
ttyv2
ttyv3
ttyv4
ttyv5
ttyv6
ttyv7
ttyv8
ttyv9
ttyva
ttyvb
ttyvc
ttyvd
ttyve
ttyvf
ttyw0
ttyw1
ttyw2
ttyw3
ttyw4
ttyw5
ttyw6
ttyw7
ttyw8
ttyw9
ttywa
ttywb
ttywc
ttywd
ttywe
ttywf
ttyx0
ttyx1
ttyx2
ttyx3
ttyx4
ttyx5
ttyx6
ttyx7
ttyx8
ttyx9
ttyxa
ttyxb
ttyxc
ttyxd
ttyxe
ttyxf
ttyy0
ttyy1
ttyy2
ttyy3
ttyy4
ttyy5
ttyy6
ttyy7
ttyy8
ttyy9
ttyya
ttyyb
ttyyc
ttyyd
ttyye
ttyyf
ttyz0
ttyz1
ttyz2
ttyz3
ttyz4
ttyz5
ttyz6
ttyz7
ttyz8
ttyz9
ttyza
ttyzb
ttyzc
ttyzd
ttyze
ttyzf
urandom
usbdev1.1_ep00
usbdev1.1_ep81
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev4.1_ep00
usbdev4.1_ep81
usbdev5.1_ep00
usbdev5.1_ep81
usbdev5.4_ep00
usbdev5.4_ep81
usbdev6.1_ep00
usbdev6.1_ep81
usbdev7.1_ep00
usbdev7.1_ep81
usbdev8.1_ep00
usbdev8.1_ep81
vcs
vcs1
vcs2
vcs3
vcs4
vcs5
vcs6
vcs7
vcsa
vcsa1
vcsa2
vcsa3
vcsa4
vcsa5
vcsa6
vcsa7
vmci
vmmon
vmnet0
vmnet1
vmnet8
xconsole
zero

```

```
sudo lspci -v
```

```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 82d3
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 82d3
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a880 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ac00 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] Vendor Specific Information <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 8311
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 82d4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 82d4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 82d4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at a080 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a400 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a480 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe7ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] Vendor Specific Information <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 82d4

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 9000 [size=8]
	I/O ports at 8c00 [size=4]
	I/O ports at 8880 [size=8]
	I/O ports at 8800 [size=4]
	I/O ports at 8480 [size=16]
	I/O ports at 8400 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information <?>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix, ata_generic, pata_acpi

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: medium devsel, IRQ 15
	Memory at fe7ff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information <?>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix, ata_generic, pata_acpi

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
	Subsystem: PC Partner Limited Device e970
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe8e0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at b000 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
	Subsystem: PC Partner Limited Device aa38
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at c800 [size=256]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sky2
	Kernel modules: sky2

03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8212
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at feaffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: pata_marvell
	Kernel modules: pata_marvell, ahci, ata_generic, pata_acpi

05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
	Subsystem: ASUSTeK Computer Inc. Device 811a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at e800 [size=256]
	Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Kernel driver in use: skge
	Kernel modules: skge

05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8294
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394


```

```
dmesg
```

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-server (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 20:13:12 UTC 2009 (Ubuntu 2.6.27-11.27-server)
[    0.000000] Command line: root=/dev/mapper/isw_bjifjeaedi_System1 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
[    0.000000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff70000 page 4k
[    0.000000] kernel direct mapping tables up to cff70000 @ 10000-16000
[    0.000000] last_map_addr: cff70000 end: cff70000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ 14000-1e000
[    0.000000] last_map_addr: 230000000 end: 230000000
[    0.000000] RAMDISK: 376fa000 - 37fef7c7
[    0.000000] ACPI: RSDP 000FB460, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFF70000, 0040 (r1 A_M_I_ OEMRSDT   8000805 MSFT       97)
[    0.000000] ACPI: FACP CFF70200, 0084 (r2 A_M_I_ OEMFACP   8000805 MSFT       97)
[    0.000000] ACPI: DSDT CFF70440, 963E (r1  A0999 A0999001        1 INTL 20060113)
[    0.000000] ACPI: FACS CFF7E000, 0040
[    0.000000] ACPI: APIC CFF70390, 006C (r1 A_M_I_ OEMAPIC   8000805 MSFT       97)
[    0.000000] ACPI: MCFG CFF70400, 003C (r1 A_M_I_ OEMMCFG   8000805 MSFT       97)
[    0.000000] ACPI: OEMB CFF7E040, 0081 (r1 A_M_I_ AMI_OEM   8000805 MSFT       97)
[    0.000000] ACPI: HPET CFF79A80, 0038 (r1 A_M_I_ OEMHPET   8000805 MSFT       97)
[    0.000000] ACPI: OSFR CFF79AC0, 00B0 (r1 A_M_I_ OEMOSFR   8000805 MSFT       97)
[    0.000000] ACPI: SSDT CFF7E8D0, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20060113)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [0000000000019000 - 000000000001dfff]
[    0.000000]   bootmap [000000000001e000 -  0000000000063fff] pages 46
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0230000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
[    0.000000]   #3 [00376fa000 - 0037fef7c7]          RAMDISK ==> [00376fa000 - 0037fef7c7]
[    0.000000]   #4 [000009cc00 - 0000100000]    BIOS reserved ==> [000009cc00 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #6 [0000014000 - 0000019000]          PGTABLE ==> [0000014000 - 0000019000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20008bfffff] PMD -> [ffff880028200000-ffff8800301fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000cff70
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2096892
[    0.000000]   DMA zone: 2082 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 831408 pages, LIFO batch:31
[    0.000000]   Normal zone: 1225728 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
[    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ee00000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2059218
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=/dev/mapper/isw_bjifjeaedi_System1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2499.714 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Calgary: detecting Calgary via BIOS EBDA area
[    0.010000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.010000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.010000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.010000] Memory: 8173884k/9175040k available (3115k kernel code, 213684k reserved, 1577k data, 540k init)
[    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.010000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.010000] hpet clockevent registered
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.42 BogoMIPS (lpj=24997140)
[    0.010000] Security Framework initialized
[    0.010000] SELinux:  Disabled at boot.
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.010000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 0/0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] ACPI: Core revision 20080609
[    0.010810] ACPI: Checking initramfs for custom DSDT
[    0.330376] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.432361] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.432364] Using local APIC timer interrupts.
[    0.440001] APIC timer calibration result 20830962
[    0.440002] Detected 20.830 MHz APIC timer.
[    0.440100] Booting processor 1/1 ip 6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4999.45 BogoMIPS (lpj=24997282)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 1/1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.600506] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.600524] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.610102] Booting processor 2/2 ip 6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 4999.47 BogoMIPS (lpj=24997393)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 2/2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] CPU2: Thermal monitoring enabled (TM2)
[    0.770566] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.770584] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.780081] Booting processor 3/3 ip 6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 4999.47 BogoMIPS (lpj=24997399)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 3/3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] CPU3: Thermal monitoring enabled (TM2)
[    0.940522] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.940539] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.950017] Brought up 4 CPUs
[    0.950019] Total of 4 processors activated (19997.84 BogoMIPS).
[    0.950078] CPU0 attaching sched-domain:
[    0.950080]  domain 0: span 0-1 level MC
[    0.950081]   groups: 0 1
[    0.950084]   domain 1: span 0-3 level CPU
[    0.950086]    groups: 0-1 2-3
[    0.950088]    domain 2: span 0-3 level NODE
[    0.950090]     groups: 0-3
[    0.950093] CPU1 attaching sched-domain:
[    0.950094]  domain 0: span 0-1 level MC
[    0.950096]   groups: 1 0
[    0.950098]   domain 1: span 0-3 level CPU
[    0.950099]    groups: 0-1 2-3
[    0.950101]    domain 2: span 0-3 level NODE
[    0.950103]     groups: 0-3
[    0.950105] CPU2 attaching sched-domain:
[    0.950106]  domain 0: span 2-3 level MC
[    0.950108]   groups: 2 3
[    0.950110]   domain 1: span 0-3 level CPU
[    0.950111]    groups: 2-3 0-1
[    0.950114]    domain 2: span 0-3 level NODE
[    0.950115]     groups: 0-3
[    0.950118] CPU3 attaching sched-domain:
[    0.950119]  domain 0: span 2-3 level MC
[    0.950120]   groups: 3 2
[    0.950122]   domain 1: span 0-3 level CPU
[    0.950124]    groups: 2-3 0-1
[    0.950126]    domain 2: span 0-3 level NODE
[    0.950127]     groups: 0-3
[    0.950252] net_namespace: 1552 bytes
[    0.950252] Booting paravirtualized kernel on bare hardware
[    0.950252] Time: 18:56:20  Date: 04/03/09
[    0.950252] NET: Registered protocol family 16
[    0.950268] ACPI: bus type pci registered
[    0.950268] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.950268] PCI: Not using MMCONFIG.
[    0.950268] PCI: Using configuration type 1 for base access
[    0.950750] ACPI: EC: Look up EC in DSDT
[    0.968794] ACPI: Interpreter enabled
[    0.968796] ACPI: (supports S0 S1 S3 S4 S5)
[    0.968813] ACPI: Using IOAPIC for interrupt routing
[    0.968869] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.971733] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.978523] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.984374] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.984374] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:01.0: PME# disabled
[    0.984374] PCI: 0000:00:1a.0 reg 20 io port: [a800, a81f]
[    0.984374] PCI: 0000:00:1a.1 reg 20 io port: [a880, a89f]
[    0.984374] PCI: 0000:00:1a.2 reg 20 io port: [ac00, ac1f]
[    0.984374] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fe7ffc00, fe7fffff]
[    0.984374] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:1a.7: PME# disabled
[    0.984374] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fe7f8000, fe7fbfff]
[    0.984374] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:1b.0: PME# disabled
[    0.984374] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:1c.0: PME# disabled
[    0.984374] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:1c.4: PME# disabled
[    0.984374] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:1c.5: PME# disabled
[    0.984374] PCI: 0000:00:1d.0 reg 20 io port: [a080, a09f]
[    0.984374] PCI: 0000:00:1d.1 reg 20 io port: [a400, a41f]
[    0.984374] PCI: 0000:00:1d.2 reg 20 io port: [a480, a49f]
[    0.984374] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fe7ff800, fe7ffbff]
[    0.984374] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.984374] pci 0000:00:1d.7: PME# disabled
[    0.984374] PCI: 0000:00:1f.2 reg 10 io port: [9000, 9007]
[    0.984374] PCI: 0000:00:1f.2 reg 14 io port: [8c00, 8c03]
[    0.984374] PCI: 0000:00:1f.2 reg 18 io port: [8880, 8887]
[    0.984374] PCI: 0000:00:1f.2 reg 1c io port: [8800, 8803]
[    0.984374] PCI: 0000:00:1f.2 reg 20 io port: [8480, 848f]
[    0.984374] PCI: 0000:00:1f.2 reg 24 io port: [8400, 840f]
[    0.984374] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fe7ff400, fe7ff4ff]
[    0.984374] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.984374] PCI: 0000:00:1f.5 reg 10 io port: [a000, a007]
[    0.984374] PCI: 0000:00:1f.5 reg 14 io port: [9c00, 9c03]
[    0.984374] PCI: 0000:00:1f.5 reg 18 io port: [9880, 9887]
[    0.984374] PCI: 0000:00:1f.5 reg 1c io port: [9800, 9803]
[    0.984374] PCI: 0000:00:1f.5 reg 20 io port: [9480, 948f]
[    0.984374] PCI: 0000:00:1f.5 reg 24 io port: [9400, 940f]
[    0.984374] PCI: 0000:01:00.0 reg 10 64bit mmio: [d0000000, dfffffff]
[    0.984374] PCI: 0000:01:00.0 reg 18 64bit mmio: [fe8e0000, fe8effff]
[    0.984374] PCI: 0000:01:00.0 reg 20 io port: [b000, b0ff]
[    0.984374] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe8c0000, fe8dffff]
[    0.984374] pci 0000:01:00.0: supports D1
[    0.984374] pci 0000:01:00.0: supports D2
[    0.984374] PCI: 0000:01:00.1 reg 10 64bit mmio: [fe8fc000, fe8fffff]
[    0.984374] pci 0000:01:00.1: supports D1
[    0.984374] pci 0000:01:00.1: supports D2
[    0.984374] PCI: bridge 0000:00:01.0 io port: [b000, bfff]
[    0.984374] PCI: bridge 0000:00:01.0 32bit mmio: [fe800000, fe8fffff]
[    0.984374] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.984374] PCI: bridge 0000:00:1c.0 64bit mmio pref: [fdf00000, fdffffff]
[    0.984374] PCI: 0000:03:00.0 reg 10 io port: [dc00, dc07]
[    0.984374] PCI: 0000:03:00.0 reg 14 io port: [d880, d883]
[    0.984374] PCI: 0000:03:00.0 reg 18 io port: [d800, d807]
[    0.984374] PCI: 0000:03:00.0 reg 1c io port: [d480, d483]
[    0.984374] PCI: 0000:03:00.0 reg 20 io port: [d400, d40f]
[    0.984374] PCI: 0000:03:00.0 reg 24 32bit mmio: [feaffc00, feafffff]
[    0.984374] pci 0000:03:00.0: supports D1
[    0.984374] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.984374] pci 0000:03:00.0: PME# disabled
[    0.984374] PCI: bridge 0000:00:1c.4 io port: [d000, dfff]
[    0.984374] PCI: bridge 0000:00:1c.4 32bit mmio: [fea00000, feafffff]
[    0.984374] PCI: 0000:02:00.0 reg 10 64bit mmio: [fe9fc000, fe9fffff]
[    0.984374] PCI: 0000:02:00.0 reg 18 io port: [c800, c8ff]
[    0.984374] PCI: 0000:02:00.0 reg 30 32bit mmio: [fe9c0000, fe9dffff]
[    0.990018] pci 0000:02:00.0: supports D1
[    0.990019] pci 0000:02:00.0: supports D2
[    0.990021] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.990025] pci 0000:02:00.0: PME# disabled
[    0.990051] PCI: bridge 0000:00:1c.5 io port: [c000, cfff]
[    0.990054] PCI: bridge 0000:00:1c.5 32bit mmio: [fe900000, fe9fffff]
[    0.990092] PCI: 0000:05:02.0 reg 10 32bit mmio: [febfc000, febfffff]
[    0.990098] PCI: 0000:05:02.0 reg 14 io port: [e800, e8ff]
[    0.990119] PCI: 0000:05:02.0 reg 30 32bit mmio: [febc0000, febdffff]
[    0.990132] pci 0000:05:02.0: supports D1
[    0.990133] pci 0000:05:02.0: supports D2
[    0.990134] pci 0000:05:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.990138] pci 0000:05:02.0: PME# disabled
[    0.990161] PCI: 0000:05:03.0 reg 10 32bit mmio: [febfb000, febfbfff]
[    0.990195] pci 0000:05:03.0: supports D1
[    0.990197] pci 0000:05:03.0: supports D2
[    0.990198] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.990201] pci 0000:05:03.0: PME# disabled
[    0.990232] pci 0000:00:1e.0: transparent bridge
[    0.990234] PCI: bridge 0000:00:1e.0 io port: [e000, efff]
[    0.990237] PCI: bridge 0000:00:1e.0 32bit mmio: [feb00000, febfffff]
[    0.990261] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.990492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.990598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.990748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.990849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.990964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.010120] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.010252] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.010382] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    1.010512] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.010641] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.010772] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    1.010901] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.011030] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.011094] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - D9, should be D0 [20080609]
[    1.011094] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.011094] pnp: PnP ACPI init
[    1.011094] ACPI: bus type pnp registered
[    1.011094] pnp: PnP ACPI: found 17 devices
[    1.011094] ACPI: ACPI bus type pnp unregistered
[    1.011094] PCI: Using ACPI for IRQ routing
[    1.050009] NET: Registered protocol family 8
[    1.050010] NET: Registered protocol family 20
[    1.050025] NetLabel: Initializing
[    1.050025] NetLabel:  domain hash size = 128
[    1.050025] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.050025] NetLabel:  unlabeled traffic allowed by default
[    1.050045] PCI-GART: No AMD northbridge found.
[    1.050049] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.050053] hpet0: 4 64-bit timers, 14318180 Hz
[    1.052952] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    1.052953]    actual entries 65586
[    1.053021] AppArmor: AppArmor Filesystem Enabled
[    1.053036] ACPI: RTC can wake from S4
[    1.060006] Switched to high resolution mode on CPU 0
[    1.060547] Switched to high resolution mode on CPU 1
[    1.060574] Switched to high resolution mode on CPU 3
[    1.060617] Switched to high resolution mode on CPU 2
[    1.090019] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.090027] system 00:07: ioport range 0x290-0x29f has been reserved
[    1.090033] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.090035] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.090037] system 00:08: ioport range 0x500-0x57f has been reserved
[    1.090039] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    1.090042] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.090044] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.090046] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    1.090052] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[    1.090058] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.090060] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.090065] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    1.090071] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    1.090073] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    1.090075] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    1.090077] system 00:10: iomem range 0x100000-0xcfffffff could not be reserved
[    1.095639] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.095642] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    1.095644] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe8fffff
[    1.095647] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.095650] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    1.095651] pci 0000:00:1c.0:   IO window: disabled
[    1.095655] pci 0000:00:1c.0:   MEM window: disabled
[    1.095657] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    1.095662] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    1.095664] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    1.095668] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    1.095671] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.095675] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    1.095677] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    1.095681] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    1.095683] pci 0000:00:1c.5:   PREFETCH window: disabled
[    1.095688] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.095691] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    1.095694] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    1.095697] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
[    1.095708] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.095711] pci 0000:00:01.0: setting latency timer to 64
[    1.095716] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.095719] pci 0000:00:1c.0: setting latency timer to 64
[    1.095725] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.095727] pci 0000:00:1c.4: setting latency timer to 64
[    1.095733] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.095735] pci 0000:00:1c.5: setting latency timer to 64
[    1.095740] pci 0000:00:1e.0: setting latency timer to 64
[    1.095743] bus: 00 index 0 io port: [0, ffff]
[    1.095744] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    1.095746] bus: 01 index 0 io port: [b000, bfff]
[    1.095747] bus: 01 index 1 mmio: [fe800000, fe8fffff]
[    1.095748] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    1.095749] bus: 01 index 3 mmio: [0, 0]
[    1.095751] bus: 04 index 0 mmio: [0, 0]
[    1.095752] bus: 04 index 1 mmio: [0, 0]
[    1.095753] bus: 04 index 2 mmio: [fdf00000, fdffffff]
[    1.095754] bus: 04 index 3 mmio: [0, 0]
[    1.095755] bus: 03 index 0 io port: [d000, dfff]
[    1.095756] bus: 03 index 1 mmio: [fea00000, feafffff]
[    1.095758] bus: 03 index 2 mmio: [0, 0]
[    1.095759] bus: 03 index 3 mmio: [0, 0]
[    1.095760] bus: 02 index 0 io port: [c000, cfff]
[    1.095761] bus: 02 index 1 mmio: [fe900000, fe9fffff]
[    1.095763] bus: 02 index 2 mmio: [0, 0]
[    1.095764] bus: 02 index 3 mmio: [0, 0]
[    1.095765] bus: 05 index 0 io port: [e000, efff]
[    1.095766] bus: 05 index 1 mmio: [feb00000, febfffff]
[    1.095767] bus: 05 index 2 mmio: [f0000000, f00fffff]
[    1.095769] bus: 05 index 3 io port: [0, ffff]
[    1.095770] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    1.095778] NET: Registered protocol family 2
[    1.200233] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.201447] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.204333] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.204699] TCP: Hash tables configured (established 524288 bind 65536)
[    1.204702] TCP reno registered
[    1.230117] NET: Registered protocol family 1
[    1.230206] checking if image is initramfs... it is
[    1.868507] Freeing initrd memory: 9173k freed
[    1.872442] audit: initializing netlink socket (disabled)
[    1.872457] type=2000 audit(1238784980.871:1): initialized
[    1.877792] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.879673] VFS: Disk quotas dquot_6.5.1
[    1.879733] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.879802] msgmni has been set to 15982
[    1.879888] io scheduler noop registered
[    1.879889] io scheduler anticipatory registered
[    1.879891] io scheduler deadline registered (default)
[    1.879977] io scheduler cfq registered
[    1.880120] pci 0000:01:00.0: Boot video device
[    1.880247] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.880268] pcieport-driver 0000:00:01.0: found MSI capability
[    1.880288] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.880342] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.880431] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.880456] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.880481] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.880532] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.880592] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.880687] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.880712] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.880737] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.880787] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.880840] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.880936] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.880961] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.880986] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.881038] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.881091] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.911121] hpet_resources: 0xfed00000 is busy
[    1.911217] Linux agpgart interface v0.103
[    1.911225] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.911369] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.911893] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.913149] brd: module loaded
[    1.913200] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.913285] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.913286] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.913791] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.954220] mice: PS/2 mouse device common for all mice
[    1.954362] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.954383] rtc0: alarms up to one month, y3k, hpet irqs
[    1.954436] cpuidle: using governor ladder
[    1.954438] cpuidle: using governor menu
[    1.954722] TCP cubic registered
[    1.954951] registered taskstats version 1
[    1.955062]   Magic number: 5:13:948
[    1.955073] tty ttya3: hash matches
[    1.955119] tty tty5: hash matches
[    1.955164] rtc_cmos 00:03: setting system clock to 2009-04-03 18:56:21 UTC (1238784981)
[    1.955171] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.955173] EDD information not available.
[    1.955203] Freeing unused kernel memory: 540k freed
[    1.955332] Write protecting the kernel read-only data: 4352k
[    1.974986] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.035335] device-mapper: uevent: version 1.0.3
[    2.035544] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.046422] device-mapper: dm-raid45: initialized v0.2427
[    2.052461] fuse init (API version 7.9)
[    2.066663] ACPI: SSDT CFF7E0D0, 01F3 (r1 DpgPmm  P001Ist       11 INTL 20060113)
[    2.066997] processor ACPI0007:00: registered as cooling_device0
[    2.067346] ACPI: SSDT CFF7E2D0, 01F3 (r1 DpgPmm  P002Ist       12 INTL 20060113)
[    2.067652] processor ACPI0007:01: registered as cooling_device1
[    2.067997] ACPI: SSDT CFF7E4D0, 01F3 (r1 DpgPmm  P003Ist       12 INTL 20060113)
[    2.068306] processor ACPI0007:02: registered as cooling_device2
[    2.068653] ACPI: SSDT CFF7E6D0, 01F3 (r1 DpgPmm  P004Ist       12 INTL 20060113)
[    2.068957] processor ACPI0007:03: registered as cooling_device3
[    2.087483] md: linear personality registered for level -1
[    2.090058] md: multipath personality registered for level -4
[    2.092376] md: raid0 personality registered for level 0
[    2.095926] md: raid1 personality registered for level 1
[    2.098092] xor: automatically using best checksumming function: generic_sse
[    2.142502]    generic_sse:  9163.600 MB/sec
[    2.142504] xor: using function: generic_sse (9163.600 MB/sec)
[    2.143551] async_tx: api initialized (async)
[    2.312525] raid6: int64x1   2225 MB/s
[    2.482519] raid6: int64x2   3078 MB/s
[    2.652505] raid6: int64x4   2886 MB/s
[    2.822518] raid6: int64x8   2141 MB/s
[    2.992508] raid6: sse2x1    4278 MB/s
[    3.162512] raid6: sse2x2    5070 MB/s
[    3.332510] raid6: sse2x4    7194 MB/s
[    3.332511] raid6: using algorithm sse2x4 (7194 MB/s)
[    3.332513] md: raid6 personality registered for level 6
[    3.332515] md: raid5 personality registered for level 5
[    3.332516] md: raid4 personality registered for level 4
[    3.346912] md: raid10 personality registered for level 10
[    3.469749] usbcore: registered new interface driver usbfs
[    3.469769] usbcore: registered new interface driver hub
[    3.469802] usbcore: registered new device driver usb
[    3.471407] USB Universal Host Controller Interface driver v3.0
[    3.471455] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.471465] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.471468] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.471501] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.471533] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    3.471658] usb usb1: configuration #1 chosen from 1 choice
[    3.471678] hub 1-0:1.0: USB hub found
[    3.471683] hub 1-0:1.0: 2 ports detected
[    3.475080] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.477500] No dock devices found.
[    3.486934] SCSI subsystem initialized
[    3.497913] libata version 3.00 loaded.
[    3.572803] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.572812] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.572816] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.572842] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.572873] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    3.572944] usb usb2: configuration #1 chosen from 1 choice
[    3.572962] hub 2-0:1.0: USB hub found
[    3.572968] hub 2-0:1.0: 2 ports detected
[    3.682754] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.682763] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.682765] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.682788] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    3.682818] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    3.682887] usb usb3: configuration #1 chosen from 1 choice
[    3.682905] hub 3-0:1.0: USB hub found
[    3.682911] hub 3-0:1.0: 2 ports detected
[    3.792828] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.792842] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.792845] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.792877] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    3.796779] ehci_hcd 0000:00:1a.7: debug port 1
[    3.796784] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.796789] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[    3.821273] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.821396] usb usb4: configuration #1 chosen from 1 choice
[    3.821419] hub 4-0:1.0: USB hub found
[    3.821425] hub 4-0:1.0: 6 ports detected
[    3.920329] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.920338] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.920340] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.920372] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.920401] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    3.920516] usb usb5: configuration #1 chosen from 1 choice
[    3.920537] hub 5-0:1.0: USB hub found
[    3.920542] hub 5-0:1.0: 2 ports detected
[    4.140891] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.140896] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.140898] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.140917] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.140942] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    4.141006] usb usb6: configuration #1 chosen from 1 choice
[    4.141024] hub 6-0:1.0: USB hub found
[    4.141029] hub 6-0:1.0: 2 ports detected
[    4.250901] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.250906] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.250909] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.250927] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.250946] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    4.251008] usb usb7: configuration #1 chosen from 1 choice
[    4.251027] hub 7-0:1.0: USB hub found
[    4.251031] hub 7-0:1.0: 2 ports detected
[    4.260011] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    4.361100] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.361111] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.361113] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.361142] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    4.365034] ehci_hcd 0000:00:1d.7: debug port 1
[    4.365038] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.365044] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[    4.401258] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.401334] usb usb8: configuration #1 chosen from 1 choice
[    4.401364] hub 8-0:1.0: USB hub found
[    4.401369] hub 8-0:1.0: 6 ports detected
[    4.621184] ata_piix 0000:00:1f.2: version 2.12
[    4.621196] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.621199] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.621244] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.624219] scsi0 : ata_piix
[    4.624415] scsi1 : ata_piix
[    4.625956] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
[    4.625960] ata2: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
[    4.813759] usb 5-1: device not accepting address 2, error -71
[    4.870033] hub 5-0:1.0: unable to enumerate USB device on port 1
[    5.130065] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.170291] ata1.00: ATA-7: ST3250410AS, 4.AAA, max UDMA/133
[    5.170294] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.205217] ata1.01: ATA-7: ST3250620AS, 3.AAE, max UDMA/133
[    5.205220] ata1.01: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.240288] ata1.00: configured for UDMA/133
[    5.313508] ata1.01: configured for UDMA/133
[    5.322512] usb 5-1: new low speed USB device using uhci_hcd and address 4
[    5.478545] usb 5-1: configuration #1 chosen from 1 choice
[    5.490970] usbcore: registered new interface driver hiddev
[    5.506710] input: HID 045e:0009 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
[    5.580104] input,hidraw0: USB HID v1.00 Mouse [HID 045e:0009] on usb-0000:00:1d.0-1
[    5.580117] usbcore: registered new interface driver usbhid
[    5.580118] usbhid: v2.6:USB HID core driver
[    5.820066] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.860273] ata2.00: ATA-7: ST3250410AS, 4.AAA, max UDMA/133
[    5.860276] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.887156] ata2.01: ATA-7: ST3250620AS, 3.AAJ, max UDMA/133
[    5.887159] ata2.01: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.920304] ata2.00: configured for UDMA/133
[    5.987117] ata2.01: configured for UDMA/133
[    5.987220] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      4.AA PQ: 0 ANSI: 5
[    5.987317] scsi 0:0:1:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[    5.987397] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      4.AA PQ: 0 ANSI: 5
[    5.987475] scsi 1:0:1:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[    5.987638] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.987672] pata_marvell 0000:03:00.0: setting latency timer to 64
[    5.987785] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.987788] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    5.987826] ata_piix 0000:00:1f.5: setting latency timer to 64
[    5.987857] scsi2 : pata_marvell
[    5.987927] scsi4 : pata_marvell
[    5.987955] ata3: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    5.987957] ata4: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    5.988021] scsi3 : ata_piix
[    5.988094] scsi5 : ata_piix
[    5.989410] ata5: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
[    5.989413] ata6: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
[    6.290051] ata3.01: NODEV after polling detection
[    6.461268] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.461279] sky2 0000:02:00.0: setting latency timer to 64
[    6.461296] sky2 0000:02:00.0: v1.22 addr 0xfe9fc000 irq 17 Yukon-2 EC Ultra rev 3
[    6.461619] sky2 eth0: addr 00:22:15:9c:61:97
[    6.500042] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.551747] ata5.00: ATA-7: ST3250620AS, 3.AAJ, max UDMA/133
[    6.551750] ata5.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.643376] ata5.00: configured for UDMA/133
[    7.150043] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.203950] ata6.00: ATA-7: ST3250620AS, 3.AAJ, max UDMA/133
[    7.203953] ata6.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    7.287247] ata6.00: configured for UDMA/133
[    7.287339] scsi 3:0:0:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[    7.287435] scsi 5:0:0:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[    7.287514] skge 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.287549] skge 1.13 addr 0xfebfc000 irq 18 chip Yukon-Lite rev 9
[    7.287790] skge eth1: addr 00:22:15:9c:79:4e
[    7.287828] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.339915] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febfb000-febfb7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    7.354990] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.355021] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    7.355051] scsi 1:0:0:0: Attached scsi generic sg2 type 0
[    7.355078] scsi 1:0:1:0: Attached scsi generic sg3 type 0
[    7.355106] scsi 3:0:0:0: Attached scsi generic sg4 type 0
[    7.355138] scsi 5:0:0:0: Attached scsi generic sg5 type 0
[    7.366387] Driver 'sd' needs updating - please use bus_type methods
[    7.366473] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    7.366485] sd 0:0:0:0: [sda] Write Protect is off
[    7.366487] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.366506] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.366557] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    7.366567] sd 0:0:0:0: [sda] Write Protect is off
[    7.366569] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.366589] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.366594]  sda: sda1 sda2 < sda5 >
[    7.414768] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.414818] sd 0:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    7.414830] sd 0:0:1:0: [sdb] Write Protect is off
[    7.414831] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    7.414851] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.414897] sd 0:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    7.414907] sd 0:0:1:0: [sdb] Write Protect is off
[    7.414909] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    7.414928] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.414930]  sdb:
[    7.435679] sd 0:0:1:0: [sdb] Attached SCSI disk
[    7.435739] sd 1:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.435751] sd 1:0:0:0: [sdc] Write Protect is off
[    7.435753] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.435772] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.435830] sd 1:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.435841] sd 1:0:0:0: [sdc] Write Protect is off
[    7.435842] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.435861] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.435863]  sdc: sdc1 sdc2 < sdc5 >
[    7.484811] sd 1:0:0:0: [sdc] Attached SCSI disk
[    7.484867] sd 1:0:1:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    7.484879] sd 1:0:1:0: [sdd] Write Protect is off
[    7.484881] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    7.484900] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.484940] sd 1:0:1:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    7.484950] sd 1:0:1:0: [sdd] Write Protect is off
[    7.484952] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    7.484971] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.484974]  sdd: unknown partition table
[    7.501472] sd 1:0:1:0: [sdd] Attached SCSI disk
[    7.501532] sd 3:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.501547] sd 3:0:0:0: [sde] Write Protect is off
[    7.501549] sd 3:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    7.501575] sd 3:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.501623] sd 3:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.501633] sd 3:0:0:0: [sde] Write Protect is off
[    7.501635] sd 3:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    7.501654] sd 3:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.501656]  sde: unknown partition table
[    7.516319] sd 3:0:0:0: [sde] Attached SCSI disk
[    7.516364] sd 5:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
[    7.516375] sd 5:0:0:0: [sdf] Write Protect is off
[    7.516377] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    7.516396] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.516437] sd 5:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
[    7.516448] sd 5:0:0:0: [sdf] Write Protect is off
[    7.516449] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    7.516468] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.516470]  sdf: sdf1 sdf3
[    7.535233] sd 5:0:0:0: [sdf] Attached SCSI disk
[    8.662639] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001760b34]
[    9.292596] device-mapper: dm-raid45: /dev/sdb is raid disk 0
[    9.292599] device-mapper: dm-raid45: /dev/sdd is raid disk 1
[    9.292601] device-mapper: dm-raid45: /dev/sde is raid disk 2
[    9.292606] device-mapper: dm-raid45: /dev/sdf is raid disk 3
[    9.292608] device-mapper: dm-raid45: 128/128/256 sectors chunk/io/recovery size, 64 stripes
[    9.292610] device-mapper: dm-raid45: algorithm "xor_32", 8 chunks with 7950MB/s
[    9.292612] device-mapper: dm-raid45: RAID5 (left asymmetric) set with net 3/4 devices
[    9.292686] device-mapper: dm-raid45: No regions to recover
[    9.454645] PM: Starting manual resume from disk
[    9.454648] PM: Resume from partition 254:3
[    9.454649] PM: Checking hibernation image.
[    9.454798] PM: Resume from disk failed.
[    9.497437] EXT3-fs: INFO: recovery required on readonly filesystem.
[    9.497439] EXT3-fs: write access will be enabled during recovery.
[    9.798917] kjournald starting.  Commit interval 5 seconds
[    9.798936] EXT3-fs: dm-2: orphan cleanup on readonly fs
[    9.832833] ext3_orphan_cleanup: deleting unreferenced inode 10108940
[    9.850202] ext3_orphan_cleanup: deleting unreferenced inode 10108941
[    9.850214] EXT3-fs: dm-2: 2 orphan inodes deleted
[    9.850215] EXT3-fs: recovery complete.
[    9.852319] EXT3-fs: mounted filesystem with ordered data mode.
[   12.534288] udevd version 124 started
[   12.909530] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.943386] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.076480] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.110315] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   13.132532] ACPI: Power Button (FF) [PWRF]
[   13.132629] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   13.212549] ACPI: Power Button (CM) [PWRB]
[   13.318344] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.318368] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.778561] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.778589] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.148696] loop: module loaded
[   15.188477] lp: driver loaded but no devices found
[   15.434588] Adding 9928128k swap on /dev/mapper/isw_bjifjeaedi_System5.  Priority:-1 extents:1 across:9928128k
[   15.813032] EXT3 FS on dm-2, internal journal
[   19.166815] kjournald starting.  Commit interval 5 seconds
[   19.186627] EXT3 FS on dm-0, internal journal
[   19.186632] EXT3-fs: recovery complete.
[   19.187463] EXT3-fs: mounted filesystem with ordered data mode.
[   19.698076] type=1505 audit(1238784999.625:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4807
[   19.698218] type=1505 audit(1238784999.625:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4807
[   19.908626] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.965972] sky2 eth0: enabling interface
[   20.764249] NET: Registered protocol family 10
[   20.764586] lo: Disabled Privacy Extensions
[   20.764916] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.688935] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   21.690044] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.175239] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.855256] ppdev: user-space parallel port driver
[   25.012347] Bridge firewalling registered
[   25.062132] vnet0: starting userspace STP failed, starting kernel STP
[   25.387394] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   25.387572] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   25.387575] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   25.387576] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   27.940518] Bluetooth: Core ver 2.13
[   27.940568] NET: Registered protocol family 31
[   27.940569] Bluetooth: HCI device and connection manager initialized
[   27.940573] Bluetooth: HCI socket layer initialized
[   27.947960] Bluetooth: L2CAP ver 2.11
[   27.947964] Bluetooth: L2CAP socket layer initialized
[   28.067948] Bluetooth: SCO (Voice Link) ver 0.6
[   28.067953] Bluetooth: SCO socket layer initialized
[   28.075017] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.075021] Bluetooth: BNEP filters: protocol multicast
[   28.324064] Bluetooth: RFCOMM socket layer initialized
[   28.324079] Bluetooth: RFCOMM TTY layer initialized
[   28.324080] Bluetooth: RFCOMM ver 1.10
[   31.115906] /dev/vmmon[5810]: Module vmmon: registered with major=10 minor=165
[   31.115921] /dev/vmmon[5810]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   31.115928] /dev/vmmon[5810]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   31.115930] /dev/vmmon[5810]: Module vmmon: initialized
[   31.241812] /dev/vmci[5824]: VMCI: Driver initialized.
[   31.241895] /dev/vmci[5824]: Module vmci: registered with major=10 minor=59
[   31.241897] /dev/vmci[5824]: Module vmci: initialized
[   31.243618] mtrr: type mismatch for d0000000,1000000 old: write-back new: write-combining
[   31.623075] /dev/vmnet: open called by PID 5876 (vmnet-bridge)
[   31.623085] /dev/vmnet: hub 0 does not exist, allocating memory.
[   31.623092] /dev/vmnet: port on hub 0 successfully opened
[   31.624037] bridge-eth0: up
[   31.624042] bridge-eth0: attached
[   31.851382] /dev/vmnet: open called by PID 5887 (vmnet-dhcpd)
[   31.851400] /dev/vmnet: hub 1 does not exist, allocating memory.
[   31.851408] /dev/vmnet: port on hub 1 successfully opened
[   31.969258] /dev/vmnet: open called by PID 5905 (vmnet-dhcpd)
[   31.969274] /dev/vmnet: hub 8 does not exist, allocating memory.
[   31.969283] /dev/vmnet: port on hub 8 successfully opened
[   32.114372] /dev/vmnet: open called by PID 5910 (vmnet-natd)
[   32.114387] /dev/vmnet: port on hub 8 successfully opened
[   32.480345] skge eth1: enabling interface
[   32.484797] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   32.662509] eth0: no IPv6 routers present
[   32.820379] /dev/vmnet: open called by PID 6200 (vmnet-netifup)
[   32.820382] /dev/vmnet: open called by PID 6199 (vmnet-netifup)
[   32.820991] /dev/vmnet: port on hub 8 successfully opened
[   32.820994] /dev/vmnet: port on hub 1 successfully opened
[   35.280005] vnet0: no IPv6 routers present
[   42.840008] vmnet8: no IPv6 routers present
[   43.730005] vmnet1: no IPv6 routers present
[ 3527.821923] /dev/vmmon[7324]: PTSC: initialized at 2499713000 Hz using TSC
[ 3527.827793] /dev/vmmon[7324]: INTELRDMSR(0x8b) = 0x0000070300000000
[ 3527.827799] /dev/vmmon[7324]: INTELRDMSR(0x17) = 0x08100000a9c4c71e
[ 3527.827810] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x0000070300000000
[ 3527.827812] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x0000070300000000
[ 3527.827814] /dev/vmmon[5246]: INTELRDMSR(0x8b) = 0x0000070300000000
[ 3527.827816] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x08100000a9c4c71e
[ 3527.827818] /dev/vmmon[5246]: INTELRDMSR(0x17) = 0x08100000a9c4c71e
[ 3527.827821] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x08100000a9c4c71e
[ 3530.012632] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 3530.012657] device eth0 entered promiscuous mode
[ 3530.012662] bridge-eth0: enabled promiscuous mode
[ 3530.012664] /dev/vmnet: port on hub 0 successfully opened
[ 3550.535863] device eth0 left promiscuous mode
[ 3550.535874] bridge-eth0: disabled promiscuous mode
[ 3550.536404] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 3550.536420] device eth0 entered promiscuous mode
[ 3550.536423] bridge-eth0: enabled promiscuous mode
[ 3550.536425] /dev/vmnet: port on hub 0 successfully opened
[ 5110.464965] device eth0 left promiscuous mode
[ 5110.464984] bridge-eth0: disabled promiscuous mode
[ 5110.465038] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 5110.465050] device eth0 entered promiscuous mode
[ 5110.465053] bridge-eth0: enabled promiscuous mode
[ 5110.465055] /dev/vmnet: port on hub 0 successfully opened
[ 5118.058530] device eth0 left promiscuous mode
[ 5118.058548] bridge-eth0: disabled promiscuous mode
[ 5118.058595] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 5118.058607] device eth0 entered promiscuous mode
[ 5118.058611] bridge-eth0: enabled promiscuous mode
[ 5118.058612] /dev/vmnet: port on hub 0 successfully opened
[ 5689.771221] device eth0 left promiscuous mode
[ 5689.771233] bridge-eth0: disabled promiscuous mode
[ 5689.771870] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 5689.771883] device eth0 entered promiscuous mode
[ 5689.771886] bridge-eth0: enabled promiscuous mode
[ 5689.771887] /dev/vmnet: port on hub 0 successfully opened
[ 5694.626083] device eth0 left promiscuous mode
[ 5694.626094] bridge-eth0: disabled promiscuous mode
[ 5694.626639] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 5694.626652] device eth0 entered promiscuous mode
[ 5694.626655] bridge-eth0: enabled promiscuous mode
[ 5694.626656] /dev/vmnet: port on hub 0 successfully opened
[ 7315.181897] device eth0 left promiscuous mode
[ 7315.181914] bridge-eth0: disabled promiscuous mode
[ 7315.181969] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 7315.181981] device eth0 entered promiscuous mode
[ 7315.181984] bridge-eth0: enabled promiscuous mode
[ 7315.181986] /dev/vmnet: port on hub 0 successfully opened
[ 7321.412131] device eth0 left promiscuous mode
[ 7321.412143] bridge-eth0: disabled promiscuous mode
[ 7321.412196] /dev/vmnet: open called by PID 7328 (vmware-vmx)
[ 7321.412210] device eth0 entered promiscuous mode
[ 7321.412214] bridge-eth0: enabled promiscuous mode
[ 7321.412216] /dev/vmnet: port on hub 0 successfully opened
[ 9425.149931] mtrr: no MTRR for d0000000,1000000 found
[ 9426.734258] mtrr: type mismatch for d0000000,1000000 old: write-back new: write-combining
[10100.668038] mtrr: no MTRR for d0000000,1000000 found
[10101.781608] mtrr: type mismatch for d0000000,1000000 old: write-back new: write-combining

```

---

### Post by BkkBonanza on 2009-04-04
The kernel headers are not enough to compile a kernel. These are used for compiling modules that need kernel information.

To compile a new kernel you need to install the kernel source package as well. There are some good tutorials around on how to do this and it's been more than a year since I needed to so I couldn't say off hand. I vaguely remember the general process. Use google - "ubuntu compile kernel source" or something liek that.

Ooops. I just saw now that you aren't trying to compile the kernel. Then you need the sources for the module you want. Find that and then cd into the directory and run make. It will find the Makefile there and know it's target. Generally make && make install are needed. Probably need to use sudo as well.

Generally people download the tar file into /usr/src and then use tar to untar it like tar -xzvf mymodule.tar.gz and then cd into the package source and then make.

---

### Post by shinobitux on 2009-04-05
Thank you, BkkBonaza.

I'll try that. I start looking for the ide-generic source so I can try as you suggest.

Thanks again for your help. If you get a chance, have any good ideas where I could look for the source code? I'm googling it now.

~shinobitux

---

### Post by shinobitux on 2009-04-05
Ok, I found ide-generic.c as part of the linux kernel source I downloaded from kernel.org.

However, I still can't make heads or tails of the Makefile:

```

#
# link order is important here
#

EXTRA_CFLAGS				+= -Idrivers/ide

ide-core-y += ide.o ide-ioctls.o ide-io.o ide-iops.o ide-lib.o ide-probe.o \
	      ide-taskfile.o ide-pm.o ide-park.o ide-pio-blacklist.o ide-sysfs.o

# core IDE code
ide-core-$(CONFIG_IDE_TIMINGS)		+= ide-timings.o
ide-core-$(CONFIG_IDE_ATAPI)		+= ide-atapi.o
ide-core-$(CONFIG_BLK_DEV_IDEPCI)	+= setup-pci.o
ide-core-$(CONFIG_BLK_DEV_IDEDMA)	+= ide-dma.o
ide-core-$(CONFIG_BLK_DEV_IDEDMA_SFF)	+= ide-dma-sff.o
ide-core-$(CONFIG_IDE_PROC_FS)		+= ide-proc.o
ide-core-$(CONFIG_BLK_DEV_IDEACPI)	+= ide-acpi.o
ide-core-$(CONFIG_IDE_LEGACY)		+= ide-legacy.o

obj-$(CONFIG_IDE)			+= ide-core.o

obj-$(CONFIG_IDE_ARM)			+= ide_arm.o

obj-$(CONFIG_BLK_DEV_ALI14XX)		+= ali14xx.o
obj-$(CONFIG_BLK_DEV_UMC8672)		+= umc8672.o
obj-$(CONFIG_BLK_DEV_DTC2278)		+= dtc2278.o
obj-$(CONFIG_BLK_DEV_HT6560B)		+= ht6560b.o
obj-$(CONFIG_BLK_DEV_QD65XX)		+= qd65xx.o
obj-$(CONFIG_BLK_DEV_4DRIVES)		+= ide-4drives.o

obj-$(CONFIG_BLK_DEV_GAYLE)		+= gayle.o
obj-$(CONFIG_BLK_DEV_FALCON_IDE)	+= falconide.o
obj-$(CONFIG_BLK_DEV_MAC_IDE)		+= macide.o
obj-$(CONFIG_BLK_DEV_Q40IDE)		+= q40ide.o
obj-$(CONFIG_BLK_DEV_BUDDHA)		+= buddha.o

obj-$(CONFIG_BLK_DEV_AEC62XX)		+= aec62xx.o
obj-$(CONFIG_BLK_DEV_ALI15X3)		+= alim15x3.o
obj-$(CONFIG_BLK_DEV_AMD74XX)		+= amd74xx.o
obj-$(CONFIG_BLK_DEV_ATIIXP)		+= atiixp.o
obj-$(CONFIG_BLK_DEV_CELLEB)		+= scc_pata.o
obj-$(CONFIG_BLK_DEV_CMD64X)		+= cmd64x.o
obj-$(CONFIG_BLK_DEV_CS5520)		+= cs5520.o
obj-$(CONFIG_BLK_DEV_CS5530)		+= cs5530.o
obj-$(CONFIG_BLK_DEV_CS5535)		+= cs5535.o
obj-$(CONFIG_BLK_DEV_CS5536)		+= cs5536.o
obj-$(CONFIG_BLK_DEV_SC1200)		+= sc1200.o
obj-$(CONFIG_BLK_DEV_CY82C693)		+= cy82c693.o
obj-$(CONFIG_BLK_DEV_DELKIN)		+= delkin_cb.o
obj-$(CONFIG_BLK_DEV_HPT366)		+= hpt366.o
obj-$(CONFIG_BLK_DEV_IT8172)		+= it8172.o
obj-$(CONFIG_BLK_DEV_IT8213)		+= it8213.o
obj-$(CONFIG_BLK_DEV_IT821X)		+= it821x.o
obj-$(CONFIG_BLK_DEV_JMICRON)		+= jmicron.o
obj-$(CONFIG_BLK_DEV_NS87415)		+= ns87415.o
obj-$(CONFIG_BLK_DEV_OPTI621)		+= opti621.o
obj-$(CONFIG_BLK_DEV_PDC202XX_OLD)	+= pdc202xx_old.o
obj-$(CONFIG_BLK_DEV_PDC202XX_NEW)	+= pdc202xx_new.o
obj-$(CONFIG_BLK_DEV_PIIX)		+= piix.o
obj-$(CONFIG_BLK_DEV_RZ1000)		+= rz1000.o
obj-$(CONFIG_BLK_DEV_SVWKS)		+= serverworks.o
obj-$(CONFIG_BLK_DEV_SGIIOC4)		+= sgiioc4.o
obj-$(CONFIG_BLK_DEV_SIIMAGE)		+= siimage.o
obj-$(CONFIG_BLK_DEV_SIS5513)		+= sis5513.o
obj-$(CONFIG_BLK_DEV_SL82C105)		+= sl82c105.o
obj-$(CONFIG_BLK_DEV_SLC90E66)		+= slc90e66.o
obj-$(CONFIG_BLK_DEV_TC86C001)		+= tc86c001.o
obj-$(CONFIG_BLK_DEV_TRIFLEX)		+= triflex.o
obj-$(CONFIG_BLK_DEV_TRM290)		+= trm290.o
obj-$(CONFIG_BLK_DEV_VIA82CXXX)		+= via82cxxx.o

# Must appear at the end of the block
obj-$(CONFIG_BLK_DEV_GENERIC)		+= ide-pci-generic.o

obj-$(CONFIG_IDEPCI_PCIBUS_ORDER)	+= ide-scan-pci.o

obj-$(CONFIG_BLK_DEV_CMD640)		+= cmd640.o

obj-$(CONFIG_BLK_DEV_IDE_PMAC)		+= pmac.o

obj-$(CONFIG_IDE_H8300)			+= ide-h8300.o

obj-$(CONFIG_IDE_GENERIC)		+= ide-generic.o
obj-$(CONFIG_BLK_DEV_IDEPNP)		+= ide-pnp.o

ide-gd_mod-y += ide-gd.o
ide-cd_mod-y += ide-cd.o ide-cd_ioctl.o ide-cd_verbose.o

ifeq ($(CONFIG_IDE_GD_ATA), y)
	ide-gd_mod-y += ide-disk.o ide-disk_ioctl.o
ifeq ($(CONFIG_IDE_PROC_FS), y)
	ide-gd_mod-y += ide-disk_proc.o
endif
endif

ifeq ($(CONFIG_IDE_GD_ATAPI), y)
	ide-gd_mod-y += ide-floppy.o ide-floppy_ioctl.o
ifeq ($(CONFIG_IDE_PROC_FS), y)
	ide-gd_mod-y += ide-floppy_proc.o
endif
endif

obj-$(CONFIG_IDE_GD)			+= ide-gd_mod.o
obj-$(CONFIG_BLK_DEV_IDECD)		+= ide-cd_mod.o
obj-$(CONFIG_BLK_DEV_IDETAPE)		+= ide-tape.o

obj-$(CONFIG_BLK_DEV_IDECS)		+= ide-cs.o

obj-$(CONFIG_BLK_DEV_PLATFORM)		+= ide_platform.o

obj-$(CONFIG_BLK_DEV_IDE_ICSIDE)	+= icside.o
obj-$(CONFIG_BLK_DEV_IDE_RAPIDE)	+= rapide.o
obj-$(CONFIG_BLK_DEV_PALMCHIP_BK3710)	+= palm_bk3710.o

obj-$(CONFIG_BLK_DEV_IDE_AU1XXX)	+= au1xxx-ide.o

obj-$(CONFIG_BLK_DEV_IDE_TX4938)	+= tx4938ide.o
obj-$(CONFIG_BLK_DEV_IDE_TX4939)	+= tx4939ide.o
obj-$(CONFIG_BLK_DEV_IDE_AT91)		+= at91_ide.o

```

Looks to me like this file was meant to be built with the whole kernel maybe called by the root Makefile. But then again I'm no expert.

(30 minutes later)

I think I got it! I read through the README in the root kernel source directory and did:

```

make menuconfig
make drivers/ide/ide-generic.ko

```

and sure enough I got the file! Now I just have to do the same thing on the server add the newly created module right?

Do I have to use the source from the same kernel? Or can I use the source for the latest kernel (that's what I just did)?

~Isaac

---

### Post by BkkBonanza on 2009-04-06
The kernel / module sources tend to be picky. You should use the same versions unless you know differently in a particular case. Some module or driver sources are meant to work against several versions (like compat-wireless) but often they will fail without the correct version kernel source.

---

### Post by HermanAB on 2009-04-06
First compile and install the kernel unmodified in order to ensure that it works correctly.  Then install the modified module and recompile - only the one that changed will actually compile so this time it will be quick.  Some Googling will find you many howtos.

---

### Post by shinobitux on 2009-04-07
Thanks for all the help guys. My associate has had the server down for the last couple days so I'll try compiling the module as soon as he's got it hooked up.

The only thing I'm worried about is the fact that he's not going to want to manually manage and update his kernel, so I'll have to leave the ubuntu 2.6.27-11-server kernel installed. The linux-headers package for 2.6.27-11-server doesn't contain the necessary source to compile ide-generic.ko but I'll see if I can use the missing *.c and headers from the kernel.org sources.

Again, thanks guys!

~shinobitux

---

