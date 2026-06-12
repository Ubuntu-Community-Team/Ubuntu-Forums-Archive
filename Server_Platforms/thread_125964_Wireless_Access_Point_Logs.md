---
title: "Wireless Access Point Logs"
date: 2006-02-05
forum: Server Platforms
---

### Post by lexor on 2006-02-05
I am getting a request for wireless access from a neighbours wireless network card on average about 5 times every second it usally gos on for days at a time.

I dont really know what to make of it, it may be one of the two listed.

1) I know you can set up your wireless card to seek and access any wireless access point untill it gets a connection so thats whats happening ?

2) My wireless access point is getting some kinda brute force attack ?

The wireless access point has mac address filtering so only know macs get a access and the get a know IP cause DHCP is turned off. ( Easy To Spoof)

Its got WPA-PSK TKIP security with a very long password, so its as secure as it can be. ( Not Easy To Spoof)

So is it just that the neighbours wireless network card is setup wrong or is it a brute force attack.

---

### Post by ubernoob on 2006-02-10
he has probably set up his network card wrong. What does the log say? If you are tired of the messages, you can probably change the level of reporting to the log. From informational to critical or something similar.

---

### Post by lexor on 2006-02-12
Sure its called roaming, the wireless card keeps searching for access untill it gets it. I got a Sitecom WL-133 USB Adapter and it does this as I noticed the MAC address in the router logs.

Its an annoying feature if you ask me :)

---

### Post by towsonu2003 on 2006-02-13
let her/him log in for a while and monitor actions via ethereal. you'll understand whether s/he is intentionally trying to hack (visit "bad" sites, or log on to ip adresses that looks weird etc) or just dont know about it (trying to log on to yahoo/gmail/hotmail/other account on a wireless network). if s/he visits a bad site, keep the log and further secure your wireless. may be s/he is just trying to get a kernel update (big download) with sources for his/her ubuntu? ;)

---

