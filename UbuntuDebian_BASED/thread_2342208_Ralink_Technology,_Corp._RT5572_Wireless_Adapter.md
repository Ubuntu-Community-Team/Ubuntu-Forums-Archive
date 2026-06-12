---
title: "Ralink Technology, Corp. RT5572 Wireless Adapter"
date: 2016-11-04
forum: Ubuntu/Debian BASED
---

### Post by d1kiy on 2016-11-04
Hello. Mb somebody can help me. My adapter doesn't see Wi-Fi connections.


```
**iwconfig**
wlan0 IEEE 802.11 ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm 
Retry short limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off


**lsusb**
Bus 001 Device 002: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter


**dmesg | grep rt2**
[ 19.552590] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5592, rev 0222 detected
[ 20.482802] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 000f detected
[ 20.532364] usbcore: registered new interface driver rt2800usb
[ 30.001246] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 30.115328] rt2800usb 1-1:1.0: firmware: direct-loading firmware rt2870.bin
[ 30.115341] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
```


I'm beginner in Linux, so I hope i'll find help here. Thank you
P.S. Sorry for my english

---

### Post by jeremy31 on 2016-11-04
Welcome to the forums, it does appear that the wireless is functional from what you have posted.  Please see the wireless script link in my signature and post your results

---

### Post by d1kiy on 2016-11-04
```



########## wireless info START ##########


Report from: 04 Nov 2016 19:13 EDT -0400


Booted last: 04 Nov 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Kali
Description:	Kali GNU/Linux Rolling
Release:	kali-rolling
Codename:	kali-rolling


##### kernel ############################


Linux 4.7.0-kali1-amd64 #1 SMP Debian 4.7.8-1kali1 (2016-10-24) x86_64 unknown unknown GNU/Linux


Parameters: ro, initrd=/install/gtk/initrd.gz, quiet


##### desktop ###########################


default


##### lspci #############################


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
	Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
	Kernel driver in use: e1000


##### lsusb #############################


Bus 001 Device 002: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              643072  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              569344  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
rfkill                 24576  4 cfg80211,bluetooth
usbcore               241664  7 rt2x00usb,ohci_hcd,ohci_pci,rt2800usb,ehci_hcd,ehci_pci,usbhid


##### interfaces ########################


source /etc/network/interfaces.d/*


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
        inet6 fe80::a00:27ff:fedd:907f  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 47  bytes 30464 (29.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 56  bytes 5641 (5.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 1482  bytes 88898 (86.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1482  bytes 88898 (86.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG    100    0        0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


search lan
nameserver 192.168.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       472     1  0 19:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82540EM Gigabit Ethernet Controller (PRO/1000 MT Desktop Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 7.3.21-k8-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       72bba8c5-22d3-4bcd-b3fc-05bd6935f351
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   72bba8c5-22d3-4bcd-b3fc-05bd6935f351 | Wired connection 1
IP4.ADDRESS[1]:                         10.0.2.15/24
IP4.GATEWAY:                            10.0.2.2
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        filename = Kali.pxe
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_broadcast_address = 1
DHCP4.OPTION[10]:                       next_server = 10.0.2.4
DHCP4.OPTION[11]:                       requested_netbios_scope = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.2.15
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1478387476
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.2.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = lan
DHCP4.OPTION[23]:                       routers = 10.0.2.2
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.2.0
DHCP4.OPTION[28]:                       requested_routers = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.2.2
IP6.ADDRESS[1]:                         fe80::a00:27ff:fedd:907f/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.7.0-kali1-amd64
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/net/wlan0
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


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


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


eth0      no frequency information.


lo        no frequency information.


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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     79C8FF0D61161719C1D2E53
depends:        rt2x00lib,rt2800lib,rt2x00usb,usbcore
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3E02E7B225AE34CEA3C7285
depends:        usbcore,rt2x00lib,mac80211
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     499284BE0462DFC9ABF2B9C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
nohwcrypt: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/libhackrf0.conf]
blacklist hackrf


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   20.406392] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5592, rev 0222 detected
[   21.325508] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 000f detected
[   30.949328] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   30.954010] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   30.954727] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.961415] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.961478] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   31.008206] rt2800usb 1-1:1.0: firmware: direct-loading firmware rt2870.bin
[   31.008219] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[   38.853669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)


########## wireless info END ############


```

---

### Post by chili555 on 2016-11-05
If you reboot with the ethernet detached, is the result the same?```
sudo iwlist wlan0 scan
```

---

### Post by jeremy31 on 2016-11-05
Only thing I can recommend is ```
sudo iw reg set US
```

Everything but the empty scan results make it appear to be working fine

---

### Post by d1kiy on 2016-11-05
> **chili555 said:**
> If you reboot with the ethernet detached, is the result the same?```
sudo iwlist wlan0 scan
```

```
wlan0     Interface doesn't support scanning : Network is down


```

> **jeremy31 said:**
> Only thing I can recommend is ```
sudo iw reg set US
```

Everything but the empty scan results make it appear to be working fine

It didn't help. Empty list again =(

From yesterday I did some changes for make it work, but without result.
So better I send new log:
```
########## wireless info START ##########

Report from: 05 Nov 2016 14:48 EDT -0400


Booted last: 05 Nov 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Kali
Description:	Kali GNU/Linux Rolling
Release:	kali-rolling
Codename:	kali-rolling


##### kernel ############################


Linux 4.7.0-kali1-amd64 #1 SMP Debian 4.7.8-1kali1 (2016-10-24) x86_64 unknown unknown GNU/Linux


Parameters: ro, initrd=/install/gtk/initrd.gz, quiet


##### desktop ###########################


default


##### lspci #############################


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
	Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
	Kernel driver in use: e1000


##### lsusb #############################


Bus 001 Device 002: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              643072  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              569344  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
rfkill                 24576  4 cfg80211,bluetooth
usbcore               241664  7 rt2x00usb,ohci_hcd,ohci_pci,rt2800usb,ehci_hcd,ehci_pci,usbhid


##### interfaces ########################


source /etc/network/interfaces.d/*


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
        inet6 fe80::a00:27ff:fedd:907f  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 470  bytes 368325 (359.6 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 291  bytes 21951 (21.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 337864  bytes 20271796 (19.3 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 337864  bytes 20271796 (19.3 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG    100    0        0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


search lan
nameserver 192.168.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       556     1  0 06:09 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82540EM Gigabit Ethernet Controller (PRO/1000 MT Desktop Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 7.3.21-k8-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       72bba8c5-22d3-4bcd-b3fc-05bd6935f351
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   72bba8c5-22d3-4bcd-b3fc-05bd6935f351 | Wired connection 1
IP4.ADDRESS[1]:                         10.0.2.15/24
IP4.GATEWAY:                            10.0.2.2
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        filename = Kali.pxe
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_broadcast_address = 1
DHCP4.OPTION[10]:                       next_server = 10.0.2.4
DHCP4.OPTION[11]:                       requested_netbios_scope = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.2.15
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1478454488
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.2.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = lan
DHCP4.OPTION[23]:                       routers = 10.0.2.2
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.2.0
DHCP4.OPTION[28]:                       requested_routers = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.2.2
IP6.ADDRESS[1]:                         fe80::a00:27ff:fedd:907f/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.7.0-kali1-amd64
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/net/wlan0
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


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     79C8FF0D61161719C1D2E53
depends:        rt2x00lib,rt2800lib,rt2x00usb,usbcore
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3E02E7B225AE34CEA3C7285
depends:        usbcore,rt2x00lib,mac80211
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     499284BE0462DFC9ABF2B9C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.7.0-kali1-amd64/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       4.7.0-kali1-amd64 SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
nohwcrypt: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/libhackrf0.conf]
blacklist hackrf


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 3645.437371] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1000 with error -110 (repeated 92 times)
[ 3656.528723] ieee80211 phy0: rt2800_wait_csr_ready: Error - Unstable hardware
[ 3656.640407] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -110
[ 3656.748843] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x7010 with error -110
[ 3656.857409] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0404 with error -110
[27461.686940] e1000: eth0 NIC Link is Down
[27467.705676] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[27570.794514] e1000: eth0 NIC Link is Down
[27574.808823] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX


########## wireless info END ############



```

Thank you very much for trying to help me

---

