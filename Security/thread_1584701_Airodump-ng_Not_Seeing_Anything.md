---
title: "Airodump-ng Not Seeing Anything?"
date: 2010-09-29
forum: Security
---

### Post by GrantStoner on 2010-09-29
What could be some causes of airodump-ng not being able to find any networks? ```
grant@TheHaxLab:~$ sudo airmon-ng start ra0
[sudo] password for grant: 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
848	NetworkManager
857	avahi-daemon
858	avahi-daemon
1016	wpa_supplicant
2255	dhclient
Process with PID 2255 (dhclient) is running on interface ra0


Interface	Chipset		Driver

ra0		Ralink 2560 PCI	rt2500 (monitor mode enabled)

grant@TheHaxLab:~$ sudo airodump-ng ra0



 CH  6 ][ BAT: 2 hours 18 mins ][ Elapsed: 44 s ][ 2010-09-29 10:48            
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                               
                                                                               
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes     
                                                                               

grant@TheHaxLab:~$ 

```
I can't even see my own home network.

---

