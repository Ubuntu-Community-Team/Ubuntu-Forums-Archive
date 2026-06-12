---
title: "Can't log in/connect from outside"
date: 2009-05-28
forum: Server Platforms
---

### Post by brown_ghost on 2009-05-28
I just install a fresh copy of Ubuntu 9.04, I have 3 network cards because I have two separate networks in my office (1.Internet 2. Intranet & 3rd card is for static ip. I have setup all cards successfully & I'm able to go online & get new updates (through static ip only) & I have added proftpd. Well I have 2 offices I can log in remote to test proftpd but I'm unable to log in, I can't ping it or log in through ssh either (on static ip only). I have unplugged the other two cards leaving the static ip so I can ping it and log in through ssh from one of my pcs in my office from the separate network going out to the static ip. I have rebooted and everything comes up good, I have also restarted the proftpd and it's up, does anyone know why I can't see it from out side my office? oh one more thing, all 3 offices are connected via vpn so I'm able to ping and log in through ssh to the card on that network but not on static ip card.

---

### Post by FarehamWeather on 2009-05-28
have you opened port 22 on the firewall that protect the network from the internet?

---

