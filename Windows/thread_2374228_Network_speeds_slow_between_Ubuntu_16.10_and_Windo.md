---
title: "Network speeds slow between Ubuntu 16.10 and Windows 10"
date: 2017-10-13
forum: Windows
---

### Post by illectronic on 2017-10-13
I have windows 10 with the Ubuntu Linux subsystem acting as a server.  It also has as an SMB share. The other box is an actual ubuntu installation.
All machines have modern SSD drives
I have eliminated any potential issues with cabling or switches by using a direct connection. Even with the cat6 cable directly connecting the two machines it gets only 30MB/s over rsync SSH to the Windows box from the Ubuntu box and 20MB/S from Windows to Ubuntu. The same speeds occur with SMB transfers to and from.
I have also changed the NIC cards. The windows box has a PCIE Intel NIC card. The Ubuntu box has a USB 3.0 gigabit startech USB adapter.

When I transfer to and from my macbook air to the Windows Box, I get 60/MB sec.  Something tells me something is restricting speeds on the Ubuntu Box. Since it happens with any protocol or NIC that I have tried, I am stumped as to what it can be.

Thanks in advance

---

### Post by praseodym on 2017-10-13
Please show the outputs from your server:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by illectronic on 2017-10-15
Weird it's not listing the USB NIC

```

root@dell-laptop:/home/oren# lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 79)
    Subsystem: Intel Corporation Wireless 3165 [8086:4410]
    Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:0768]
    Kernel modules: r8169
root@dell-laptop:/home/oren# lsmod
Module                  Size  Used by
md4                    16384  0
ax88179_178a           28672  0
rfcomm                 77824  0
nls_utf8               16384  1
cifs                  704512  2
ccm                    20480  0
fscache                61440  1 cifs
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
dell_led               16384  1
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
rtsx_usb_ms            20480  0
rtsx_usb_sdmmc         28672  0
memstick               16384  1 rtsx_usb_ms
usbnet                 45056  1 ax88179_178a
mii                    16384  2 usbnet,ax88179_178a
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_multitouch         20480  0
nls_iso8859_1          16384  1
snd_soc_skl            65536  0
snd_soc_skl_ipc        49152  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        28672  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
snd_soc_core          233472  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
intel_rapl             20480  0
snd_pcm_dmaengine      16384  1 snd_soc_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_intel          36864  3
kvm_intel             200704  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
i2c_designware_platform    16384  0
kvm                   593920  1 kvm_intel
i2c_designware_core    20480  1 i2c_designware_platform
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
btusb                  45056  0
dell_laptop            20480  0
dell_smbios            16384  3 dell_wmi,dell_led,dell_laptop
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
dcdbas                 16384  1 dell_smbios
irqbypass              16384  1 kvm
arc4                   16384  2
btrtl                  16384  1 btusb
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
dell_smm_hwmon         16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_seq_midi           16384  0
pcbc                   16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
aesni_intel           167936  0
snd_rawmidi            32768  1 snd_seq_midi
iwlmvm                372736  0
mac80211              782336  1 iwlmvm
aes_x86_64             20480  1 aesni_intel
wl                   6447104  0
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
uvcvideo               90112  0
iwlwifi               225280  1 iwlmvm
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
input_leds             16384  0
joydev                 20480  0
videobuf2_vmalloc      16384  1 uvcvideo
serio_raw              16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
snd                    77824  19 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
cfg80211              602112  4 wl,iwlmvm,iwlwifi,mac80211
soundcore              16384  1 snd
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
idma64                 20480  0
virt_dma               16384  1 idma64
shpchp                 36864  0
processor_thermal_device    16384  0
mei_me                 40960  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_pch_thermal      16384  0
mei                   102400  1 mei_me
intel_lpss_pci         16384  0
hci_uart               98304  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
int3403_thermal        16384  0
bluetooth             557056  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
int3400_thermal        16384  0
int3402_thermal        16384  0
dell_rbtn              16384  0
acpi_thermal_rel       16384  1 int3400_thermal
intel_lpss_acpi        16384  0
industrialio           69632  2 acpi_als,kfifo_buf
tpm_crb                16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
acpi_pad              180224  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
mac_hid                16384  0
nfsd                  339968  1
auth_rpcgss            61440  1 nfsd
nfs_acl                16384  1 nfsd
lockd                  94208  1 nfsd
parport_pc             32768  0
grace                  16384  2 nfsd,lockd
ppdev                  20480  0
sunrpc                335872  5 auth_rpcgss,nfsd,nfs_acl,lockd
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
amdgpu               1560576  1
i915                 1449984  103
ttm                    98304  1 amdgpu
i2c_algo_bit           16384  2 amdgpu,i915
drm_kms_helper        151552  2 amdgpu,i915
psmouse               139264  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  8 amdgpu,i915,ttm,drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
wmi                    16384  2 dell_wmi,dell_led
i2c_hid                20480  0
hid                   118784  2 i2c_hid,hid_multitouch
pinctrl_sunrisepoint    28672  0
video                  40960  3 dell_wmi,dell_laptop,i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   77824  0
root@dell-laptop:/home/oren# ifconfig -a
enx00249b297f12 Link encap:Ethernet  HWaddr 00:24:9b:29:7f:12  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c502:a2e:8c3a:2c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:952199 (952.1 KB)  TX bytes:233012 (233.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:436918 (436.9 KB)  TX bytes:436918 (436.9 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.10.10.10  P-t-P:10.10.10.9  Mask:255.255.255.255
          inet6 addr: fe80::f257:366e:556:88fb/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:526350 (526.3 KB)  TX bytes:103596 (103.5 KB)

wlp2s0    Link encap:Ethernet  HWaddr 70:1c:e7:44:27:62  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@dell-laptop:/home/oren# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

root@dell-laptop:/home/oren# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
root@dell-laptop:/home/oren# 


```

---

### Post by illectronic on 2017-10-18
bump

---

### Post by Morbius1 on 2017-10-19
I know this isn't helpful but you have a rather unique situation here.

You aren't running Ubuntu as a stand alone system. You are running it under Win10 using it's [COLOR=#0000cd]Windows Subsystem for Linux. [/COLOR][COLOR=#000000]

It's hard enough to determine speed issues with a stand alone system let alone one that is running as a service within another OS. It just seems to be more a question for a Windows 10 forum.[/COLOR]
[h=2][/h]

---

### Post by howefield on 2017-10-19
Thread moved to the "*Windows*" sub forum.

---

### Post by illectronic on 2017-10-19
Then why would transfers from os x be faster to windows? I think this is a ubuntu issue. Move it back please.

---

