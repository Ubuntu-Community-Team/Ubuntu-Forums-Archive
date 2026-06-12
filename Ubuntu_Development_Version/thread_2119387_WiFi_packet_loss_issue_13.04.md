---
title: "WiFi packet loss issue 13.04"
date: 2013-02-23
forum: Ubuntu Development Version
---

### Post by Carmageddon on 2013-02-23
hello guys!

I have  a problem where many packets get lost (pings, web pages sometimes either load slow or dont load at all, iwconfig shows it).

Since this is a new hardware on which I directly installed Ubuntu without testing in windows, its very hard for me to tell, whether it is Driver issue, Ubuntu issue, or bug related to RR 13.04?

```
iwconfig wlan0 
wlan0     IEEE 802.11bgn  ESSID:"Gensek"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:E3:38:4C:C0   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9653  Invalid misc:16470   Missed beacon:0

```

The Wifi card is D-Link DWA-538

EDIT:  I should point out, that the computer is located in the same location as for the last 2+ years, but then I had another motherboard with built in wifi card (which only had 1 antenna, this one has two so I dont believe it could be reception issues).

---

### Post by Carmageddon on 2013-02-26
Bump.

I replaced the router as it had other issues, and the issue has not changed...

Please, any ideas?

---

### Post by Slixt on 2013-05-18
I have the same issue man. I've noticed packetloss in ifconfig wlan0 and webpages sometimes are slow and rarely but it does happen they don't load sometimes. I play muds at times (yeah yeah) but, even they start to suffer from it as I'll suddenly get no responce for a bit. Just a second or two.. occasionally like 15 seconds but, mud or any game it's enough for you get a gameover. I had the issue in 12.10 too but, 13.04 is better with it so.. I don't even know. I'm using a Belkan n300 stick right now since in 13.04 the internal card became absolute junk(not that it was good in 12.04 either, the rtl8291ce set seems to be problematic). It just drops connection randomly, has HUGE hangs.. etc etc. Far worse than in 12.10 but, yeah. I've just had such horrible luck with this laptop.

---

### Post by Carmageddon on 2013-05-19
> **Slixt said:**
> I have the same issue man. I've noticed packetloss in ifconfig wlan0 and webpages sometimes are slow and rarely but it does happen they don't load sometimes. I play muds at times (yeah yeah) but, even they start to suffer from it as I'll suddenly get no responce for a bit. Just a second or two.. occasionally like 15 seconds but, mud or any game it's enough for you get a gameover. I had the issue in 12.10 too but, 13.04 is better with it so.. I don't even know. I'm using a Belkan n300 stick right now since in 13.04 the internal card became absolute junk(not that it was good in 12.04 either, the rtl8291ce set seems to be problematic). It just drops connection randomly, has HUGE hangs.. etc etc. Far worse than in 12.10 but, yeah. I've just had such horrible luck with this laptop.

Well, I "solved" it by creating a Gbit LAN infrastructure from the router to every room in the house using a Gbit Switch 8-)

However, we could try to localize the problem: perhaps we have a common Wi-Fi card, motherboard?
What is your wifi card (exact model please), and motherboard?

---

