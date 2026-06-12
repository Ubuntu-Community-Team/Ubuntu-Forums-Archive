---
title: "Aircrack-ng Captures WPA Handshake but Doesn't Display"
date: 2011-10-20
forum: Security
---

### Post by GrantStoner on 2011-10-20
I have more of an annoyance than an "issue". When testing my own home network I noticed airodump-ng doesn't tell me when I'm capturing a WPA handshake. There's been no updates to Aircrack-ng for a while so I wouldn't imagine the problem lies with Aircrack-ng. When I```
airodump-ng --channel 11 --bssid BL:AH:BL:AH:BL:AH -w foo mon0
```and then```
aireplay-ng --deauth 7 -a BL:AH:BL:AH:BL:AH -c HA:HA:HA:HA:HA:HA mon0
```it used to display "WPA handshake" or whatever in the airodump-ng window. Now I can't tell if my captures are successful or not until I run them all through ```
aircrack-ng -w wordlist.lst file.cap
```This didn't used to happen - it used to tell me when I was performing a WPA handshake.

Also, I'd like to know if anyone has been able to patch iwlagn to play nice with compat-wireless? It seems like some compat wireless versions build, some don't. Some completely take away my wlan0 and eth0 when I install them. And many others just plain don't work. I remember finding a release a while ago that worked when I was first learning about aricrack-ng, so I searched for around that time. I finally found a compat-wireless release from June 2011 that works okay - except I'm wondering if the "WPA handshake" problem is directly related to that release or not.

[http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless) <--- these are the instructions I'm following for patching iwlagn with compat-wireless.

---

### Post by Dangertux on 2011-10-20
> **GrantStoner said:**
> I have more of an annoyance than an "issue". When testing my own home network I noticed airodump-ng doesn't tell me when I'm capturing a WPA handshake. There's been no updates to Aircrack-ng for a while so I wouldn't imagine the problem lies with Aircrack-ng. When I```
airodump-ng --channel 11 --bssid BL:AH:BL:AH:BL:AH -w foo mon0
```and then```
aireplay-ng --deauth 7 -a BL:AH:BL:AH:BL:AH -c HA:HA:HA:HA:HA:HA mon0
```it used to display "WPA handshake" or whatever in the airodump-ng window. Now I can't tell if my captures are successful or not until I run them all through ```
aircrack-ng -w wordlist.lst file.cap
```This didn't used to happen - it used to tell me when I was performing a WPA handshake.

Also, I'd like to know if anyone has been able to patch iwlagn to play nice with compat-wireless? It seems like some compat wireless versions build, some don't. Some completely take away my wlan0 and eth0 when I install them. And many others just plain don't work. I remember finding a release a while ago that worked when I was first learning about aricrack-ng, so I searched for around that time. I finally found a compat-wireless release from June 2011 that works okay - except I'm wondering if the "WPA handshake" problem is directly related to that release or not.

[http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless) <--- these are the instructions I'm following for patching iwlagn with compat-wireless.

What version of airodump-ng are you running? And have you tested it without a deauth attack, IE: just authenticate to the WAP with another card to see if it indicates that the capture has occured?

I've not seen this happen before.

---

### Post by GrantStoner on 2011-10-21
Version 1.1 - latest from the *buntu repos.
Capture occurs successfully - airodump-ng just doesn't tell me if it has or has not, so I have to run it through aircrack-ng to find out.

---

### Post by Dangertux on 2011-10-21
> **GrantStoner said:**
> Version 1.1 - latest from the *buntu repos.
Capture occurs successfully - airodump-ng just doesn't tell me if it has or has not, so I have to run it through aircrack-ng to find out.

Yeah I noted the same behavior in Ubuntu 11.04 after testing it.

However under backtrack 5 and 5 r1 it does not behave this way. 

Have you filed a bug report?

---

### Post by GrantStoner on 2011-11-16
I have not filed a bug report. I will though, thanks. It seems the issue is with Ubuntu 11.04 not aircrack-ng - I've noticed this is only on my 11.04 box, and only since I upgraded from 10.10

Thanks for the insight. Sorry for the late reply.

---

