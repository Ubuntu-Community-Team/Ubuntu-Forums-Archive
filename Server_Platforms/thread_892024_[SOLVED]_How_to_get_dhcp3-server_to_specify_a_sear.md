---
title: "[SOLVED] How to get dhcp3-server to specify a search domain?"
date: 2008-08-16
forum: Server Platforms
---

### Post by jerome1232 on 2008-08-16
I couldn't figure this out from online guides or the man page.

I just got my server box running as a dhcp and dns server for my lan.
I would like the dhcp server to give my dhcp clients home.lan as a search domain so that I can be lazy and type 'server' instead of 'server.home.lan' when I connect to it. 

Any help would be appreciated.

---

### Post by StickyStyle on 2008-08-16
```
option domain-name "home.lan";
```

---

### Post by jerome1232 on 2008-08-17
Thanks I had that option set, and actually it was working, I was just testing by doing a 'dig server' and it didn't come back correctly (came back with out an answer), however later I just had the brilliant idea to test with my browser and it works using just 'server'.

---

