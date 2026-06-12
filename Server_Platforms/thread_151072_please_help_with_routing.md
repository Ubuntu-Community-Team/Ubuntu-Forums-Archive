---
title: "please help with routing"
date: 2006-03-27
forum: Server Platforms
---

### Post by LordMerlin on 2006-03-27
Hello everyone!

So, I setup Linux as a PDC, DHCP, caching DNS server, and want it to route internet traffic for the LAN

My setup is as follows:


iBurst Modem (pppoe connection - get's IP from ISP - 196.2.108.xxx)
              |
              |
              |
eth0 (192.168.0.2) 
              ||
Linux box
              ||
eth2 (192.168.10.1 - running DHCP)
              |
              |
              |
24 port hub
          |              |                |                   |     |
XP PC 1         XP PC 2      XP PC 3        etc etc

The XP PC's can ping 192.168.10.1 & 192.168.0.1, but not 196.2.108.xxx, nor for example google.com. I tried running 
"iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE", but that doesn't seem todo anyting. In fact, I followed the [** Howto Share internet connection**]("http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+sharing")

Can somone please assit me with this?

---

