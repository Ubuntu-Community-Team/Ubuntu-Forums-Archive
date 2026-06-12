---
title: "Some ports on my router's LAN interface are open"
date: 2020-04-27
forum: Security
---

### Post by linuxyogi on 2020-04-27
```
$ nmap 192.168.225.1
Starting Nmap 7.70 ( https://nmap.org ) at 2020-04-27 17:10 IST
Nmap scan report for embms.jio.local (192.168.225.1)
Host is up (0.014s latency).
Not shown: 995 closed ports
PORT     STATE    SERVICE
53/tcp   filtered domain
80/tcp   open     http
5555/tcp filtered freeciv
6666/tcp open     irc
7777/tcp open     cbt

Nmap done: 1 IP address (1 host up) scanned in 1.36 seconds

```

This is not the WAN side. Its the IP of my router AKA default gateway.

I tested my router on grc.com and it passed the test.

Should I be worried ?

---

### Post by EuclideanCoffee on 2020-04-27
Do not worry.

Try closing these ports and check your router for a few days. See if they reopen. If they reopen, you have a problem and should contact whoever administrates your router. If it is you, you may need to get a new router or ISP.

---

