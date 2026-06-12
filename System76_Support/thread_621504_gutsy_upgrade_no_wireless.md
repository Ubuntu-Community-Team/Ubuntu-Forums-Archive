---
title: "gutsy upgrade no wireless"
date: 2007-11-23
forum: System76 Support
---

### Post by dgermann on 2007-11-23
Hi--

Had wireless with 7.04 and now not.

Upgraded to Gutsy 7.10, and also tried this: [http://ubuntuforums.org/showthread.php?t=588510]("http://ubuntuforums.org/showthread.php?t=588510")

system is gazv4.

Thanks for your help!

---

### Post by daengbo on 2007-11-23
What kind of wireless card do you have? Is it an rt2500, rt61, or rt73?

---

### Post by dgermann on 2007-11-24
daengbo--

Thanks for helping!

Hmmm....

I do not know how to tell. I went to System>Preferences>Hardware (Device Manager) and find 82801 Mobile PCI Bridge, and a lot of numbers that start with 945GM, and 940 and 943, but nothing in the whole list that starts with rt, as far as I am seeing. Am I looking in the right place?

---

### Post by daengbo on 2007-11-24
Is your wireless built into the mother board?

---

### Post by dgermann on 2007-11-24
I am guessing so, since I do not have a pcmcia card.

Is there a way to tell other than that? With hardware I am at a loss.... :(

---

### Post by daengbo on 2007-11-25
You have an Intel chipset, so I guess you'll have an Intel Pro Wireless chip, which should be identified and useful under Gutsy.

Open a terminal and type 
lspci

and 

lsmod

Give us the results of those commands, please.

---

### Post by dgermann on 2007-11-25
daengbo--

Many thanks for your help!

OK, here goes:
```
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
doug@ubuntu:~$ lsmod
Module                  Size  Used by
xt_limit                3584  8 
xt_tcpudp               4224  10 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
nls_cp437               6784  3 
cifs                  237428  242 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
i915                   25856  2 
drm                    83348  3 i915
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  1227 
sbs                    19592  0 
button                  8976  438 
dock                   10656  0 
battery                11012  2582 
container               5504  0 
ac                      6148  27666 
asus_acpi              17308  161 
sbp2                   24072  0 
lp                     12580  0 
snd_hda_intel          22808  1803 
snd_hda_codec         207872  1 snd_hda_intel
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81156  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            35584  0 
joydev                 11328  0 
snd_seq_midi            9728  0 
pcmcia                 41388  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54384  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24580  2 snd_pcm,snd_seq
snd_seq_device          9740  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             37412  0 
parport                37448  3 ppdev,lp,parport_pc
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
sdhci                  18828  0 
mmc_core               28420  1 sdhci
pcspkr                  4224  0 
snd                    56580  1341 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
psmouse                39952  0 
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              25620  1 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  3 drm,intel_agp
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
evdev                  11136  6 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
r8169                  32260  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  7 dm_mirror,dm_snapshot
thermal                14344  270 
processor              32072  219 thermal
fan                     5764  5 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
doug@ubuntu:~$ 

```

---

### Post by pboggio on 2007-11-25
I believe i am having the same problem with my upgrade.  Only I did a clean upgrade.  Formatted the drive and did a fresh install of 7.10.  Now my wireless does not work.  I tried swapping out the wifi card  for another known good card and got the same result.
I can see the wireless network name, but I type in the passphase and it just hangs at "waiting for network key for the wireless network..." for a minute before dumping me back to the enter passphrase window.

Here is the output from my lspci and lsmod

```
******@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0e.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
00:0e.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
00:0e.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 70)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
******@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
sony_laptop            32088  0 
sonypi                 23960  0 
ppdev                  10244  0 
powernow_k7             8872  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k7,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
container               5504  0 
battery                11012  0 
button                  8976  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
ac                      6148  0 
af_packet              24840  2 
sg                     36764  0 
sd_mod                 30336  0 
sbp2                   24072  0 
lp                     12580  0 
loop                   19076  0 
joydev                 11328  0 
snd_via82xx_modem      16264  0 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx
acx                    98692  0 
snd_ac97_codec        100644  2 snd_via82xx_modem,snd_via82xx
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
ac97_bus                3200  1 snd_ac97_codec
usb_storage            73024  0 
snd_pcm                80388  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
pcmcia                 41388  0 
libusual               18448  1 usb_storage
psmouse                39952  0 
snd_seq_oss            33152  0 
pcspkr                  4224  0 
serio_raw               8068  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_viapro             10004  0 
via_ircc               27668  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
irda                  202300  1 via_ircc
i2c_core               26112  1 i2c_viapro
snd                    54660  14 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_via82xx_modem,snd_via82xx,snd_pcm
crc_ccitt               3072  1 irda
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  1 via_agp
evdev                  11136  7 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  5 sg,sd_mod,sbp2,usb_storage,libata
uhci_hcd               26640  0 
usbcore               138632  6 acx,usb_storage,libusual,usbhid,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
8139cp                 25088  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
thermal                14344  0 
processor              32072  2 powernow_k7,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

### Post by j.c.sackett on 2007-11-25
I believe my problem is the same--I have just purchased a darter ultra and on powering it up out of the box today I had no wireless. I ran the System76 driver and still no wireless.

---

### Post by thomasaaron on 2007-11-26
J.c.  sackett,

There is a button above your keyboard that will turn on your wireless.
It is the one to the right of the P2 button.

---

### Post by daengbo on 2007-11-26
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

This is the line that identifies your wireless card. It should be supported with a kernel driver. Have you visited System -> Administration -> Restricted Driver Manager to try selecting or deselecting the driver for the card? Are you sure that your wireless switch is on?

---

### Post by dgermann on 2007-11-26
Thomas--

Does that Fn-F2 on my GAZV4 have something to do with my issue? Following your post I played with it while connecting and now I am connected. Not sure what I did or if I can replicate it....

Thanks!

PS: Last night I was not even able to see from my laptop any signal at all from my router; tonight it is 80%. Last night it was raining steadily; tonight it is humid out, but not raining. Could that explain the signal strength?

---

### Post by thomasaaron on 2007-11-27
It kind of sounds like you have a buggy router.

Fn+F2 on the GazV4 should turn the wireless radio on and off.

---

### Post by dgermann on 2007-11-27
Thomas--

Thanks for your help, Thomas! ):P

Will have to check out the router. I went to a coffee shop tonight and was readily able to connect to their hot spot. Back in the office, the connection came up very quickly.

Actually have a second router (both are Netgear WNR854T) which when I get a free couple hours (got any to lend me? <grin>) I can put on line and see if it works better. I have not had good experiences with routers. About 5 months ago I replaced a Linksys router which had given me fits (it was actually a replacement of a prior linksys) with a new Netgear. Then in November that failed, Netgear issued me an rma and replaced the router. In the meantime I bought a new one which is the one currently up and running. So that makes wha?t--5 routers in 2 years! :)

---

### Post by thomasaaron on 2007-11-28
Wow! There's some luck for ya!

I've been using the same ol' Linksys for three years with n'ere a problem. I know some people don't like Linksys, and I'd be happy to try a different one -- if this stupid thing would just break! :lolflag:

---

### Post by j.c.sackett on 2007-12-03
Thomas--

Thanks so much. I can't believe that was the source of my problem.

I feel like a nitwit, but I've got a wireless connection! :-P

---

