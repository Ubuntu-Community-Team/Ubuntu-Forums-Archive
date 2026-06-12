---
title: "Mobile broadband and ufw"
date: 2010-10-14
forum: Security
---

### Post by danbojan on 2010-10-14
I'm trying a mobile broadband internet connection and I have a few questions. After I installed Ubuntu, I went to grc.com and scanned my system and it came out stealth before I enabled the ufw firewall? I was puzzled and have been trying to figure out why. I was hoping someone could explain it. From what I've been able to gather, when you connect with mobile broadband you actually connect to your providers network and they assign you a APN. So, instead of getting your ip address, a website would get the APN instead or maybe the providers ip address? (I'm not sure how that works), and everything would go through the providers network, which is already firewalled? Is this right? If so, that would explain the stealth scan from grc.com. I still would like to have a personal firewall on my machine to protect it from my providers network or if I use a wireless connection, which leads me to my next questions about ufw.
 First, can someone confrim that the default settings for ufw are deny for incoming(that's what I want)? I just did #sudo ufw enable. Do I need to do #sudo ufw default deny? Also, does ufw work by default on interfaces other than eth0, like wlan0, or ppp0, or do I need to change the configuration, if so, how? Thanks

---

### Post by cariboo on 2010-10-15
Shields Up only scans up to port 1055, on a default Ubuntu install there is nothing open to respond to the request that shields up makes. Another thing to keep in mind, is that if you are behind a router, Shields Up is checking your router, not your computer.

Web browsers use random high ports to connect to web sites, so you'll never see any ports open with a regular port scan.

```
sudo ufw enable
```

is good enough for most people, unless you start running servers. You can check to see if the rules are working, by running nmap from another computer on your internal network.

---

