---
title: "how can i do this"
date: 2008-10-07
forum: Server Platforms
---

### Post by nnamdi on 2008-10-07
pls a server for instance i have pc that i want to the server i have two network cards on it i will be puttin the live IP from my ISP on one then the other would a static IP or dhcp how do i bind the cards together so i could enable internet connection sharing on them cos i want to make my server a linux platform in a cafe

---

### Post by cdenley on 2008-10-07
> **nnamdi said:**
> pls a server for instance i have pc that i want to the server i have two network cards on it i will be puttin the live IP from my ISP on one then the other would a static IP or dhcp how do i bind the cards together so i could enable internet connection sharing on them cos i want to make my server a linux platform in a cafe

It sounds like you need to configure NAT routing. I think firestarter can do this for you.
```

sudo apt-get install firestarter

```
or it looks like these steps would work
[http://revsys.com/writings/quicktips/nat.html](http://revsys.com/writings/quicktips/nat.html)
If you don't want to assign ip's manually, you need a dhcp server.

---

### Post by HermanAB on 2008-10-07
Read the Advanced Routing Howto on tldp.org

Cheers,

Herman

---

