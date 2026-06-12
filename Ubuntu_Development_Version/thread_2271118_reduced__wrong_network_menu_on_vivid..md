---
title: "reduced / wrong network menu on vivid."
date: 2015-03-27
forum: Ubuntu Development Version
---

### Post by corradoventu on 2015-03-27
on ubuntu vivid the network menu is reduced an does not work properly.
same menu is complete in ubuntu trusty and utopic installed on same PC different partitions.
attached the images from vivid and utopic.

---

### Post by grahammechanical on 2015-03-27
If we disable networking we get that reduced menu. If after enabling networking we still get that reduced menu the problem could be this, as seen at the very top of the menu

> No network devices available

Are the networking devices (ethernet and WiFi adapters) switched off in the BIOS/UEFI boot system? Or by some keyboard short cut? Is Windows on this machine? From what I have heard, if we disable networking in Windows then Ubuntu is unable to switch the adapters on when it loads. I do not know if this applies to this machine or not.

Run this command

```
rfkill list
```

You should see this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


If Soft blocked = yes. Then the Wifi adapter is switched off in Ubuntu but if Hard blocked = yes. Then the WiFi adapter is switched off in hardware.

I do not think that this a bug in Ubuntu Vivid as these are common issues on all versions of Ubuntu. Now, it all depends on the type of network adapters on the motherboard. If we only have one ethernet adapter then we can try these two commands

```
sudo ifdown eth0
sudo ifup eth0
```

If we have two ethernet adapters then the second ethernet adapter would be eth1. If we have a WiFi adapter, then we can try

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

For some reason taking a network adapter down and then taking it up seems to fix things. Whereas, simply taking the adapter up does not work.

Regards.

---

### Post by corradoventu on 2015-03-28
i see:
corrado@corrado-vivid64:~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hp-gps: GPS
	Soft blocked: yes
	Hard blocked: yes
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
corrado@corrado-vivid64:~$

---

### Post by ventrical on 2015-03-28
> **corradoventu said:**
> on ubuntu vivid the network menu is reduced an does not work properly.
same menu is complete in ubuntu trusty and utopic installed on same PC different partitions.
attached the images from vivid and utopic.

Have your actually created a network yet? Check Connection Information and see. They may have got wiped or it didn't auto create. If this is not the case then it must be an indicator bug.

Regards..

---

### Post by corradoventu on 2015-03-29
sorry, i was not clear describing the problem. the network works fine, just the menu is wrong. i'm writing this note in vivid being connected via wifi. probabily the menu was ok some days ago because i was able to enter the password for my wifi.

---

### Post by corradoventu on 2015-03-29
also if i ask for a list i have a long list with many wifi points ... i include some lines of the list.
```
corrado@corrado-vivid64:~$ sudo iwlist sc
eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: DC:0B:1A:5E:E8:3F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Telecom-73991993"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001394ce024fb
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 001054656C65636F6D2D3733393931393933
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
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B00010310470010C5F9A5D061EB03AA555FE5E09A9DC28710210003414442102300074147574946494E1024000630303030303110420004303030311054000800060050F20400011011000D41472042617369632057694669100800020088103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:04:ED:57:3B:93
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Sitecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015fdb2b9160
                    Extra: Last beacon: 3136ms ago
                    IE: Unknown: 000753697465636F6D
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 32080C1218602430486C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1D:8B:68:BF:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Alice-56806185"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f0711d4701
                    Extra: Last beacon: 2532ms ago
                    IE: Unknown: 000E416C6963652D3536383036313835
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD600050F204104A00011010440001021041000100103B0001031047001000000000000000000000000000000000102100001023000010240000104200001054000800000000000000001011000E416C6963652D3536383036313835100800020000
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: DC:9F:DB:60:BE:76
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)

```

---

### Post by corradoventu on 2015-03-29
my ubuntu vivid was installed from a daily (alpha?) the 28-oct-14 and then updated each 2 or 3 days ...

today I installed the last daily (26-mar-15) on a different partition and the problem disappeared.
thanks, and sorry for the alarm.
if needed for debug i still have the partition with the bug.

---

