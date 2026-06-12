---
title: "VPN + PPTP wants wireless, but should have wired"
date: 2011-10-27
forum: Server Platforms
---

### Post by andvik on 2011-10-27
Hi! 
I am trying to set up a VPN for transmission according to [http://ubuntuforums.org/showthread.php?t=1472045](http://ubuntuforums.org/showthread.php?t=1472045) 
All goes well, except for that it wants to use my wireless connection rather than wired, which it is supposed to use as I dont use the wireless. Been trying a few different things like adding "/dev/net/tun" to /etc/ppp/peers/ipredator's second line or adding it manually by

pon ipredator /dev/net/tun

But then I get an error-message 

/usr/sbin/pppd: pty option precludes specifying device name

Anyone got a sollution for me? I am rather bad at linux in general, so be gentle.

Thanks

---

