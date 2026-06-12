---
title: "iwconfig doesn't show wlan0"
date: 2018-07-18
forum: Ubuntu/Debian BASED
---

### Post by fakincantauria on 2018-07-18
Hi, a few hours ago I wrote a post asking for wifi because it doesn't appear ([https://ubuntuforums.org/showthread.php?t=2396558](https://ubuntuforums.org/showthread.php?t=2396558)), but now i want to use Kali with VirtualBox, but I can't connect because the bridged adapter don't give the option of wlan0 and when I put iwconfig on terminal appears this:

```
lo        no wireless extensions.

eno1      no wireless extensions.

wlo1      IEEE 802.11  ESSID:"ENTELHOGAR-169"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:C7:71:58:99:EB   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:195   Missed beacon:0


```

Can you help me plz, thanks a lot :guitar:

---

### Post by wildmanne39 on 2018-07-18
*Thread moved to **Ubuntu/Debian BASED for a more appropriate fit**.*

This is the name of your connection:
```
wlo1 IEEE 802.11 ESSID:"ENTELHOGAR-169"
```
it is no longer named wlan0 from 16.04 and newer versions, so that is not your issue.

Running kali in virtualbox you do not need to make the wireless work, just use the internet connection of your host.

---

### Post by fakincantauria on 2018-07-18
wajsjasjasjsa thanks! I feel a little stupid but thank you :biggrin: :biggrin::biggrin::biggrin::biggrin::biggrin::biggrin:

---

