---
title: "Sharing folder to XBMC on Xbox"
date: 2011-04-03
forum: Server Platforms
---

### Post by fizgig on 2011-04-03
So I've had this working forever.  I just moved and now I'm having problems.  I have an ubuntu server sharing a directory with user permissions.

I can easily browse the share from my XP computer after I type in the username of "xbox" and pw of "xbox".  I can browse around with no trouble.

Thing is, I can't get to my server from the xbox.  I'm using IP addressing to do this instead of dns or netbios.  It should be really simple.  I keep getting the "lock preferences" screen on xbmc on the xbox.

The samba log says:

```
[2011/04/03 10:18:20,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/04/03 10:18:20,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```


I have found countless posts about the "lock preferences" screen but they all seem to relate to folders shared on Windows and changing to "simple file sharing" to fix.  I don't have that option with Ubuntu so I'm stuck.

---

### Post by fizgig on 2011-04-03
Turned out to be the new network setup.

I added the actual IP address of the server to the /etc/hosts file.  Not only does it work now, the sudo command works faster.

---

