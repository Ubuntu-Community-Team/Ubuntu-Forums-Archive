---
title: "boyyyy 2 SCSI boards (LSI Megarais onbord) (Adaptec PCI)"
date: 2009-04-02
forum: Server Platforms
---

### Post by lerberus on 2009-04-02
ubuntu server 8.10
This post will probably have no replies. Well here it goes.

I have 2 SCSI boards in this server:
 - LSIMegaraid onboard with 4 300.gb physical hard drives. 2 virtual raid 1.
 
- Adaptec ASC-39320A (PCI Externel) that connects to a Dynamic Storage Factory 16 hard drive vault. Only have 13 drives here :(.

The LSIMegaraid is working fine and mounted correctly only showing 2 300.gb drives (the other 2 are just mirrored copies).


Now the PCI Adaptec SCSI... no way of getting it to work. It does not get detected... it think :)

system info, if any more info let me know:

**they show up in the PCI directive $ lspci**
00:00.0 Host bridge: Intel Corporation 5000P Chipset Memory Controller Hub (rev 92)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 2-3 (rev 92)
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 92)
00:04.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 4-5 (rev 92)
00:05.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 (rev 92)
00:06.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 6-7 (rev 92)
00:07.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 (rev 92)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 92)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 92)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 92)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 92)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.2 SATA controller: Intel Corporation 631xESB/632xESB SATA AHCI Controller (rev 09)
00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)
01:00.0 PCI bridge: Intel Corporation 80333 Segment-A PCI Express-to-PCI Express Bridge
01:00.2 PCI bridge: Intel Corporation 80333 Segment-B PCI Express-to-PCI Express Bridge
02:0e.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS
05:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09)
05:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B (rev 09)
**07:08.0 SCSI storage controller: Adaptec ASC-39320A U320 (rev 10)**
**07:08.1 SCSI storage controller: Adaptec ASC-39320A U320 (rev 10)**
09:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
09:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
0a:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
0a:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)
0a:02.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E3 (rev 01)
10:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev b5)
11:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5715 Gigabit Ethernet (rev a3)
11:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5715 Gigabit Ethernet (rev a3)
12:05.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)


**But when I $ lsscsi**
[0:2:0:0]    disk    LSI      MegaRAID SAS RMB 1.02  -       
[0:2:1:0]    disk    LSI      MegaRAID SAS RMB 1.02  -       
[9:0:0:0]    cd/dvd  HL-DT-ST DVD-ROM GDR8082N 0B11  -

**Also, when I  $ cat /proc/scsi/scsi**
Attached devices:
Host: scsi0 Channel: 02 Id: 00 Lun: 00
  Vendor: LSI      Model: MegaRAID SAS RMB Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 02 Id: 01 Lun: 00
  Vendor: LSI      Model: MegaRAID SAS RMB Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi9 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVD-ROM GDR8082N Rev: 0B11
  Type:   CD-ROM                           ANSI  SCSI revision: 05


Any scsi genius around that could help?

Thanks in advance
Pedro
p.s.ubuntu rules... except for the scsi part :)

---

### Post by petersenmde on 2009-04-02
I'm using this same Adaptec pci card in my Dell PowerEdge 2900 with Dell's version of the LSI Megaraid.This is Ubuntu 8.04 LTS server which uses the 2.6.24-23-server kernel.
I have a DLT tape backup hooked internally to the Adaptec card.

Maybe the driver is not loaded? I think it is called aic79xx.

Mark

---

### Post by lerberus on 2009-04-03
Uffff.... one reply.

I thinkk the driver is loaded:# lsmod

Module                  Size  Used by
binfmt_misc            16904  1
rfcomm                 44432  0
sco                    18308  2
bridge                 56980  0
stp                    10628  1 bridge
bnep                   20480  2
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0
speedstep_lib          12676  0
cpufreq_conservative    14600  0
cpufreq_powersave       9856  0
cpufreq_stats          13188  0
cpufreq_userspace      11396  0
cpufreq_ondemand       14988  0
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0
wmi                    14504  0
video                  25232  0
output                 11008  1 video
sbs                    19464  0
sbshc                  13440  1 sbs
battery                18436  0
ipv6                  263460  39
ipt_LOG                13700  4
iptable_mangle         10880  0
iptable_nat            13448  0
nf_nat                 25368  1 iptable_nat
nf_conntrack_ipv4      21900  3 iptable_nat,nf_nat
nf_conntrack           72032  3 iptable_nat,nf_nat,nf_conntrack_ipv4
af_packet              25600  2
iptable_filter         10752  1
ip_tables              19600  3 iptable_mangle,iptable_nat,iptable_filter
x_tables               22916  3 ipt_LOG,iptable_nat,ip_tables
ac                     12292  0
lp                     17156  0
loop                   23180  0
evdev                  17696  6
iTCO_wdt               18596  0
psmouse                45200  0
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13444  0
pcspkr                 10624  0
parport_pc             39460  1
parport                42604  3 ppdev,lp,parport_pc
container              11520  0
button                 14224  0
i5000_edac             16900  0
edac_core              48300  3 i5000_edac
shpchp                 38164  0
pci_hotplug            34976  1 shpchp
ext3                  133000  1
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0
cdrom                  43040  1 sr_mod
pata_acpi              12160  0
usbhid                 35968  0
hid                    50560  1 usbhid
ata_piix               24708  0
sd_mod                 42392  3
crc_t10dif              9984  1 sd_mod
sg                     39220  0
ahci                   37004  0
tg3                   130308  0
ata_generic            12804  0
libphy                 27392  1 tg3
libata                176928  4 pata_acpi,ata_piix,ahci,ata_generic
ehci_hcd               44428  0
uhci_hcd               30864  0
dock                   16656  1 libata
usbcore               149872  4 usbhid,ehci_hcd,uhci_hcd
[B]aic79xx               181464  0
scsi_transport_spi     30336  1 aic79xx[/B]
megaraid_sas           38320  2
scsi_mod              155212  7 sr_mod,sd_mod,sg,libata,aic79xx,scsi_transport_spi,megaraid_sas
raid10                 30592  0
raid456               134928  0
async_xor              10496  1 raid456
async_memcpy            9728  1 raid456
async_tx               11008  3 raid456,async_xor,async_memcpy
xor                    23688  2 raid456,async_xor
raid1                  30080  0
raid0                  15488  0
multipath              15104  0
linear                 13440  0
md_mod                 93596  6 raid10,raid456,raid1,raid0,multipath,linear
thermal                23708  0
processor              42284  1 thermal
fan                    12420  0
fbcon                  47392  0
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60700  1


Thanks.

---

### Post by lerberus on 2009-04-03
SOLVED:
It had to be something stupid... the scsi termination plugs for the unused scsi ports on the vault.

Thanks Mark.

---

