---
title: "Static ip no apt-get"
date: 2010-07-05
forum: Server Platforms
---

### Post by bodiedoo on 2010-07-05
I know i am a noob but i need some help. I installed LAMP and set up a static ip using /etc/network/interfaces. it works for apache, i can get to my site, but i can't use apt-get update or ping google. help?

---

### Post by sil3nt on 2010-07-05
Hi you probably need to add your router or modem as the gateway seen as though your using a static address. 

do a ifconfig get the ip of your gateway and add it to the /etc/network/interfaces

eg 

```
gateway = xxx.xxx.xxx.xxx
```

---

### Post by bodiedoo on 2010-07-05
ok thanks it works!!
 
on a side note i tried it before but it did not work,anyway it does now:p

---

