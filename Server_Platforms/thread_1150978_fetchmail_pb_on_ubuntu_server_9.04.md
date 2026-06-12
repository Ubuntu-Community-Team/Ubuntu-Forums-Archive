---
title: "fetchmail pb on ubuntu server 9.04"
date: 2009-05-06
forum: Server Platforms
---

### Post by doudoufr on 2009-05-06
Hi everybody
First of all, sorry for my english or if i'm not clear, because i'm french....:P

I've installed an email server with ubuntu 9.04, postfix, amavis, spamassassin, clamav and zarafa. 

i've got an external email account which I retrieve with fetchmail

when I chek the log with logcheck i see this line : 

```
kernel: [21101.576585] TCP(fetchmail:4217): Application bug, race in MSG_PEEK.
```

what does it mean ? there is a bug in fetchmail ?


Also i've got this one : 
```
May  5 22:52:59 blablabox fetchmail[21275]: Connexion failed with localhost:smtp [::1/25] : Connexion refused.
```

I don't know what it means. I searched google, and the only thing I found is that fetchmail doesn't find a mail server....!!! (not my case i've got one => postfix)...so I don't know !

and the last one I can't explained
```
type=1503 audit(1241607729.224:13): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=113 name="/var/lib/amavis/amavis-20090506T130209-03276/parts/" pid=31128 profile="/usr/sbin/clamd"
```

Also googleized this one but...the only thing I found is to swith to debian.....:confused:

So someone could help me please ? thannnnks !

---

### Post by doudoufr on 2009-05-07
up ?

---

