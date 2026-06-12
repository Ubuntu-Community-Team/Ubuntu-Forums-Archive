---
title: "Kudu Professional WiFi Connection Lost"
date: 2014-07-12
forum: System76 Support
---

### Post by wagb278 on 2014-07-12
How can I diagnose the cause (and rectify) of intermitant loss of wifi connection between a Kudu Pro and WiFi router (Actiontec model GT784WN)?  Are there any issues reported with the Kadu Pro and the basic wifi component (Intel Centrino 2230)? 

The Kadu Pro is running Linux Mint-16 (64-bit); but that shouldn't matter.  We just don't like the Unity environment and GUI experience. 

With two devices (router and computer) it is difficult to determine which is the culpret. Is there a log or something, and what would I look for? 

I'm trying to help a friend that I convinced to buy the Kudu Pro and switch to Linux; the friend complains that Wifi drops 3 to 6 times a day.  The friend reports that restarting the computer usually restores wifi; so I suspect it is a computer, not router, issue.  I was present when this happed once but a restart was not convient so we connected to the router via Ethernet which worked just fine. Location (wifi coverage) is not an issue; computer is used about 20 feet from the router.  

If WiFi connectivity drops out, shouldn't there be a deamon running that reconnects - assuming it was a temporary hick-up. 

I have helped two friends switch to Linux and both bought from System76 based on my reommendations, the other person got a Gazelle Pro and has no problems.  Of couse people and the computer usage are different, but these people are mostly Internet and Email users - nothing fancy.

Thanks for any advise.

---

### Post by varunendra on 2014-07-13
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by wagb278 on 2014-07-15
Thanks Varun - it will be a couple of days before I get access to the friends computer to run the script. Remember this is an intermittant problem.  My understanding is that when the wifi quits a computer restart restores the wifi connection I will ask again if that is true.

---

### Post by wagb278 on 2014-07-17
I got access to the System76 Kudu laptop. 
Here are the results of running that script: 

```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Laptop 3.11.0-12-generic x86_64,  Linux Mint 16 Petra, petra

CPU    : Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
Memory : 7905 MB
Uptime : 15:44:09 up 45 min,  2 users,  load average: 0.09, 0.07, 0.05


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless-AC 3160 [8086:0070]
	Kernel driver in use: iwlwifi
--
05:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
	Subsystem: CLEVO/KAPOK Computer Device [1558:6500]
	Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 004: ID 0781:555f SanDisk Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"Molly"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Molly>   
          Bit Rate=72.2 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-21 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:84   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                161349  0 
mac80211              596969  1 iwlmvm
iwlwifi               165398  1 iwlmvm
cfg80211              479757  3 iwlwifi,mac80211,iwlmvm
wmi                    19070  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID                | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
===============================o=============o=========o==============o=========o===========o==============o===========
 eth0  [Ethernet connection 1] | Wired       | r8169   | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
    DNS:             205.171.2.25
-------------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0  [SES-Wi-Fi]            | 802.11 WiFi | iwlwifi | connected    | no      | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *Molly:          Infra, <MAC C-01 Molly>, Freq 2437 MHz, Rate 54 Mb/s, Strength 98 WPA WPA2
    Motorola3347:    Infra, <MAC C-NA Motorola3347 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2

    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
    DNS:             205.171.2.25
-------------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

Heuberger Sitting Area : ssid=Heuberger Sitting Area | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Irving Wi-Fi         : ssid=MP898 | ipv4=auto | ipv6=auto 
Motorola3347         : ssid=Motorola3347 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SES-Wi-Fi            : ssid=Molly | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.443/0.541/0.639/0.098 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.035/0.038/0.003 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
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
          Cell 01 - Address: <MAC C-01 Molly>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"Molly"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001cdfdf4d7
                    Extra: Last beacon: 28ms ago
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
filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     584DCDF51978B1AA013695D
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.11.0-12-generic/kernel/net/mac80211/mac80211.ko
srcversion:     367212A7EC9CD2205F8C5C9
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B3EF32124305F5D1F6E94A5
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
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
filename:       /lib/modules/3.11.0-12-generic/kernel/net/wireless/cfg80211.ko
srcversion:     1FEC83877CF068095FA2F9F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b3 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


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

BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=a2e11b73-aa97-4151-9ca3-cc6d2ef1dc13 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.567369] audit: initializing netlink socket (disabled)
[    0.666497] wmi: Mapper loaded
[    0.671745] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.156416] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.156466] iwlwifi 0000:04:00.0: irq 48 for MSI/MSI-X
[   10.249437] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.283369] iwlwifi 0000:04:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[   10.364017] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   10.364063] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   10.364205] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   10.478853] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   11.407731] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.755455] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   12.755598] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   12.765143] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.765307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.330760] wlan0: authenticate with <MAC C-01 Molly>
[   20.332167] wlan0: send auth to <MAC C-01 Molly> (try 1/3)
[   20.334119] wlan0: authenticated
[   20.334810] wlan0: associate with <MAC C-01 Molly> (try 1/3)
[   20.338309] wlan0: RX AssocResp from <MAC C-01 Molly> (capab=0x411 status=0 aid=3)
[   20.339557] wlan0: associated
[   20.339637] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

	======== Done ========

```
I hope you can see something in there that causes ocasional dropout of WiFi and why it needs a computer restart to restore wifi. 

Thanks!

---

### Post by varunendra on 2014-07-18
There are more than one thing you can try to optimize the wireless connectivity. Try them in the sequence suggested, and stop where it seems stable and strong enough.

[indent]**1)** If it is not a problem, try upgrading your kernel version. The newer driver and the newer firmware that comes with it are supposed to support AC speeds a bit better.

**2)** This change you should certainly make regardless of whether it seems to help or not - Change the encryption type in the router/Access-Point from WPA/WPA2 mixed mode to pure WPA2-PSK with AES. No mixed mode, no TKIP.

**3)** Apart from changing the encryption type, also try changing the channel from 6 (or 'auto') to 1 or 11. Channel 6 is not bad, but usually channels 1 and 11 offer the best signal quality if they are not already too crowded by neighbourhood APs.

**4)** Again in the router, if operating on 2.4 GHz band, make sure it is set to 20 MHz mode, not 20/40 auto mode. The intel driver 'iwlwifi' has been found to work better with 20 MHz mode when operating on 2.4 GHz band. Reboot the router after saving any changes to make sure they take effect properly.

**5)** If the above changes don't seem to help, try a driver parameter in Ubuntu itself. To try it, open a terminal (Ctrl-Alt-T) and run the following code in it (you may copy-paste it to avoid typo) -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
```
This change will take effect after a reboot.[/indent]

There are also some driver parameters with the iwlwifi driver that may be helpful in some cases. A detailed description of these is given in this post : [http://ubuntuforums.org/showpost.php?p=12943350](http://ubuntuforums.org/showpost.php?p=12943350)

---

### Post by wagb278 on 2014-07-19
Thanks Varun,  I will try your suggestions the next time I have access to the friend's computer. 

I will report back afterward.

---

### Post by wagb278 on 2014-08-07
I did update to a newer kernal - 3.13.0-27.

I discovered that somehow a Soft Block was being set on the WiFi on the Kadu Pro laptop.  I don't know what process is setting the Block. 

It was discovered using the command: 
```
rfkill list
```

That command showed that the Wireless LAN had a soft block turned on.
Running the following command removed that Block and permitted reenabling the Wireless network via the actions in the Network Panel. 
```
sudo rfkill unblock all
```

The obvious disable transmitting button (Fn+F11) is not being used so it is not a human action causing the outage.  Somehow the Laptop is doing it itself. 

If anyone at System76 reads this thread - please provide some ideas as to where to look for what process might be setting the Soft Block and how to prevent it from happening. I am beginning to think it is a failure of some component in this new Kadu Pro; but hope it is some malforming software process.

---

