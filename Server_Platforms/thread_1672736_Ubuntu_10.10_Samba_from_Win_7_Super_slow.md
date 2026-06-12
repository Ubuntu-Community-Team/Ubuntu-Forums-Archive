---
title: "Ubuntu 10.10 Samba from Win 7 Super slow"
date: 2011-01-21
forum: Server Platforms
---

### Post by killer50stang on 2011-01-21
This was working flawless before I updated to 10.10. Now it's so slow I might as well use a thumb drive instead of the network. I see this in some of the logs:

```
lib/util_sock.c:get_peer_addr_internal(1607)
smbd[1034]: getpeername failed. Error was Transport endpoint is not
connected
smbd[1034]: read_socket_with_timeout: client 0.0.0.0 read error =
Connection reset by peer. 
```

Any ideas?

---

### Post by elico on 2011-01-21
what do you mean works slow?
the pear getname?

there is a bug that makes samba \mdns in ubnutu 10 to wrok slow.. nsswitch,conf look up for it.
but still dont understand your problem..

---

### Post by sentinelace on 2011-01-21
When I try to browse a share that has been created by samba from a windows client, it either hangs my pc or comes up after like 5minutes which is crazy.  hopefully that makes sense.

---

### Post by sentinelace on 2011-01-26
It seems to do this in XP pc's too.  Anyone?

---

### Post by sentinelace on 2011-02-09
Okay, tested windows 2000 and it works like it should.  I'm lost but I need this fixed.  Now the other weird thing is ubuntu 7.04 samba on my other server is working fine.

---

