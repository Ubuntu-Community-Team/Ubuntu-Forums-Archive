---
title: "54 Mb/s wireless speed limit with Ubuntu Server"
date: 2012-02-17
forum: Server Platforms
---

### Post by bakegoodz on 2012-02-17
I have a Ubuntu 11.10 samba server that uses wireless for it's network connection. Why it is not wired ethernet is for different discussion. The problem is that connecting via the console it is limited to 54 Mb/s. That is the only factor I can see, because when I boot the Live CD of Ubuntu 11.10 on the same hardware in the exact same location, same Atheros ath9k kernel module, all other factors being the same except that I connect to the wireless via tha GUI Network Manager it connects at 195 Mb/s. I have verified the speed via "iwconfig" command and by file transfers speed too. Is this a limitation in the console based software, or is there a problem with my configuration. Here is my config files:

/etc/network/interfaces

    auto lo
    iface lo inet loopback

    auto wlan0
    iface wlan0 inet dhcp
    wpa-driver wext
    wpa-conf /etc/wpa_supplicant.conf

/etc/wpa_supplicant.conf (wpa keys have been removed)

    network={
    ssid="livefire"
    #psk="****"
    psk=*************
    }

---

### Post by bakegoodz on 2012-03-01
Woohoo! I was reading about Sensitivity Range (ACK Timing) in wireless and that it only needs to be set to 2x the farthest distance you could be from the access point. So I changed the Sensitivity Range (ACK Timing) in DD-WRT from 2000 to 50 (pretty generous for my house) and the speed went up to 117 Mb/s

---

