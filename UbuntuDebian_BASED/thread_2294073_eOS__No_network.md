---
title: "eOS  No network"
date: 2015-09-09
forum: Ubuntu/Debian BASED
---

### Post by p.callan on 2015-09-09
Works for a second then stops. I get no wifi at all. Rebooting sometimes helps, sometimes not (wired). Writing this from phone. Took the following outputs from terminal. How can I solve this problem?
```

User@X552L:~$ uname -a
Linux X552L 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
user@X552L:~$ lspci -nnk | grep -iA2 net
02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave Device [1a3b:2161]
	Kernel driver in use: rtl8821ae
user@X552L:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 002 Device 014: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]
Bus 002 Device 009: ID 04e8:1f0a Samsung Electronics Co., Ltd 
Bus 002 Device 008: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 0951:1665 Kingston Technology 
Bus 002 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 002: ID 192f:0916 Avago Technologies, Pte. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@X552L:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
ctr                    13049  2 
ccm                    17773  2 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               410016  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69509  0 
wl                   6367833  0 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
arc4                   12608  2 
asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143630  0 
kvm                   452047  1 kvm_intel
snd_hda_codec_realtek    77514  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  4 
snd_hda_codec_hdmi     47548  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17393  0 
serio_raw              13483  0 
btusb                  32497  0 
bluetooth             446409  11 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
rtl8821ae             546666  0 
lpc_ich                21093  0 
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
snd_soc_rt5640         93042  0 
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
mac80211              652777  1 rtl8821ae
snd_hwdep              17698  1 snd_hda_codec
snd_compress           19200  1 snd_soc_core
snd_pcm_dmaengine      15172  1 snd_soc_core
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
rtsx_pci_ms            18168  0 
cfg80211              498458  3 wl,mac80211,rtl8821ae
memstick               16966  1 rtsx_pci_ms
mei_me                 19696  0 
mei                    87875  1 mei_me
shpchp                 37047  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
dw_dmac                12835  0 
dw_dmac_core           28390  1 dw_dmac
snd                    79468  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
i2c_hid                18726  0 
soundcore              15047  2 snd,snd_hda_codec
snd_soc_sst_acpi       13007  0 
8250_dw                13551  0 
i2c_designware_platform    12979  0 
i2c_designware_core    14768  1 i2c_designware_platform
spi_pxa2xx_platform    23079  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
uas                    27255  0 
usb_storage            66545  2 uas
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  3 i2c_hid,hid_generic,usbhid
nouveau              1206535  1 
rtsx_pci_sdmmc         23043  0 
i915                  906106  6 
mxm_wmi                13021  1 nouveau
ttm                    93588  1 nouveau
i2c_algo_bit           13413  2 i915,nouveau
r8169                  71694  0 
mii                    13934  1 r8169
drm_kms_helper         61574  2 i915,nouveau
rtsx_pci               46259  2 rtsx_pci_ms,rtsx_pci_sdmmc
drm                   311018  8 ttm,i915,drm_kms_helper,nouveau
psmouse               106767  0 
ahci                   34142  2 
libahci                32424  1 ahci
wmi                    19193  3 mxm_wmi,nouveau,asus_wmi
video                  20128  3 i915,nouveau,asus_wmi
sdhci_acpi             13351  0 
sdhci                  43685  1 sdhci_acpi

``````

user@X552L:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MyNW 5Ghz"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: BC:AE:C5:EA:E5:1E   
          Bit Rate=6 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

tun0      no wireless extensions.

``````

user@X552L:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr ac:9e:17:0a:a1:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25240 (25.2 KB)  TX bytes:25240 (25.2 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.114.0.20  P-t-P:10.114.0.20  Mask:255.255.0.0
          inet6 addr: fd70:92a7:8b12:72::1012/112 Scope:Global
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6575547 errors:0 dropped:6572932 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1227 (1.2 KB)  TX bytes:9861302060 (9.8 GB)

wlan0     Link encap:Ethernet  HWaddr 54:27:1e:dc:c7:f9  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5627:1eff:fedc:c7f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:650 errors:0 dropped:1 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82436 (82.4 KB)  TX bytes:66845 (66.8 KB)

``````

user@X552L:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.114.0.1
nameserver 127.0.1.1

```

---

### Post by PaulW2U on 2015-09-09
*Thread moved to **Ubuntu/Debian BASED**.*

I've moved your thread here as you're not using an official flavour of Ubuntu. Please also use CODE tags when posting terminal output, thanks.

---

### Post by p.callan on 2015-10-10
So it has been a month and I'm still having these problems. Can anybody help please?

---

