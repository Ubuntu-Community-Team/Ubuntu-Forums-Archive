---
title: "ufw doesn't seem to like NFS"
date: 2008-05-19
forum: Server Platforms
---

### Post by sq377 on 2008-05-19
I have an NFS server running on my server, and it functions perfectly without using ufw.

UFW Rules:
```
111:tcp                    ALLOW   Anywhere
111:udp                    ALLOW   Anywhere
2049:tcp                   ALLOW   Anywhere
2049:udp                   ALLOW   Anywhere
32771:tcp                  ALLOW   Anywhere
32771:udp                  ALLOW   Anywhere

```

nmap from laptop (ufw enabled):
```
PORT      STATE  SERVICE
111/tcp   open   rpcbind
2049/tcp  open   nfs
32771/tcp closed sometimes-rpc5
```
It would seem the problem is the 32771 port isn't being forwarded correctly, does anyone have any idea what I can do to fix this?  I would like to stick with ufw if possible.

---

