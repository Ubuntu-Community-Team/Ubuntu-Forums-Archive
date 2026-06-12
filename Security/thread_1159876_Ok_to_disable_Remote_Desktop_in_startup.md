---
title: "Ok to disable Remote Desktop in startup?"
date: 2009-05-15
forum: Security
---

### Post by risingsun on 2009-05-15
Hi, quick question, but I noticed that remote desktop was selected amongst the startup applications. Since it's effectively disabled in the config anyway for no access (i.e. the default value I think) is it safe to turn it off in the startup applications since I'm not aware of any reason that needs it to be turned on.

I think it's been that way since I reinstalled my machine since I presume that's how it is by default (i.e. loads on startup but config disables any connections) and I didn't know about it till recently anyway, but I'd prefer it off since the fewer attack vectors the better (though as it is currently is secure anyway by default, correct?)

Many thanks :)

---

### Post by cariboo on 2009-05-15
You can disable it, but in a default installation there is nothing listening on any ports that are accessable from another computer, so disabling it shouldn't make any difference. 

This is the output of nmap localhost on a 2 day old install of Karmic Koala:

```
nmap localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2009-05-15 11:40 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds
```

---

