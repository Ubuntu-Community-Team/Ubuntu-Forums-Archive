---
title: "port forwarding while daemon not listening"
date: 2014-12-22
forum: Security
---

### Post by r.stiltskin on 2014-12-22
If I have my router configured to forward port 873 to a particular attached host while rsyncd is not running on that host, does this create a security risk that I should worry about?  I don't know of any other programs listening on that port -- certainly nothing that I've set up.

---

### Post by CharlesA on 2014-12-22
If nothing is listening, how would it allow a connection?

FWIW, I white list whatever IPs I connect from so I don't have ports exposed to the entire internet. It's easier to manage for me.

---

### Post by r.stiltskin on 2014-12-22
> **CharlesA said:**
> If nothing is listening, how would it allow a connection?

Thanks. That was my understanding but I figured it wouldn't hurt to hear other points of view since I don't know what I don't know.  ;)

I've considered whitelisting but worried that I might someday need access from some odd location so settled for blacklisting most of the world instead.  Understanding of course that it still leaves a lot of potential bad guys.

---

### Post by CharlesA on 2014-12-23
I whitelist a few of the IPs I connect from regularly and use a VPN if I am on the road.

---

