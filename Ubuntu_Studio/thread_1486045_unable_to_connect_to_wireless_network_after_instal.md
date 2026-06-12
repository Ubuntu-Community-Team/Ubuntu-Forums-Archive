---
title: "unable to connect to wireless network after install"
date: 2010-05-17
forum: Ubuntu Studio
---

### Post by malrost on 2010-05-17
After a clean install of Ubuntu Studio 10.04 amd64, I have no network access. 

I skipped configuring the wireless card during the install because it only allowed for WEP networks. I only have access to two wireless networks. One has WPA Version 1 encryption, the other uses 802.1x. I have no wired ethernet connection available, and so I cannot download packages to install, such as wicd.

[This thread]("http://ubuntuforums.org/showthread.php?t=1485225") seemed related, and I followed its steps up to the point where iwlist scan identified the networks I'd like to join. How to do that?

What is the next step -- how can I now connect to the WPA wireless network? It uses an ASCII string as the password. I've read the man pages on iwlist, iwconfig, and wireless. The following command is not working, and I'm stumped.

```
sudo iwconfig wlan0 key s:password
```


Below is the output of the following commands:
[LIST=1]
[*]dmesg | grep -e ath -e wlan -ie radio
[*]lshw -C Network
[*]sudo iwlist scan (The listed output is an excerpt -- the two desired networks have multiple entries, all of which are listed. My neighbors' access points, however, have been removed.)
[*]lspci -nn | grep -i ralink
[*]cat /etc/issue
[/LIST]

1. 
```
dmesg | grep -e ath -e wlan -ie radio
(standard input)
```

2. 
```
lshw -C Network
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wlan0
       version: 00
       serial: 00:18:39:14:ca:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:fc010000-fc017fff
```


3.
```
sudo iwlist scan
]wlan0     Scan completed :
                  Cell 03 - Address: 00:03:52:CF:ED:C1
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004c7894d
                    Extra: Last beacon: 1015ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:03:52:CF:ED:C0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004c7805c
                    Extra: Last beacon: 1017ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: 00:03:52:CF:F8:90
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000537f6ea
                    Extra: Last beacon: 961ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: 00:03:52:CF:F8:91
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000005380567
                    Extra: Last beacon: 957ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:03:52:CF:F6:90
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000050794f4
                    Extra: Last beacon: 833ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: 00:03:52:CF:F6:91
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000005079f4c
                    Extra: Last beacon: 830ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: 00:03:52:DC:80:E1
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000007710e6
                    Extra: Last beacon: 827ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 00:03:52:DC:80:E0
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000770bfb
                    Extra: Last beacon: 829ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: 00:03:52:CF:FA:90
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004af9729
                    Extra: Last beacon: 511ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 20 - Address: 00:03:52:CF:FA:91
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004af9c14
                    Extra: Last beacon: 510ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: 00:03:52:DB:F2:40
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006bd0181
                    Extra: Last beacon: 505ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 22 - Address: 00:03:52:DB:F2:41
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006bd0a73
                    Extra: Last beacon: 502ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: 00:03:52:DA:53:F0
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"bls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000045a22d4
                    Extra: Last beacon: 547ms ago
                    IE: Unknown: 0003626C73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 26 - Address: 00:03:52:DA:53:F1
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"bls-med"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000045a2acf
                    Extra: Last beacon: 545ms ago
                    IE: Unknown: 0007626C732D6D6564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```


4.
```
lspci -nn | grep -i ralink
01:07.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```

5.
```
cat /etc/issue
Ubuntu 10.04 LTS \n \l
```

---

### Post by malrost on 2010-05-17
Marking this as solved. Since I was working from a clean install, it was easier just to install 10.04 LTS and install Studio on top of it with the following from [here]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy"):

```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

