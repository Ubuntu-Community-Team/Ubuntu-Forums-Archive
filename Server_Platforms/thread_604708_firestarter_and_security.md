---
title: "firestarter and security"
date: 2007-11-06
forum: Server Platforms
---

### Post by ub9876 on 2007-11-06
i installed firestarter. is this thing a scam??? whats the story??

---

### Post by trak87 on 2007-11-06
It's not a scam.

Firestarter is merely a frontend to the iptables program. You need to run through Firestarter once to set it up. Then when you reboot it should start automatically.

If you type "sudo iptables -L -n" and get the following, you don't yet have firestarter set up property: 

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```

---

