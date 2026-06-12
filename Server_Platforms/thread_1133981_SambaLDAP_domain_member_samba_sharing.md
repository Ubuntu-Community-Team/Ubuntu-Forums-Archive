---
title: "Samba/LDAP domain member samba sharing"
date: 2009-04-23
forum: Server Platforms
---

### Post by shizakapayou on 2009-04-23
I have a Server 8.04.2 system running Samba and OpenLDAP.  File sharing works fine from it, but on another server, also running 8.04.2, I cannot get a Samba share working.  An XP machine can see that the share is there, but when trying to connect, I get a username/password prompt, which simply doesn't do anything - no rejection or anything.  Here's what I'm seeing in the samba logs from the XP machine:

```
[2009/04/08 14:10:23, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2009/04/08 14:10:23, 0] lib/util_sock.c:send_smb(761)
  Error writing 4 bytes to client. -1. (Connection reset by peer)

```

If I do su -l username, and use the username and password I'm using on the XP machine, I can log in to the server with the problem.  Any ideas?

---

