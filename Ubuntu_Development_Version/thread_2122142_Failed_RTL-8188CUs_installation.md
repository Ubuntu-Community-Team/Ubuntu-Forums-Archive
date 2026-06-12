---
title: "Failed RTL-8188CUs installation"
date: 2013-03-04
forum: Ubuntu Development Version
---

### Post by kurt18947 on 2013-03-04
There seem to be a fair number of posts regarding devices using the RealTek 8188CUs chip.  I have an Edimax EW-7811Un which works great with Realtek's driver on 12.04 & 12.10.     I installed it on a machine running the latest 13.04 daily.  Realtek's driver does not install on 13.04 so far; I've included the script.  The adapter behaved as it has on previous installs.  It's recognized, the light comes on steady,should flash.   it seems networks but after entering the passphrase, it is not recognized and returns to the 'enter passphrase' windows.  I thought the 'dmesg' output might shed some light but I'm nowhere near knowledgeable enough to know what it means.   I thought I'd copy/paste some output for your perusal and amusement:).  First off:

Linux ubuntu1304-2ndfloor 3.8.0-9-generic #18-Ubuntu SMP Thu Feb 28 17:02:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Sorry the formatting is not better.  I'm not sure how to fix it.

```


lsmod

Module                        Size  Used by
arc4                            12615  2 
rtl8192cu                    67699  0 
rtlwifi                          79673  1 rtl8192cu
rtl8192c_common        48779  1 rtl8192cu
mac80211              606411  3 rtlwifi,rtl8192c_common,rtl8192cu
cfg80211              510937  2 mac80211,rtlwifi
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
usblp                  18111  0 
nvidia               9350503  38 
snd_hda_codec_realtek    78399  1 
wmi                    19070  0 
snd_hda_intel          39619  3 
snd_hda_codec         136128  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_core              62003  0 
sp5100_tco             13929  0 
snd_rawmidi            30180  1 snd_seq_midi
k10temp                13126  0 
edac_mce_amd           23114  0 
r8712u                187938  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
i2c_piix4              13266  0 
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                91076  0 
microcode              22881  0 
serio_raw              13215  0 
joydev                 17377  0 
mac_hid                13205  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
usb_storage            57199  0 
hid_generic            12540  0 
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  5 hid_generic,usbhid,hid_logitech_dj
ahci                   25731  1 
libahci                31364  1 ahci
r8169                  67446  0 
pata_acpi              13038  0 
pata_atiixp            13242  0 


```

dmesg

```


e="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   11.543274] Bluetooth: Core ver 2.16
[   11.543309] NET: Registered protocol family 31
[   11.543311] Bluetooth: HCI device and connection manager initialized
[   11.543496] Bluetooth: HCI socket layer initialized
[   11.543499] Bluetooth: L2CAP socket layer initialized
[   11.543504] Bluetooth: SCO socket layer initialized
[   11.553617] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.553622] Bluetooth: BNEP filters: protocol multicast
[   11.553632] Bluetooth: BNEP socket layer initialized
[   11.568154] Bluetooth: RFCOMM TTY layer initialized
[   11.568167] Bluetooth: RFCOMM socket layer initialized
[   11.568169] Bluetooth: RFCOMM ver 1.11
[   11.574721] ppdev: user-space parallel port driver
[   11.659679] r8169 0000:02:00.0 eth0: link down
[   11.659715] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.660103] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.920027] r8712u: CustomerID = 0x0000
[   11.920032] r8712u: MAC Address from efuse = 5c:d9:98:42:1e:54
[   11.920034] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   11.920359] usbcore: registered new interface driver r8712u
[   12.158620] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input15
[   12.794692] r8712u: 1 RCR=0x153f00e
[   12.795440] r8712u: 2 RCR=0x553f00e
[   12.902435] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.902700] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.930469] usblp1: removed
[   12.932614] usblp 3-1.2:1.0: usblp1: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01F3
[   12.994810] init: udev-fallback-graphics main process (1252) terminated with status 1
[   13.021088] init: gdm main process (1262) killed by TERM signal
[   13.037516] init: plymouth-splash main process (1280) terminated with status 1
[   13.210516] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.897130] NVRM: GPU at 0000:01:00: GPU-23057fb9-ed35-9ffe-7fe9-f39432772a83
[   33.609290] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.611219] r8712u: [r8712_got_addbareq_event_callback] mac = 00:18:f8:5c:88:f4, seq = 0, tid = 0
[  493.906191] show_signal_msg: 48 callbacks suppressed
[  493.906197] menu-cached[2004]: segfault at 100000007 ip 00007f77d093acaa sp 00007fff5728db20 error 4 in libc-2.17.so[7f77d08bb000+1be000]
[  494.711399] NVRM: GPU at 0000:01:00: GPU-23057fb9-ed35-9ffe-7fe9-f39432772a83
[  636.164439] NVRM: GPU at 0000:01:00: GPU-23057fb9-ed35-9ffe-7fe9-f39432772a83
[ 2909.093445] NVRM: GPU at 0000:01:00: GPU-23057fb9-ed35-9ffe-7fe9-f39432772a83
[ 3008.930551] NVRM: GPU at 0000:01:00: GPU-23057fb9-ed35-9ffe-7fe9-f39432772a83
[ 3072.641078] usb 1-3: USB disconnect, device number 2
[ 3187.192203] usb 1-2: new high-speed USB device number 5 using ehci-pci
[ 3187.326076] usb 1-2: New USB device found, idVendor=7392, idProduct=7811
[ 3187.326088] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3187.326096] usb 1-2: Product: 802.11n WLAN Adapter
[ 3187.326103] usb 1-2: Manufacturer: Realtek
[ 3187.326108] usb 1-2: SerialNumber: 00e04c000001
[ 3187.395820] cfg80211: Calling CRDA to update world regulatory domain
[ 3187.478407] cfg80211: World regulatory domain updated:
[ 3187.478417] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3187.478424] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3187.478431] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3187.478436] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3187.478441] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3187.478446] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3187.505848] rtl8192cu: Chip version 0x10
[ 3187.600513] rtl8192cu: MAC address: 80:1f:02:34:36:f1
[ 3187.600525] rtl8192cu: Board Type 0
[ 3187.600871] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 3187.600951] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 3187.601203] usbcore: registered new interface driver rtl8192cu
[ 3187.656297] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3187.657446] rtlwifi: wireless switch is on
[ 3187.758678] rtl8192cu: MAC auto ON okay!
[ 3187.797197] rtl8192cu: Tx queue select: 0x05
[ 3188.168710] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3188.169072] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3264.084563] wlan1: authenticate with 00:18:f8:5c:88:f4
[ 3264.100201] wlan1: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[ 3264.112585] wlan1: send auth to 00:18:f8:5c:88:f4 (try 1/3)
[ 3264.130687] wlan1: authenticated
[ 3264.135071] wlan1: associate with 00:18:f8:5c:88:f4 (try 1/3)
[ 3264.149986] wlan1: RX AssocResp from 00:18:f8:5c:88:f4 (capab=0x411 status=0 aid=1)
[ 3264.150219] wlan1: associated
[ 3264.150301] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3272.163491] wlan1: deauthenticated from 00:18:f8:5c:88:f4 (Reason: 15)
[ 3272.178662] cfg80211: Calling CRDA to update world regulatory domain
[ 3272.188630] cfg80211: World regulatory domain updated:
[ 3272.188638] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3272.188646] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3272.188652] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3272.188656] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3272.188661] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3272.188665] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
ubuntu1304@ubuntu1304:~$ 


```

Failed RealTek install script

```

Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-9-generic/build M=/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-9-generic'
  CC [M]  /home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
In file included from /home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:23:0:
/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h: In function ‘thread_enter’:
/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h:575:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
In file included from /home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:24:
/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/ubuntu1304/Desktop/8188/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-9-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
ubuntu1304@ubuntu1304-2ndfloor:~/Desktop/8188$ 

```

---

### Post by praseodym on 2013-03-04
First: Did you install all compilation tools necessary?
```

sudo apt-get install linux-headers-generic build-essential dkms
```
2nd: Did you run the script as root?```

sudo sh ./install.sh
```
Whats the problem with the module r8712u, which is still loaded? Maybe the "new" Realtek driver does not work yet with kernel 3.8?!

Alternatively, try this driver with dkms:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5210562](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5210562)

But it was tested up to 12.10 only.

---

### Post by mörgæs on 2013-03-04
Moved to the development forum.
If this is a regression a bug report would be great.

---

### Post by grahammechanical on 2013-03-04
How familiar are you with wireless networking troubleshooting? You might need this [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)   If as you say, it sees networks (I am assuming "seems" is a misspelling - do it all the time myself) then that usually is an indication that the driver has been installed and is recognizing the wireless adapter. When we are brought back to the authentication window it is usually an indication that there is an issue with the passphrase or the encryption method set. Network Manager is usually good at setting the encryption method without user input. Try running the code suggested in that link ```
nm-tool
``` What does it show you. Also ```
rfkill list
```  Regards.

---

### Post by kurt18947 on 2013-03-04
> **praseodym said:**
> First: Did you install all compilation tools necessary?
```

sudo apt-get install linux-headers-generic build-essential dkms
```
2nd: Did you run the script as root?```

sudo sh ./install.sh
```
Whats the problem with the module r8712u, which is still loaded? Maybe the "new" Realtek driver does not work yet with kernel 3.8?!

Alternatively, try this driver with dkms:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5210562](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5210562)

But it was tested up to 12.10 only.

Hi praseodym, thanks for checking in.  I did run the script as root.  I did not download linux-headers generic build-essential dkms, I can try that, I will also try your linked driver.  r8712u works perfectly with the rtl-8192SU adapter in all versions I've tried.  The only glitch with r8712u is that it requires a minor modification to resume properly after suspending.  The script from RealTek works perfectly up through 12.10 but I've never gotten the 'baked-in' module to work with this adapter.  I did report my experience to RealTek.  It's possible they'll release an update to their installer once 13.04 is close to release.  Getting 'baked-in' support would be good, this is a useful adapter for portable machines.

---

### Post by sremick on 2013-05-07
Was there ever any progress on this?  I am using a RTL8192CU-based USB adapter on Xubuntu which seems to share a driver with the 8188. With 12.10 and the baked-in driver, it would detect but I got the same symptoms as the OP where it'd keep prompting for the wireless password even when I entered it in correctly. I blacklisted it and downloaded the v3.4.4_4749.20120806 driver from Realtek, compiled and installed it and it had been working fine from there. Then with every kernel update on 12.10 I'd have to recompile/reinstall but I just got used to that. Now I upgraded Xubuntu to 13.04 and it won't compile. I tried looking for a newer version but there was only a slightly-newer one, v3.4.4_4749.20121105, which exhibits the same compile error for me as the OP mentioned.  From countless other posts on these forums, as well as other forums and even blog posts dedicated to the issue, the baked-in driver for the RTL8188/8192, while existing, has had known problems for a very long time. It'd certainly be nice if the baked-in driver had been fixed in 13.04 but that's clearly not the case so we're stuck trying to get the manually-compiled one to work... which used to, but not any more.

---

### Post by kurt18947 on 2013-05-08
Yes, Tim Phillips has produced a great solution to this problem.  See this thread:

[http://ubuntuforums.org/showthread.php?t=2092934&page=2&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&page=2&highlight=8188CUs)

Tim has made available a .deb file that fixes the 13.04 installation bug and included a dkms fix so it's no longer necessary to recompile after each kernel upgrade.  Here's a link to the .deb file:

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

Do note that you need to blacklist the original drivers.

---

