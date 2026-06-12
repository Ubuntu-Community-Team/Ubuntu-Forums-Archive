---
title: "VPS Server connections fails everyday at 00:00:00 and 05:20:00"
date: 2013-03-25
forum: Server Platforms
---

### Post by JAMXST on 2013-03-25
Hi All, 

I got this new VPS (Ubuntu 12) and it works great. Somehow at midnight sharp and twenty past five am, the network connection fails for 30 minutes to 1 hour or 2. It happens everyday sharp. Can't find any error in log files. When connection via VNC thru my host provider everything seems ok. Low memory, low CPU usage, nothing strange. I've tring to find the problem for the last 10 days.... can't figure it out.

I could use some help.

Thanks in advanced J.A.

---

### Post by JAMXST on 2013-03-25
With a OS fresh install the connection is alright, but after installing apache, mysql and php the connections starts to fail again at the exacte same time.
There are no crons running at that time, no new processes running, there are no special consumption of memory or cpu. When connected via VPN i can check that apache web server and mysql is running as usual, file site pages can be dowloaded thru localhost, even though i cannot access them thu my ip adress or domain name.

I don't know where to look anymore. I tried everything i have in my bag of tricks already.

My hosting provider stated that there are no connections issues on their side, they also checked my system and sated that aparently everything is ok , mas somehow, at midnight GTM and 5:20 am the connections fails.

Even changed the system time, and the connection keeps failing at the same exact time. Do not changed along with the system and hardware time. In those periods i'm unable to http, ftp, ssh, ping or traceroute the server.

Please, help.

Best Regards, J.A.

---

