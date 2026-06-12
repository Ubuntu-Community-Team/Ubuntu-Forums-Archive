---
title: "Uue 5.7 wireless not connecting"
date: 2018-07-03
forum: Ubuntu/Debian BASED
---

### Post by PaulinPattaya on 2018-07-03
OK, I'm not totally new to Linux, but not a guru either.   I have a new install of Ubuntu Ultimate Edition 5.7 64 bit on an HP laptop with all the updates available.   My wireless card detects my router, but will not connect to it for some reason, I've been through similar threads trying the fixes and advice others have had with no success.   Help please.

---

### Post by praseodym on 2018-07-04
Please run the wireless scipt from the sticky thread and show the outputs

---

### Post by PaulinPattaya on 2018-07-04
Not sure Ii'm running the command you want, but here's the output from what I ran.
```
 description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: wlp19s0
       version: ff
       serial: 68:14:01:20:e1:25
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.13.0-46-generic firmware=N/A latency=255 link=no maxl
atency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
       resources: irq:16 ioport:3000(size=256) memory:c2000000-c2003fff

```

---

### Post by praseodym on 2018-07-05
Please show
```

lspci -nnk
lsmod
dmesg | grep key
```

---

### Post by PaulinPattaya on 2018-07-05
```
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
        Subsystem: Hewlett-Packard Company Haswell-ULT DRAM Controller [103c:80c4]
        Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b
)
        Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller [103c:80c4]
        Kernel driver in use: i915
        Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
        Subsystem: Hewlett-Packard Company Haswell-ULT HD Audio Controller [103c:80c4]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0a03] (rev 0b)
        Subsystem: Hewlett-Packard Company Device [103c:80c4]
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series USB xHCI HC [103c:80c4]
        Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series HECI [103c:80c4]
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series HD Audio Controller [103c:80c4]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 5 [8086:9c18] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 6 [8086:9c1a] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series LPC Controller [103c:80c4]
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series SATA Controller 1 [AHCI mode] [103c:80c4]
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series SMBus Controller [103c:80c4]
        Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 8 Series Thermal [8086:9c24] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series Thermal [103c:80c4]
        Kernel driver in use: intel_pch_thermal
        Kernel modules: intel_pch_thermal
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet control
ler [10ec:8136] (rev 07)
        Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80c2]
        Kernel driver in use: r8169
        Kernel modules: r8169
0d:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / 
M430] [1002:6660] (rev 83)
        Subsystem: Hewlett-Packard Company Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430] [103c:80c4]
        Kernel driver in use: radeon
        Kernel modules: radeon, amdgpu
13:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
        Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
        Kernel driver in use: rtl8723be
        Kernel modules: rtl8723be, wl

```

```
Module                  Size  Used by
rfcomm                 77824  14
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_soc_rt298          36864  0
snd_hda_codec_realtek    98304  1
snd_soc_rt286          40960  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
cmac                   16384  1
snd_soc_ssm4567        16384  0
snd_soc_rl6347a        16384  2 snd_soc_rt298,snd_soc_rt286
wl                   6447104  0
snd_hda_intel          40960  4
snd_soc_core          229376  3 snd_soc_ssm4567,snd_soc_rt298,snd_soc_rt286
bnep                   20480  2
crct10dif_pclmul       16384  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_compress           20480  1 snd_soc_core
crc32_pclmul           16384  0
arc4                   16384  2
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
pcbc                   16384  0
ac97_bus               16384  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm                98304  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_hda_codec_hdmi,snd_soc_rt29
8,snd_soc_rt286,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               90112  0
aesni_intel           188416  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
crypto_simd            16384  1 aesni_intel
btusb                  45056  0
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
glue_helper            16384  1 aesni_intel
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
media                  40960  2 uvcvideo,videodev
rtl8723be              98304  0
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
btintel                16384  1 btusb
btcoexist             131072  1 rtl8723be
hp_wmi                 16384  0
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
bluetooth             544768  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb
mac80211              782336  3 rtl_pci,rtlwifi,rtl8723be
joydev                 20480  0
ecdh_generic           24576  1 bluetooth
intel_cstate           20480  0
intel_rapl_perf        16384  0
input_leds             16384  0
serio_raw              16384  0
sparse_keymap          16384  1 hp_wmi
snd                    81920  21 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_
codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
intel_pch_thermal      16384  0
cfg80211              614400  3 wl,mac80211,rtlwifi
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
wmi_bmof               16384  0
shpchp                 36864  0
processor_thermal_device    16384  0
snd_soc_sst_acpi       16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
lpc_ich                24576  0
binfmt_misc            20480  1
int3403_thermal        16384  0
dw_dmac                16384  0
mac_hid                16384  0
tpm_crb                16384  0
8250_dw                16384  0
spi_pxa2xx_platform    24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_pad              180224  0
hp_wireless            16384  0
int3406_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
dw_dmac_core           24576  1 dw_dmac
kvm                   589824  0
irqbypass              16384  1 kvm
sunrpc                335872  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
btrfs                1097728  0
xor                    24576  1 btrfs
raid6_pq              118784  1 btrfs
amdgpu               2019328  0
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
i915                 1822720  26
radeon               1478656  1
ttm                    94208  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
psmouse               147456  0
drm_kms_helper        167936  3 amdgpu,radeon,i915
ahci                   36864  1
syscopyarea            16384  1 drm_kms_helper
libahci                32768  1 ahci
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
drm                   360448  15 amdgpu,radeon,i915,ttm,drm_kms_helper
mii                    16384  1 r8169
wmi                    24576  2 wmi_bmof,hp_wmi
sdhci_acpi             16384  0
video                  40960  2 int3406_thermal,i915
sdhci                  45056  1 sdhci_acpi
i2c_hid                20480  0
hid                   118784  1 i2c_hid
```

```
[    1.389164] Initialise system trusted keyrings
[    1.392620] Asymmetric key parser 'x509' registered
[    1.547959] Loaded X.509 cert 'Build time autogenerated kernel key: d56b251149d5ea1d12d54032a8b6a4c4d5cc0c81'
[    1.549867] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.551281] Key type big_key registered
[   23.978139] input: HP Wireless hotkeys as /devices/virtual/input/input7
[   26.554578] input: HP WMI hotkeys as /devices/virtual/input/input8
[   28.219600] wl: module verification failed: signature and/or required key missing - tainting kernel

```

---

### Post by wildmanne39 on 2018-07-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

In the future please put all this information into one post using code tags instead of creating several posts one after the other.

Thanks

---

### Post by PaulinPattaya on 2018-07-05
Roger wilco, my apologies but I just woke up and haven't had my coffee yet, just trying to reply promptly because I know I'm in a different time zone than most.

lspci -nnk

```

00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
        Subsystem: Hewlett-Packard Company Haswell-ULT DRAM Controller [103c:80c4]
        Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b
)
        Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller [103c:80c4]
        Kernel driver in use: i915
        Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
        Subsystem: Hewlett-Packard Company Haswell-ULT HD Audio Controller [103c:80c4]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0a03] (rev 0b)
        Subsystem: Hewlett-Packard Company Device [103c:80c4]
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series USB xHCI HC [103c:80c4]
        Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series HECI [103c:80c4]
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series HD Audio Controller [103c:80c4]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 5 [8086:9c18] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 6 [8086:9c1a] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series LPC Controller [103c:80c4]
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series SATA Controller 1 [AHCI mode] [103c:80c4]
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series SMBus Controller [103c:80c4]
        Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 8 Series Thermal [8086:9c24] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series Thermal [103c:80c4]
        Kernel driver in use: intel_pch_thermal
        Kernel modules: intel_pch_thermal
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet control
ler [10ec:8136] (rev 07)
        Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80c2]
        Kernel driver in use: r8169
        Kernel modules: r8169
0d:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / 
M430] [1002:6660] (rev 83)
        Subsystem: Hewlett-Packard Company Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430] [103c:80c4]
        Kernel driver in use: radeon
        Kernel modules: radeon, amdgpu
13:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
        Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
        Kernel driver in use: rtl8723be
        Kernel modules: rtl8723be, wl
```

lsmod
```


Module                  Size  Used by
rfcomm                 77824  14
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_soc_rt298          36864  0
snd_hda_codec_realtek    98304  1
snd_soc_rt286          40960  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
cmac                   16384  1
snd_soc_ssm4567        16384  0
snd_soc_rl6347a        16384  2 snd_soc_rt298,snd_soc_rt286
wl                   6447104  0
snd_hda_intel          40960  4
snd_soc_core          229376  3 snd_soc_ssm4567,snd_soc_rt298,snd_soc_rt286
bnep                   20480  2
crct10dif_pclmul       16384  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_compress           20480  1 snd_soc_core
crc32_pclmul           16384  0
arc4                   16384  2
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
pcbc                   16384  0
ac97_bus               16384  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm                98304  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_hda_codec_hdmi,snd_soc_rt29
8,snd_soc_rt286,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               90112  0
aesni_intel           188416  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
crypto_simd            16384  1 aesni_intel
btusb                  45056  0
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
glue_helper            16384  1 aesni_intel
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
media                  40960  2 uvcvideo,videodev
rtl8723be              98304  0
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
btintel                16384  1 btusb
btcoexist             131072  1 rtl8723be
hp_wmi                 16384  0
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
bluetooth             544768  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb
mac80211              782336  3 rtl_pci,rtlwifi,rtl8723be
joydev                 20480  0
ecdh_generic           24576  1 bluetooth
intel_cstate           20480  0
intel_rapl_perf        16384  0
input_leds             16384  0
serio_raw              16384  0
sparse_keymap          16384  1 hp_wmi
snd                    81920  21 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_
codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
intel_pch_thermal      16384  0
cfg80211              614400  3 wl,mac80211,rtlwifi
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
wmi_bmof               16384  0
shpchp                 36864  0
processor_thermal_device    16384  0
snd_soc_sst_acpi       16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
lpc_ich                24576  0
binfmt_misc            20480  1
int3403_thermal        16384  0
dw_dmac                16384  0
mac_hid                16384  0
tpm_crb                16384  0
8250_dw                16384  0
spi_pxa2xx_platform    24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_pad              180224  0
hp_wireless            16384  0
int3406_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
dw_dmac_core           24576  1 dw_dmac
kvm                   589824  0
irqbypass              16384  1 kvm
sunrpc                335872  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
btrfs                1097728  0
xor                    24576  1 btrfs
raid6_pq              118784  1 btrfs
amdgpu               2019328  0
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
i915                 1822720  26
radeon               1478656  1
ttm                    94208  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
psmouse               147456  0
drm_kms_helper        167936  3 amdgpu,radeon,i915
ahci                   36864  1
syscopyarea            16384  1 drm_kms_helper
libahci                32768  1 ahci
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
drm                   360448  15 amdgpu,radeon,i915,ttm,drm_kms_helper
mii                    16384  1 r8169
wmi                    24576  2 wmi_bmof,hp_wmi
sdhci_acpi             16384  0
video                  40960  2 int3406_thermal,i915
sdhci                  45056  1 sdhci_acpi
i2c_hid                20480  0
hid                   118784  1 i2c_hid
```

dmesg | grep key
```

[    1.389164] Initialise system trusted keyrings
[    1.392620] Asymmetric key parser 'x509' registered
[    1.547959] Loaded X.509 cert 'Build time autogenerated kernel key: d56b251149d5ea1d12d54032a8b6a4c4d5cc0c81'
[    1.549867] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.551281] Key type big_key registered
[   23.978139] input: HP Wireless hotkeys as /devices/virtual/input/input7
[   26.554578] input: HP WMI hotkeys as /devices/virtual/input/input8
[   28.219600] wl: module verification failed: signature and/or required key missing - tainting kernel
```

---

### Post by praseodym on 2018-07-08
There is a Broadcom driver installed:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Reboot

---

### Post by PaulinPattaya on 2018-07-08
Thank you very much, it's finding more wireless networks now, but still won't connect to mine.

---

### Post by praseodym on 2018-07-08
Please run the wirless script from the sticky thread and show the outputs.

SecureBoot is turned off?

---

### Post by howefield on 2018-07-08
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by PaulinPattaya on 2018-07-08
Yes, SecureBoot is turned off.
lspci -nnk
```


00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
        Subsystem: Hewlett-Packard Company Haswell-ULT DRAM Controller [103c:80c4]
        Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b
)
        Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller [103c:80c4]
        Kernel driver in use: i915
        Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
        Subsystem: Hewlett-Packard Company Haswell-ULT HD Audio Controller [103c:80c4]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0a03] (rev 0b)
        Subsystem: Hewlett-Packard Company Device [103c:80c4]
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series USB xHCI HC [103c:80c4]
        Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series HECI [103c:80c4]
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series HD Audio Controller [103c:80c4]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 5 [8086:9c18] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 6 [8086:9c1a] (rev e4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series LPC Controller [103c:80c4]
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series SATA Controller 1 [AHCI mode] [103c:80c4]
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series SMBus Controller [103c:80c4]
        Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 8 Series Thermal [8086:9c24] (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series Thermal [103c:80c4]
        Kernel driver in use: intel_pch_thermal
        Kernel modules: intel_pch_thermal
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet control
ler [10ec:8136] (rev 07)
        Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80c2]
        Kernel driver in use: r8169
        Kernel modules: r8169
0d:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / 
M430] [1002:6660] (rev 83)
        Subsystem: Hewlett-Packard Company Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430] [103c:80c4]
        Kernel driver in use: radeon
        Kernel modules: radeon, amdgpu
13:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
        Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
        Kernel driver in use: rtl8723be
        Kernel modules: rtl8723be
```



lsmod
```


Module                  Size  Used by
rfcomm                 77824  14
cmac                   16384  1
bnep                   20480  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_soc_rt298          36864  0
snd_soc_rt286          40960  0
pcbc                   16384  0
snd_soc_rl6347a        16384  2 snd_soc_rt298,snd_soc_rt286
arc4                   16384  2
rtl8723be              98304  0
snd_soc_ssm4567        16384  0
snd_soc_core          229376  3 snd_soc_ssm4567,snd_soc_rt298,snd_soc_rt286
snd_hda_codec_realtek    98304  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
aesni_intel           188416  2
btcoexist             131072  1 rtl8723be
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
snd_hda_intel          40960  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_compress           20480  1 snd_soc_core
rtl8723_common         24576  1 rtl8723be
glue_helper            16384  1 aesni_intel
rtl_pci                32768  1 rtl8723be
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_hda_codec_hdmi,snd_soc_rt29
8,snd_soc_rt286,snd_soc_core
binfmt_misc            20480  1
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
mac80211              782336  3 rtl_pci,rtlwifi,rtl8723be
uvcvideo               90112  0
intel_cstate           20480  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq_midi           16384  0
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
cfg80211              614400  2 mac80211,rtlwifi
snd_seq_midi_event     16384  1 snd_seq_midi
media                  40960  2 uvcvideo,videodev
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
intel_rapl_perf        16384  0
snd                    81920  21 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_
codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
input_leds             16384  0
shpchp                 36864  0
joydev                 20480  0
btusb                  45056  0
kvm                   589824  0
soundcore              16384  1 snd
serio_raw              16384  0
intel_pch_thermal      16384  0
wmi_bmof               16384  0
mei_me                 40960  0
irqbypass              16384  1 kvm
btrtl                  16384  1 btusb
mac_hid                16384  0
mei                   102400  1 mei_me
btbcm                  16384  1 btusb
lpc_ich                24576  0
processor_thermal_device    16384  0
btintel                16384  1 btusb
bluetooth             544768  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3400_thermal        16384  0
acpi_pad              180224  0
acpi_thermal_rel       16384  1 int3400_thermal
tpm_crb                16384  0
int3406_thermal        16384  0
int3403_thermal        16384  0
int3402_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
spi_pxa2xx_platform    24576  0
8250_dw                16384  0
hp_wireless            16384  0
snd_soc_sst_acpi       16384  0
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
sunrpc                335872  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
btrfs                1097728  0
xor                    24576  1 btrfs
raid6_pq              118784  1 btrfs
amdgpu               2019328  0
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
i915                 1822720  25
radeon               1478656  1
ttm                    94208  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
drm_kms_helper        167936  3 amdgpu,radeon,i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               147456  0
ahci                   36864  1
drm                   360448  14 amdgpu,radeon,i915,ttm,drm_kms_helper
libahci                32768  1 ahci
r8169                  86016  0
mii                    16384  1 r8169
wmi                    24576  2 wmi_bmof,hp_wmi
sdhci_acpi             16384  0
video                  40960  2 int3406_thermal,i915
sdhci                  45056  1 sdhci_acpi
i2c_hid                20480  0
hid                   118784  1 i2c_hid
```


dmesg | grep key
```


[    1.419083] Initialise system trusted keyrings
[    1.422437] Asymmetric key parser 'x509' registered
[    1.582086] Loaded X.509 cert 'Build time autogenerated kernel key: d56b251149d5ea1d12d54032a8b6a4c4d5cc0c81'
[    1.584668] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.585723] Key type big_key registered
[   23.512470] input: HP Wireless hotkeys as /devices/virtual/input/input7
[   25.414258] input: HP WMI hotkeys as /devices/virtual/input/input8
[   31.396143] Modules linked in: cmac bnep intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp crct10dif_pclmul crc
32_pclmul ghash_clmulni_intel snd_soc_rt298 snd_soc_rt286 pcbc snd_soc_rl6347a arc4 rtl8723be snd_soc_ssm4567 snd_soc_core
 snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_codec_generic aesni_intel btcoexist aes_x86_64 crypto_simd snd_hda_intel
 snd_hda_codec snd_compress rtl8723_common glue_helper rtl_pci snd_hda_core ac97_bus snd_pcm_dmaengine snd_hwdep snd_pcm b
infmt_misc rtlwifi cryptd mac80211 uvcvideo intel_cstate videobuf2_vmalloc videobuf2_memops snd_seq_midi videobuf2_v4l2 vi
deobuf2_core videodev cfg80211 snd_seq_midi_event media snd_rawmidi snd_seq snd_seq_device snd_timer intel_rapl_perf snd h
p_wmi sparse_keymap input_leds shpchp joydev btusb kvm soundcore serio_raw intel_pch_thermal
```

---

