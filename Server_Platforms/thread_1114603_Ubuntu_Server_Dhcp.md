---
title: "Ubuntu Server Dhcp"
date: 2009-04-02
forum: Server Platforms
---

### Post by MikeyPooh on 2009-04-02
i have a Question, I Am Trying to get Dhcp working and i am wondering, I was always setting the hosts File as follws

127.0.0.1 localhost.localdomain  localhost
192.168.1.0  gatekeeper.wow-stargate.net    gatekeeper

is this the correct way to set this file up or should it be as follws

127.0.0.1 localhost.localdomain    localhost
192.168.1.1 gatekeeper.wow-stargate.net   gatekeeper


Thanks

Mike

---

### Post by bluefrog on 2009-04-03
second.

you can't use 0 and 255 to end an IP address

---

### Post by Iowan on 2009-04-03
192.168.1.1 would be better - you might also see if it works with ```
127.0.1.1 gatekeeper.wow-stargate.net gatekeeper
```

---

