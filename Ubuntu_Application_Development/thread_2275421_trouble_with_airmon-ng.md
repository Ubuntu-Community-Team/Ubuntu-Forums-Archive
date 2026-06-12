---
title: "trouble with airmon-ng"
date: 2015-04-26
forum: Ubuntu Application Development
---

### Post by zfree on 2015-04-26
hi,
  my wireless card is AR9285,and the driver is ath9k. the OS of my laptop is ubuntu 15.04. i installed the aircrack-ng. however, when i used it, i got troubles:
```

root@izfree-K40IN:/home/izfree# iwconfig 
wlan0     IEEE 802.11bgn  ESSID:"A815"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=135 Mb/s   Tx-Power=13 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

lxcbr0    no wireless extensions.
```
and i try to make the wireless card work in monitor mode with airmon-ng
```

root@izfree-K40IN:/home/izfree# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
574    avahi-daemon
586    NetworkManager
667    avahi-daemon
731    wpa_supplicant
26908    dhclient
Process with PID 26908 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Atheros AR9285    ath9k - [phy0]SIOCSIFFLAGS: Name not unique on network

                (monitor mode enabled on mon0)


```
when i run iwconfig, i found wlan0 and mon0 are both in managed mode. mon0 did not connect the AP.
```

root@izfree-K40IN:/home/izfree# iwconfig 
wlan0     IEEE 802.11bgn  ESSID:"A815"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=81 Mb/s   Tx-Power=13 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

lo        no wireless extensions.

mon0      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=13 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

lxcbr0    no wireless extensions.


```
can anybody help me?

---

### Post by lisati on 2015-04-26
Support for airmon-ng is usually discouraged on this forum. You might have better luck [here]("https://forum.aircrack-ng.org/").

Thread closed.

---

