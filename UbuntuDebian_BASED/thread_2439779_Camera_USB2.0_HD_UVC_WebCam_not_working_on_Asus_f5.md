---
title: "Camera USB2.0 HD UVC WebCam not working on Asus f550"
date: 2020-04-01
forum: Ubuntu/Debian BASED
---

### Post by wtbaster on 2020-04-01
I have an Asus f550lc with ZorinOS (based on Ubuntu 18.04.2)


Camera had never work with zorin. When I launch Cheese, it said that "There were an error to reproduce video of webcam" and in Skype the webcam turn on turn off intermittently

with lsusb:

```
 Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 016: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 03f0:1198 Hewlett-Packard HID-compliant mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

with usb-devices
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.03
S:  Manufacturer=Linux 5.3.0-45-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.03
S:  Manufacturer=Linux 5.3.0-45-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=1198 Rev=07.04
S:  Manufacturer=HP
S:  Product=HP USB 1000dpi Laser Mouse
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid


T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#= 16 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b40a Rev=69.64
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=USB2.0 HD UVC WebCam
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=05.03
S:  Manufacturer=Linux 5.3.0-45-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

with lsmod: 

```

Module                  Size  Used by
rfcomm                 81920  16
bnep                   24576  2
rtbth                  90112  1
bluetooth             573440  38 rtbth,bnep,rfcomm
ecdh_generic           16384  1 bluetooth
ecc                    32768  1 ecdh_generic
ccm                    20480  6
binfmt_misc            24576  1
nls_iso8859_1          16384  1
nvidia_uvm             36864  0
mei_hdcp               24576  0
intel_rapl_msr         20480  0
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             241664  0
kvm                   651264  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
aesni_intel           372736  4
snd_hda_codec_hdmi     57344  1
snd_hda_intel          53248  8
aes_x86_64             20480  1 aesni_intel
snd_intel_nhlt         20480  1 snd_hda_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
nvidia              10584064  87 nvidia_uvm
intel_cstate           20480  0
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
intel_rapl_perf        20480  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib             126976  2 rt2800mmio,rt2800pci
asus_nb_wmi            28672  0
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
asus_wmi               32768  1 asus_nb_wmi
rt2x00lib              61440  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
sparse_keymap          16384  1 asus_wmi
joydev                 28672  0
input_leds             16384  0
mac80211              847872  3 rt2x00pci,rt2x00lib,rt2800lib
serio_raw              20480  0
mxm_wmi                16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
intel_pch_thermal      16384  0
snd_timer              36864  2 snd_seq,snd_pcm
cfg80211              704512  2 rt2x00lib,mac80211
snd                    86016  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
rtsx_pci_ms            24576  0
eeprom_93cx6           16384  1 rt2800pci
memstick               20480  1 rtsx_pci_ms
libarc4                16384  1 mac80211
lpc_ich                24576  0
mei_me                 40960  1
mei                   102400  3 mei_hdcp,mei_me
processor_thermal_device    20480  0
intel_rapl_common      24576  2 intel_rapl_msr,processor_thermal_device
soundcore              16384  1 snd
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     20480  1 processor_thermal_device
asus_wireless          20480  0
mac_hid                16384  0
int3400_thermal        20480  0
acpi_thermal_rel       16384  1 int3400_thermal
sch_fq_codel           20480  6
cuse                   16384  3
uvcvideo               94208  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
videodev              208896  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
rtsx_pci_sdmmc         28672  0
i915                 1937408  4
i2c_algo_bit           16384  1 i915
psmouse               151552  0
drm_kms_helper        180224  1 i915
r8169                  81920  0
syscopyarea            16384  1 drm_kms_helper
rtsx_pci               69632  2 rtsx_pci_sdmmc,rtsx_pci_ms
sysfillrect            16384  1 drm_kms_helper
ahci                   40960  2
realtek                20480  1
sysimgblt              16384  1 drm_kms_helper
libahci                32768  1 ahci
fb_sys_fops            16384  1 drm_kms_helper
drm                   491520  10 drm_kms_helper,nvidia,i915
video                  49152  2 asus_wmi,i915
wmi                    32768  2 asus_wmi,mxm_wmi

```

with dmesg | grep usb:
```
[    0.275797] usbcore: registered new interface driver usbfs
[    0.275797] usbcore: registered new interface driver hub
[    0.275797] usbcore: registered new device driver usb
[    1.731133] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.03
[    1.731135] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.731137] usb usb1: Product: EHCI Host Controller
[    1.731138] usb usb1: Manufacturer: Linux 5.3.0-45-generic ehci_hcd
[    1.731140] usb usb1: SerialNumber: 0000:00:1d.0
[    1.733212] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.03
[    1.733214] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.733216] usb usb2: Product: xHCI Host Controller
[    1.733217] usb usb2: Manufacturer: Linux 5.3.0-45-generic xhci-hcd
[    1.733218] usb usb2: SerialNumber: 0000:00:14.0
[    1.736032] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.03
[    1.736034] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.736035] usb usb3: Product: xHCI Host Controller
[    1.736037] usb usb3: Manufacturer: Linux 5.3.0-45-generic xhci-hcd
[    1.736038] usb usb3: SerialNumber: 0000:00:14.0
[    2.066994] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.074997] usb 2-1: new low-speed USB device number 2 using xhci_hcd
[    2.096097] usb 1-1: New USB device found, idVendor=8087, idProduct=8000, bcdDevice= 0.04
[    2.096100] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.230891] usb 2-1: New USB device found, idVendor=03f0, idProduct=1198, bcdDevice= 7.04
[    2.230893] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.230895] usb 2-1: Product: HP USB 1000dpi Laser Mouse
[    2.230897] usb 2-1: Manufacturer: HP
[    2.359058] usb 2-5: new high-speed USB device number 3 using xhci_hcd
[    2.413254] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[    2.413257] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.413259] usb 2-5: Product: USB2.0 HD UVC WebCam
[    2.413260] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.413261] usb 2-5: SerialNumber: 0x0001
[    2.428860] usbcore: registered new interface driver usbhid
[    2.428862] usbhid: USB HID core driver
[    2.432651] input: HP HP USB 1000dpi Laser Mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:03F0:1198.0001/input/input14
[    2.432771] hid-generic 0003:03F0:1198.0001: input,hidraw0: USB HID v2.00 Mouse [HP HP USB 1000dpi Laser Mouse] on usb-0000:00:14.0-1/input0
[    2.432907] hid-generic 0003:03F0:1198.0002: hiddev0,hidraw1: USB HID v2.00 Device [HP HP USB 1000dpi Laser Mouse] on usb-0000:00:14.0-1/input1
[    5.171700] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input15
[    5.171840] usbcore: registered new interface driver uvcvideo
[  351.565934] usb 2-5: USB disconnect, device number 3
[  351.884821] usb 2-5: new high-speed USB device number 4 using xhci_hcd
[  351.938164] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[  351.938170] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[  351.938173] usb 2-5: Product: USB2.0 HD UVC WebCam
[  351.938176] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[  351.938179] usb 2-5: SerialNumber: 0x0001
[  351.945261] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input25
[  354.820089] usb 2-5: USB disconnect, device number 4
[  355.128825] usb 2-5: new high-speed USB device number 5 using xhci_hcd
[  355.181766] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[  355.181770] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[  355.181772] usb 2-5: Product: USB2.0 HD UVC WebCam
[  355.181774] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[  355.181776] usb 2-5: SerialNumber: 0x0001
[  355.187780] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input26
[  358.473568] usb 2-5: USB disconnect, device number 5
[  358.788872] usb 2-5: new high-speed USB device number 6 using xhci_hcd
[  358.841995] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[  358.841997] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[  358.841999] usb 2-5: Product: USB2.0 HD UVC WebCam
[  358.842000] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[  358.842001] usb 2-5: SerialNumber: 0x0001
[  358.848819] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input27
[  361.243323] usb 2-5: USB disconnect, device number 6
[  361.568904] usb 2-5: new high-speed USB device number 7 using xhci_hcd
[  362.157721] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[  362.157725] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[  362.157728] usb 2-5: Product: USB2.0 HD UVC WebCam
[  362.157729] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[  362.157731] usb 2-5: SerialNumber: 0x0001
[  362.164006] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input28
[  363.973299] usb 2-5: USB disconnect, device number 7
[  364.304931] usb 2-5: new high-speed USB device number 8 using xhci_hcd
[  364.357878] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[  364.357881] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[  364.357893] usb 2-5: Product: USB2.0 HD UVC WebCam
[  364.357894] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[  364.357896] usb 2-5: SerialNumber: 0x0001
[  364.364065] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input29
[ 1359.923455] usb 2-5: USB disconnect, device number 8
[ 1360.242907] usb 2-5: new high-speed USB device number 9 using xhci_hcd
[ 1360.296099] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 1360.296101] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 1360.296103] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 1360.296104] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 1360.296105] usb 2-5: SerialNumber: 0x0001
[ 1360.303432] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input30
[ 1424.383823] usb 2-5: USB disconnect, device number 9
[ 1424.726686] usb 2-5: new high-speed USB device number 10 using xhci_hcd
[ 1424.779751] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 1424.779753] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 1424.779754] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 1424.779755] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 1424.779756] usb 2-5: SerialNumber: 0x0001
[ 1424.785580] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input31
[ 1450.546072] usb 2-5: USB disconnect, device number 10
[ 1450.870511] usb 2-5: new high-speed USB device number 11 using xhci_hcd
[ 1450.923661] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 1450.923670] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 1450.923676] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 1450.923681] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 1450.923686] usb 2-5: SerialNumber: 0x0001
[ 1450.931657] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input32
[ 1453.305184] usb 2-5: USB disconnect, device number 11
[ 1453.654540] usb 2-5: new high-speed USB device number 12 using xhci_hcd
[ 1453.707884] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 1453.707889] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 1453.707892] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 1453.707895] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 1453.707897] usb 2-5: SerialNumber: 0x0001
[ 1453.714952] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input33
[ 1456.479099] usb 2-5: USB disconnect, device number 12
[ 1456.810505] usb 2-5: new high-speed USB device number 13 using xhci_hcd
[ 1456.864160] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 1456.864166] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 1456.864170] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 1456.864173] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 1456.864175] usb 2-5: SerialNumber: 0x0001
[ 1456.871653] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input34
[ 1984.013794] usb 2-5: USB disconnect, device number 13
[ 1984.327505] usb 2-5: new high-speed USB device number 14 using xhci_hcd
[ 1984.380697] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 1984.380702] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 1984.380706] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 1984.380709] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 1984.380711] usb 2-5: SerialNumber: 0x0001
[ 1984.387954] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input35
[ 2017.419997] usb 2-5: USB disconnect, device number 14
[ 2017.726591] usb 2-5: new high-speed USB device number 15 using xhci_hcd
[ 2017.780090] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a, bcdDevice=69.64
[ 2017.780096] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 2017.780100] usb 2-5: Product: USB2.0 HD UVC WebCam
[ 2017.780103] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[ 2017.780105] usb 2-5: SerialNumber: 0x0001
[ 2017.788083] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input36
```

May someone help me to fix the webcam problem, please? Thank you so much

---

