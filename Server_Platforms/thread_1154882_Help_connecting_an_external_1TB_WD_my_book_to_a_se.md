---
title: "Help connecting an external 1TB WD my book to a server"
date: 2009-05-10
forum: Server Platforms
---

### Post by Astro6312 on 2009-05-10
All,

I have an old DELL 600SC server with ubuntu 8.4 LTS server and a 1TB western digital my book connected to a USB port.  I am using this external drive for backup.  The problem I have is the USB port is USB 1.1.  It is painfully slow and sometimes causes timeout of large files transfers.

I am looking to connect to a faster port.  This my book as USB 2, Firewire and ESata ports. My server has some [free PCI ports]("http://www.2cpu.com/articles/38_1.html")

My options are:
[LIST]
[*] Esata PCI card
[*] USB2 PCI card
[*] Firewire PCI card
[/LIST]

Any advice on which one will work faster and any suggestion on which card is well supported on Ubuntu 8.04 LTS server.

I have researched for hours and not sure what is the best approach and which chipset will work with Ubuntu.  

Quite hard to make a choice.  Any real world experience is appreciated.

Some information on my system:
```
**lspci**
00:00.0 Host bridge: Broadcom GCNB-LE Host Bridge (rev 32)
00:00.1 Host bridge: Broadcom GCNB-LE Host Bridge
00:02.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 RAID bus controller: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID (rev 01)
00:08.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0e.0 IDE interface: Broadcom CSB6 IDE Controller (rev a0)
00:0f.0 Host bridge: Broadcom CSB6 South Bridge (rev a0)
00:0f.1 IDE interface: Broadcom CSB6 RAID/IDE Controller (rev a0)
00:0f.2 USB Controller: Broadcom CSB6 OHCI USB Controller (rev 05)
00:0f.3 ISA bridge: Broadcom GCLE-2 Host Bridge

```
```

**lsusb**
Bus 001 Device 003: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000  
```

```
**dmesg | grep -i book**
[ 2432.111310] input: Western Digital My Book as /devices/pci0000:00/0000:00:0f.2/usb1/1-1/1-1:1.1/input/input3
[ 2432.139922] input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:0f.2-1
[ 2437.375986] scsi 5:0:0:0: Direct-Access     WD       My Book          1016 PQ: 0 ANSI: 4

```

```
**lsmod**
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14592  1 
fat                    54300  1 vfat
usb_storage            73408  1 
libusual               18980  1 usb_storage
nfnetlink_queue        13120  1 
nfnetlink               5784  2 nfnetlink_queue
nf_conntrack_ipv4      19080  3 
ipt_REJECT              5632  1 
xt_tcpudp               4096  4 
ipt_iprange             2688  4 
xt_state                3328  3 
nf_conntrack           66752  2 nf_conntrack_ipv4,xt_state
xt_mark                 2816  6 
xt_NFQUEUE              2816  3 
iptable_filter          3840  1 
ip_tables              14820  1 iptable_filter
x_tables               16132  7 ipt_REJECT,xt_tcpudp,ipt_iprange,xt_state,xt_mark,xt_NFQUEUE,ip_tables
lp                     12324  0 
loop                   19076  0 
ipv6                  272804  22 
psmouse                40208  0 
serio_raw               7940  0 
dcdbas                  9508  0 
button                  9232  0 
evdev                  12928  0 
sworks_agp             10656  0 
i2c_piix4               9612  0 
agpgart                34760  1 sworks_agp
i2c_core               24832  1 i2c_piix4
parport_pc             36644  1 
parport                37704  2 lp,parport_pc
pcspkr                  4224  0 
ext3                  136584  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 32128  1 
hid                    38784  1 usbhid
sr_mod                 17828  0 
cdrom                  37280  1 sr_mod
pata_acpi               8320  0 
ata_generic             8324  0 
sg                     36496  0 
sd_mod                 30720  5 
ohci_hcd               25604  0 
pata_serverworks       11008  0 
usbcore               146028  6 usb_storage,libusual,usbhid,ohci_hcd
libata                159344  3 pata_acpi,ata_generic,pata_serverworks
3w_xxxx                27808  2 
scsi_mod              151180  6 usb_storage,sr_mod,sg,sd_mod,libata,3w_xxxx
e1000                 126656  0 
thermal                16796  0 
processor              37000  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

```

Thanks

Simon

---

### Post by Xipher on 2009-05-10
I'm thinking eSATA might be your best choice if you're looking for something that's going to be faster and designed for the I/O of disk access.

---

### Post by Astro6312 on 2009-05-10
Yes this is what I think also, the challenge is to find a PCI-Esata card that Ubuntu will auto-detect (install) and will work at 3Gbits/s.

Anyone know of a company/chip set that works fine, without having to fiddle with compiling drivers in the kernel, something I want to avoid.

Thanks

---

