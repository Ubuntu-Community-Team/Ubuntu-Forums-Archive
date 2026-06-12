---
title: "Firestarter and Webmin Bandwidth Monitor"
date: 2010-01-07
forum: Server Platforms
---

### Post by olki on 2010-01-07
Hello,

I'm new to Ubuntu and I'm installing a server to act as a firewall between a local network and internet.

I've installed Firestarter becaused it worked straitgh away (it seems that FS is configuring the routing as well). I've tried to remove it, and then I lost the access from LAN to Internet. (I don't know why -perhaps the routing is disabled then- , so I prefer to keep it). 

The problem is that Webmin Bandwidth Monitor (bandwidthd) is not logging anything when FS is active. Does someone has an idea on how I could make it work?

PS: I've tried cacti and some other stuff, but it is far too complicated for me.

Thank you very much.

---

### Post by nimrodwebdesign on 2010-03-30
From what I understand *FireStarter* is just a GUI for *iptables*. 

Webmin puts bandwidth logging rules into *iptables*.

I suspect therefore that *FireStarter* is removing or blocking those logging rules.

You may find you need to add them manually through *FireStarter*.


I hope that puts you in the right direction (if you are still looking for an answer).

---

### Post by spynappels on 2010-03-30
You can also use Webmin to configure the Firewall, and doing it this way makes it really intuitive, much better than UFW. I've never used Firestarter, so cannot comment on that, but using Webmin, the firewall setup is dead easy.

---

