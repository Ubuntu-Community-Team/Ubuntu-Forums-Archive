---
title: "WIFI not working (no access points available)"
date: 2017-04-07
forum: Ubuntu/Debian BASED
---

### Post by tomstorey on 2017-04-07
I have been using Elementary OS on my laptop for a little while now and decided to dual boot it on my PC alongside Windows 10. However it can't detect my home wifi whilst Windows 10 detects it just fine. When i go to connect to a network it says there are no access points available. I'd really appreciate any help people can give.

Thanks in advance

---

### Post by howefield on 2017-04-07
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by tomstorey on 2017-04-10
Any help? I think it could be something to do with an old kernel

---

### Post by kc1di on 2017-04-10
Let's start with a look at your setup - can you go to a terminal and type the following commands and post the output here. I'm assuming you have ethernet access.

```
lshw -C network
lsmod
rfkill list
ifconfig
```

---

### Post by tomstorey on 2017-04-10
Thanks a lot for the help! I do yes, here are the outputs:

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 06
       serial: 74:d4:35:5e:d4:b2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:29 ioport:d000(size=256) memory:fe800000-fe800fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: RTL8192CE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 01
       serial: 80:1f:02:e1:76:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=4.4.0-72-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:c000(size=256) memory:fe700000-fe703fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp2s0u1u3
       serial: 02:20:37:05:07:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.63 link=yes multicast=yes

Module                  Size  Used by
rndis_host             16384  0
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
nvram                  16384  0
video                  40960  0
msr                    16384  0
joydev                 20480  0
input_leds             16384  0
wl                   6447104  0
kvm_amd                65536  0
kvm                   544768  1 kvm_amd
arc4                   16384  2
rtl8192ce              57344  0
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        53248  1 rtl8192ce
irqbypass              16384  1 kvm
rtlwifi                77824  3 rtl_pci,rtl8192c_common,rtl8192ce
mac80211              737280  3 rtl_pci,rtlwifi,rtl8192ce
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
snd_hda_intel          40960  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
cfg80211              565248  3 wl,mac80211,rtlwifi
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              16384  1 snd_hda_codec
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_seq_midi           16384  0
gf128mul               16384  1 lrw
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              16384  0
shpchp                 36864  0
edac_mce_amd           24576  0
edac_core              53248  0
fam15h_power           16384  0
i2c_piix4              24576  0
k10temp                16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
pata_acpi              16384  0
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  9
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        155648  1 radeon
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  7 ttm,drm_kms_helper,radeon
pata_atiixp            16384  0
ahci                   36864  2
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  2 r8169,usbnet
fjes                   28672  0


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


enp2s0u1u3 Link encap:Ethernet  HWaddr 02:20:37:05:07:01  
          inet addr:192.168.42.63  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::640f:9691:e9ff:d609/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6546 errors:1 dropped:0 overruns:0 frame:1
          TX packets:5019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6458215 (6.4 MB)  TX bytes:923217 (923.2 KB)

enp3s0    Link encap:Ethernet  HWaddr 74:d4:35:5e:d4:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:126309 (126.3 KB)  TX bytes:126309 (126.3 KB)

wlp5s0    Link encap:Ethernet  HWaddr 80:1f:02:e1:76:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Hope this helps

---

### Post by tomstorey on 2017-04-12
Anyone know what the issue is?

---

