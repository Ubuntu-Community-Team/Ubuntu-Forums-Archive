---
title: "networking problem?"
date: 2009-04-20
forum: Server Platforms
---

### Post by mstrap123 on 2009-04-20
i recently successfully setup a samba server using 8.04. i can mount/access the samba share from window xp, however the connection to the server keep disconnecting i even tried connect using putty and it return msg connection refused. i tried restart samba and it can connect again. then after a while it cannot connect again. wat is the cause for this is it the network that causing this?

---

### Post by silbro on 2009-04-20
if the server sais connection refused it means you dont have ssh installed on the server. Try to ping the server for a while and also from the server and see if you already lose packets there.

edit:
did you try using another switch ? another port on the switch? (if you have one that is ;) )

---

### Post by mstrap123 on 2009-04-20
i have already installed ssh on the server. i can log in using putty. what i mean is the connection to the server disconnected some time causing samba and putty unable to connect into the server

---

### Post by mstrap123 on 2009-04-23
any1 have the same problem?

---

### Post by silbro on 2009-04-28
what about the switch, have you tried switching it or use another port?

---

### Post by mstrap123 on 2009-04-29
i have tried another port that is running greatly..and still encounter the same problem, i tried to continuous ping the server from the xp side and whenever the ttl=127 then the connection fail, normally if the ttl=64 then the connection is ok.

Reply from 192.168.0.20: bytes=32 time<1ms TTL=127

---

