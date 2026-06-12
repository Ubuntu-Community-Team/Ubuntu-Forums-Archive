---
title: "Slow WiFi connection - Ubuntu 18.04 #2"
date: 2018-06-03
forum: Ubuntu/Debian BASED
---

### Post by SreckoMicic on 2018-06-03
I have exactly the same problem, Wifi is at least 2x slower than on Win machine (dual boot). It started after upgrading to 17.10 and still happening on 18.04 (fresh install). Download speed does not go over 900Kb/S (usually around 750KB) compared to 2MB/s on Win machine (usually topd). Also browsing is noticeable slower. I am using USB wifi.
Also attaching script output.

Tried DNSSEC = no. Tried iwconfig poweroff. Tried other solutions and nothing.

Last resort before I decide to ditch Linux completely.

[ATTACH]279955[/ATTACH]

---

### Post by jeremy31 on 2018-06-03
Split from [https://ubuntuforums.org/showthread.php?t=2392876&p=13772911](https://ubuntuforums.org/showthread.php?t=2392876&p=13772911)

Please try ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot

Moved to Ubuntu/Debian based

---

### Post by chili555 on 2018-06-03
> Cell 01 - Address: <MAC 'ZTE8358A2' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"ZTE8358A2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f117f90ed
                    Extra: Last beacon: 544ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKPlease, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

---

### Post by SreckoMicic on 2018-06-04
Nothing has changed. Did that command  and also changed to WPA AES. Thing is that I have few workstation with 16.04 and download speed is average 2MB. Also on this machines when it was 16.04, same hardware, download speed was around 2MB.

---

### Post by SreckoMicic on 2018-06-04
Also it has nothing to do with router, I tired different one, different modem, different DSL and still it is the same. It must be something with Ubuntu or drivers for wifi....

---

