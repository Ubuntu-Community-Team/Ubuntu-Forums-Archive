---
title: "Can't connect to WPA2 networks on Atheros AR9285 (ath9k driver) on Ubuntu 16.04"
date: 2016-12-17
forum: Ubuntu/Debian BASED
---

### Post by mnavarrocarter on 2016-12-17
Hey Guys!

I would really appreciate some help on this issue. My Wifi works pretty well, but the thing is I can't connect to any WPA2 network (that's how far I've gone in my troubleshooting). I'm posting the output of the wireless script troubleshooter you guys have. Also, relevant info to be mentioned: I'm running Elementary OS, which is based on Ubuntu 16.04. Only major changes I've made on the system is that I disabled dnsmasq (It was messing with my connection a lot) and that I updated my kernel version to the 4.6.3-040603-generic x86_64. That's it pretty much. I hope you can give me a hand with this!

wireless-info.txt output:
```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


SAMRV410-EOS 4.6.3-040603-generic x86_64,  elementary OS 0.4 Loki, loki


CPU    : Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
Memory : 3883 MB
Uptime : 17:20:05 up 40 min,  1 user,  load average: 0,07, 0,24, 0,27




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
    Subsystem: Samsung Electronics Co Ltd 88E8040 PCI-E Fast Ethernet Controller [144d:c571]
    Kernel driver in use: sky2
    Kernel modules: sky2
06:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Askey Computer Corp. AR9285 Wireless Network Adapter (PCI-Express) [144f:7173]
    Kernel driver in use: ath9k
    Kernel modules: ath9k, wl




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2232:1006 Silicon Motion 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlp6s0    IEEE 802.11bgn  ESSID:"EO-Estudiantes"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 EO-Estudiantes>   
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:193   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                Soft blocked  Hard blocked
0: phy0: Wireless LAN              no            no
1: samsung-wlan: Wireless LAN      no            no
2: hci0: Bluetooth                 no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


wl                   6365184  0
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              745472  1 ath9k
cfg80211              581632  5 wl,ath,ath9k_common,ath9k,mac80211




module parameters ~~~~~~~~~~~~~~~~~~


ath9k         (7): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | led_active_high=-1 | nohwcrypt=0 | ps_enable=0 | use_chanctx=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (6): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | minstrel_vht_only=Y | probe_wait_ms=500




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 190.160.0.15
nameserver 200.30.192.14
nameserver 200.83.1.5




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp6s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp6s0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 9.422/10.242/11.062/0.820 ms


--- 190.160.0.15 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms




--- 200.30.192.14 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms




--- 200.83.1.5 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms






iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : es_CL.UTF-8)
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlp6s0    13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.462 GHz (Channel 11)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlp6s0    Scan completed :
          Cell 01 - Address: <MAC C-01 EO-Estudiantes>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"EO-Estudiantes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a4b0af986
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Monamu>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Monamu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012def88415e
                    Extra: Last beacon: 1796ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 ARRIS-3642>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ARRIS-3642"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000068b2af336f
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 DIRECT-cAM2020 Series>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-cAM2020 Series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000059f5fb0d1
                    Extra: Last beacon: 192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[wl]
filename:       /lib/modules/4.6.3-040603-generic/extra/wl.ko
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[ath9k]
filename:       /lib/modules/4.6.3-040603-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     776E843D7E0E114337A1640
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.6.3-040603-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     D54A06ADEF2CA13387377B0
depends:        ath9k_hw,cfg80211,ath


[ath9k_hw]
filename:       /lib/modules/4.6.3-040603-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     D4BA98E5EFCDE1DED2E5A56
depends:        ath


[ath]
filename:       /lib/modules/4.6.3-040603-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211


[mac80211]
filename:       /lib/modules/4.6.3-040603-generic/kernel/net/mac80211/mac80211.ko
srcversion:     0F85316D3D74DC638291862
depends:        cfg80211
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.6.3-040603-generic/kernel/net/wireless/cfg80211.ko
srcversion:     64D16DD2A026E169A36027A
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-4.6.3-040603-generic root=UUID=5c9047cf-43ea-448d-8f69-f66ae30e29aa ro quiet splash acpi_backlight=vendor vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.901676] audit: initializing netlink subsys (disabled)
[    1.012952] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.959960] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040215)
[    4.302103] ath: phy0: ASPM enabled: 0x42
[    4.302108] ath: EEPROM regdomain: 0x65
[    4.302110] ath: EEPROM indicates we should expect a direct regpair map
[    4.302113] ath: Country alpha2 being used: 00
[    4.302114] ath: Regpair used: 0x65
[    4.428036] wl: module license 'MIXED/Proprietary' taints kernel.
[    4.461381] wl: module verification failed: signature and/or required key missing - tainting kernel
[    4.549377] ath9k 0000:06:00.0 wlp6s0: renamed from wlan0
[    5.255396] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[    5.270249] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[    5.364785] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[    5.865837] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.260800] wlp6s0: authenticate with <MAC C-01 EO-Estudiantes>
[    6.275117] wlp6s0: send auth to <MAC C-01 EO-Estudiantes> (try 1/3)
[    6.277000] wlp6s0: authenticated
[    6.277249] ath9k 0000:06:00.0 wlp6s0: disabling HT/VHT due to WEP/TKIP use
[    6.284039] wlp6s0: associate with <MAC C-01 EO-Estudiantes> (try 1/3)
[    6.288170] wlp6s0: RX AssocResp from <MAC C-01 EO-Estudiantes> (capab=0x431 status=0 aid=1)
[    6.288266] wlp6s0: associated
[    6.288300] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[   84.829506] wlp6s0: deauthenticating from <MAC C-01 EO-Estudiantes> by local choice (Reason: 3=DEAUTH_LEAVING)
[   84.891462] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[   85.736857] wlp6s0: authenticate with <MAC C-01 EO-Estudiantes>
[   85.754649] wlp6s0: send auth to <MAC C-01 EO-Estudiantes> (try 1/3)
[   85.762335] wlp6s0: authenticated
[   85.762530] ath9k 0000:06:00.0 wlp6s0: disabling HT/VHT due to WEP/TKIP use
[   85.764047] wlp6s0: associate with <MAC C-01 EO-Estudiantes> (try 1/3)
[   85.769671] wlp6s0: RX AssocResp from <MAC C-01 EO-Estudiantes> (capab=0x431 status=0 aid=1)
[   85.769790] wlp6s0: associated
[   85.769850] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[   89.185584] wlp6s0: deauthenticating from <MAC C-01 EO-Estudiantes> by local choice (Reason: 3=DEAUTH_LEAVING)
[   89.309870] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[   90.061897] wlp6s0: authenticate with <MAC C-01 EO-Estudiantes>
[   90.081492] wlp6s0: send auth to <MAC C-01 EO-Estudiantes> (try 1/3)
[   90.086874] wlp6s0: authenticated
[   90.087085] ath9k 0000:06:00.0 wlp6s0: disabling HT/VHT due to WEP/TKIP use
[   90.088096] wlp6s0: associate with <MAC C-01 EO-Estudiantes> (try 1/3)
[   90.095029] wlp6s0: RX AssocResp from <MAC C-01 EO-Estudiantes> (capab=0x431 status=0 aid=1)
[   90.095147] wlp6s0: associated
[   90.095198] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[   94.220203] wlp6s0: deauthenticating from <MAC C-01 EO-Estudiantes> by local choice (Reason: 3=DEAUTH_LEAVING)
[   94.339079] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[   94.868713] wlp6s0: authenticate with <MAC C-01 EO-Estudiantes>
[   94.889581] wlp6s0: send auth to <MAC C-01 EO-Estudiantes> (try 1/3)
[   94.898345] wlp6s0: authenticated
[   94.898556] ath9k 0000:06:00.0 wlp6s0: disabling HT/VHT due to WEP/TKIP use
[   94.900047] wlp6s0: associate with <MAC C-01 EO-Estudiantes> (try 1/3)
[   94.903325] wlp6s0: RX AssocResp from <MAC C-01 EO-Estudiantes> (capab=0x431 status=0 aid=1)
[   94.903438] wlp6s0: associated
[   94.903487] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[ 1517.637818] wlp6s0: deauthenticating from <MAC C-01 EO-Estudiantes> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1517.729874] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[ 1518.540834] wlp6s0: authenticate with <MAC C-01 EO-Estudiantes>
[ 1518.558433] wlp6s0: send auth to <MAC C-01 EO-Estudiantes> (try 1/3)
[ 1518.560381] wlp6s0: authenticated
[ 1518.560505] ath9k 0000:06:00.0 wlp6s0: disabling HT/VHT due to WEP/TKIP use
[ 1518.564040] wlp6s0: associate with <MAC C-01 EO-Estudiantes> (try 1/3)
[ 1518.566729] wlp6s0: RX AssocResp from <MAC C-01 EO-Estudiantes> (capab=0x431 status=0 aid=1)
[ 1518.566849] wlp6s0: associated
[ 1518.566898] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready


    ======== Done ========

```

---

### Post by jeremy31 on 2016-12-17
*Thread moved to **Ubuntu/Debian BASED**.*

The access point EO-Estudiantes doesn't appear to be using WPA2, it is using WPA with TKIP and it is causing issues

---

### Post by mnavarrocarter on 2016-12-17
> [COLOR=#000000]The access point EO-Estudiantes doesn't appear to be using WPA2, it is using WPA with TKIP and it is causing issue[/COLOR][COLOR=#000000]
[/COLOR]
Hey jeremy31, first: sorry for the bad placement of the thread in the forum. Second: thanks for moving it and for taking the time to answer.

How come access point EO-Estudiantes is causing issues? Could you be more specific? I'm connected to it and I have no problems because it is WPA. But I have another WPA2 network where I cannot connect.

---

### Post by praseodym on 2016-12-18
Hi,

there are 2 drivers loaded:
```

sudo modprobe -rfv wl ath9k
sudo modprobe -v ath9k
```
Uninstall the Broadcom driver

---

### Post by mnavarrocarter on 2016-12-18
I uninstalled the Broadcom driver but the issue is still present. Is a very interesting issue: everything on my internet works perfect, except I cannot connect to any WPA2 network. Encryption problem? I don't really know.

For troubleshooting also changed my wireless card to a old miniPCI Broadcom to test. Didn't work too (that is, only in WPA2 networks). So at this point I think I can say it is not a driver problem. Maybe is a distro issue? I'm sure it has something to do with the way passwords are encrypted. 

If you have some other ideas to solve the issue I'm listening. Thanks!

---

