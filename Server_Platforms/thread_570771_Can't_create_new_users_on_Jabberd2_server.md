---
title: "Can't create new users on Jabberd2 server"
date: 2007-10-08
forum: Server Platforms
---

### Post by emil.s on 2007-10-08
I have installled Jabberd2. It seems to work... But when i try to create a new user from some client (Gabber / Pidgin) i get the message "Host Gone".

And the c2s log says:
```
Mon Oct  8 23:52:06 2007 [notice] shutting down
Mon Oct  8 23:52:07 2007 [notice] starting up
Mon Oct  8 23:52:07 2007 [info] process id is 6602, written to /var/run/jabberd2/c2s.pid
Mon Oct  8 23:52:07 2007 [notice] initialised auth module 'mysql'
Mon Oct  8 23:52:07 2007 [notice] [domain.xx] configured; realm=(null)
Mon Oct  8 23:52:07 2007 [notice] attempting connection to router at 127.0.0.1, port=5347
Mon Oct  8 23:52:07 2007 [notice] connection to router established
Mon Oct  8 23:52:07 2007 [notice] [0.0.0.0, port=5222] listening for connections
Mon Oct  8 23:52:07 2007 [notice] ready for connections
Mon Oct  8 22:00:24 2007 [notice] [7] [127.0.0.1, port=49761] connect
Mon Oct  8 22:00:24 2007 [notice] [7] [127.0.0.1, port=49761] disconnect
```

Note the two last lines...

Does anyone have a solution for this?

---

### Post by darkpixel on 2008-02-02
> **emil.s said:**
> I have installled Jabberd2. It seems to work... But when i try to create a new user from some client (Gabber / Pidgin) i get the message "Host Gone".

Does anyone have a solution for this?

Sorry for a late reply, but I ran across your post while I was having the same issue.

I removed the cachain element from the c2s.xml file and the issue resolved itself.

---

