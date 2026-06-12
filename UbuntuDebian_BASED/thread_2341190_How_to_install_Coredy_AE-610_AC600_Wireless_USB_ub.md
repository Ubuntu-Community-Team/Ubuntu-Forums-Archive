---
title: "How to install Coredy AE-610 AC600 Wireless USB ubuntu based 64b linux distro"
date: 2016-10-25
forum: Ubuntu/Debian BASED
---

### Post by antoniocgregorio on 2016-10-25
How to install Coredy AE-610 AC600 Wireless USB ubuntu based 64b linux distro

Please help... thank you

---

### Post by jeremy31 on 2016-10-25
*Thread moved to **Networking & Wireless**.*

Please post the results from terminal- use CTRL + t to open a terminal window, enter ```
lsusb
```

Welcome to the forums

---

### Post by antoniocgregorio on 2016-10-25
Bus 001 Device 003: ID 0e8d:7610 MediaTek Inc.

The complete lsubs is:
Bus 002 Device 005: ID 058f:3821 Alcor Micro Corp. 
Bus 002 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0e8d:7610 MediaTek Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I want to disable the internal WLAN Adapter and use the one on usb with antenna.
Please help. Thanks alot...

The instructions on the site and cd does not work...

---

### Post by jeremy31 on 2016-10-25
Please see the wireless script link in my signature and post your results since you want to disable the internal adapter

---

### Post by antoniocgregorio on 2016-10-25
Not working... update done!
s-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2016-10-26 02:09:30--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2016-10-26 02:09:31--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.12.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.12.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info       100%[===================>]  15.78K  71.0KB/s    in 0.2s    

Last-modified header missing -- time-stamps turned off.
2016-10-26 02:09:32 (71.0 KB/s) - &#8216;wireless-info&#8217; saved [16156/16156]

---

### Post by antoniocgregorio on 2016-10-25
```
########## wireless info START ##########

Report from: 26 Oct 2016 02:09 CEST +0200

Booted last: 26 Oct 2016 00:00 CEST +0200

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Linux Lite 3.0
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xfce

##### lspci #############################

##### lsusb #############################

Bus 002 Device 005: ID 058f:3821 Alcor Micro Corp. 
Bus 002 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0e8d:7610 MediaTek Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF1]>' [IF1]>  
          inet addr:10.57.218.51  Bcast:10.57.219.255  Mask:255.255.254.0
          inet6 addr: fe80::8f73:78de:798a:dadd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1319138 (1.3 MB)  TX bytes:469927 (469.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  IEEE 802.11bgn  ESSID:"Astra_Hotel"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Astra_Hotel' [AC2]>   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:64   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.57.218.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF1]>
10.57.218.0     0.0.0.0         255.255.254.0   U     600    0        0 wlx<IF from MAC [IF1]>

##### resolv.conf #######################

nameserver 127.0.1.1
search pwlan.ch

##### network managers ##################

Installed:

    NetworkManager

Running:

root       832     1  0 01:59 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/net/wlx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Astra Manual
GENERAL.CON-UUID:                       1e38c495-79dd-4de5-b23a-73b4e7036ead
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1e38c495-79dd-4de5-b23a-73b4e7036ead | Astra Manual
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   028200fd-2c3d-42b2-a535-0c72e96bc94c | Swisscom
IP4.ADDRESS[1]:                         10.57.218.51/23
IP4.GATEWAY:                            10.57.218.1
IP4.DNS[1]:                             195.186.152.32
IP4.DNS[2]:                             195.186.216.32
IP4.DOMAIN[1]:                          pwlan.ch
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1477441419
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.57.218.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.57.218.51
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = pwlan.ch
DHCP4.OPTION[19]:                       dhcp_renewal_time = 480
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 10.57.219.255
DHCP4.OPTION[22]:                       domain_name_servers = 195.186.152.32 195.186.216.32
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 960
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 840
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.254.0
DHCP4.OPTION[28]:                       network_number = 10.57.218.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 10.57.218.1
IP6.ADDRESS[1]:                         fe80::8f73:78de:798a:dadd/64
IP6.GATEWAY:                            

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Swisscom             <MAC 'Swisscom' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  --           no        
Swisscom_Auto_Login  <MAC 'Swisscom_Auto_Login' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X  no        
Astra_Hotel          <MAC 'Astra_Hotel' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  --           yes     * 

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

[[/etc/NetworkManager/system-connections/Astra_Hotel]] (600 root)
[connection] id=Astra_Hotel | type=wifi | permissions=user:linux:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Astra_Hotel
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Astra Manual]] (600 root)
[connection] id=Astra Manual | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Astra_Hotel
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Swisscom]] (600 root)
[connection] id=Swisscom | type=wifi | permissions=user:tugatux:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Swisscom
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Zurich (based on set time zone)

country CH: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlx<IF from MAC [IF1]>  13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'Swisscom' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"Swisscom"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b7d92f9156d
                    Extra: Last beacon: 32ms ago
          Cell 02 - Address: <MAC 'Astra_Hotel' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"Astra_Hotel"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b7d92f9d7e4
                    Extra: Last beacon: 32ms ago
          Cell 03 - Address: <MAC 'Swisscom_Auto_Login' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Swisscom_Auto_Login"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b7d92f97a17
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
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
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[rtl8192cu]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2C9D776AE1B25BDC5405217
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     856F91AC5F9AFDB1993D1E4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     68438042FA7FFFCF4EB1B75
depends:        rtlwifi
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[rtl8192cu]
debug: 0
swenc: N

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  859.313758] wlx<IF from MAC [IF1]>: authenticate with <MAC 'Astra_Hotel' [AC2]>
[  859.340329] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[  859.343125] wlx<IF from MAC [IF1]>: authenticated
[  859.345454] wlx<IF from MAC [IF1]>: associate with <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[  859.364164] wlx<IF from MAC [IF1]>: RX AssocResp from <MAC 'Astra_Hotel' [AC2]> (capab=0x421 status=0 aid=2)
[  859.366020] wlx<IF from MAC [IF1]>: associated
[  859.778903] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:6c:41:6a:ca:6c:6a:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=255 ID=38804 PROTO=2  (repeated 2 times)
[  861.376428] wlx<IF from MAC [IF1]>: Limiting TX power to 16 dBm as advertised by <MAC 'Astra_Hotel' [AC2]>
[  883.142232] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=193.134.255.93 DST=10.57.218.51 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=32398 PROTO=TCP SPT=443 DPT=40168 WINDOW=0 RES=0x00 RST URGP=0 
[  884.138909] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=172.217.23.66 DST=10.57.218.51 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=34002 PROTO=TCP SPT=443 DPT=43514 WINDOW=0 RES=0x00 RST URGP=0 
[  884.138983] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=172.217.23.66 DST=10.57.218.51 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=34003 PROTO=TCP SPT=443 DPT=43514 WINDOW=0 RES=0x00 RST URGP=0 
[  884.143441] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=172.217.23.66 DST=10.57.218.51 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=34004 PROTO=TCP SPT=443 DPT=43514 WINDOW=0 RES=0x00 RST URGP=0 
[  927.807760] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=193.135.3.34 DST=10.57.218.51 LEN=52 TOS=0x00 PREC=0x00 TTL=54 ID=11969 PROTO=TCP SPT=80 DPT=33234 WINDOW=235 RES=0x00 ACK FIN URGP=0 
[  928.234598] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=193.135.3.34 DST=10.57.218.51 LEN=52 TOS=0x00 PREC=0x00 TTL=54 ID=12189 PROTO=TCP SPT=80 DPT=33234 WINDOW=235 RES=0x00 ACK FIN URGP=0 
[  929.091059] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=193.135.3.34 DST=10.57.218.51 LEN=52 TOS=0x00 PREC=0x00 TTL=54 ID=12987 PROTO=TCP SPT=80 DPT=33234 WINDOW=235 RES=0x00 ACK FIN URGP=0 
[  930.802505] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:02:00:00:01:a4:dc:08:00 SRC=193.135.3.34 DST=10.57.218.51 LEN=52 TOS=0x00 PREC=0x00 TTL=54 ID=14469 PROTO=TCP SPT=80 DPT=33234 WINDOW=235 RES=0x00 ACK FIN URGP=0 
[ 1049.673725] wlx<IF from MAC [IF1]>: deauthenticating from <MAC 'Astra_Hotel' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1057.456913] wlx<IF from MAC [IF1]>: authenticate with <MAC 'Astra_Hotel' [AC2]>
[ 1057.486213] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[ 1057.588248] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 2/3)
[ 1057.692233] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 3/3)
[ 1057.796253] wlx<IF from MAC [IF1]>: authentication with <MAC 'Astra_Hotel' [AC2]> timed out
[ 1058.784771] wlx<IF from MAC [IF1]>: authenticate with <MAC 'Astra_Hotel' [AC2]>
[ 1058.809465] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[ 1058.912178] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 2/3)
[ 1058.986914] wlx<IF from MAC [IF1]>: authenticated
[ 1058.988208] wlx<IF from MAC [IF1]>: associate with <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[ 1059.092162] wlx<IF from MAC [IF1]>: associate with <MAC 'Astra_Hotel' [AC2]> (try 2/3)
[ 1059.196156] wlx<IF from MAC [IF1]>: associate with <MAC 'Astra_Hotel' [AC2]> (try 3/3)
[ 1059.201019] wlx<IF from MAC [IF1]>: RX AssocResp from <MAC 'Astra_Hotel' [AC2]> (capab=0x421 status=0 aid=2)
[ 1059.202966] wlx<IF from MAC [IF1]>: associated
[ 1059.743851] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:6c:41:6a:ca:6c:6a:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=255 ID=38851 PROTO=2  (repeated 3 times)
[ 1059.813372] wlx<IF from MAC [IF1]>: Limiting TX power to 16 dBm as advertised by <MAC 'Astra_Hotel' [AC2]>
[ 1060.740252] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:6c:41:6a:ca:6c:6a:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=255 ID=38851 PROTO=2  (repeated 3 times)
[ 1101.288361] wlx<IF from MAC [IF1]>: deauthenticating from <MAC 'Astra_Hotel' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1102.205799] wlx<IF from MAC [IF1]>: authenticate with <MAC 'Astra_Hotel' [AC2]>
[ 1102.231653] wlx<IF from MAC [IF1]>: send auth to <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[ 1102.233873] wlx<IF from MAC [IF1]>: authenticated
[ 1102.237205] wlx<IF from MAC [IF1]>: associate with <MAC 'Astra_Hotel' [AC2]> (try 1/3)
[ 1102.259782] wlx<IF from MAC [IF1]>: RX AssocResp from <MAC 'Astra_Hotel' [AC2]> (capab=0x421 status=0 aid=2)
[ 1102.275035] wlx<IF from MAC [IF1]>: associated
[ 1102.737930] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:6c:41:6a:ca:6c:6a:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=255 ID=38867 PROTO=2 
[ 1103.260746] wlx<IF from MAC [IF1]>: Limiting TX power to 16 dBm as advertised by <MAC 'Astra_Hotel' [AC2]>
[ 1103.737238] [UFW BLOCK] IN=wlx<IF from MAC [IF1]> OUT= MAC=<MAC 'wlx<IF from MAC [IF1]>' [IF1]>:6c:41:6a:ca:6c:6a:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=255 ID=38867 PROTO=2 

########## wireless info END ############
```

---

### Post by howefield on 2016-10-26
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by jeremy31 on 2016-10-26
You may want to consider returning this wifi card as I see a lot of warnings when I try to compile modules from source code on github and some of them fail

---

