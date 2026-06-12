---
title: "[SOLVED] about ktorrent and azureus"
date: 2008-04-27
forum: The Cafe
---

### Post by robertchahine on 2008-04-27
i used to share my file and download my torrents with azureus.But i have a router, so sometimes there's some NAT errors or something like that.When i used ktorrent , i find it faster and better, but when i use ktorrent ,browsing become slower than when i use azureus.
can somebody tell me why or how to fix this ?

---

### Post by kodoku on 2008-04-27
> **robertchahine said:**
> i used to share my file and download my torrents with azureus.But i have a router, so sometimes there's some NAT errors or something like that.When i used ktorrent , i find it faster and better, but when i use ktorrent ,browsing become slower than when i use azureus.
can somebody tell me why or how to fix this ?

The NAT error can be fixed by forwarding the specific ports that you have configured azureus or ktorrent to use to listen for incoming connections.  This is usually done through the control panel of your specific router. It should be something labeled with "Port Forwarding" or something.  Enable a range of ports, like 31424-31463, and then set azureus or ktorrent to use the ports in that range.

The slow browsing thing is probably caused by ktorrent overloading your bandwidth. Because it can punch through the NAT (I'm guessing), it is maxing out your connection capacity. First make sure you are not maxing out your upload capacity.  Limit your upload speed to ~70% of your max upload speed.  If necessary, you could also lower the number of connections to something like 120, also done in preferences.

Hope that helps.

---

### Post by NightwishFan on 2008-04-27
Just limit your speeds to something acceptable to your connection, it is easy with ktorrent, just find it under configure.

---

### Post by stoeptegel on 2008-04-29
Try lowering the maximum number of connection setups, 10 should be a safe number. See whether this had some effect.

---

### Post by robertchahine on 2008-05-02
thanks guys for your replies.
In fact, the number of connection per torrent was 120 by default. So i change it to 50 (like the azureus configuration).And in the terminal i allowed the port 6881 to download and upload. everything seems to be ok and fine.When i'm browsing i limit the download speed to 10 Kb/s . but when i'm free i turn it again to unlimited.

---

### Post by renzokuken on 2008-05-02
try not to use 6881, go higher to about 50000 or more, some ISPs throttle that port

---

### Post by robertchahine on 2008-05-02
ok man, i will try that now to see if there any difference

---

### Post by renzokuken on 2008-05-02
its also a good idea to change it every so often, i change mine every couple of weeks. some clients have a setting for randomising it which works well if your client and router support uPnP

---

### Post by robertchahine on 2008-05-02
i will try that man ;) thanks

---

