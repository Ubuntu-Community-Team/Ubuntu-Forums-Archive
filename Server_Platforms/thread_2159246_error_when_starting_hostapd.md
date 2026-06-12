---
title: "error when starting hostapd"
date: 2013-07-02
forum: Server Platforms
---

### Post by helmii on 2013-07-02
when starting my hostapd with: service hostapd start (or service hostapd restart)
there is a problem and an error message which is:
* Starting advanced IEEE 802.11 management hostapd                      [fail]

this is my /etc/hostapd-1.0/hostapd/hostapd.conf if that helps:
hw_mode=g
interface=wlan1
channel=1
wpa_passphrase=*********
wpa=2
ssid=RaspWIFI
thx for ur help :))

---

### Post by DJ_Max on 2013-07-02
What do your logs say, what about dmesg?

---

