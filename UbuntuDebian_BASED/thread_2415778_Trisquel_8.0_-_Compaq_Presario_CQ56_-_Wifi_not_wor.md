---
title: "Trisquel 8.0 - Compaq Presario CQ56 - Wifi not working."
date: 2019-03-31
forum: Ubuntu/Debian BASED
---

### Post by leba39 on 2019-03-31
Hello everyone, I'm wondering if anyone could help me with this issue. I'd just installed Trisquel 8.0 on my Compaq Presario CQ56 (with its unfamous RT5390 wireless card) and I can't seem to get my WIFI going.

It says "Device not ready". The wifi switch on my laptop is currently red and it seems to do nothing at all.

I had a similar experience a few years back when I was using Lubuntu. I posted a similar thread here and got it working thanks to the magnificient help of "wildmanne39", to whom I'm still grateful. The link to that thread is this one (you can notice that I'm logged in with another user but that's because I forgot my credentials):

[https://ubuntuforums.org/showthread.php?t=2352890](https://ubuntuforums.org/showthread.php?t=2352890)

I already tried those very same steps but I'm getting nothing this time -either I'm doing them wrong or that solution isn't working anymore-. I went ahead and executed the wireless script to obtain info. The output is this:

```


########## wireless info START ##########


Report from: 31 Mar 2019 20:48 CEST +0200


Booted last: 31 Mar 2019 00:00 CET +0100


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Trisquel
Description:    Trisquel GNU/Linux 8.0, Flidas
Release:    8.0
Codename:    flidas


##### kernel ############################


Linux 4.4.0-143-generic #169+8.0trisquel2 SMP Tue Mar 19 04:55:45 UTC 2019 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Trisquel-mini


##### lspci #############################


02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    DeviceName: plug in device WLAN
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1605]
    Kernel driver in use: r8169


##### lsusb #############################


Unknown line at line 2468
Bus 002 Device 002: ID 0bda:58e0 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f3:0232 Elan Microelectronics Corp. Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              49152  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              663552  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              499712  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.0.165/24 brd 192.168.0.255 scope global dynamic enp3s0
       valid_lft 84661sec preferred_lft 84661sec
    inet6 fe80::dcc0:1bd7:6bb6:2ed7/64 scope link 
       valid_lft forever preferred_lft forever
3: wlo1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlo1' [IF2]> brd <MAC address>


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


default via 192.168.0.1 dev enp3s0 proto static metric 100 
169.254.0.0/16 dev enp3s0 scope link metric 1000 
192.168.0.0/24 dev enp3s0 proto kernel scope link src 192.168.0.165 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       951     1  0 20:12 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexión cableada 1
GENERAL.CON-UUID:                       b03f6b19-535e-3137-a7e1-29d7a22096d2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b03f6b19-535e-3137-a7e1-29d7a22096d2 | Conexión cableada 1
IP4.ADDRESS[1]:                         192.168.0.165/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1554142743
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.165
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::dcc0:1bd7:6bb6:2ed7/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe (U98Z077.00 Half-size Mini PCIe Card)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-143-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlo1
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### Netplan config ####################


##### iw reg get ########################


Region: Europe/Madrid (based on set time zone)


country ES: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp3s0    no frequency information.


wlo1      13 channels in total; available frequencies :
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


wlo1      Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BC6BFD2B9908BF174EEB977
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C6D1A5D54B56AB8E61D5A73
depends:        rt2800lib,rt2x00lib,rt2x00mmio
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 


[rt2800lib]
filename:       /lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     9C888DC1E0B053A56F1B5D4
depends:        rt2x00lib,mac80211,crc-ccitt
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 


[rt2x00pci]
filename:       /lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 


[rt2x00lib]
filename:       /lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C5D09D684243C14C5DFCF56
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 


[mac80211]
filename:       /lib/modules/4.4.0-143-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C8423B465D0E10D7D269F05
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-143-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     652D6E09D5CB85B718E634E
depends:        
retpoline:      Y
intree:         Y
vermagic:       4.4.0-143-generic SMP mod_unload modversions 686 retpoline 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: Y


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


[/etc/modprobe.d/disable-pcsp.conf]
blacklist snd-pcsp


[/etc/modprobe.d/disable-radeon.conf]
blacklist radeon


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/openfwwf.conf]
options b43 qos=0
options b43 nohwcrypt=1


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=y


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   81.785075] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   81.816112] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[   81.816172] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   81.849733] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   81.849814] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[   81.849817] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[   81.860949] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[   81.860957] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[   82.266474] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[   82.266480] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[   82.266500] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[   82.266503] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[   82.266742] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[   82.266746] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[   82.266759] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[   82.266762] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[   83.398808] r8169 0000:03:00.0 enp3s0: link up
[   83.398823] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   93.004287] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[   93.004293] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[   93.004311] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[   93.004314] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[   93.004509] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[   93.004513] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[   93.004526] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[   93.004529] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  103.008057] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  103.008065] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  103.008086] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  103.008090] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  103.008334] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  103.008338] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  103.008353] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  103.008356] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  113.004819] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  113.004825] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  113.004843] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  113.004847] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  113.005042] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  113.005046] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  113.005059] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  113.005062] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  123.006254] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  123.006260] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  123.006278] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  123.006281] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  123.006479] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  123.006483] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  123.006498] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  123.006501] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  133.012490] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  133.012496] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  133.012514] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  133.012518] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  133.012711] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  133.012715] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  133.012729] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  133.012732] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  259.828785] r8169 0000:03:00.0 enp3s0: link down
[  333.024971] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  333.056133] r8169 0000:03:00.0 enp3s0: link down
[  333.056215] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  333.058362] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  333.058497] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  333.058503] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  333.058533] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  333.058539] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  333.071830] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  333.071837] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  333.071858] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  333.071861] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  333.072153] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[  333.072158] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[  333.072172] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[  333.072176] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
[  455.670957] r8169 0000:03:00.0 enp3s0: link up
[  455.670978] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 1627.999655] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file '/*(DEBLOBBED)*/'
[ 1627.999664] 0000:02:00.0: Missing Free firmware (non-Free firmware loading is disabled)
[ 1627.999694] rt2800pci 0000:02:00.0: Direct firmware load failed with error -2
[ 1627.999700] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware


########## wireless info END ############



```

I've noticed that the NetworkManager general driver is not the rt2800pci that seems to work fine with this type of problem. I've also found the output of dmesg to be very different from that of the previous thread that I linked. (Probably has to do with Trisquel free software policies, I really hope there is a way around this other than buying an external wireless card or changing distro).

Anyways I'm not expert at all, all help is apreciated!

Thanks.

---

### Post by oldos2er on 2019-03-31
Moved to Ubuntu/Debian BASED.

---

