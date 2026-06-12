---
title: "Lost WiFi in Saucy (ASUS EeePC 701)"
date: 2013-09-18
forum: Ubuntu Development Version
---

### Post by TunaCanTommy on 2013-09-18
Have done a clean install of Lubuntu Saucy onto an ASUS 701.  Running fine, except no WiFi.
WLAN0 will see the nearby AccessPoints and when I try to access my home network the the proper encryptino key nothing happens ? ?
I've been searching the forums for a possible solution for about a week now -  getting frustrated!

EDIT: I tried a Wireless N USB adapter and it didn't provide WiFi either.

See the following output from the wireless_script from the forum:


```
*************** info trace ***************

***** uname -a *****

Linux eeepc 3.11.0-7-generic #14-Ubuntu SMP Mon Sep 16 18:41:57 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu Saucy Salamander (development branch)
Release:	13.10
Codename:	saucy

***** lspci *****

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
	Kernel driver in use: ath5k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L2 Fast Ethernet [1969:2048] (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
	Kernel driver in use: atl2

***** lsusb *****

Bus 001 Device 004: ID eb1a:2761 eMPIA Technology, Inc. EeePC 701 integrated Webcam
Bus 001 Device 003: ID 0951:1606 Kingston Technology Eee PC 701 SD Card Reader [ENE UB6225]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

ath5k                 134963  0 
ath                    19187  1 ath5k
mac80211              513247  1 ath5k
cfg80211              401436  3 ath,ath5k,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    EHA63-BURC:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    4VDQL:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    UDRSR:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             68.238.112.12



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"EHA63-BURC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000351ad9722e
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000A45484136332D42555243
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010CD526D2AC99FF9304021A397F35A68111021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"4VDQL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001167ad8047
                    Extra: Last beacon: 11160ms ago
                    IE: Unknown: 0005345644514C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B


***** resolv.conf *****

nameserver 127.0.1.1
search home

***** blacklist *****

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

filename:       /lib/modules/3.11.0-7-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     B7A923930DCF3B82CF57D26
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.11.0-7-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

filename:       /lib/modules/3.11.0-7-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-7-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x1969:0x2048 (atl2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   19.296595] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   19.296895] ath5k 0000:01:00.0: registered as 'phy0'
[   22.728070] ath: EEPROM regdomain: 0x60
[   22.728084] ath: EEPROM indicates we should expect a direct regpair map
[   22.728094] ath: Country alpha2 being used: 00
[   22.728099] ath: Regpair used: 0x60
[   22.879049] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   23.725956] systemd-udevd[353]: renamed network interface wlan0 to wlan1
[   25.384341] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.386356] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready

****************** done ******************

```

Thanks for any assistance !

---

### Post by VinDSL on 2013-09-18
Might try WiCD  That's what I use.

Here's a pretty good tutorial for setting it up:  [http://peppermintos.net/viewtopic.php?f=11&t=5916](http://peppermintos.net/viewtopic.php?f=11&t=5916)

Works great in Ubuntu, et al.

---

### Post by TunaCanTommy on 2013-09-18
Thanks VinDSL . . . I did give WICD a try but I hit that problem about 'Could not connect to wicd's D-Bus interface'.
Got so wrapped around the axel trying to solve that problem that I had to do another clean install . . 
Thanks for the link on how to get past the D-Bus interface problem in WICD.
Shall give it another try . . . !

EDIT:  I got WICD working, but can not find where to enter the encryption key for my home network ? ?

---

### Post by VinDSL on 2013-09-18
Cranked up the Dell Latitude (Gorgar)...


[INDENT][[IMG]http://vindsl.com/images/vindsl-peppermint4-wicd-2(650x407).png[/IMG]]("http://vindsl.com/images/vindsl-peppermint4-wicd-2.png")[/INDENT]


'Xanthador' is my WAP.  

[LIST]
[*]Click on 'Properties' and a second window pops up.
[/LIST]

I use WPA2 encryption, so:  

[LIST]
[*]I selected 'WPA 1/2 (Passphrase)'
[*]Entered the passphrase
[*]Saved
[/LIST]

And, it's off_to_the_races.  ;)

---

### Post by VinDSL on 2013-09-18
> **TunaCanTommy said:**
> Thanks VinDSL . . .

Got so wrapped around the axel trying to solve that problem that I had to do another clean install . . 
Welcome.  I love WiCD (and hate NM), so it's my pleasure.  

I understand your frustration.  I've always named my machines after Ghostbuster characters.

Xanthador is my WAP:  [http://ghostbusters.wikia.com/wiki/Xanthador](http://ghostbusters.wikia.com/wiki/Xanthador)

Gorgar is my Dell Latitude:  [http://ghostbusters.wikia.com/wiki/Gorgar](http://ghostbusters.wikia.com/wiki/Gorgar)

And, I'm on Zuul, right now:  [http://ghostbusters.wikia.com/wiki/Zuul](http://ghostbusters.wikia.com/wiki/Zuul)

Gives me comfort, in some odd way.  LoL!  :D

---

### Post by TunaCanTommy on 2013-09-23
Thanks for your help VinDSL . . .  I installed Peppermint into my ASUS EeePC 701 and all is good.
Will mark this thread solved.

---

### Post by VinDSL on 2013-09-23
My pleasure ;)

---

### Post by VinDSL on 2013-09-26
> **TunaCanTommy said:**
> I installed Peppermint into my ASUS EeePC 701 and all is good.
Just thought I would mention...

Yesterday, I installed the [3.10.12-saucy mainline kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.12-saucy/") on my raring-based Peppermint 4 Dell Latitude D620.

Works great.  A definite improvement, all the way around.

Haven't tried it on my Eee PC 1000HD yet.

Might want to try Linux 3.10.12, if you feel adventurous.  ;)

---

