---
title: "ufw and shoutcast"
date: 2015-06-23
forum: Security
---

### Post by nicky5 on 2015-06-23
I am using UFW firewall to block all the ports and only enabled port 22, 80 and 9384 port for shoutcast radio. Port 80 works all fine and I can browse webpages. I also can login to ssh on port 22. However, for shoutcast, it doesn't work. When I try to connect to shoutcast using SAM broadcast on port 9384 it doesn't connect. If I disable UFW then SAM easily connects to shoutcast server.


Is there any setting that I need to change?


Enabled port using:
```
sudo ufw allow 9384/tcp




To                         Action      From
--                         ------      ----
9384/tcp                   ALLOW       Anywhere
9384/tcp (v6)              ALLOW       Anywhere (v6)
```




```
netstat -alpn | grep :9384


tcp        0      0 0.0.0.0:9384            0.0.0.0:*               LISTEN      18235/sc_serv
```

I can access the shoutcast server web panel though.

---

### Post by bashiergui on 2015-06-23
Connect to shoutcast and then look at your ufw logs to see what ports are getting blocked. Then open thise up on your firewall.

---

### Post by nicky5 on 2015-06-23
> **bashiergui said:**
> Connect to shoutcast and then look at your ufw logs to see what ports are getting blocked. Then open thise up on your firewall.

Thanks for a quick tip. I noticed that for Shoutcast, you need to open two ports ([COLOR=#000000][FONT=Ubuntu Mono]9384 and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]9385[/FONT][/COLOR]) not just one.

---

