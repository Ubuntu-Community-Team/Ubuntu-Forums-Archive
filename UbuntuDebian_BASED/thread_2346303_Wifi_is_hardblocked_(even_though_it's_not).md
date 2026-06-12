---
title: "Wifi is hardblocked (even though it's not)"
date: 2016-12-13
forum: Ubuntu/Debian BASED
---

### Post by jkal on 2016-12-13
My wireless connection appears to be blocked by a hardware switch, even though my hard switch is in the proper position.  I've done all the obvious fixes, rfkill unblock all, reseting bios, hard restart, reload OS, but nothing works.  Here is some random info to get started.

```


########## wireless info START ##########

Report from: 13 Dec 2016 13:10 EST -0500

Booted last: 13 Dec 2016 00:00 EST -0500

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

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Sony Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [104d:9077]
    Kernel driver in use: r8169

09:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 003 Device 002: ID 0bda:0186 Realtek Semiconductor Corp. Card Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:03f5 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 276d:1119  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

ath9k                  94208  0
ath9k_common           32768  1 ath9k
ath9k_hw              446464  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              638976  1 ath9k
cfg80211              573440  4 ath,ath9k_common,ath9k,mac80211
rfkill                 24576  5 cfg80211,sony_laptop,bluetooth

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 130.49.78.6  netmask 255.255.248.0  broadcast 130.49.79.255
        inet6 fe80::1a1e:e282:2c58:216  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 30746  bytes 9328385 (8.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5223  bytes 650405 (635.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 18  bytes 1058 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18  bytes 1058 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         130.49.72.1     0.0.0.0         UG    100    0        0 eth0
130.49.72.0     0.0.0.0         255.255.248.0   U     100    0        0 eth0
136.142.15.13   130.49.72.1     255.255.255.255 UGH   100    0        0 eth0

##### resolv.conf #######################

search resnet.pitt.edu
nameserver 136.142.57.10
nameserver 136.142.188.73
nameserver 136.142.188.76
nameserver 136.142.15.13

##### network managers ##################

Installed:

    NetworkManager

Running:

root       418     1  0 13:02 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Profile 1
GENERAL.CON-UUID:                       90159a1e-f255-4e8f-b4d6-ce3f5ce74808
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5f05cbec-2916-45fb-8ac5-b8b6adacf86c | Wired connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   90159a1e-f255-4e8f-b4d6-ce3f5ce74808 | Profile 1
IP4.ADDRESS[1]:                         130.49.78.6/21
IP4.GATEWAY:                            130.49.72.1
IP4.ROUTE[1]:                           dst = 136.142.15.13/32, nh = 130.49.72.1, mt = 100
IP4.DNS[1]:                             136.142.57.10
IP4.DNS[2]:                             136.142.188.73
IP4.DNS[3]:                             136.142.188.76
IP4.DNS[4]:                             136.142.15.13
IP4.DOMAIN[1]:                          resnet.pitt.edu
IP4.WINS[1]:                            136.142.57.225
IP4.WINS[2]:                            136.142.140.17
IP4.WINS[3]:                            136.142.185.225
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
DHCP4.OPTION[11]:                       expiry = 1481653989
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 130.49.72.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 130.49.78.6
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = resnet.pitt.edu
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 130.49.79.255
DHCP4.OPTION[21]:                       domain_name_servers = 136.142.57.10 136.142.188.73 136.142.188.76 136.142.15.13
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 1800
DHCP4.OPTION[24]:                       netbios_name_servers = 136.142.57.225 136.142.140.17 136.142.185.225
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.248.0
DHCP4.OPTION[27]:                       network_number = 130.49.72.0
DHCP4.OPTION[28]:                       requested_routers = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 136.142.15.13
IP6.ADDRESS[1]:                         fe80::1a1e:e282:2c58:216/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express) (T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.6.0-kali1-amd64
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/0000:09:00.0/net/wlan0
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

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SETUP-PITT-WIFI]] (600 root)
[connection] id=SETUP-PITT-WIFI | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SETUP-PITT-WIFI
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIRELESS-PITTNET]] (600 root)
[connection] id=WIRELESS-PITTNET | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WIRELESS-PITTNET
[802-1x] system-ca-certs=true
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dd-wrt]] (600 root)
[connection] id=dd-wrt | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=dd-wrt
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: US/Eastern (based on set time zone)

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

wlan0     13 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
depends:        ath
intree:         Y
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.6.0-kali1-amd64/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-kali1-amd64 SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0

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

find: ‘/etc/pm/*.d’: No such file or directory

##### udev rules ########################

##### dmesg #############################

[   11.964684] ath: phy0: Enable LNA combining
[   11.967196] ath: phy0: ASPM enabled: 0x42
[   11.967208] ath: EEPROM regdomain: 0x65
[   11.967212] ath: EEPROM indicates we should expect a direct regpair map
[   11.967219] ath: Country alpha2 being used: 00
[   11.967222] ath: Regpair used: 0x65
[   12.256700] radeon 0000:01:05.0: firmware: direct-loading firmware radeon/RS780_pfp.bin
[   12.257666] radeon 0000:01:05.0: firmware: direct-loading firmware radeon/RS780_me.bin
[   12.343364] radeon 0000:01:05.0: firmware: direct-loading firmware radeon/R600_rlc.bin
[   12.375777] radeon 0000:01:05.0: firmware: direct-loading firmware radeon/RS780_uvd.bin
[   24.338688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.344125] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.437262] r8169 0000:02:00.0: firmware: direct-loading firmware rtl_nic/rtl8168e-1.fw
[   24.644450] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   24.644558] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.166340] r8169 0000:02:00.0 eth0: link up
[   26.166368] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############



```
My wireless worked on Windows, so I am confident this is a Linux issue.  Any tips?  I can't view any wifi networks as my airplane mode is on.  
Here is my rfkill.
```

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by jeremy31 on 2016-12-13
Moved to Ubuntu/Debian based

---

### Post by wildmanne39 on 2016-12-13
Boot windows and make sure the wireless is still turned on, I recommend turning it off then back on and let it connect in windows. 

Then boot ubuntu and see if it is on because if it got turned off in windows and you boot ubuntu it will stay off.

You can also make sure it is on in the bios but I believe it is or I do not think the card will show up in the output.
Thanks

---

### Post by jkal on 2016-12-13
> **wildmanne39 said:**
> Boot windows and make sure the wireless is still turned on, I recommend turning it off then back on and let it connect in windows. 

Then boot ubuntu and see if it is on because if it got turned off in windows and you boot ubuntu it will stay off.

You can also make sure it is on in the bios but I believe it is or I do not think the card will show up in the output.
Thanks
When I installed Linux I had it replace Windows.  So I don't have windows anymore.  And there is no wireless setting in my BIOS.  I've also reset my BIOS multiple times.

---

### Post by wildmanne39 on 2016-12-13
Are you sure it was turned on at the time you started to remove windows?

The wifi button on the computer will not turn it on? sometimes there is also a function key combination that turns it on, like f5 have you checked your documentation?

Go to the top right corner of the screen and click on network manager icon, is networking and wireless network enabled? or are they grayed out?

---

### Post by jkal on 2016-12-13
> **wildmanne39 said:**
> Are you sure it was turned on at the time you started to remove windows?

The wifi button on the computer will not turn it on? sometimes there is also a function key combination that turns it on, like f5 have you checked your documentation?

Go to the top right corner of the screen and click on network manager icon, is networking and wireless network enabled? or are they grayed out?
I believe it was ON when I replaced windows.  I don't see a button combo that toggles wifi but there is a hard switch at the bottom of the laptop.  This switch does nothing to enable/disable airplane mode.  It won't let me switch the wifi on and airplane mode off in network manager.

---

### Post by wildmanne39 on 2016-12-13
Let's try:
```
sudo modprobe -rv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
```
Does it come on?

---

### Post by jkal on 2016-12-13
> **wildmanne39 said:**
> Let's try:
```
sudo modprobe -rv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
```
Does it come on?
Nothing, even after a reboot.

---

### Post by wildmanne39 on 2016-12-13
That is what I was afraid of, you can try to put the network to come on before boot possibly in the bios other then that I would look at your documentation to see if there is another way to turn wifi on.

You should run the live version of the OS and see if wifi works from it.

You might update your bios, you would have to start a new thread on how to do that if you need help.

I have seen people that have reinstalled windows to turn the wifi on, I am not recommending that but it is an option as a last resort.
I have no further suggestions.

---

### Post by jkal on 2016-12-13
> **wildmanne39 said:**
> That is what I was afraid of, you can try to put the network to come on before boot possibly in the bios other then that I would look at your documentation to see if there is another way to turn wifi on.

You should run the live version of the OS and see if wifi works from it.

You might update your bios, you would have to start a new thread on how to do that if you need help.

I have seen people that have reinstalled windows to turn the wifi on, I am not recommending that but it is an option as a last resort.
I have no further suggestions. My Sony Vaio model number is VPCEE31FX if that helps?

---

### Post by wildmanne39 on 2016-12-13
I am sorry I looked through all the manuals for that model and none of them showed how to enable wireless it just said it needed to be turned on.

It is also possible that you removed windows while it was in hibernation mode and that would turn the wifi off, I recommend trying the live version of kali if they have one and see if it works.

If not I recommend installing windows and if it works I would do a dual boot.

---

### Post by jkal on 2016-12-13
> **wildmanne39 said:**
> I am sorry I looked through all the manuals for that model and none of them showed how to enable wireless it just said it needed to be turned on.

It is also possible that you removed windows while it was in hibernation mode and that would turn the wifi off, I recommend trying the live version of kali if they have one and see if it works.

If not I recommend installing windows and if it works I would do a dual boot.
I no longer have a copy of windows now that I removed it to install linux.  I first installed Ubuntu and had wifi issues and then installed kali and the wifi issues remained.  Anything else I should try?

If this helps, I had it fixed the other day, but it just recently un fixed itself.  This is my reddit post that logs the steps I've taken already.
[https://www.reddit.com/r/Kalilinux/comments/5htl6l/says_my_wifi_is_hard_blocked_even_though_its_not/](https://www.reddit.com/r/Kalilinux/comments/5htl6l/says_my_wifi_is_hard_blocked_even_though_its_not/)

---

### Post by jeremy31 on 2016-12-13
Do the results of ```
rfkill list all
```
Change with the position of the switch?

If nothing else there is a video on youtube about using a piece of electrical tape to cover a pin on the wifi card that will usually allow the wifi to be used

Here it is [https://www.youtube.com/watch?v=yzAKcmlaH1M&t=6s](https://www.youtube.com/watch?v=yzAKcmlaH1M&t=6s)

---

### Post by wildmanne39 on 2016-12-13
No, I am sorry I have no further suggestions, I have no idea how what you have been trying to do with Kali has played into your issue but from looking at that link it is nothing I or anyone here can help with, we do not support hacking of any kind so I recommend using the Kali forum.
Thread Closed!

---

