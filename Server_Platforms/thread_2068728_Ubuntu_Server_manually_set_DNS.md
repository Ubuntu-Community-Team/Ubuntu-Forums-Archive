---
title: "Ubuntu Server manually set DNS"
date: 2012-10-09
forum: Server Platforms
---

### Post by wh33t on 2012-10-09
Hey Ubuforums,

Quick question here. I have a ubuntu server up and running with a static IP address, no issues there. The problem I'm having is that whenever I reboot the machine it seems to lose it's DNS settings. I can set the DNS settings manually by doing a sudo nano /etc/resolv.conf and manually adding in "nameserver 192.168.1.254" and then DNS begins to work, but for some reason I lose this configuration upon reboot. 

How do I get around this?

---

### Post by Doug S on 2012-10-09
Add the DNS addresses to your /etc/network/interfaces file.
There is an example in the 12.04 server guide [here]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution").

---

### Post by wh33t on 2012-10-09
> **Doug S said:**
> Add the DNS addresses to your /etc/network/interfaces file.
There is an example in the 12.04 server guide [here]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution").

Thank you. I'll check that out.

---

