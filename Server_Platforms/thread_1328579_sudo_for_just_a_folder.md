---
title: "sudo for just a folder"
date: 2009-11-16
forum: Server Platforms
---

### Post by xkaliburx on 2009-11-16
Afternoon all ....

We have a dev server that some outside people are working on.  Most of their work they can do as user X, but one thing involves restarting a service that only root can do.

So, I am wondering in the sudoer's file, can you say this user can sudo ONLY to folder X?

Trying to read the doc's/man page, but usually get better results consulting the forum.

Tnx

---

### Post by scorp123 on 2009-11-16
You can add a certain username or a group and then let them execute certain things ... without password if you want.

Example from my own system:

```
# Members of admin group may open VPN's via tuncfg
%admin ALL=NOPASSWD: /sbin/tuncfg

# Same for Hamachi users here:
%hamachi ALL=NOPASSWD: /sbin/tuncfg

# OpenVPN for John
john	ALL=NOPASSWD: /usr/sbin/openvpn --config /etc/openvpn/customers/client.conf
```

So the result here is that these people and groups may execute above commands --and _ONLY_ exactly above commands-- without being asked a password.

John above can even open VPN tunnels ... but only if he triggers the command exactly as above.

I guess this is what you want?

---

### Post by xkaliburx on 2009-11-16
"guess", it was right on the head.  Reading all the command alias stuff, etc. all solved with one clean real-life example!

Thanks a lot!

---

