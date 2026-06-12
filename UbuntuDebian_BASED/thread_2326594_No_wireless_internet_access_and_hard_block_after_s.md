---
title: "No wireless internet access and hard block after suspend/log out, Ubuntu 16.04"
date: 2016-06-02
forum: Ubuntu/Debian BASED
---

### Post by Vaibhav_Bhasin on 2016-06-02
I recently installed Ubuntu(16.04) as well as elementary OS(Freya) on my laptop(Separately at different times). I ran into an issue common to both of them:
I do not get Internet access when I use wireless, but wifi works on all my other devices and on the same laptop in windows(dual boot). Ethernet works fine. And the other problem regarding wireless is if I suspend the session or log out, and log in again after either, wifi does not connect and it shows that wifi is disabled by hardware switch and  it does not switch back on, in settings if I switch it back, it automatically switches to off side. I tried the rfkill and other methods described at other places but none worked for me.

Result of the script mentioned in pinned post:

```

########## wireless info START ##########

Report from: 02 Jun 2016 22:58 IST +0530

Booted last: 02 Jun 2016 22:19 IST +0530

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Freya
Release:    0.3.2
Codename:    freya

##### kernel ############################

Linux 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:00:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:8096]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

wl                   6369280  0 
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              94208  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              708608  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  3 wl,mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23947735 (23.9 MB)  TX bytes:4458053 (4.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5742278 (5.7 MB)  TX bytes:783056 (783.0 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1025     1  0 22:19 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Vaibhav]] (600 root)
[connection] id=Vaibhav | type=802-11-wireless
[802-11-wireless] ssid=Vaibhav | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-39-generic/extra/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[rtl8723be]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     B60F970654516A3D2F6FC24
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath5k.conf]
options ath5k no_hw_rfkill_switch=1

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

[/etc/modprobe.d/custom-wireless.conf]
options ath5k nohwcrypt

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1217.260682] wlan0: direct probe to <MAC address> (try 1/3)
[ 1217.463414] wlan0: direct probe to <MAC address> (try 2/3)
[ 1217.667214] wlan0: direct probe to <MAC address> (try 3/3)
[ 1217.871064] wlan0: authentication with <MAC address> timed out
[ 1229.172896] wlan0: authenticate with <MAC address>
[ 1229.196550] wlan0: direct probe to <MAC address> (try 1/3)
[ 1229.399706] wlan0: direct probe to <MAC address> (try 2/3)
[ 1229.603517] wlan0: direct probe to <MAC address> (try 3/3)
[ 1229.807297] wlan0: authentication with <MAC address> timed out
[ 1244.775925] wlan0: authenticate with <MAC address>
[ 1245.230904] wlan0: direct probe to <MAC address> (try 1/3)
[ 1245.432071] wlan0: direct probe to <MAC address> (try 2/3)
[ 1245.635867] wlan0: direct probe to <MAC address> (try 3/3)
[ 1245.839647] wlan0: authentication with <MAC address> timed out
[ 1255.151620] r8169 0000:09:00.0 eth0: link up
[ 1257.124926] wlan0: authenticate with <MAC address>
[ 1257.149463] wlan0: direct probe to <MAC address> (try 1/3)
[ 1257.352507] wlan0: direct probe to <MAC address> (try 2/3)
[ 1257.556273] wlan0: direct probe to <MAC address> (try 3/3)
[ 1257.760043] wlan0: authentication with <MAC address> timed out
[ 1258.327079] r8169 0000:09:00.0 eth0: link down
[ 1268.439957] rtlwifi: rtlwifi: wireless switch is on
[ 1269.075228] r8169 0000:09:00.0 eth0: link down
[ 1269.075307] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1292.282963] r8169 0000:09:00.0 eth0: link up
[ 1292.282970] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2266.707176] r8169 0000:09:00.0 eth0: link down
[ 2270.558586] r8169 0000:09:00.0 eth0: link up
[ 2271.145090] r8169 0000:09:00.0 eth0: link down
[ 2274.766568] r8169 0000:09:00.0 eth0: link up
[ 2283.212749] r8169 0000:09:00.0 eth0: link down
[ 2286.132237] r8169 0000:09:00.0 eth0: link up

########## wireless info END ############


```

---

### Post by howefield on 2016-06-02
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Vaibhav_Bhasin on 2016-07-03
Bump!

---

### Post by howefield on 2016-07-03
Feel free to give a daily bump rather than waiting a month :)

---

