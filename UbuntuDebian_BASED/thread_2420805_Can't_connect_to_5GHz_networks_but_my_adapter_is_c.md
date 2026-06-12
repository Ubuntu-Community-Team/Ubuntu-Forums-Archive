---
title: "Can't connect to 5GHz networks but my adapter is capable"
date: 2019-06-11
forum: Ubuntu/Debian BASED
---

### Post by zazukih on 2019-06-11
Before Installing Deepin I had Mint 18 and I could connect perfectly to 5GHz networks, but right now that I installed Deepin I can't connect to 5GHz networks but I can connect to 2.4Ghz ones. My network adapter is a Broadcom one so I followed the pinned post and didn't work. 
Here's my wireless info pastebin

```
########## wireless info START ##########

Report from: 11 Jun 2019 11:16 CEST +0200


Booted last: 11 Jun 2019 00:00 CEST +0200


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Deepin
Description:	Deepin 15.10.1
Release:	15.10.1
Codename:	stable


##### kernel ############################


Linux 4.15.0-30deepin-generic #31 SMP Fri Nov 30 04:29:02 UTC 2018 x86_64 unknown unknown GNU/Linux


Parameters: ro, splash, quiet, DEEPIN_GFXMODE=0,1024x768


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:3388]
	Kernel driver in use: r8169


0d:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless Network Adapter [103c:145c]
	Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 002 Device 003: ID 0000:0538  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0603:00f1 Novatek Microelectronics Corp. Keyboard (Labtec Ultra Flat Keyboard)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:d281 Suyin Corp. 
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


Failed to read SecureBoot


##### lsmod #############################


brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
bcma                   57344  2 brcmsmac
mac80211              778240  1 brcmsmac
cfg80211              622592  2 brcmsmac,mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 wmi_bmof,hp_wmi


##### interfaces ########################


[/etc/network/interfaces]
source-directory /etc/network/interfaces.d


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
4: wlp13s0b1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp13s0b1' [IF2]> brd <MAC address>
    inet 192.168.43.218/24 brd 192.168.43.255 scope global noprefixroute dynamic wlp13s0b1
       valid_lft 3312sec preferred_lft 3312sec
    inet6 fe80::2f74:b963:af80:cb4d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlp13s0b1  IEEE 802.11  ESSID:"Nozomu"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Nozomu' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0


##### route #############################


default via 192.168.43.42 dev wlp13s0b1 proto dhcp metric 600 
192.168.43.0/24 dev wlp13s0b1 proto kernel scope link src 192.168.43.218 metric 600 


##### resolv.conf #######################


[644 root '/etc/resolv.conf']
nameserver 192.168.43.42


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2691     1  0 10:28 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp13s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.15.0-30deepin-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp13s0b1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:0d:00.0/bcma0:1/net/wlp13s0b1
GENERAL.IP-IFACE:                       wlp13s0b1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Nozomu
GENERAL.CON-UUID:                       80caaa05-4716-41ba-afa4-de57bea11453
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.43.218/24
IP4.GATEWAY:                            192.168.43.42
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.43.42, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.43.0/24, nh = 0.0.0.0, mt = 600
IP4.DNS[1]:                             192.168.43.42
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.42
DHCP4.OPTION[5]:                        ip_address = 192.168.43.218
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.42
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.42
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1560247908
DHCP4.OPTION[20]:                       host_name = alessandro-PC
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.43.42
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::2f74:b963:af80:cb4d/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   80caaa05-4716-41ba-afa4-de57bea11453 | Nozomu


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/eno1
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID             BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Nozomu           <MAC 'Nozomu' [AC1]>  Infra  6     2437 MHz  130 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     *      
SecmoticSDCA_3   <MAC 'SecmoticSDCA_3' [AC4]>  Infra  7     2442 MHz  65 Mbit/s   79      &#9602;&#9604;&#9606;_  WPA2       no             
JAZZTEL_EEaD     <MAC 'JAZZTEL_EEaD' [AC7]>  Infra  1     2412 MHz  130 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
Orange-BC76      <MAC 'Orange-BC76' [AC5]>  Infra  6     2437 MHz  65 Mbit/s   45      &#9602;&#9604;__  WPA2       no             
TERAPIA URBANA   <MAC 'TERAPIA URBANA' [AN5]>  Infra  9     2452 MHz  130 Mbit/s  44      &#9602;&#9604;__  WPA2       no             
MIWIFI_2G_etAW   <MAC 'MIWIFI_2G_etAW' [AC3]>  Infra  1     2412 MHz  405 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no             
MOVISTAR_4C4F    <MAC 'MOVISTAR_4C4F' [AC12]>  Infra  6     2437 MHz  130 Mbit/s  34      &#9602;&#9604;__  WPA2       no             
MOVISTAR_8EE9    <MAC 'MOVISTAR_8EE9' [AN8]>  Infra  6     2437 MHz  130 Mbit/s  34      &#9602;&#9604;__  WPA2       no             
MIWIFI_2G_dkPJ   <MAC 'MIWIFI_2G_dkPJ' [AC10]>  Infra  6     2437 MHz  130 Mbit/s  34      &#9602;&#9604;__  WPA2       no             
CLISIMED         <MAC 'CLISIMED' [AC16]>  Infra  7     2442 MHz  130 Mbit/s  34      &#9602;&#9604;__  WPA2       no             
Lowi5AC4         <MAC 'Lowi5AC4' [AN11]>  Infra  10    2457 MHz  130 Mbit/s  34      &#9602;&#9604;__  WPA2       no             
_ONOWiFi         <MAC '_ONOWiFi' [AN12]>  Infra  3     2422 MHz  130 Mbit/s  30      &#9602;___  --         no             
MiFibra-C350     <MAC 'MiFibra-C350' [AN13]>  Infra  9     2452 MHz  130 Mbit/s  30      &#9602;___  WPA2       no             
MOVISTAR_CBF4    <MAC 'MOVISTAR_CBF4' [AC11]>  Infra  6     2437 MHz  130 Mbit/s  29      &#9602;___  WPA2       no             
MOVISTAR_68E5    <MAC 'MOVISTAR_68E5' [AN15]>  Infra  11    2462 MHz  130 Mbit/s  29      &#9602;___  WPA2       no             
PTVTELECOM_Py6u  <MAC 'PTVTELECOM_Py6u' [AC9]>  Infra  6     2437 MHz  130 Mbit/s  22      &#9602;___  WPA1 WPA2  no             
CREA             <MAC 'CREA' [AC6]>  Infra  6     2437 MHz  54 Mbit/s   22      &#9602;___  WPA2       no             
MOVISTAR_7032    <MAC 'MOVISTAR_7032' [AC14]>  Infra  6     2437 MHz  130 Mbit/s  20      &#9602;___  WPA2       no             
MIWIFI_2G_7mHa   <MAC 'MIWIFI_2G_7mHa' [AC13]>  Infra  6     2437 MHz  130 Mbit/s  19      &#9602;___  WPA2       no             
PTVTELECOM_32Kx  <MAC 'PTVTELECOM_32Kx' [AC15]>  Infra  6     2437 MHz  130 Mbit/s  17      &#9602;___  WPA1 WPA2  no             


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager config #############


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=true
[device]
wifi.scan-rand-mac-address=no
[connectivity]
uri=http://packages.deepin.com/misc/check_network_status.txt


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Nozomu]] (600 root)
[connection] id=Nozomu | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp13s0b1' [IF2]> | mac-address-blacklist= | ssid=Nozomu
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: Europe/Madrid (based on set time zone)


global
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


phy#0
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eno1      no frequency information.


wlp13s0b1  11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      11   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)


wlp13s0b1  Scan completed :
          Cell 01 - Address: <MAC 'Nozomu' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"Nozomu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001f861e8f
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MiFibra-DEC0' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"MiFibra-DEC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011afd162b6
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MIWIFI_2G_etAW' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MIWIFI_2G_etAW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a4ef94180
                    Extra: Last beacon: 1568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'SecmoticSDCA_3' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"SecmoticSDCA_3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000fc77979
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Orange-BC76' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Orange-BC76"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012820fe428
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'CREA' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"CREA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000174f8541183
                    Extra: Last beacon: 144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'JAZZTEL_EEaD' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_EEaD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a4f9bdb88
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'MIWIFI_2G_uhYf' [AC8]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MIWIFI_2G_uhYf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a4f748f18
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'PTVTELECOM_Py6u' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"PTVTELECOM_Py6u"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a63dd0288
                    Extra: Last beacon: 532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'MIWIFI_2G_dkPJ' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MIWIFI_2G_dkPJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000025ac24188
                    Extra: Last beacon: 256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'MOVISTAR_CBF4' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_CBF4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f72a16d739
                    Extra: Last beacon: 252ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'MOVISTAR_4C4F' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_4C4F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016cdbcf183
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'MIWIFI_2G_7mHa' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"MIWIFI_2G_7mHa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000010267918a
                    Extra: Last beacon: 200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'MOVISTAR_7032' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_7032"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f3377c183
                    Extra: Last beacon: 500ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'PTVTELECOM_32Kx' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"PTVTELECOM_32Kx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001da1f180
                    Extra: Last beacon: 120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'CLISIMED' [AC16]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"CLISIMED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a470eb183
                    Extra: Last beacon: 208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'Orange-Antonio' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Orange-Antonio"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a4c85196
                    Extra: Last beacon: 108ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/4.15.0-30deepin-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     9C9FAD7751B9B9193924D1D
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
retpoline:      Y
intree:         Y
name:           brcmsmac
vermagic:       4.15.0-30deepin-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[brcmutil]
filename:       /lib/modules/4.15.0-30deepin-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     389318E018771B5453D0B02
depends:        
retpoline:      Y
intree:         Y
name:           brcmutil
vermagic:       4.15.0-30deepin-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[bcma]
filename:       /lib/modules/4.15.0-30deepin-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F4DB57748318105D28C557A
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       4.15.0-30deepin-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[mac80211]
filename:       /lib/modules/4.15.0-30deepin-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-30deepin-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.15.0-30deepin-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-30deepin-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


brcmsmac


##### modprobe options ##################


[/etc/modprobe.d/bcm.conf]
blacklist b43
blacklist wl


[/etc/modprobe.d/blacklist.conf]
blacklist b43
blacklist ssb


[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 bt_coex_active=0 power_save=0 swcrypto=1


[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


find: ‘/etc/pm/*.d’: No such file or directory


##### udev rules ########################


##### dmesg #############################


[ 1256.870312] wlp13s0b1: associated
[ 1256.890241] IPv6: ADDRCONF(NETDEV_CHANGE): wlp13s0b1: link becomes ready
[ 1256.952103] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1822.120719] wlp13s0b1: deauthenticated from <MAC 'Nozomu' [AC1]> (Reason: 3=DEAUTH_LEAVING)
[ 1822.177813] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1822.177836] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1822.177838] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1822.986682] wlp13s0b1: authenticate with <MAC 'Nozomu' [AC1]>
[ 1822.987502] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 1/3)
[ 1823.091996] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 2/3)
[ 1823.280704] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 3/3)
[ 1823.456527] wlp13s0b1: authentication with <MAC 'Nozomu' [AC1]> timed out
[ 1837.872045] IPv6: ADDRCONF(NETDEV_UP): wlp13s0b1: link is not ready
[ 1842.848629] wlp13s0b1: authenticate with <MAC 'Nozomu' [AC1]>
[ 1842.848728] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 1/3)
[ 1842.850513] wlp13s0b1: authenticated
[ 1842.857044] wlp13s0b1: associate with <MAC 'Nozomu' [AC1]> (try 1/3)
[ 1842.861245] wlp13s0b1: RX AssocResp from <MAC 'Nozomu' [AC1]> (capab=0x411 status=0 aid=1)
[ 1842.861941] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1842.861947] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1842.861958] wlp13s0b1: associated
[ 1842.877404] IPv6: ADDRCONF(NETDEV_CHANGE): wlp13s0b1: link becomes ready
[ 1847.329343] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2382.789726] wlp13s0b1: deauthenticated from <MAC 'Nozomu' [AC1]> (Reason: 3=DEAUTH_LEAVING)
[ 2382.831598] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2382.831606] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2382.831608] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2383.648189] wlp13s0b1: authenticate with <MAC 'Nozomu' [AC1]>
[ 2383.649405] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2383.720537] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 2/3)
[ 2383.858165] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 3/3)
[ 2384.035926] wlp13s0b1: authentication with <MAC 'Nozomu' [AC1]> timed out
[ 2390.979939] wlp13s0b1: authenticate with <MAC 'Nozomu' [AC1]>
[ 2390.980851] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2390.982768] wlp13s0b1: authenticated
[ 2390.991005] wlp13s0b1: associate with <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2390.994950] wlp13s0b1: RX AssocResp from <MAC 'Nozomu' [AC1]> (capab=0x411 status=0 aid=1)
[ 2390.995556] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2390.995562] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2390.995566] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2390.995577] wlp13s0b1: associated
[ 2518.634053] wlp13s0b1: deauthenticating from <MAC 'Nozomu' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2518.635115] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2518.635121] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2518.635123] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2519.843189] wlp13s0b1: authenticate with <MAC 'Nozomu' [AC1]>
[ 2519.843291] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2519.844792] wlp13s0b1: authenticated
[ 2519.846168] wlp13s0b1: associate with <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2519.849433] wlp13s0b1: RX AssocResp from <MAC 'Nozomu' [AC1]> (capab=0x411 status=0 aid=1)
[ 2519.850130] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2519.850137] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2519.850147] wlp13s0b1: associated
[ 2519.935336] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2611.450756] wlp13s0b1: deauthenticating from <MAC 'Nozomu' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2611.452999] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2611.453010] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2611.453012] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2612.023717] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[ 2624.257426] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[ 2624.257459] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[ 2624.257486] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[ 2624.257539] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[ 2624.270026] bcma: bus0: Bus registered
[ 2624.284747] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[ 2624.286156] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[ 2624.288113] brcmsmac bcma0:1 wlp13s0b1: renamed from wlan0
[ 2624.429639] IPv6: ADDRCONF(NETDEV_UP): wlp13s0b1: link is not ready
[ 2624.496273] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2624.496298] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[ 2624.496550] IPv6: ADDRCONF(NETDEV_UP): wlp13s0b1: link is not ready (repeated 2 times)
[ 2625.293953] wlp13s0b1: authenticate with <MAC 'Nozomu' [AC1]>
[ 2625.296181] wlp13s0b1: send auth to <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2625.297709] wlp13s0b1: authenticated
[ 2625.299681] wlp13s0b1: associate with <MAC 'Nozomu' [AC1]> (try 1/3)
[ 2625.308472] wlp13s0b1: RX AssocResp from <MAC 'Nozomu' [AC1]> (capab=0x411 status=0 aid=1)
[ 2625.309162] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2625.309176] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2625.309195] wlp13s0b1: associated
[ 2625.329494] IPv6: ADDRCONF(NETDEV_CHANGE): wlp13s0b1: link becomes ready
[ 2625.412336] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)


########## wireless info END ############
```

---

### Post by jeremy31 on 2019-06-11
Moved to Ubuntu/Debian based

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1010931/comments/38](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1010931/comments/38)

---

