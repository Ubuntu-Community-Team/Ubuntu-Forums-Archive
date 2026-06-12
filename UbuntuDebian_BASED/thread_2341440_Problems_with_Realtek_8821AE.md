---
title: "Problems with Realtek 8821AE"
date: 2016-10-28
forum: Ubuntu/Debian BASED
---

### Post by moso2 on 2016-10-28
Yes, another user with WiFi issues.

This is a problem that's been annoying me for quite some time now.
I can connect fine to an AP, but after a random amount of time (I have a feeling it's tied to IP TTL), I'm unable to resolve hosts. As if my DNS resolver stops working.
The problem even extends to ***localhost***, as I'm unable to resolve the vagrant sites I have running, which are set in ***/etc/hosts***. I'm still connected to the AP - I don't get disconnected at any point.

The only solution to get back online (so far) is to reconnect through the top panel, or run:
```
sudo service network-manager restart
```

I've tried the following:
- The usual, skipping DHCP, setting DNS servers manually (twice), etc.
- Run an upstream kernel, as some users pointed out it was fixed upstream.
- [Different drivers]("https://github.com/lwfinger/rtlwifi_new").
- Disable Bluetooth and IPv6 - the latter through ***/etc/sysctl.conf***.
- Echo'ing configurations through modprobe.

I've also tried testing different distro's: I'm currently running elementaryOS Loki (16.04 based), pure Ubuntu 16.04, Solus (just to try something not-Ubuntu-based), Budgie Remix (both 16.04 and 16.10 variants), and pure Ubuntu 16.10.
The latter might work best, as I was unable to reproduce the error during the 45 minutes of testing I did on a live CD, however, as I mentioned I also tried the 16.10 variant of Budgie Remix and the error was there within a minute.

I have a feeling that it's tied to the router I'm connecting to, however, I'm unable to configure it as it's the company's network, and I'm not going to mess with that.
I would be able to do small tinkering through the web UI (I have access), if any of you have a solition. The reason I have this feeling is, that I've also tried with a WiFi dongle (sadly also by Realtek), and experienced the same issues.

If any of you have a hint what to try next, I'd really appreciate it.

PS: It's working fine in Windows :(

---

### Post by moso2 on 2016-11-28
Bump...

I'm getting really desperate

---

### Post by jeremy31 on 2016-11-28
Can you run the wireless script, see link in my signature

Welcome to the forums

---

### Post by moso2 on 2016-11-29
> **jeremy31 said:**
> Can you run the wireless script, see link in my signature

Welcome to the forums
```


########## wireless info START ##########


Report from: 29 Nov 2016 14:57 CET +0100


Booted last: 29 Nov 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	elementary
Description:	elementary OS 0.4 Loki
Release:	0.4
Codename:	loki


##### kernel ############################


Linux 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Pantheon


##### lspci #############################


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave RTL8821AE 802.11ac PCIe Wireless Network Adapter [1a3b:2161]
	Kernel driver in use: rtl8821ae


04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
4: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wl                   6365184  0
rtl8821ae             225280  0
btcoexist             180224  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  6 btcoexist,rtl_pci,rtl_usb,rtl8192c_common,rtl8192cu,rtl8821ae
mac80211              737280  6 rtl8xxxu,rtl_pci,rtl_usb,rtlwifi,rtl8192cu,rtl8821ae
cfg80211              565248  3 wl,mac80211,rtlwifi
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback
iface wlx<IF from MAC [IF3]> inet manual


##### ifconfig ##########################


enp4s0f1  Link encap:Ethernet  HWaddr <MAC 'enp4s0f1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::11e4:8c8c:7149:e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6023416 (6.0 MB)  TX bytes:664653 (664.6 KB)


wlx<IF from MAC [IF3]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF3]>' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0f1  no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:"eyeforce"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'eyeforce' [AN3]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


wlx<IF from MAC [IF3]>  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       925     1  0 14:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-47-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     eyeforce 2
GENERAL.CON-UUID:                       b1c61cb8-d0db-497a-9065-daf6aa9b0e1f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b1c61cb8-d0db-497a-9065-daf6aa9b0e1f | eyeforce 2
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   55e6b32a-c516-4d2e-b15f-090250e559c3 | eyeforce 1
IP4.ADDRESS[1]:                         192.168.1.24/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       expiry = 1480428352
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.24
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 208.67.222.222 208.67.220.220
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::11e4:8c8c:7149:e5/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp4s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.1/net/enp4s0f1
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         wlx<IF from MAC [IF3]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/wlx<IF from MAC [IF3]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF3]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                 <MAC '--' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
HouseGuest         <MAC 'HouseGuest' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
eyeforce           <MAC 'eyeforce' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Telenor41896F      <MAC 'Telenor41896F' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
eyeforce           <MAC 'eyeforce' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
HouseGuest         <MAC 'HouseGuest' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
ZyXEL_399C         <MAC 'ZyXEL_399C' [AN7]>  Infra  13    2472 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
CableBox-2410      <MAC 'CableBox-2410' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
NETGEAR95          <MAC 'NETGEAR95' [AN9]>  Infra  2     2417 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
HomeBox-8070_2.4G  <MAC 'HomeBox-8070_2.4G' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
ZyXEL_ADAC         <MAC 'ZyXEL_ADAC' [AN11]>  Infra  8     2447 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/eyeforce]] (600 root)
[connection] id=eyeforce | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=eyeforce
[ipv4] method=auto
[ipv6] method=link-local


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP 1]] (600 root)
[connection] id=AndroidAP 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eyeforce 2]] (600 root)
[connection] id=eyeforce 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=eyeforce
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eyeforce 1]] (600 root)
[connection] id=eyeforce 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=eyeforce
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Copenhagen (based on set time zone)


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


enp4s0f1  no frequency information.


wlp3s0    32 channels in total; available frequencies :
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


wlx<IF from MAC [IF3]>  13 channels in total; available frequencies :
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


##### iwlist scan #######################


wlp3s0    Failed to read scan data : Resource temporarily unavailable


lo        Interface doesn't support scanning.


wlx<IF from MAC [IF3]>  Interface doesn't support scanning : Network is down


enp4s0f1  Interface doesn't support scanning.


##### module infos ######################


[rtl8xxxu]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     6318AD97B9A7F66A430B132
depends:        mac80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)


[rtl8192cu]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     1E38F9EBFF16759B9165DC6
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     27C0F77F8DACB3348CB7E8F
depends:        mac80211,rtlwifi
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[rtl8192c_common]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     60F35EAD11049C72542116B
depends:        rtlwifi
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[wl]
filename:       /lib/modules/4.4.0-47-generic/extra/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[rtl8821ae]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     E0FCD0E171EB4D1C4C2F8E8
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B5DB05F5C727F9D7AAF6E69
depends:        mac80211,rtlwifi
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     AE963536CD7366B572F5D4F
depends:        mac80211,cfg80211
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]


[rtl8192cu]
debug: 1
swenc: N


[rtl8821ae]
debug: 1
disable_watchdog: N
fwlps: N
int_clear: Y
ips: N
msi: Y
swenc: Y
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae swenc=1 ips=0 fwlps=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    3.430125] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[    3.699497] IPv6: ADDRCONF(NETDEV_UP): enp4s0f1: link is not ready
[    3.718155] rtlwifi: channel plan 0x0
[    3.718156] rtlwifi: bad channel plan 0x0
[    3.718157] rtlwifi: country code 11
[    3.718182] Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    3.718967] r8169 0000:04:00.1 enp4s0f1: link down
[    3.719052] IPv6: ADDRCONF(NETDEV_UP): enp4s0f1: link is not ready
[    3.719504] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[    3.723886] rtl8192cu 1-1:1.0 wlx<IF from MAC [IF3]>: renamed from wlan0
[    3.793405] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.683831] wlp3s0: authenticate with <MAC 'eyeforce' [AN5]>
[    6.684221] wlp3s0: send auth to <MAC 'eyeforce' [AN5]> (try 1/3)
[    6.784420] wlp3s0: send auth to <MAC 'eyeforce' [AN5]> (try 2/3)
[    6.792763] wlp3s0: authenticated
[    6.796454] wlp3s0: associate with <MAC 'eyeforce' [AN5]> (try 1/3)
[    6.800793] wlp3s0: RX AssocResp from <MAC 'eyeforce' [AN5]> (capab=0x431 status=0 aid=1)
[    6.801017] wlp3s0: associated
[    6.801182] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   42.547345] wlp3s0: authenticate with <MAC 'eyeforce' [AN3]>
[   42.547724] wlp3s0: send auth to <MAC 'eyeforce' [AN3]> (try 1/3)
[   42.550542] wlp3s0: authenticated
[   42.553788] wlp3s0: associate with <MAC 'eyeforce' [AN3]> (try 1/3)
[   42.557213] wlp3s0: RX AssocResp from <MAC 'eyeforce' [AN3]> (capab=0x431 status=0 aid=10)
[   42.557434] wlp3s0: associated


########## wireless info END ############

```

Though, it's obviously working at the moment - otherwise I wouldn't be able to post this.

---

### Post by howefield on 2016-11-29
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by moso2 on 2016-12-07
After exhausting every idea I could possibly come up with, I decided to replace the WiFi module with one of the brand Atheros by Qualcomm.

Everything seems to be in order, so I guess the issue was never software.

---

### Post by spectatorx on 2016-12-09
This may be odd and kinda bruteforce solution, as it may be related to device drivers in kernel update kernel to latest available version and see if it works now. Deb packages with kernel you can download from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

If it still making problems, after kernel update, then just uninstall latest kernel packages.

---

