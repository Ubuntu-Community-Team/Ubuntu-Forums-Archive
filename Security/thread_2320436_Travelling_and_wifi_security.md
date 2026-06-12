---
title: "Travelling and wifi security ?"
date: 2016-04-14
forum: Security
---

### Post by oygle on 2016-04-14
Travelling here and there and most places have free wifi. They give out a username and pwd. When at home I'm behind a router/firewall (NAT), but when using other peoples wifi, is there some extra security I can run for the wifi connection ?

ufw is currently active.

---

### Post by kurt18947 on 2016-04-14
What do you want to do while traveling? Basic browsing & webmail or more? If you have a wifi adapter that's 'plug & play', you could use a live install on a flash drive. When you get home, nuke and reimage the flash drive. Any nasties picked up along the way should disappear. Another option would be to create or clone a separate partition on your hard drive. Same deal - use the temporary partition while connecting to untrusted networks and nuke it when you get home. Enabling the firewall included in most distros is painless but I'm not sure it's as effective as an isolated partition.

---

### Post by oygle on 2016-04-14
Basically browsing and web mail. But I may have to do internet banking or login to a cpanel side of a website. All these are "https" connection. 

The wifi is built in to the laptop. I do have an external hard drive with me, so did wonder if there was an easy way to ..

* No internet traffic at all to hard drive
* allow internet traffic to the external. (then as you say, wipe the external when I get home).

I have GUFW running, enabled, full logging, incoming deny, outgoing allow.

Thanks  :)

---

### Post by howefield on 2016-04-14
Thread moved to the "*Security*" forum as requested.

---

### Post by oygle on 2016-04-14
> **howefield said:**
> Thread moved to the "*Security*" forum as requested.

Thanks :)

---

### Post by sherman-dougherty on 2016-04-25
Why not use a VPN service or set up your own ssh server to tunnel to for Internet access while away? VPN is my go to, but if at all possible I avoid public wi-fi. I'd rather use my iPad Air and VPN over the cellular network than public wi-fi on a 'real machine'. Too many ways to get past my VPN if you're an advanced hacker and my machine is up too long.

---

### Post by sammiev on 2016-04-25
I travel a lot and use a VPN service for many years now.

So far, so good.

---

### Post by kurt18947 on 2016-04-26
"But I may have to do internet banking or login to a cpanel side of a website. All these are "https" connection."

If it were me, I'd pay for a VPN provider or set one up myself for those functions. There have been enough https/TLS issues that I wouldn't trust only that on a public wifi connection. I try to avoid logging onto sensitive sites from public internet connections and have been successful so far. I don't worry much about web browsing and email.

---

### Post by bashiergui on 2016-04-26
> **oygle said:**
> Basically browsing and web mail. But I may have to do internet banking or login to a cpanel side of a website. All these are "https" connection. 
Our wireless devices, by default, constantly try to connect to the last networks they were on. To accomplish this they actively scan their neighborhood by sending out probe requests. Your computer says "I'm looking for AT&T Wifi." A bad guy can easily intercept these requests and respond "I'm AT&T Wifi." Your computer will join and it will look like normal internet traffic to you. But a bad guy will actually be seeing everything you're doing, and probably stripping ssl so that https connections are not encrypted anymore.


The way to protect yourself is to use a VPN like everyone said and make sure you're connecting to a legitimate wifi. Don't automatically join networks and occasionally delete old networks.

---

### Post by HermanAB on 2016-04-27
Tor is useful when you are in strange places.

BTW, the computers do not send scan messages looking for WiFi hot spots.  The WiFi hot spots broadcast their SSID every so often - that is what your computer picks up.  However, anyone can pretend to be anyone else and it is very easy to set up fake hot spots.

---

### Post by DuckHook on 2016-04-27
> **HermanAB said:**
> ...it is very easy to set up fake hot spots.+1

Crackers routinely do this using nothing more than their laptops.

@OP That guy sitting across from you at Starbucks could be running one right now, and if he was good at it, you would never know. That banking site he is spoofing could look just like yours.

As others have said, VPN.

---

### Post by bashiergui on 2016-04-27
> **HermanAB said:**
> Tor is useful when you are in strange places.
What security advantages does that offer?

---

### Post by atl45 on 2016-05-30
For open wi-fi, taking into account what you've said you would use it for, I honestly think the simplest option is to use a Live OS with Tor (most obvious example being Tails (Debian-based). Any novice can learn how to install Tails on a USB in a short time and you don't have to go through the hassle of learning how to configure things properly. From there, you may wish to install a persistent volume on the same USB, if you need one. Ensure you familiarize yourself with the various security precautions for using Tails.

---

