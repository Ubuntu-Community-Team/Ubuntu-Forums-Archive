---
title: "Wifi in Bonobo bonp5"
date: 2014-03-14
forum: System76 Support
---

### Post by Joe_Knapka on 2014-03-14
More like cry-fi...

I have a 2-year old Bonobo Extreme that I recently upgraded to Ubuntu 13.10. I find the rtl8188ce wifi card to be so flaky as to be unusable. It simply will not stay associated with either of my access points (I have an old 11g that I recently replaced with an 11n). With either AP, dmesg shows frequent re-associations, and several times a day it gets into a state where the wifi stops working entirely and I must reboot. When the "must reboot" situation occurs, dmesg shows repeated "rtlwifi [blah blah]: sta is NULL" messages. I have several other wireless devices on the same network that have no problems. I only noticed this now because for over a year, this machine sat on a desk with an Ethernet cable plugged into it. In the past month, it has gone from occasional use to being my full-time work machine, and it's REALLY GREAT except for this one issue.

I've tried both the Realtek rtl8192ce driver, and the modified version from [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver). Neither changed the behavior significantly.
 
I've tried adding the "ips=0" and "fwlps=0" options to /etc/modprobe.d/rtl8192ce.conf. No effect.

I've tried setting the retries to 20, and the rts threshold to 500, using iwconfig. This sort of seems to help, but not really -- subjectively, performance seems to improve, but eventually I still end up having to reboot.

I've opened the bottom of the machine up and blew out all the dust and cruft (there wasn't much). No joy.

Any suggestions would be much appreciated. I'd even resort to swapping out the wifi card for a better-supported one, if that's possible. But a software or configuration solution would be preferable.

Thanks,

- JK

---

### Post by varunendra on 2014-03-16
Welcome to the forums!

Looks like you have tried all I usually suggest, but I'd still like to see the current setup details. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Joe_Knapka on 2014-03-18
Hi Varun,

Thank you for your reply. I've pasted the wireless script output below. A couple of notes:

1) The internal wifi card shows up as wlan1, because I picked up a Belkin N150 USB adapter and configured the USB adapter as wlan0 in udev. (I did that so that my VirtualBox guests would continue to see the correct bridged network adapter name.) I had blacklisted all the rtl8188ce-related modules so that the kernel only picks up the USB adapter. This has worked around the problem, but having the USB adapter sticking out of the side of the machine is annoying and I'd much rather get the internal wifi working.

2) I disconnected the Belkin USB, un-blacklisted the rtl8188ce modules, rebooted, and ran the wireless script immediately after reboot. The machine was definitely using the internal wifi when I ran the script. Within five minutes after running the script, it had re-associated with the access point twice according to dmesg :-( I couldn't log on to the forums to post this until I switched back to the USB wifi.

Script output:


```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux bonobo-joe 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:7100]
    Kernel driver in use: jme

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:9196]
    Kernel driver in use: rtl8192ce

##### lsusb #####

Bus 002 Device 004: ID 5986:0308 Acer, Inc 
Bus 002 Device 003: ID 147e:1001 Upek TCS5B Fingerprint sensor
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 125f:a15a A-DATA Technology Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan1     IEEE 802.11bgn  ESSID:"BROCKTON"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.101.1   0.0.0.0         UG    0      0        0 wlan1
192.168.101.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #####

nameserver 127.0.1.1
domain jk
search jk
nameserver 192.168.101.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan1  [BROCKTON] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Prudent:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ATT98Zdw6a:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    2WIRE952:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Red Wi-Fi de Enrique: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    2WIRE724:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    family:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *BROCKTON:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA2

  IPv4 Settings:
    Address:         192.168.101.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.101.1

    DNS:             192.168.101.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"BROCKTON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005910510325
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000842524F434B544F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDAA0050F204104A0001101044000102103B000103104700108459C88E60B98B06FD15AA2117B75C7B102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000652542D4E31321042001162633A65653A37623A66313A39343A35341054000800060050F20400011011000652542D4E3132100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"2WIRE952"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000063dd11c3cc0
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 00083257495245393532
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"ATT98Zdw6a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ae44a1c8e
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000A41545439385A64773661
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"family"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008ca5c160c
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000666616D696C79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD740050F204104A0001101044000102103B00010310470010B9F539A2ECABE5766B6925393AB97054102100074C696E6B73797310230004453930301024000776312E302E30311042000234321054000800060050F20400011011000445393030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Red Wi-Fi de Enrique"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000024b5b9f8180
                    Extra: Last beacon: 976ms ago
                    IE: Unknown: 00145265642057692D466920646520456E7269717565
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301730320
                    IE: Unknown: DD0E0017F2070001010620C9D0A6BECC
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Habits"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008a061b4148
                    Extra: Last beacon: 2532ms ago
                    IE: Unknown: 0006486162697473
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880F8EDA5AF9650103C000101
                    IE: Unknown: 050400010030
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503002A127A
                    IE: Unknown: DD07000C4307000000

##### iwlist channel #####

wlan1     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### lsmod #####

rtl8192ce             137725  0 
rtlwifi               110108  1 rtl8192ce
mac80211              597268  2 rtlwifi,rtl8192ce
cfg80211              480503  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7B1C05B089A32851C837B52
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 0 is off)
 (bool)
parm:           fwlps:using no linked fw control power save (default 0 is off)
 (bool)

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     38C683C46FA4C16AD6DE717
depends:        mac80211,cfg80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 

##### modules #####

lp
rtc
lp
rtc

##### blacklist #####

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

##### udev rules #####
Binary file /etc/udev/rules.d/70-persistent-net.rules matches

##### dmesg #####

[    9.427326] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.427495] rtlwifi: wireless switch is on
[   18.782508] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   18.782682] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.499481] wlan1: authenticate with <MAC address removed>
[   20.519627] wlan1: send auth to <MAC address removed> (try 1/3)
[   20.521985] wlan1: authenticated
[   20.523118] wlan1: associate with <MAC address removed> (try 1/3)
[   20.526508] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   20.526625] wlan1: associated
[   20.526644] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   28.623224] wlan1: deauthenticated from <MAC address removed> (Reason: 15)
[   29.572959] wlan1: authenticate with <MAC address removed>
[   29.593023] wlan1: send auth to <MAC address removed> (try 1/3)
[   29.594661] wlan1: authenticated
[   29.596600] wlan1: associate with <MAC address removed> (try 1/3)
[   29.600114] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   29.600222] wlan1: associated
[   37.725659] wlan1: deauthenticated from <MAC address removed> (Reason: 15)
[   38.678573] wlan1: authenticate with <MAC address removed>
[   38.698568] wlan1: send auth to <MAC address removed> (try 1/3)
[   38.702229] wlan1: authenticated
[   38.706143] wlan1: associate with <MAC address removed> (try 1/3)
[   38.711364] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   38.711470] wlan1: associated

########## wireless info END ############

```

---

### Post by varunendra on 2014-03-19
Despite you having said that you already tried the driver from github, I'd like to see how it performs with the compat drivers we have tested many times by now.

Please follow this post to install it : [http://ubuntuforums.org/showpost.php?p=12926946](http://ubuntuforums.org/showpost.php?p=12926946)

If needed, please also try the parameters as well : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

You should also try changing the channel in the router to 1 or 11 (or 13 if it is available). They usually offer better signal quality and sometimes it helps.

And just curious -

* Why did you have to bother to edit the "udev rules" part of the script? Some tricks/entries you don't want to share with us? :)
* Whose Access-Point is the one with ESSID "ATT98Zdw6a" ? By its signal strength (70/70) it looks like yours. If so, it is using a highly discouraged encryption type. Probably not related to the problem in hand here, but you might wish to change its encryption to pure WPA2-AES (CCMP).

---

### Post by Joe_Knapka on 2014-03-20
Hi Varun,

I did not change anything about the wireless diagnostic script (at least, not intentionally - did you notice something different than what you expected?). When I mentioned udev, I meant that when I added the Belkin USB wifi adapter, I needed it to appear as wlan0 because I have virtual machines that expect to use wlan0 to connect to the network, and reconfiguring that in the VMs is a pain.

I will give the github driver a try (or another try, possibly).

Also, I'm sorry for the delayed replies - I have subscribed to this thread, but I didn't see the last email notification.

Thanks,

Joe

---

### Post by Joe_Knapka on 2014-03-20
Hi Varun,

The backport driver definitely works better! Twenty minutes into a reboot using the internal wifi, and I have not yet seen the card re-associate with my AP. (Which, incidentally, is not the one you were concerned about re encryption - I'm using WPA2/AES).

In the default configuration, speed tests are still pretty flaky compared with the USB wifi adapter. With the USB I get consistent 12Mbps results from the Dallas server at [http://speakeasy.net/speedtest/](http://speakeasy.net/speedtest/) . The internal card is all over the place, varying between 3Mbps and 12Mpbs, and often varying that much within a single test. (This is interesting to me, because this particular USB uses the rtl8188CU chip, whereas the internal one is an rtl8188CE. I assume these basically the same part, except with USB vs PCIe interface logic? I wonder if comparing the two drivers would lead to some insight about performance differences.)

In any case, I found that doing:

  sudo iwconfig wlan1 retry 10 rts 512

makes everything better! I can consistently hit the SpeakEasy test server and get >9Mbps results.  I still get more variance than with the USB adapter, but this is probably good enough unless some other problem manifests.
 
I'm going to run with this driver for a day or so before marking this SOLVED, but it's looking good. Thank you very much for your help and your patience!

- Joe

---

### Post by Joe_Knapka on 2014-03-20
One other thing I forgot to mention: the USB wifi adapter always shows 5 bars of signal quality in the wifi status icon, whereas when I'm using the internal one that icon changes a lot, showing anything between 0 and 5 bars at any given moment.

Still no re-associations, though :-)

- Joe

---

### Post by Joe_Knapka on 2014-03-21
Just a final note:

The instructions in the last post from Varunendra in this thread have made the rtl8188ce internal wifi card in this Bonobo Extreme work acceptably well. I have been using it for an entire day, on three different wifi networks, with no serious problems.

As well as installing the back-ported rtl8192ce driver as Varun describes, I found it necessary to issue the following iwconfig command in order to get acceptable wifi performance:

[COLOR=#000000]sudo iwconfig wlan1 retry 10 rts 512
[/COLOR]
(you should replace "wlan1" with your actual wifi interface).

The laptop's internal wifi still does not perform quite as well as the Belkin N150 USB wifi adapter I have been using as a temporary stopgap measure. However, it is working well enough for my purposes, and most importantly, the frequent access-point re-association problem seems to have been completely fixed.

I am marking this thread SOLVED.

---

### Post by varunendra on 2014-03-21
Sorry for not being able to reply sooner. Unfortunately, I still can't promise speedy replies for a few more days, although I'll try my best.

I'm glad that you consider it solved, and is definitely encouraging that the compat driver is performing better. I don't fully trust the 'Signal Strength' displayed by these drivers, but if the transfer speed is fluctuating too, that is enough to keep my BP and heart-beat-rate above normal.:|

I'd strongly recommend to try those parameters I linked to in my first post (the 2nd link) if you haven't already. Especially the "ips" and "fwlps" parameters, because fluctuating signal is normally an indication of power management issue, and those parameters disable power management *(management usually means "saving", which further means trouble for wifi if not done properly)*.

Also make sure "Power Management" in the output of "iwconfig" command _Always_ appears to be "off".

Let me know if you need help with these. If you do, please post back with a fresh report of "wireless_script" which you can find in the "Wireless Script" link in my signature (with instructions to run it).

Not promising I can make it any better though, but I'd be happy to assist if you don't mind tinkering without any promises. :p

---

### Post by Joe_Knapka on 2014-03-21
Hi Varun,

I'm happy to keep tinkering. I added ips=0, fwlps=0, and swenc=1 individually and together to the module options, and confirmed that the module was loaded with those options as configured. None of them seems to have made much difference. The thing that really helps is the iwconfig to set retry=10 and rts=512. 

Power management is always off.

I also notice that the signal strength as reported by iwconfig is very unstable, from -20dBm to -100dBm. This is not the case when I use the USB wifi adapter. I am starting to wonder if perhaps the antenna lead has come loose from the internal wifi card.

Joe

---

### Post by varunendra on 2014-03-21
Yes, loose antenna contacts is one of the two remaining suspects if the power management part is confirmed to be okay. The other suspect is neighbourhood signal interference (even if the USB adapter doesn't have this problem, as different drivers have different abilities to deal with it). Did you change the channel as recommended (1 or 11) in the router?

I'd also recommend you install powertop -
```
sudo apt-get install powertop
```
Then run it with -
```
sudo powertop
```
Press the 'Left' arrow key after it starts, to quickly go to its last tab. Here you should see various settings with "Good" or "Bad" prefixes. Highlighting any of the settings and pressing 'Enter' toggles its state between "Good" and "Bad". Make sure the "Wireless Power Management" is set to "Bad" ;) *(yeah, good means power saving, which we don't want on wireless).*

---

### Post by Joe_Knapka on 2014-03-21
Hi Varun,

I just noticed something odd. In the dmesg output, I see this:

rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin

However, there is an rtl8188efw firmware file in /lib/firmware/rtlwifi, which based on the name looks like it might be a better choice.  Though I realize that the rtl8192c firmware may actually be the appropriate thing for this particular part, it's not totally obvious whether that's true.

- Joe

---

### Post by varunendra on 2014-03-21
Which firmware to use is hard-coded in the driver, you can not change it. What you can do is to fool the driver by renaming the file to the one it is asking for (of course while backing up the original ones beforehand). But I'm pretty sure that will either produce errors, or will break driver's functionality (temporarily - as long as you don't give it the original firmware again).

Which firmware files a driver can work with can be determined with "modinfo" command. For example, -
```
modinfo rtl8192ce
```
..gives -
```
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
```
..which means it won't accept any other firmware files. Of these three listed above, which one it'll ask for depends on what kind of chip was detected (there is quite a variety of them).

Easy enough to try, and I have no reason to discard the possibility altogether, but I seriously doubt it'll work.

---

### Post by Joe_Knapka on 2014-03-21
OK, I think I will not try the firmware thing. I have on occasion killed hardware by flashing it with the wrong firmware :-P

I don't suppose there's a teardown manual or video for this machine (bonp5) so I can check the antenna lead? I wasn't able to find one with a quick Google. I had the bottom panel off the machine, but I could not see the wifi card and I'm nervous about randomly unscrewing stuff inside a $2000US laptop.

---

### Post by Joe_Knapka on 2014-03-21
powertop reports "Bad" status for "Wireless Power Saving for interface wlan1" (which is the internal wifi)... So that's good, right?

---

### Post by varunendra on 2014-03-21
> **Joe_Knapka said:**
> I had the bottom panel off the machine, but I could not see the wifi card and I'm nervous about randomly unscrewing stuff inside a $2000US laptop.
Good idea not to try without knowing 'HowTo'. I have broken those plastic locks several times on several laptops while trying on my own :p

> **Joe_Knapka said:**
> powertop reports "Bad" status for "Wireless Power Saving for interface wlan1" (which is the internal wifi)... So that's good, right?
Yeah, "Bad" is "good" :D. Unfortunately, it not helping our cause is not :|


Also unfortunate that I don't have more ideas at this point now. You may try compiling the latest compat driver instead of the one we tried, but at least two threads I addressed yesterday reported problems with Realtek drivers in kernel 3.13, so I'm skeptical about its backported version also.

---

