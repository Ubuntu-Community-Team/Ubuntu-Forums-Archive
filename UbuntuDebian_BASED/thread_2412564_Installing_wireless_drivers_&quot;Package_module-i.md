---
title: "Installing wireless drivers &quot;Package module-init-tools is not installed&quot;"
date: 2019-02-14
forum: Ubuntu/Debian BASED
---

### Post by psudo on 2019-02-14
Hello,

I recently purchased the following usb wireless nic:

[https://www.amazon.com/EDUP-ac600Mbps-Wireless-External-10-6-10-13/dp/B01CCMUN8C/ref=sr_1_4?ie=UTF8&qid=1549298796&sr=8-4&keywords=usb+wireless+network+adapter](https://www.amazon.com/EDUP-ac600Mbps-Wireless-External-10-6-10-13/dp/B01CCMUN8C/ref=sr_1_4?ie=UTF8&qid=1549298796&sr=8-4&keywords=usb+wireless+network+adapter)

It came with drivers for linux, but when I try to extract them, I get the following:

```
root@kali:~# dpkg -i ./dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb 
dpkg: warning: downgrading dkms from 2.6.1-4 to 2.2.0.3-1.1ubuntu5.14.04.5
(Reading database ... 357990 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.5) over (2.6.1-4) ...
dpkg: warning: unable to delete old directory '/etc/dkms/template-dkms-mkbmdeb/debian': Directory not empty
dpkg: warning: unable to delete old directory '/etc/dkms/template-dkms-mkbmdeb': Directory not empty
dpkg: dependency problems prevent configuration of dkms:
 dkms depends on module-init-tools; however:
  Package module-init-tools is not installed.

dpkg: error processing package dkms (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.8.4-2+b1) ...
Errors were encountered while processing:
 dkms

The service is running. 
```

```
root@kali:~# service module-init-tools status
&#9679; systemd-modules-load.service - Load Kernel Modules
   Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: active (exited) since Sat 2019-02-09 13:56:56 EST; 20min ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 11748 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=0/SUCCESS)
 Main PID: 11748 (code=exited, status=0/SUCCESS)

Feb 09 13:56:56 kali systemd[1]: Starting Load Kernel Modules...
Feb 09 13:56:56 kali systemd[1]: Started Load Kernel Modules.
```

It says that Package module-init-tools is not installed, but as you can see, it is installed and the service is running. 

Any suggestions on how to proceed?

Innumerable appreciations,
~psudo

---

### Post by Claus7 on 2019-02-15
Hello,

are you sure that you have to install the drivers in question? As the messages suggest, you have to downgrade dkms packages in order for the installation to proceed, something that might brick your system. Have you checked the adapter if it is working out of the box?

Regards!

---

### Post by psudo on 2019-02-15
If my understanding is correct, I should be able to run airmon-ng for a list of nics

I dont get anything when I do that, so I assume that it is not working out of the box.

This is a VM running on vbox.

running lsusb, the device is found

Here is the dmesg output:

```
[  308.727126] usb 1-2: new full-speed USB device number 3 using ohci-pci
[  309.248079] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x84 has invalid maxpacket 512, setting to 64
[  309.248080] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x5 has invalid maxpacket 512, setting to 64
[  309.248082] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x6 has invalid maxpacket 512, setting to 64
[  309.248083] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x8 has invalid maxpacket 512, setting to 64
[  309.248085] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x9 has invalid maxpacket 512, setting to 64
[  309.279311] usb 1-2: New USB device found, idVendor=0bda, idProduct=0811, bcdDevice= 2.00
[  309.279313] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  309.279314] usb 1-2: Product: 802.11ac WLAN Adapter 
[  309.279315] usb 1-2: Manufacturer: Realtek 
[  309.279316] usb 1-2: SerialNumber: 00e04XXXXXXXX
```

---

### Post by Claus7 on 2019-02-16
Hello,

so you are trying to make this wireless usb adapter work, from ubuntu under VB. 
From the messages you get, it seems that the device is recognized. 

The drivers you are trying to install are like these?
wireless-driver-center.blogspot.com/2016/09/download-edup-ep-db1607-driver-for.html
[www.szedup.com/support/driver-download/ep-db1607-driver/](www.szedup.com/support/driver-download/ep-db1607-driver/)

1) Maybe, if you install this latest driver your machine might work (if indeed this driver is newer than the one you have already tried to install).

2) what do you get from the command: lsusb?

3) I suppose that the machine is working for the host OS.

4) Do you see any available networks under network settings in ubuntu?

5) Could you provide a little more info about your network? Is this supposed to be connected to a laptop computer? What do you mean that it should work for a list of nics?

6) If it is not a fuss, you could check if it is working under ubuntu 14.04, as it seems that the drivers you have at your disposal are for an older set of kernels.

Just some thoughts and clarification questions at the time,
Regards!

---

### Post by psudo on 2019-02-19
1) Maybe, if you install this latest driver your machine might work (if  indeed this driver is newer than the one you have already tried to  install).

I'll try this. Thanks

2) what do you get from the command: lsusb?

```
root@kali:~# lsusb
Bus 001 Device 003: ID 0bda:0811 Realtek Semiconductor Corp. <--- this is the usb wireless nic
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

3) I suppose that the machine is working for the host OS.

The VM or the USB wireless NIC?

4) Do you see any available networks under network settings in ubuntu?

No.

5) Could you provide a little more info about your network? Is this  supposed to be connected to a laptop computer? What do you mean that it  should work for a list of nics?

This is a Kali VM running on vbox on my desktop computer. (Trust me, I tried to get this on the kali forum, but the admin is asleep at the wheel. I never received the confirmation email for the registration and never received anything back after multiple emails were sent.) By list of nics, I mean, in my research I've found that airmon-ng is supposed to list the available wireless nics. Here is the output from airmon-ng:

```
root@kali:~# airmon-ng

PHY    Interface    Driver        Chipset


root@kali:~# 

6) If it is not a fuss, you could check if it is working under ubuntu  14.04, as it seems that the drivers you have at your disposal are for an  older set of kernels.

These drivers were included on a cd that came with the USB wireless nic. I assume they are outdated. Im running kernel ver:

root@kali:~# uname -r
4.18.0-kali2-amd64
```

I downloaded the new drivers. They did appear to be "newer" even though they're etill from 2016. I'm getting a similar error:

```
root@kali:~/linux/linux# ./install.sh 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gz
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_query.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi_sms4.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_rtl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/rtw_efuse.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sta_mgt.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_io.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_rf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_vht.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_set.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_iol.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_odm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ap.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_pwrctrl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_tdls.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_bt_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_eeprom.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_beamforming.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wlan_util.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_p2p.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp_ioctl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ieee80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_br_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mem.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_security.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_br_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_pci.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mp_custom_oid.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_vht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_iol.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swabb.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/little_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/big_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swab.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/generic.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_io.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8821APwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_conf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ip.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wifi_regd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_vendor_req.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_efuse.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_android.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/xmit_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/autoconf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_query.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wapi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wifi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_version.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/if_ether.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mlme_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_beamforming.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_data.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/circ_buf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalPwrSeqCmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_byteorder.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/nic_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wlan_bssdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_p2p.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/custom_gpio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ethernet.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_rtl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/wireless.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_qos.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_phycfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ap.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/recv_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_pwrctrl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_odm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_h2c.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mem.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_tdls.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_set.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/basic_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_bt_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_eeprom.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/h2clbk.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_phy_regdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/cmd_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_security.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_bsd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalVerDef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sta_info.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/runwpa
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/clean
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Kconfig
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/ifcfg-wlan0
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Makefile
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/wlan0dhcp
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/hal_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/efuse_mask.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11N.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_pre_define.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11AC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/hal_usb_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_hal_init.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rxdesc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8821APwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rf6052.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8812PwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_halinit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtcOutSrc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/HalPwrSeqCmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_phy.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/wifi_regd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/custom_gpio_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/xmit_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/mlme_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/os_intfs.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/recv_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_android.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/osdep_service.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_WMT_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_arm_act_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNnI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_sprd_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_RTK_DMP_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51
Authentication requested [root] for make clean:
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-kali2-amd64/build M=/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-kali2-amd64'
  CC [M]  /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:41:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:267:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:268:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:343:2: error: implicit declaration of function &#8216;allow_signal&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:353:6: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
  if (signal_pending (current))
      ^~~~~~~~~~~~~~
      timer_pending
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:355:3: error: implicit declaration of function &#8216;flush_signals&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:95:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h: At top level:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h:412:13: error: &#8216;file_path&#8217; redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^~~~~~~~~
In file included from /usr/src/linux-headers-4.18.0-kali2-common/include/linux/compat.h:17:0,
                 from /usr/src/linux-headers-4.18.0-kali2-common/include/linux/ethtool.h:17,
                 from /usr/src/linux-headers-4.18.0-kali2-common/include/linux/netdevice.h:41,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:35,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:41,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/usr/src/linux-headers-4.18.0-kali2-common/include/linux/fs.h:2884:14: note: previous declaration of &#8216;file_path&#8217; was here
 extern char *file_path(struct file *, char *, int);
              ^~~~~~~~~
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:65:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c: In function &#8216;btinfo_evt_dump&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3293:2: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3296:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3308:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3311:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3314:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   ^~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
make[4]: *** [/usr/src/linux-headers-4.18.0-kali2-common/scripts/Makefile.build:323: /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1
make[3]: *** [/usr/src/linux-headers-4.18.0-kali2-common/Makefile:1531: _module_/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[2]: *** [Makefile:146: sub-make] Error 2
make[1]: *** [Makefile:8: all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-kali2-amd64'
make: *** [Makefile:1551: modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
root@kali:~/linux/linux#
```

I checked the "Compile make driver error: 2" and found that there is a package that I can download. ( [https://ubuntuforums.org/showthread.php?t=2339960](https://ubuntuforums.org/showthread.php?t=2339960) )

```
sudo apt-get install rtl8812au-dkms gave me the following:

root@kali:~# sudo apt-get install rtl8812au-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtl8812au-dkms
```

I searched for the repo and got this page:

[https://packages.ubuntu.com/cosmic/all/rtl8812au-dkms/download](https://packages.ubuntu.com/cosmic/all/rtl8812au-dkms/download)

I manually downloaded rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb and extracted it. I ran 'make all' and then 'make clean'

The make appeared to work. Now Im stuck again and dont know how to proceed. I rebooted the system thinking it might load the new drivers, but its the same. 

lsusb, lists the adapter and airmon-ng still gives me nothing. 

Thanks again for your help and suggestions.

---

### Post by Claus7 on 2019-02-20
Hello,

oooh! There is a lot of progress here. Let us see what we can get:

> **psudo said:**
> 
1) Maybe, if you install this latest driver your machine might work (if  indeed this driver is newer than the one you have already tried to  install).

I'll try this. Thanks


You are welcome. As I can see you have more about this later on...

> **psudo said:**
> 
2) what do you get from the command: lsusb?

root@kali:~# lsusb
Bus 001 Device 003: ID 0bda:0811 Realtek Semiconductor Corp. <--- this is the usb wireless nic


So, ubuntu can see the nic with the packages already installed.

> **psudo said:**
> 
3) I suppose that the machine is working for the host OS.

The VM or the USB wireless NIC?


If you are using a virtual machine, then there should be a host Operating System. For that system, does the usb wireless nic work as it should?

> **psudo said:**
> 
4) Do you see any available networks under network settings in ubuntu?

No.


If things were OK, I guest you should...

> **psudo said:**
> 
5) Could you provide a little more info about your network? Is this  supposed to be connected to a laptop computer? What do you mean that it  should work for a list of nics?

This is a Kali VM running on vbox on my desktop computer. 
...


So, you are using VB. The host OS is the one you have primarily on your desktop computer. Is this usb working OK with that OS?


> **psudo said:**
> I downloaded the new drivers. They did appear to be "newer" even though they're etill from 2016. I'm getting a similar error:

root@kali:~/linux/linux# ./install.sh 
...

Authentication requested [root] for make clean:
...
Authentication requested [root] for make driver:


You should type:
sudo ./install 
so as to make the installation as root. From the messages you are getting, there should be root permissions for the installation to proceed.

> **psudo said:**
> I checked the "Compile make driver error: 2" and found that there is a package that I can download. ( [https://ubuntuforums.org/showthread.php?t=2339960](https://ubuntuforums.org/showthread.php?t=2339960) )

....

Thanks again for your help and suggestions.

I would try first to complete the initial installation of yours as root, and then see if any packages are missing. Now, that you did this installation on your own, you might face some conflicts. I would advice you to get rid of the package you installed on your own and redo the installation. If you see in the messages that still this package is missing, then install it and try again.

You are welcome. I hope that soon enough your configuration will be up and running,
Regards!

---

### Post by psudo on 2019-02-21
The USB Wireless NIC does work on my win 10 host. Getting great speeds. 

I re-rean the install script with sudo, but I get the same thing:

```
root@kali:~/linux/linux# sudo ./install.sh 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gz
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_query.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi_sms4.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_rtl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/rtw_efuse.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sta_mgt.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_io.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_rf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_vht.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_set.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_iol.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_odm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ap.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_pwrctrl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_tdls.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_bt_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_eeprom.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_beamforming.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wlan_util.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_p2p.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp_ioctl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ieee80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_br_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mem.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_security.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_br_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_pci.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mp_custom_oid.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_vht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_iol.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swabb.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/little_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/big_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swab.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/generic.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_io.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8821APwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_conf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ip.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wifi_regd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_vendor_req.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_efuse.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_android.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/xmit_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/autoconf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_query.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wapi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wifi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_version.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/if_ether.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mlme_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_beamforming.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_data.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/circ_buf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalPwrSeqCmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_byteorder.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/nic_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wlan_bssdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_p2p.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/custom_gpio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ethernet.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_rtl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/wireless.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_qos.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_phycfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ap.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/recv_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_pwrctrl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_odm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_h2c.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mem.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_tdls.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_set.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/basic_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_bt_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_eeprom.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/h2clbk.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_phy_regdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/cmd_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_security.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_bsd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalVerDef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sta_info.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/runwpa
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/clean
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Kconfig
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/ifcfg-wlan0
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Makefile
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/wlan0dhcp
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/hal_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/efuse_mask.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11N.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_pre_define.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11AC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/hal_usb_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_hal_init.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rxdesc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8821APwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rf6052.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8812PwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_halinit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtcOutSrc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/HalPwrSeqCmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_phy.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/wifi_regd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/custom_gpio_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/xmit_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/mlme_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/os_intfs.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/recv_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_android.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/osdep_service.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_WMT_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_arm_act_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNnI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_sprd_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_RTK_DMP_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51
Authentication requested [root] for make clean:
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-kali2-amd64/build M=/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-kali2-amd64'
  CC [M]  /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:41:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:267:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:268:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:343:2: error: implicit declaration of function &#8216;allow_signal&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:353:6: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
  if (signal_pending (current))
      ^~~~~~~~~~~~~~
      timer_pending
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:355:3: error: implicit declaration of function &#8216;flush_signals&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:95:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h: At top level:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h:412:13: error: &#8216;file_path&#8217; redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^~~~~~~~~
In file included from /usr/src/linux-headers-4.18.0-kali2-common/include/linux/compat.h:17:0,
                 from /usr/src/linux-headers-4.18.0-kali2-common/include/linux/ethtool.h:17,
                 from /usr/src/linux-headers-4.18.0-kali2-common/include/linux/netdevice.h:41,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:35,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:41,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/usr/src/linux-headers-4.18.0-kali2-common/include/linux/fs.h:2884:14: note: previous declaration of &#8216;file_path&#8217; was here
 extern char *file_path(struct file *, char *, int);
              ^~~~~~~~~
In file included from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:65:0,
                 from /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c: In function &#8216;btinfo_evt_dump&#8217;:
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3293:2: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3296:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3308:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3311:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   ^~~~~~~~~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^~~~~~~~
/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3314:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   ^~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
make[4]: *** [/usr/src/linux-headers-4.18.0-kali2-common/scripts/Makefile.build:323: /root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1
make[3]: *** [/usr/src/linux-headers-4.18.0-kali2-common/Makefile:1531: _module_/root/linux/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[2]: *** [Makefile:146: sub-make] Error 2
make[1]: *** [Makefile:8: all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-kali2-amd64'
make: *** [Makefile:1551: modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
root@kali:~/linux/linux#
```

---

### Post by praseodym on 2019-02-21
Seems too old?! What about this one

[https://ubuntuforums.org/showthread.php?t=2412170&p=13836896#post13836896](https://ubuntuforums.org/showthread.php?t=2412170&p=13836896#post13836896)

---

### Post by psudo on 2019-02-26
This worked like a charm.

Thanks so much for helping me through this.

1 step forward, 2 steps back....

Since the NIC was working, I started some ethical hacking tuts and one of the first things I did was an apt-get update and upgrade. 

I have ran the update in the past, but this was the first time running apt-get upgrade and apt-get dist-upgrade

This broke the USB Wifi. 

After reboot its no longer in the network connections drop down. lsusb and airmon-ng are now as before. 

This being the case, I built a new Kali VM from scratch. I then ran the aforementioned apt update/upgrade/dist-upgrade and rebooted. I then cloned the git repo and executed the dkms commands. The last one failed. Im getting a similar error as before:

```
root@kali:~# sudo dkms install 8812au/4.2.2

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' all KVER=4.19.0-kali3-amd64...........(bad exit status: 2)
Error! Bad return status for module build on kernel: 4.19.0-kali3-amd64 (x86_64)
Consult /var/lib/dkms/8812au/4.2.2/build/make.log for more information.

______________________________________________________________

root@kali:~# cat /var/lib/dkms/8812au/4.2.2/build/make.log
DKMS make.log for 8812au-4.2.2 for kernel 4.19.0-kali3-amd64 (x86_64)
Tue Feb 26 19:50:12 MST 2019
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.19.0-kali3-amd64/build M=/var/lib/dkms/8812au/4.2.2/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.19.0-kali3-amd64'
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/os_dep/linux/os_intfs.o
/var/lib/dkms/8812au/4.2.2/build/os_dep/linux/os_intfs.c:1069:22: error: initialization of ‘u16 (*)(struct net_device *, struct sk_buff *, struct net_device *, u16 (*)(struct net_device *, struct sk_buff *, struct net_device *))’ {aka ‘short unsigned int (*)(struct net_device *, struct sk_buff *, struct net_device *, short unsigned int (*)(struct net_device *, struct sk_buff *, struct net_device *))’} from incompatible pointer type ‘u16 (*)(struct net_device *, struct sk_buff *, void *, u16 (*)(struct net_device *, struct sk_buff *, struct net_device *))’ {aka ‘short unsigned int (*)(struct net_device *, struct sk_buff *, void *, short unsigned int (*)(struct net_device *, struct sk_buff *, struct net_device *))’} [-Werror=incompatible-pointer-types]
  .ndo_select_queue = rtw_select_queue,
                      ^~~~~~~~~~~~~~~~
/var/lib/dkms/8812au/4.2.2/build/os_dep/linux/os_intfs.c:1069:22: note: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’)
cc1: some warnings being treated as errors
make[4]: *** [/usr/src/linux-headers-4.19.0-kali3-common/scripts/Makefile.build:309: /var/lib/dkms/8812au/4.2.2/build/os_dep/linux/os_intfs.o] Error 1
make[3]: *** [/usr/src/linux-headers-4.19.0-kali3-common/Makefile:1535: _module_/var/lib/dkms/8812au/4.2.2/build] Error 2
make[2]: *** [Makefile:146: sub-make] Error 2
make[1]: *** [Makefile:8: all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.19.0-kali3-amd64'
make: *** [Makefile:1064: modules] Error 2
```

I really appreciate everyone's help thus far and hope that you guys might have a suggestion for this new issue.

---

### Post by wildmanne39 on 2019-02-26
Hello, it is best to use the Kali forum for your issue, as quoted below:
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
Thread Closed!

---

### Post by howefield on 2019-02-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

