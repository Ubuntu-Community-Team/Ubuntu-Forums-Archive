---
title: "chkrootkit"
date: 2009-04-30
forum: Security
---

### Post by matt1987 on 2009-04-30
hello i just ran chkrootkit for the first time on 9.04 and found something interesting in the log...

```
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[2880], /sbin/dhclient3[3593])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
```

does this mean i have a sniffer on my wireless? and if so what can i do about it? thanks!

---

### Post by brian_p on 2009-04-30
> **matt1987 said:**
> 

does this mean i have a sniffer on my wireless? and if so what can i do about it? thanks!

Definitely not. But it does mean you have installed a useless bit of software.

Google: "chkrootkit PACKET SNIFFER".

---

### Post by matt1987 on 2009-04-30
> **brian_p said:**
> Definitely not. But it does mean you have installed a useless bit of software.

Google: "chkrootkit PACKET SNIFFER".

ok thanks!! i was getting worried for a sec heh.

---

### Post by HermanAB on 2009-05-01
Hmm, it seems that large numbers of Ubuntu users play with chrootkit.  Why, I dunno.  It doesn't actually work.  It may have been useful many years ago, but not anymore.  

Anyhoo, I have been using UNIX systems since about 1985 and I still haven't encountered a root kit that I haven't installed myself...

---

