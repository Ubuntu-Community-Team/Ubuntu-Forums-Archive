---
title: "OpenVpn remove users from database?"
date: 2008-12-08
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-08
Ubuntu 8.04 + OpenVpn 2.1_rc7

I noticed in my syslog when I start OpenVpn that it still recognizes my original "test" users, client1 and sysadmin1.  I created/signed certificates for those users, but I deleted the certificates for them.

Why are they still being allotted ips from the pool?  Can I remove them from the db instead of adding them to a revoke list?
```

Dec  8 22:49:48 desktop ovpn-server[2804]: IFCONFIG POOL LIST
Dec  8 22:49:48 desktop ovpn-server[2804]: client1,10.8.0.4
Dec  8 22:49:48 desktop ovpn-server[2804]: sysadmin1,10.8.0.8
Dec  8 22:49:48 desktop ovpn-server[2804]: anonUserPush,10.8.0.12
Dec  8 22:49:48 desktop ovpn-server[2804]: shwickUser,10.8.0.16
Dec  8 22:49:48 desktop ovpn-server[2804]: shwickUserPush,10.8.0.20
Dec  8 22:49:48 desktop ovpn-server[2804]: anonUser,10.8.0.24
Dec  8 22:49:48 desktop ovpn-server[2804]: Initialization Sequence Completed

```

Also, I push a separate ip to shwickUserPush with a config file in the ccd directory, ifconfig-push 10.8.3.1 10.8.3.2.  Why is it still taking an ip from the server subnet?

---

### Post by samosamo on 2008-12-09
ifconfig-pool-persist setting?  clear the ipp file

---

### Post by Shwick2 on 2008-12-10
yep that did it thanks!

---

