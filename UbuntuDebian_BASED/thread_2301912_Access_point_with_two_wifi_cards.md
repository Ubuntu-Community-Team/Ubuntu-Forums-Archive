---
title: "Access point with two wifi cards"
date: 2015-11-06
forum: Ubuntu/Debian BASED
---

### Post by andrea-cimatoribus on 2015-11-06
Dear all,
I am using my RaspberryPi to set up a wifi access point with two wireless cards. One of the two cards is a high-gain one, so it should work as some sort of repeater.
I am following this guide: [https://learn.adafruit.com/setting-up-a-raspberry-pi-as-a-wifi-access-point/install-software](https://learn.adafruit.com/setting-up-a-raspberry-pi-as-a-wifi-access-point/install-software)
which works just fine when the Raspberry is plugged with the ethernet connection.

However, when I change the configuration for using the two wlan0/wlan1 wireless interfaces, the interface connected to the internet does not start.
If I try:

```
ifup wlan1
```

I get the error:
```
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Failed to bring up wlan1.
```

Before configuring iptables, I was actually able to connect to the internet from the Raspberry Pi using wlan1.
The server/client connection through wlan0 works fine.

Any idea of how to make progress? Thanks.

---

### Post by howefield on 2015-11-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by andrea-cimatoribus on 2015-11-06
I moved this post on [SuperUser]("http://superuser.com/questions/996926/access-point-with-two-wireless-cards-on-linux").

---

