---
title: "Ubuntu Server Automatically Inserts a Reject Route to the Routing Table"
date: 2009-02-13
forum: Server Platforms
---

### Post by downhillgames on 2009-02-13
Heya folks here at the Ubuntu Forums,

How is everyone? My server here (which is in a VM) is doing just dandy except that every time something "new" enters the LAN and tries to access the server, the server will automatically insert a reject route to the routing table and add an entry to /etc/hosts.deny. Does anybody have ANY idea what mechanism could be responsible for this so that I may purge it with the fires of Hell?

EDIT: Oh yeah, btw, it's running 8.04.2. :)

Thanks in advance,
"Downhill Games"

PS: Here are samples of the offending portions of the routing table, and of /etc/hosts.deny:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.106        -               255.255.255.255 !H    0      -        0 -
luserhostname        -               255.255.255.255 !H    0      -        0 -

```
```

ALL: 192.168.0.106 : DENY

```

---

### Post by Dr Small on 2009-02-13
Are you running Denyhosts or Fail2ban?

---

### Post by downhillgames on 2009-02-13
Nope.

Ah hah! Portsentry was configured to be a bit overzealous about what it banned :) The only thing I know of that's running on the LAN are samba daemons, so that's probably the cause. Gonna look into it more tonight.

Yep, changing the lines in the portsentry config fixed it. Thanks for the hint. Forgot PS was installed :)

---

