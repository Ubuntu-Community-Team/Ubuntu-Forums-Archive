---
title: "Intel 7260 poor wifi speeds"
date: 2014-10-27
forum: System76 Support
---

### Post by Des.hymers on 2014-10-27
Hello, 

I am having very poor speeds when I am connected to my router with this wifi card. I typically get around 12 Mb/sec to 84 Mb/sec where other connected computers get on average 300 Mb/sec, with older wifi cards. If I run a speedtest.net from this notebook I get roughly 8 MB/sec download, and on the other PC I get 25MB/sec. 

I have read several forum posts including a few in this subform ([http://ubuntuforums.org/showthread.php?t=2247245](http://ubuntuforums.org/showthread.php?t=2247245)). None of which seems to help, perhaps I'm missing something. I know others who have this same card and have decent speeds.

here is some relevant info 

my router is a linksys AC1600, running both 2.5 ghz and 5.0 ghz. the 5.0 band seems to give me more issues then the 2.5 one.

uname -a

```

Linux des-Gazelle-Professional 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

modinfo iwlwifi | grep 7260

```

firmware:       iwlwifi-7260-7.ucode

```

wireless_script

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


des-Gazelle-Professional 3.13.0-37-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4710MQ CPU @ 2.50GHz
Memory : 15969 MB
Uptime : 10:21:15 up  1:58,  1 user,  load average: 0.35, 0.24, 0.30




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0655]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:"dhymersac"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 dhymersac>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=8 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
====================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
====================o=============o=========o=============o=========o===========o==============o===========
 eth0               | Wired       | r8169   | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 wlan0  [dhymersac] | 802.11 WiFi | iwlwifi | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    DIRECT-roku-587: Infra, <MAC C-04 DIRECT-roku-587>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    SHAW-E8E4C5:     Infra, <MAC C-02 SHAW-E8E4C5>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    dhymers5ac:      Infra, <MAC C-06 dhymers5ac>, Freq 5745 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    glarose1:        Infra, <MAC C-NA glarose1 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    dhymersac-guest: Infra, <MAC C-03 dhymersac-guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54
    *dhymersac:      Infra, <MAC C-01 dhymersac>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2


    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
--------------------+-------------+---------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


dhymersac            : ssid=dhymersac | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search rd.shawcable.net




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.460/2.033/2.607/0.575 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.014/0.016/0.019/0.004 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_CA.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz)
          Channel 128 (5.64 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 dhymersac>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"dhymersac"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006a998e2
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 SHAW-E8E4C5>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"SHAW-E8E4C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cd5f81684f
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 dhymersac-guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"dhymersac-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006a9af61
                    Extra: Last beacon: 24ms ago
          Cell 04 - Address: <MAC C-04 DIRECT-roku-587>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-587"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000663512b146
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006a8c49d
                    Extra: Last beacon: 4360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 dhymers5ac>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"dhymers5ac"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006df5724
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwlmvm]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     D8BB21196A865641A4A81D0
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/rc.local]
mount /home/des/Sites/LocalDev
exit 0


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=8
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/audio] [executable]
#!/bin/sh
# Installed by system76-driver
# Turn off sound card power savings
# Fixes HDMI hotplug when on battery power
echo N > /sys/module/snd_hda_intel/parameters/power_save_controller


[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# Installed by system76-driver
# Fixes poor Intel wireless performance when on battery power
/sbin/iwconfig wlan0 power off




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=0c388ee6-99e5-4ac9-8e90-7f209bc57692 ro i915.disable_power_well=0 quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.504927] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.505138] audit: initializing netlink socket (disabled)
[    0.898148] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.828823] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[    4.181335] wmi: Mapper loaded
[    4.230282] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[    4.445717] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    4.456833] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.456878] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    4.457112] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    4.738766] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.852937] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.702162] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    8.702385] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    8.713495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.713699] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.598796] wlan0: authenticate with <MAC C-01 dhymersac>
[   35.600774] wlan0: send auth to <MAC C-01 dhymersac> (try 1/3)
[   35.602570] wlan0: authenticated
[   35.605697] wlan0: associate with <MAC C-01 dhymersac> (try 1/3)
[   35.609511] wlan0: RX AssocResp from <MAC C-01 dhymersac> (capab=0x1411 status=0 aid=2)
[   35.610480] wlan0: associated
[   35.610506] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.622327] wlan0: deauthenticated from <MAC C-01 dhymersac> (Reason: 15)
[   47.435006] wlan0: authenticate with <MAC C-01 dhymersac>
[   47.436558] wlan0: send auth to <MAC C-01 dhymersac> (try 1/3)
[   47.438344] wlan0: authenticated
[   47.438677] wlan0: associate with <MAC C-01 dhymersac> (try 1/3)
[   47.442482] wlan0: RX AssocResp from <MAC C-01 dhymersac> (capab=0x1411 status=0 aid=2)
[   47.450338] wlan0: associated
[ 7037.274260] wlan0: authenticate with <MAC C-01 dhymersac>
[ 7037.275875] wlan0: send auth to <MAC C-01 dhymersac> (try 1/3)
[ 7037.377750] wlan0: send auth to <MAC C-01 dhymersac> (try 2/3)
[ 7037.481851] wlan0: send auth to <MAC C-01 dhymersac> (try 3/3)
[ 7037.585374] wlan0: authentication with <MAC C-01 dhymersac> timed out
[ 7048.976492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7070.977116] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7070.977336] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7070.989472] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7081.988955] wlan0: authenticate with <MAC C-01 dhymersac>
[ 7081.990030] wlan0: send auth to <MAC C-01 dhymersac> (try 1/3)
[ 7081.991847] wlan0: authenticated
[ 7081.998073] wlan0: associate with <MAC C-01 dhymersac> (try 1/3)
[ 7082.001893] wlan0: RX AssocResp from <MAC C-01 dhymersac> (capab=0x1411 status=0 aid=3)
[ 7082.002821] wlan0: associated
[ 7082.002845] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


    ======== Done ========

```

---

### Post by ajgreeny on 2014-10-27
Have a look at [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm) where you may find updated firmware for your wireless card.

There is a large table at the bottom with links to firmware for each specific card; just make sure you get the correct 7260 card from the four listed.

---

### Post by Des.hymers on 2014-10-28
Hello, and thank you for your response, I have installed the 22.15..8.0 firmware for my nic card, so far it does not seem to change the connection speed. I will monitor this over the next few days and see if it changes at all.

Thanks

---

### Post by jaylittle on 2014-10-31
When you say connection speed, what are you talking about?  Are you actually testing the speed or are you relying upon what the OS tells you what the speed is?  Hint: The later one is generally worthless.  The only way to ascertain what the speed of the wireless network in any OS is to actually transfer data and measure the amount of bandwidth.  The reported wireless speed is never accurate and represents only a theoretical maximum.

---

