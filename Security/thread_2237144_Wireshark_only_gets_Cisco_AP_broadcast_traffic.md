---
title: "Wireshark only gets Cisco AP broadcast traffic"
date: 2014-07-30
forum: Security
---

### Post by timonoj on 2014-07-30
Hi guys,

I'm a bit of new on network security, but some news shown yesterday that the Xiaomi phones are *phoning home*. So I'd like to check a couple of devices our employees have on BYOD policy. The devices aren't rooted, so I was thinking to just have wireshark capturing while I had them next to me at the office. Sadly, it seems the Cisco AP is using wifi isolation very effectively. All I can see is the SSID management packages from both APs (one for private network, another one with a more public network and no access to local IPs). I also can see from time to time a bit of I can't see any TCP/UDP traffic...How could I proceed?

I have an intel Wireless 1000-N card. I use airmon-ng to set it to monitor mode (as using the iwconfig wlan monitor didn't seem to work too well), and capture on the device "mon0" it creates. 

Is there a way to work around this? I'm not too keen on going and go mess on the cisco switch or firewall to capture from there...

Thanks a lot!

---

