---
title: "Problem with wifi 17.10, RTL8188ee, the wifi is unstable"
date: 2017-09-24
forum: Ubuntu Development Version
---

### Post by fikretkrk on 2017-09-24
Hello,

I'm new on ubuntu 17.10, my wifi doesn't work at the beginning and i install the driver, and it works.

But my wifi is very unstable, it get to 2mb/s instead of 50mb/s.

I don't know where is the problem.

Please help me

---

### Post by jeremy31 on 2017-09-24
*Thread moved to **Ubuntu Development Version**.*
See the wireless script link in my signature and post results

---

### Post by fikretkrk on 2017-09-24
```
########## wireless info START ##########

Report from: 24 Sep 2017 12:16 CEST +0200

Booted last: 24 Sep 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu Artful Aardvark (development branch)
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.14.0-041400rc1-lowlatency #201709162031 SMP PREEMPT Sun Sep 17 00:39:17 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Unity

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2212]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company RTL8188EE mini-PCIe card [103c:197d]
    Kernel driver in use: rtl8188ee

##### lsusb #############################

Bus 001 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8188ee              90112  0
rtl_pci                28672  1 rtl8188ee
rtlwifi                77824  2 rtl_pci,rtl8188ee
mac80211              790528  3 rtl_pci,rtl8188ee,rtlwifi
cfg80211              622592  2 mac80211,rtlwifi
wmi_bmof               16384  0
hp_wmi                 16384  0
sparse_keymap          16384  2 intel_hid,hp_wmi
mxm_wmi                16384  1 nouveau
wmi                    24576  4 wmi_bmof,mxm_wmi,nouveau,hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp8s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5235  bytes 443342 (443.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5235  bytes 443342 (443.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.10  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::5d62:30de:82dd:bea1  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 13940  bytes 11776232 (11.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 12854  bytes 1955790 (1.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp8s0    no wireless extensions.

wlo1      IEEE 802.11  ESSID:"karatas"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'karatas' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1968   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.0.53
search numericable.fr

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       816     1  0 12:02 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter (RTL8188EE mini-PCIe card)
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 4.14.0-041400rc1-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:0a:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     karatas 1
GENERAL.CON-UUID:                       ccaa2181-f4e6-49e6-9b62-9563c2527131
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ccaa2181-f4e6-49e6-9b62-9563c2527131 | karatas 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   (null) | (null)
IP4.ADDRESS[1]:                         192.168.0.10/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             89.2.0.1
IP4.DNS[2]:                             89.2.0.2
IP4.DOMAIN[1]:                          numericable.fr
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 89.2.0.1 89.2.0.2
DHCP4.OPTION[5]:                        ip_address = 192.168.0.10
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = numericable.fr
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1506333819
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::5d62:30de:82dd:bea1/64
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
karatas  <MAC 'karatas' [AC1]>  Infra  3     2422 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  yes     * 

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/karatas]] (600 root)
[connection] id=karatas | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=karatas
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-F2EC]] (600 root)
[connection] id=Livebox-F2EC | type=wifi | permissions=user:kurklu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-F2EC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/karatas 1]] (600 root)
[connection] id=karatas 1 | type=wifi | permissions=user:kurklu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=karatas
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp8s0    no frequency information.

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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp8s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'karatas' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"karatas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ce1c271b
                    Extra: Last beacon: 169ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/4.14.0-041400rc1-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     6A0016FD02CE062B9E3C91F
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
name:           rtl8188ee
vermagic:       4.14.0-041400rc1-lowlatency SMP preempt mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.14.0-041400rc1-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1484974AD686EE4962BD44A
depends:        mac80211,rtlwifi
intree:         Y
name:           rtl_pci
vermagic:       4.14.0-041400rc1-lowlatency SMP preempt mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtlwifi]
filename:       /lib/modules/4.14.0-041400rc1-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9E3BB6F4B7CBAE8AAAC1DF7
depends:        mac80211,cfg80211
intree:         Y
name:           rtlwifi
vermagic:       4.14.0-041400rc1-lowlatency SMP preempt mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.14.0-041400rc1-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0BE67DF8364C9A437B278FB
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.14.0-041400rc1-lowlatency SMP preempt mod_unload 
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
filename:       /lib/modules/4.14.0-041400rc1-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     879F316B9C7D996585EF269
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.14.0-041400rc1-lowlatency SMP preempt mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: N
ips: Y
msi: Y
swenc: N
swlps: N

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee fwlps=0

[/etc/modprobe.d/rtl8192ce.conf]
options rtl8192ce swenc=1 ips=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.606505] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   13.606525] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   13.750395] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.750663] rtlwifi: rtlwifi: wireless switch is on
[   14.697153] rtl8188ee 0000:0a:00.0 wlo1: renamed from wlan0
[   29.659206] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 3 times)
[   63.405607] wlo1: authenticate with <MAC 'karatas' [AC1]>
[   63.425325] wlo1: send auth to <MAC 'karatas' [AC1]> (try 1/3)
[   63.426814] wlo1: authenticated
[   63.427039] wlo1: associate with <MAC 'karatas' [AC1]> (try 1/3)
[   63.433133] wlo1: RX AssocResp from <MAC 'karatas' [AC1]> (capab=0x1411 status=0 aid=2)
[   63.433422] wlo1: associated
[   63.433432] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2017-09-24
Your wifi router is using mixed mode encryption, see if it can be changed to WPA2 only without TKIP

---

### Post by fikretkrk on 2017-09-24
It change nothing

---

### Post by rrnbtter on 2017-09-24
Greetings,
Try this.

sudo apt-get install linux-headers-generic build-essential git 
git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install


Just in case the system doesn’t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
sudo modprobe rtl8821ae (change this to your rtl wifi card.)
and reboot your system.

If your Kernel version changes
cd rtlwifi_new
sudo make install
sudo modprobe (your rtl wifi)
reboot

---

### Post by fikretkrk on 2017-09-24
I already do this, my wifi work, but it's unstable.

---

