---
title: "Low bandwidth left - Where does it go ! Monitor by IP?"
date: 2012-02-13
forum: Server Platforms
---

### Post by dudumomo on 2012-02-13
Hi there,

I am a mirror of several Free project (Sabayon beeing the biggest) and since yesterday my server is overloaded as a bandwidth point of view.

I have a lot of apache processes from port 80 and a lot of different IPs (From different countries) dowloading something somewhere from my server.

Based on iftop, I am in fact saturating my bandwidth.

Thus, I am wondering if it is possible to know what these IP are downloading.

Did I Rsync the latest movie of Universal? Haha.

Thank you for your help

---

### Post by raja.genupula on 2012-02-13
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

may be that could help you. :)

EDIT : [http://www.ihaveapc.com/2011/07/how-to-quickly-monitor-ip-traffic-from-terminal-in-linux-mint-ubuntu/](http://www.ihaveapc.com/2011/07/how-to-quickly-monitor-ip-traffic-from-terminal-in-linux-mint-ubuntu/)

---

### Post by dudumomo on 2012-02-13
I'm using IFTOP (Works great to know the consumption)
But no detail about the URL/Folder being reached.

However a friend just help me.
Need to use apachetop -f /my/log/access.log

Works great !

---

