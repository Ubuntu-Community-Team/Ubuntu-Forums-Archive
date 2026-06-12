---
title: "Galago Pro: intermittent wifi performance"
date: 2014-10-06
forum: System76 Support
---

### Post by sfinnie on 2014-10-06
I have a Galago Pro which, generally, I'm very happy with.  The only real issue is the wifi.

Typically it'll work fine when I start up.  It operates correctly for a while and then stops.  The symptoms are most obvious in firefox when the page stalls loading, usually with the status bar saying "Looking up <domain name>".

I've had a look through the forum and there are several other posts on similar topics, e.g. [here]("http://ubuntuforums.org/showthread.php?t=2169678") and [here]("http://ubuntuforums.org/showthread.php?t=2194000&highlight=wifi+intel+galago+7260").  The latter in particular seems very similar behaviour (I also have the intel 7260 option).  The solution suggests upgrading the firmware; however when I look in /lib/fimrware it shows:

```
sf@Friday:~$ ls -la /lib/firmware/iwlwifi-7260*
-rw-r--r-- 1 root root 683236 Apr 28 18:15 /lib/firmware/iwlwifi-7260-7.ucode
-rw-r--r-- 1 root root 679780 Jul 17 15:41 /lib/firmware/iwlwifi-7260-8.ucode
-rw-r--r-- 1 root root 679380 Jun 25 16:28 /lib/firmware/iwlwifi-7260-9.ucode
```

which, from looking on the intel site, appears to include the latest versions.

Any suggestions greatfully accepted.  We have several other devices using the home wifi network: android phone, ipad, macbook among others.  None of them exhibit the symptoms above so I'm reasonably confident the problem isn't with the network itself.

Thanks.

---

### Post by varunendra on 2014-10-07
Welcome to the forums sfinnie!

Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by sfinnie on 2014-10-07
Hi Varun, appreciate the reply.  Output from script as follows, any suggestions welcome.

Thanks.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Friday 3.13.0-36-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4750HQ CPU @ 2.00GHz
Memory : 15972 MB
Uptime : 12:54:22 up 3 days, 12:39,  3 users,  load average: 0.36, 0.32, 0.30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:7410]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 5986:0536 Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"HKP2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 HKP2>   
          Bit Rate=144.4 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
1: phy0: Wireless LAN      no            no
9: hci0: Bluetooth         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [HKP2]  | 802.11 WiFi | iwlwifi | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    SKY211DD:        Infra, <MAC C-02 SKY211DD>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    HONGKONGPHOOEY:  Infra, <MAC C-04 HONGKONGPHOOEY>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA
    BTWifi-X:        Infra, <MAC C-NA BTWifi-X 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    HKP2:            Infra, <MAC C-05 HKP2>, Freq 5180 MHz, Rate 54 Mb/s, Strength 90 WPA2
    *HKP2:           Infra, <MAC C-01 HKP2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA2
    TALKTALK-4DCB64: Infra, <MAC C-NA TALKTALK-4DCB64 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    NETGEAR:         Infra, <MAC C-NA NETGEAR 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    BTWifi-with-FON: Infra, <MAC C-NA BTWifi-with-FON 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15

    Address:         192.168.0.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             195.74.102.146
    DNS:             195.74.102.147
----------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0           | Wired       | e1000e  | unavailable | no      | 1000 Mb/s |              | <MAC eth0>
----------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

HKP2                 : ssid=HKP2 | permissions=user:scoot:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HONGKONGPHOOEY       : ssid=HONGKONGPHOOEY | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Test Wi-Fi Labs      : ssid=Test Wi-Fi Labs | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.448/4.638/4.828/0.190 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.023/0.025/0.027/0.002 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


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

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 HKP2>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"HKP2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006af581c2429
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 SKY211DD>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"SKY211DD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d6e4c1f98c
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 BTHub4-9JTN>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-9JTN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ea712b8207
                    Extra: Last beacon: 3724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 HONGKONGPHOOEY>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"HONGKONGPHOOEY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004819adf124
                    Extra: Last beacon: 16ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 HKP2>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"HKP2"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006af55483542
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     D8BB21196A865641A4A81D0
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=ac4faa57-5594-420f-ae74-a538607218ba ro i915.disable_power_well=0 quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.758207] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.758475] audit: initializing netlink socket (disabled)
[    2.304995] wmi: Mapper loaded
[    5.818703] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[    5.822745] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    5.854891] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.854942] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    5.855165] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    5.936873] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.062094] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.548971] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    6.549196] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    6.561366] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.561752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.793975] wlan0: authenticate with <MAC C-01 HKP2>
[   48.796250] wlan0: send auth to <MAC C-01 HKP2> (try 1/3)
[   48.798203] wlan0: authenticated
[   48.799108] wlan0: associate with <MAC C-01 HKP2> (try 1/3)
[   48.806264] wlan0: RX AssocResp from <MAC C-01 HKP2> (capab=0x1431 status=0 aid=4)
[   48.807310] wlan0: associated
[   48.807340] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  265.017923] wlan0: deauthenticating from <MAC C-01 HKP2> by local choice (reason=3)
[  269.542918] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  269.543136] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  269.554621] iwlwifi 0000:03:00.0: no hotplug settings from platform
[  269.567940] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[  269.694448] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[  273.321628] wlan0: authenticate with <MAC C-05 HKP2>
[  273.323775] wlan0: send auth to <MAC C-05 HKP2> (try 1/3)
[  273.324296] wlan0: authenticated
[  273.327886] wlan0: associate with <MAC C-05 HKP2> (try 1/3)
[  273.332786] wlan0: RX AssocResp from <MAC C-05 HKP2> (capab=0x1511 status=0 aid=2)
[  273.333886] wlan0: associated
[  273.339012] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC C-05 HKP2>
[ 3150.747058] wlan0: deauthenticating from <MAC C-05 HKP2> by local choice (reason=3)
[ 3155.175929] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3155.176147] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3155.189418] iwlwifi 0000:03:00.0: no hotplug settings from platform
[ 3155.202069] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 3155.332045] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 3158.956259] wlan0: authenticate with <MAC C-01 HKP2>
[ 3158.957829] wlan0: send auth to <MAC C-01 HKP2> (try 1/3)
[ 3158.960481] wlan0: authenticated
[ 3158.961825] wlan0: associate with <MAC C-01 HKP2> (try 1/3)
[ 3158.969891] wlan0: RX AssocResp from <MAC C-01 HKP2> (capab=0x1431 status=0 aid=1)
[ 3158.970953] wlan0: associated
[ 4368.854909] wlan0: deauthenticating from <MAC C-01 HKP2> by local choice (reason=3)
[ 4372.545152] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4372.545369] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4372.556746] iwlwifi 0000:03:00.0: no hotplug settings from platform
[ 4372.568824] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 4372.711740] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 4376.322631] wlan0: authenticate with <MAC C-05 HKP2>
[ 4376.324379] wlan0: send auth to <MAC C-05 HKP2> (try 1/3)
[ 4376.324841] wlan0: authenticated
[ 4376.325480] wlan0: associate with <MAC C-05 HKP2> (try 1/3)
[ 4376.328295] wlan0: RX AssocResp from <MAC C-05 HKP2> (capab=0x1511 status=0 aid=3)
[ 4376.329184] wlan0: associated
[ 4376.338931] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC C-05 HKP2>
[ 5988.436812] wlan0: deauthenticating from <MAC C-05 HKP2> by local choice (reason=3)
[ 6715.585495] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6715.585713] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6715.597154] iwlwifi 0000:03:00.0: no hotplug settings from platform
[ 6715.610065] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 6715.758043] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[34938.949170] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[34938.949388] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[34938.960820] iwlwifi 0000:03:00.0: no hotplug settings from platform
[34938.973632] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[34939.089535] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[34961.472966] wlan0: authenticate with <MAC C-04 HONGKONGPHOOEY>
[34961.474877] wlan0: send auth to <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[34961.476463] wlan0: authenticated
[34961.476898] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[34961.476910] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[34961.476917] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[34961.478404] wlan0: associate with <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[34961.498031] wlan0: RX AssocResp from <MAC C-04 HONGKONGPHOOEY> (capab=0x471 status=0 aid=1)
[34961.498692] wlan0: associated
[36766.327448] wlan0: deauthenticating from <MAC C-04 HONGKONGPHOOEY> by local choice (reason=3)
[36770.092610] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[36770.092828] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[36770.104318] iwlwifi 0000:03:00.0: no hotplug settings from platform
[36770.117051] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[36770.265043] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[36773.870759] wlan0: authenticate with <MAC C-04 HONGKONGPHOOEY>
[36773.872593] wlan0: send auth to <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[36773.874149] wlan0: authenticated
[36773.874447] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[36773.874456] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[36773.874460] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[36773.874680] wlan0: associate with <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[36773.893381] wlan0: RX AssocResp from <MAC C-04 HONGKONGPHOOEY> (capab=0x471 status=0 aid=1)
[36773.899950] wlan0: associated
[37753.247636] wlan0: deauthenticating from <MAC C-04 HONGKONGPHOOEY> by local choice (reason=3)
[37761.363682] wlan0: authenticate with <MAC C-04 HONGKONGPHOOEY>
[37761.364827] wlan0: send auth to <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[37761.370243] wlan0: authenticated
[37761.370425] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[37761.370432] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[37761.370437] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[37761.373285] wlan0: associate with <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[37761.390854] wlan0: RX AssocResp from <MAC C-04 HONGKONGPHOOEY> (capab=0x471 status=0 aid=1)
[37761.391492] wlan0: associated
[39392.007800] wlan0: deauthenticating from <MAC C-04 HONGKONGPHOOEY> by local choice (reason=3)
[39395.877996] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[39395.878213] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[39395.889586] iwlwifi 0000:03:00.0: no hotplug settings from platform
[39395.902261] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[39396.050189] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[39399.656335] wlan0: authenticate with <MAC C-04 HONGKONGPHOOEY>
[39399.658007] wlan0: send auth to <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[39399.659632] wlan0: authenticated
[39399.659884] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[39399.659896] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[39399.659903] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[39399.661903] wlan0: associate with <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[39399.765874] wlan0: associate with <MAC C-04 HONGKONGPHOOEY> (try 2/3)
[39399.816296] wlan0: RX AssocResp from <MAC C-04 HONGKONGPHOOEY> (capab=0x471 status=0 aid=1)
[39399.816851] wlan0: associated
[42907.706831] wlan0: deauthenticating from <MAC C-04 HONGKONGPHOOEY> by local choice (reason=3)
[42911.938851] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[42911.939078] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[42911.951567] iwlwifi 0000:03:00.0: no hotplug settings from platform
[42911.971936] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[42912.113926] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[42915.718015] wlan0: authenticate with <MAC C-04 HONGKONGPHOOEY>
[42915.719713] wlan0: send auth to <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[42915.723963] wlan0: authenticated
[42915.724242] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[42915.724254] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[42915.724262] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[42915.725646] wlan0: associate with <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[42915.747561] wlan0: RX AssocResp from <MAC C-04 HONGKONGPHOOEY> (capab=0x471 status=0 aid=1)
[42915.748203] wlan0: associated
[42937.944345] wlan0: deauthenticating from <MAC C-04 HONGKONGPHOOEY> by local choice (reason=3)
[42941.729662] wlan0: authenticate with <MAC C-05 HKP2>
[42941.731408] wlan0: send auth to <MAC C-05 HKP2> (try 1/3)
[42941.731868] wlan0: authenticated
[42941.732169] wlan0: associate with <MAC C-05 HKP2> (try 1/3)
[42941.734987] wlan0: RX AssocResp from <MAC C-05 HKP2> (capab=0x1511 status=0 aid=5)
[42941.735885] wlan0: associated
[42941.745244] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC C-05 HKP2>
[42968.186032] wlan0: authenticate with <MAC C-01 HKP2>
[42968.187703] wlan0: send auth to <MAC C-01 HKP2> (try 1/3)
[42968.189496] wlan0: authenticated
[42968.190622] wlan0: associate with <MAC C-01 HKP2> (try 1/3)
[42968.197833] wlan0: RX AssocResp from <MAC C-01 HKP2> (capab=0x1431 status=0 aid=1)
[42968.198857] wlan0: associated

    ======== Done ========


```

---

### Post by varunendra on 2014-10-07
> **sfinnie said:**
> ```

dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[   48.799108] wlan0: associate with <MAC **[COLOR="#0000FF"]C-01 HKP2[/COLOR]**> (try 1/3)
[   48.806264] wlan0: RX AssocResp from <MAC C-01 HKP2> (capab=0x1431 status=0 aid=4)
[   48.807310] wlan0: **associated**
[   48.807340] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  265.017923] wlan0: **deauthenticating from <MAC [COLOR="#0000FF"]C-01 HKP2[/COLOR]>** by local choice (reason=3)
....
[  273.321628] wlan0: **authenticate with <MAC [COLOR="#FF0000"]C-05 HKP2[/COLOR]>**
....
[  273.333886] wlan0: associated
[  273.339012] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC C-05 HKP2>
[ 3150.747058] wlan0: **deauthenticating from <MAC [COLOR="#FF0000"]C-05 HKP2[/COLOR]>** by local choice (reason=3)
....
[ 3158.956259] wlan0: **authenticate with <MAC [COLOR="#0000FF"]C-01 HKP2[/COLOR]>**
....
[ 3158.970953] wlan0: **associated**
[ 4368.854909] wlan0: **deauthenticating from <MAC [COLOR="#0000FF"]C-01 HKP2[/COLOR]>** by local choice (reason=3)
....
[ 4376.322631] wlan0: **authenticate with <MAC [COLOR="#FF0000"]C-05 HKP2[/COLOR]>**
....
[ 4376.329184] wlan0: **associated**
[ 4376.338931] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC C-05 HKP2>
[ 5988.436812] wlan0: **deauthenticating from <MAC [COLOR="#FF0000"]C-05 HKP2[/COLOR]>** by local choice (reason=3)
....
....
[34961.472966] wlan0: **authenticate with <MAC C-04 HONGKONGPHOOEY>**
....
[34961.498692] wlan0: **associated**
[36766.327448] wlan0: **deauthenticating from <MAC C-04 HONGKONGPHOOEY>** by local choice (reason=3)
....
[36773.870759] wlan0: **authenticate with <MAC C-04 HONGKONGPHOOEY>**
[36773.872593] wlan0: send auth to <MAC C-04 HONGKONGPHOOEY> (try 1/3)
[36773.874149] wlan0: authenticated
[36773.874447] iwlwifi 0000:03:00.0 wlan0: [COLOR="#FF0000"]disabling HT/VHT due to WEP/TKIP use[/COLOR]
[36773.874456] iwlwifi 0000:03:00.0 wlan0: [COLOR="#FF0000"]disabling HT as WMM/QoS is not supported by the AP[/COLOR]
[36773.874460] iwlwifi 0000:03:00.0 wlan0: [COLOR="#FF0000"]disabling VHT as WMM/QoS is not supported by the AP[/COLOR]
....
[36773.899950] wlan0: **associated**
[37753.247636] wlan0: **deauthenticating from <MAC C-04 HONGKONGPHOOEY>** by local choice (reason=3)
[37761.363682] wlan0: **authenticate with <MAC C-04 HONGKONGPHOOEY>**
*....<repeated many times>....*
[42937.944345] wlan0: **deauthenticating from <MAC C-04 HONGKONGPHOOEY>** by local choice (reason=3)
[42941.729662] wlan0: **authenticate with <MAC [COLOR="#FF0000"]C-05 HKP2[/COLOR]>**
....
[42941.735885] wlan0: **associated**
[42941.745244] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC C-05 HKP2>
[42968.186032] wlan0: **authenticate with <MAC [COLOR="#0000FF"]C-01 HKP2[/COLOR]>**
....
[42968.198857] wlan0: **associated**

```

As highlighted above, there seems to be a lot of 'hopping' activity, some might be manually initiated by you, but most of them seem to be automatically happening.

I can guess two reasons for the authenticate/deauthenticate actions, both happening in two different cases -

- When NM is switching between the two APs of the same SSID "HKP2", it could be NM's (Network Manager's) decision (or confusion) to switch to the one with better signal.
- When it repeats the authenticate/deauthenticate cycle with the third AP - "HONGKONGPHOOEY", it seems to be happening due to the inefficient encryption algorithm (TKIP) that it is using.

If the AP "HONGKONGPHOOEY" is under your control, please change its encryption type to WPA2-PSK with AES (CCMP) if it supports that.

For the 'hopping' problem with the former two AP's, you may need to bind NM with any one of them, so that it connects to only that one and doesn't even try any other APs of the same SSID. This can be done by saving the MAC address (found in the output of "sudo iwlist scan") of the preferred AP into the "BSSID" field of the Network Manager.

However, there is another tweak almost necessary with 'iwlwifi' driver these days, please try it first and see if it solves all the problems automatically. If it does, no need for above tweaks, although the encryption change suggested above should make that connection better. Here is what is needed with "iwlwifi" -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

Please try this, test the connection and make the other changes as well if required. Let us know the outcome and we may try at least one more thing if these don't solve the issue properly, or not at all.

---

### Post by sfinnie on 2014-10-07
Hi Varun, thanks for the quick & full response.  I've made the change you suggested.  All good so far, I'll see how it goes this evening.

Kind Regards.

---

### Post by varunendra on 2014-10-07
If it keeps working, it would be a favour to other users if you could mark the thread as [SOLVED] (using "Thread Tools" link above the top post) and drop System76 an email letting them know of this parameter requirement.

It may be fixed in the updates later, but right now, it seems everyone using "iwlwifi" needs this custom parameter.

---

### Post by sfinnie on 2014-10-08
Hi  Varun.  I'll monitor usage over a few days; if the situation remains improved then I'll mark the thread as solved.

Thanks again for your help.

---

### Post by varunendra on 2014-10-08
No problem. :)

---

### Post by sfinnie on 2014-10-19
Over a week's worth of good behaviour with a number of WAPs so am marking as solved.  Thanks again Varun.

---

