---
title: "problem in root and NomCourt of sshserver"
date: 2009-04-16
forum: Server Platforms
---

### Post by bnejoker on 2009-04-16
helo 
i have 2 probleme with my sshserver,
1-first 
when i put this command in terminal:
```

root@nedjemeddine-desktop:~# ssh 192.168.1.2
ssh: connect to host 192.168.1.2 port 22: No route to host
root@nedjemeddine-desktop:~# 

```
2-and the second probleme is:
when i put these command in terminal:
```

username@username-desktop:~$ ssh NomCourt
ssh: Could not resolve hostname myhost.com: Name or service not known

``` 
please someone tell me what's this .....
and thank's.

---

### Post by Bachstelze on 2009-04-16
None of these problems is related to SSH, it's your network connectivity that's the problem. Basically, 1) means that your machine can't connect to 192.168.1.2, and 2) means that you are trying to access a hostname that doesn't exist.

---

