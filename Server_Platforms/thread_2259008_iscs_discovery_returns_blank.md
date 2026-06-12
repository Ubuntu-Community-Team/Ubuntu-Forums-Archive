---
title: "iscs discovery returns blank"
date: 2015-01-01
forum: Server Platforms
---

### Post by ikki_72 on 2015-01-01
taget and initiator are version 14.04
```
initiator:~$ iscsiadm -m discovery -t st -p 192.168.56.212
```

```
target:~$ sudo netstat -tulnp | grep LISTE
tcp        0      0 0.0.0.0:3260            0.0.0.0:*               LISTEN      937/ietd        
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      849/sshd        
tcp6       0      0 :::3260                 :::*                    LISTEN      937/ietd        
tcp6       0      0 :::22                   :::*                    LISTEN      849/sshd
```

---

### Post by ikki_72 on 2015-01-01
It seemed that i forgot to put 'sudo'

---

