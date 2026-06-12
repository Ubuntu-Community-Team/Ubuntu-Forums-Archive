---
title: "A6100 Adapter Driver ???? In Kali Linux"
date: 2016-10-02
forum: Ubuntu/Debian BASED
---

### Post by jsy2005 on 2016-10-02
Hi all,

  Very very new to Linux but learning lol. I have a netgear ac600 (a6100) that I am trying to get working in Kali Linux. I have tried pretty much every single help guide/fix that I could find online from Chill555 fix to this

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/abperiasamy/rtl88...21AU_linux.git]("https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git")
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au 
Your wireless should now be working.
```


To manually editing lines of code and nothing is working. SO i got the card to be seen in kali and it even sees broadcasted SSIDs. The issue lies in putting it in to monitor mode. When I do a airmon-ng I get this.
```

[COLOR=#CC0000]**root@kali**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]# airmon-ng

PHY    Interface    Driver        Chipset

null    wlan0        ??????        NetGear, Inc. A6100 AC600 DB [Realtek RTL8811AU]
```




and when I try to do a make I get an error.

```
[B]


/root/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:[/B] In function ‘**rtw_spt_band_free**’:
**/root/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:269:20:** [COLOR=#CC0000]**error: **[/COLOR]comparison between ‘**enum ieee80211_band**’ and ‘**enum nl80211_band**’ [-Werror=enum-compare]
  if(spt_band->band == NL80211_BAND_2GHZ)
[COLOR=#4E9A06]**                    ^**[/COLOR]
**/root/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:279:25:** [COLOR=#CC0000]**error: **[/COLOR]comparison between ‘**enum ieee80211_band**’ and ‘**enum nl80211_band**’ [-Werror=enum-compare]
  else if(spt_band->band == NL80211_BAND_5GHZ)
[COLOR=#4E9A06]**                         ^**[/COLOR]
cc1: all warnings being treated as errors
/usr/src/linux-headers-4.6.0-kali1-common/scripts/Makefile.build:296: recipe for target '/root/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o' failed
make[4]: *** [/root/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o] Error 1
/usr/src/linux-headers-4.6.0-kali1-common/Makefile:1446: recipe for target '_module_/root/rtl8812AU_8821AU_linux' failed
make[3]: *** [_module_/root/rtl8812AU_8821AU_linux] Error 2
Makefile:146: recipe for target 'sub-make' failed
make[2]: *** [sub-make] Error 2
Makefile:8: recipe for target 'all' failed
make[1]: *** [all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.6.0-kali1-amd64'
Makefile:1049: recipe for target 'modules' failed
make: *** [modules] Error 2
```

and the follow up comand of make install does not work. Also see below for lsusb list.

```

Bus 001 Device 007: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Please help because I am absolutely at wits end here.

Also, important to note I am doing this on VMware

```



########## wireless info START ##########

Report from: 02 Oct 2016 02:25 EDT -0400

Booted last: 02 Oct 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Kali
Description:    Kali GNU/Linux Rolling
Release:    kali-rolling
Codename:    kali-rolling

##### kernel ############################

Linux 4.6.0-kali1-amd64 #1 SMP Debian 4.6.4-1kali1 (2016-07-21) x86_64 unknown unknown GNU/Linux

Parameters: ro, initrd=/install/initrd.gz, quiet

##### desktop ###########################

default

##### lspci #############################

02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
    DeviceName: Ethernet0
    Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]

##### lsusb #############################

Bus 001 Device 004: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

8812au               1662976  0
cfg80211              573440  1 8812au
rfkill                 24576  6 cfg80211,bluetooth
usbcore               241664  6 btusb,uhci_hcd,ehci_hcd,ehci_pci,usbhid,8812au

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.109  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::20c:29ff:fef0:b61  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2449  bytes 2748445 (2.6 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1745  bytes 189885 (185.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 133  bytes 11563 (11.2 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 133  bytes 11563 (11.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 34  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 192.168.1.111
nameserver 8.8.8.8

##### network managers ##################

Installed:

    NetworkManager

Running:

root       535     1  0 02:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82545EM Gigabit Ethernet Controller (Copper) (PRO/1000 MT Single Port Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 7.3.21-k8-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:11.0/0000:02:01.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       aa4997ac-3eae-47c2-8a33-fcdcbc96419e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   aa4997ac-3eae-47c2-8a33-fcdcbc96419e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.109/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.111
IP4.DNS[2]:                             8.8.8.8
IP6.ADDRESS[1]:                         fe80::20c:29ff:fef0:b61/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek 
GENERAL.PRODUCT:                        802.11ac WLAN Adapter 
GENERAL.DRIVER:                         rtl8812au
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Cupcake                       <MAC 'Cupcake' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
MooMoo's                      <MAC 'MooMoo's' [AC3]>  Infra  9     2452 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
theInterwebs                  <MAC 'theInterwebs' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
TG1672GC2-5G                  <MAC 'TG1672GC2-5G' [AC6]>  Infra  36    5180 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
HP-Print-08-ENVY 4500 series  <MAC 'HP-Print-08-ENVY 4500 series' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
SERIOUSLY DONT TOUCH IT       <MAC 'SERIOUSLY DONT TOUCH IT' [AN6]>  Infra  48    5240 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2      no        
HT_00d02d63fb96               <MAC 'HT_00d02d63fb96' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  0       ____  WPA2      no        
--                            <MAC '' [AC7]>  Infra  48    5240 MHz  54 Mbit/s  0       ____  WPA2      no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.24 GHz (Channel 48)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HT_00d02d63fb96' [AC1]>
                    ESSID:"HT_00d02d63fb96"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC 'Cupcake' [AC2]>
                    ESSID:"Cupcake"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 03 - Address: <MAC 'MooMoo's' [AC3]>
                    ESSID:"MooMoo's"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 04 - Address: <MAC 'theInterwebs' [AC4]>
                    ESSID:"theInterwebs"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 05 - Address: <MAC 'HP-Print-08-ENVY 4500 series' [AC5]>
                    ESSID:"HP-Print-08-ENVY 4500 series"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0001
          Cell 06 - Address: <MAC 'TG1672GC2-5G' [AC6]>
                    ESSID:"TG1672GC2-5G"
                    Protocol:IEEE 802.11an
                    Mode:Master
                    Frequency:5.18 GHz (Channel 36)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 07 - Address: <MAC '' [AC7]>
                    ESSID:""
                    Protocol:IEEE 802.11an
                    Mode:Master
                    Frequency:5.24 GHz (Channel 48)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
                    Extra:fm=0001

##### module infos ######################

[8812au]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/drivers/net/wireless/8812au.ko
version:        v4.3.20_16317.20160108
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     6261112E35D4FB03989F3AB
depends:        cfg80211,usbcore
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_rfkfree_enable:int
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_beamform_cap:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
parm:           rtw_adaptivity_th_l2h_ini:TH_L2H_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:TH_EDCCA_HL_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_kfree:default kfree config value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

[cfg80211]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[8812au]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_adaptivity_dc_backoff: 2
rtw_adaptivity_dml: 0
rtw_adaptivity_en: 0
rtw_adaptivity_mode: 0
rtw_adaptivity_th_edcca_hl_diff: 0
rtw_adaptivity_th_l2h_ini: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_amplifier_type_2g: 0
rtw_amplifier_type_5g: 0
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_beamform_cap: 2
rtw_busy_thresh: 40
rtw_bw_mode: 33
rtw_channel: 1
rtw_channel_plan: 90
rtw_chip_version: 0
rtw_decrypt_phy_file: 0
rtw_enusbss: 0
rtw_FileMaskEfuse: 0
rtw_GLNA_type: 0
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_kfree: 0
rtw_lbkmode: 0
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_OffEfuseMask: 0
rtw_pll_ref_clk_sel: 15
rtw_power_mgnt: 2
rtw_qos_opt_enable: 0
rtw_rf_config: 15
rtw_RFE_type: 64
rtw_rfintfs: 2
rtw_rfkfree_enable: 0
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_special_rf_path: 0
rtw_switch_usb_mode: 0
rtw_TxBBSwing_2G: 255
rtw_TxBBSwing_5G: 255
rtw_tx_pwr_by_rate: 0
rtw_tx_pwr_lmt_enable: 0
rtw_usb_rxagg_mode: 2
rtw_vcs_type: 1
rtw_vht_enable: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-libnfc.conf]
blacklist nfc
blacklist pn533

[/etc/modprobe.d/hackrf-blacklist.conf]
blacklist hackrf

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/libhackrf0.conf]
blacklist hackrf

[/etc/modprobe.d/open-vm-tools-dkms.conf]
install pcnet32 /sbin/modprobe -q --ignore-install vmxnet; /sbin/modprobe -q --ignore-install pcnet32 $CMDLINE_OPTS; /bin/true;

##### rc.local ##########################

exit 0

##### pm-utils ##########################

find: ‘/etc/pm/*.d’: No such file or directory

##### udev rules ########################

##### dmesg #############################

[   17.080060] RTL871X: rtl8812au v4.3.20_16317.20160108
[   19.291358] RTL871X: rtw_ndev_init(wlan0) if1 mac_addr=<MAC address>
[   28.450149] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   32.714401] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.718292] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   33.408068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.412610] RTL871X: rtw_ndev_uninit(wlan0) if1
[   87.809128] RTL871X: rtw_ndev_init(wlan0) if1 mac_addr=<MAC address>
[   87.840037] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  221.379873] RTL871X: rtw_ndev_uninit(wlan0) if1
[  226.117804] RTL871X: rtw_ndev_init(wlan0) if1 mac_addr=<MAC address>
[  226.164790] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)

########## wireless info END ############


```

---

### Post by Bucky Ball on 2016-10-02
*Thread moved to **Ubuntu/Debian based**.*

Welcome. Kali is not supported in the Ubuntu Specialised Support forums here. Good luck.

---

