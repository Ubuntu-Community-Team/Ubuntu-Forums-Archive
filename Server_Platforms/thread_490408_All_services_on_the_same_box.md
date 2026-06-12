---
title: "All services on the same box"
date: 2007-07-02
forum: Server Platforms
---

### Post by DDuong on 2007-07-02
Hello everyone!

I was just wondering if it's secure/recommended to put the following on the same box:

Firewall
DNS
Postfix
MySQL
etc

I have a feeling it's not a good idea since it can be a security hazard since everything is setup on the same box, but I would like to conserve energy and not run 3-4 boxes (I love the earth) ;)

Thanks,

David

---

### Post by duckmannz on 2007-07-02
It's fine as long as you observe simple security such as the services only listening on the interfaces that they need to (e.g. localhost for mysql) and secure other services such as SMTP, SSH etc.

---

### Post by nix4me on 2007-07-02
I wouldn't.  It's my opinion that firewall/router should be standalone.  Then everything else behind it.

nix4me

---

### Post by DDuong on 2007-07-02
Thanks all for the input!

---

