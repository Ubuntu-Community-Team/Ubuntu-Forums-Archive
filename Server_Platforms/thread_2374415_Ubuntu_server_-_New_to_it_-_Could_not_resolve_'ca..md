---
title: "Ubuntu server - New to it - Could not resolve 'ca.archive.ubuntu.com'"
date: 2017-10-15
forum: Server Platforms
---

### Post by charles-laferriere on 2017-10-15
A fresh ubuntu server install on my old pc. Trying to build a webserver from home, obviously ;)

So.

I can'get even get through the first step: sudo apt-get update. 
I get a message that : Could not resolve ca.archive.ubuntu.com


Here is what I've tried so far:

- add mirror servers to the /etc/apt/ sources.list file

- change the name server to google dns 8.8.8.8 in /etc/ resolv.conf


Now I'm clueless.
Thanks, Merci, Danke.

---

### Post by charles-laferriere on 2017-10-16
It should be noted that
sudo lshw -c network 
shows 

"*" -- where there's supposed to be eth0, en0, wlan0, etc. 
It seems that the network was not created upon installation.


cat /etc/network/interfaces results with
auto lo
iface lo inet loopback

That's it. 
No subsequent section.

---

### Post by darkod on 2017-10-16
Correct. The network doesn't seem to have been created.

Do you know which model chipset you have for the wired network? Try getting more details with:
```
lspci
```

That will list all PCI/PCI-E devices and the network should be among them.

---

### Post by charles-laferriere on 2017-10-16
Well since it was my first install, i ... reinstalled it, with an ethernet cable plugged in and selected it as my main network adapter.
The internet is now fine, through the ethernet cable at least.
Since it's going to be a server, I won't bother with wifi.
Ethernet controller: Intel corp 82577LM gigabit network Connection (rev 05)
Network controller: Broadcom Limited BCM423224 802.11a/b/g/n (rev 01)

---

### Post by darkod on 2017-10-16
OK, great.

FYI, you should always install with the cable plugged in and setting up the network. Because during the install it sets up more things, not just the network adapter. For example it sets up apt, etc.

Please mark the thread as solved, you can do that in Thread Tools above the first post.

---

### Post by charles-laferriere on 2017-10-17
All right, thanks

Solved. 
(Incoming! MOAR PROBLEMS!)

---

