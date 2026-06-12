---
title: "[Ubuntu 14.04] Ethernet Network"
date: 2016-01-24
forum: Ubuntu/Debian BASED
---

### Post by pawel16 on 2016-01-24
The Problem
Linux Lite (Ubuntu 14.04) do not want to connect with Ethernet.
I always see "Ethernet Network disconnected, but under windows
everything is fine. Linux see wifi networks and they work.

The Background:
I had an issue with my system tray so I used this
commands:
xfce4-panel --quit ; pkill xfconfd ; rm -rf ~/.config/xfce4; rm -rf ~/.config/xfce4-session ; cp -Rf /etc/skel/.config/xfce4 ~/.config/xfce4; cp -Rf /etc/skel/.config/xfce4-session ~/.config/xfce4-session ; xfce4-panel
which helped me and tray icons start to be visible, but after one day I don't have an Internet access

The Question:
How can I connect to the Internet by LAN-cable
under Linux Lite (Ubuntu 14.04)?

Some terminal outputs of these commands
which can probably help recognize my problem:
uname -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
[HTML]
jonatan@linuxlite-computer:~$ uname -a
Linux linuxlite-computer 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
jonatan@linuxlite-computer:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1096]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: AzureWave AW-NE139H Half-size Mini PCIe Card [1a3b:1139]
    Kernel driver in use: rtl8192ce
jonatan@linuxlite-computer:~$ lsmod
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
msi_wmi                13354  0 
msi_laptop             15774  0 
sparse_keymap          13948  2 msi_laptop,msi_wmi
arc4                   12608  2 
rtl8192ce              53550  0 
dm_multipath           22873  0 
ip6t_REJECT            12939  1 
xt_hl                  12521  6 
rfcomm                 69160  4 
scsi_dh                14882  1 dm_multipath
bnep                   19624  2 
ip6t_rt                13537  3 
bluetooth             391136  10 bnep,rfcomm
rtl_pci                26690  1 rtl8192ce
nf_conntrack_ipv6      18894  8 
kvm_amd                60026  0 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
snd_hda_codec_realtek    65812  1 
rtlwifi                63475  2 rtl_pci,rtl8192ce
ipt_REJECT             12541  1 
xt_LOG                 17717  10 
kvm                   455843  1 kvm_amd
xt_limit               12711  13 
snd_hda_codec_hdmi     46368  1 
rtl8192c_common        53172  1 rtl8192ce
xt_tcpudp              12884  18 
xt_addrtype            12635  4 
snd_hda_intel          56531  5 
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
mac80211              630728  3 rtl_pci,rtlwifi,rtl8192ce
xt_conntrack           12760  16 
snd_hwdep              13602  1 snd_hda_codec
joydev                 17381  0 
binfmt_misc            17468  1 
rts5139               335409  0 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nf_nat_ftp             12770  0 
nf_nat                 21841  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           97202  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
serio_raw              13462  0 
cfg80211              484040  2 mac80211,rtlwifi
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
k10temp                13126  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22155  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx               12457899  112 
snd_rawmidi            30144  1 snd_seq_midi
shpchp                 37032  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
amd_iommu_v2           19054  1 fglrx
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
pata_acpi              13038  0 
psmouse               106692  0 
r8169                  71677  0 
mii                    13934  1 r8169
pata_atiixp            13271  0 
ahci                   34091  2 
libahci                32716  1 ahci
wmi                    19177  1 msi_wmi
video                  19476  0 
jonatan@linuxlite-computer:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
pre-up ifconfig eth0 hw ether 6C:62:6D:2F:5F:9C
jonatan@linuxlite-computer:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search ds14.agh.edu.pl
jonatan@linuxlite-computer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.203.0.1      0.0.0.0         UG    0      0        0 wlan0
10.203.0.0      0.0.0.0         255.255.255.0   U     9      0        0 wlan0
jonatan@linuxlite-computer:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:2f:5f:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:121916 (121.9 KB)  TX bytes:121916 (121.9 KB)

wlan0     Link encap:Ethernet  HWaddr e0:b9:a5:34:5c:e6  
          inet addr:10.203.0.186  Bcast:10.203.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e2b9:a5ff:fe34:5ce6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:307359 (307.3 KB)  TX bytes:137324 (137.3 KB)
[/HTML]

---

### Post by howefield on 2016-01-24
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

