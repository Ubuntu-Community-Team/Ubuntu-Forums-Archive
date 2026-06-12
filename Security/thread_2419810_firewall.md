---
title: "firewall"
date: 2019-05-25
forum: Security
---

### Post by gordie692 on 2019-05-25
quick question due to ufw firewall once you enable it you don't have to enable or do you have to open everytime I always thought cupfilters built in the linux kernel was good enough

---

### Post by Rubi1200 on 2019-05-25
By default ufw is not enabled on a fresh install.

Once enabled, it is always on and running.

Unless you need to configure a specific rule there is no need to do anything.

Status can be checked with this from the terminal:

```
sudo ufw status
```

---

### Post by gordie692 on 2019-05-25
Thanks I always download the ufw firewall from the software center thats the one I use but thought the cupfilter was a firewall built in the kernel 
I don't do much on my laptop everyday browse just my online banking thats it I use chrome for one and firefox for another

---

