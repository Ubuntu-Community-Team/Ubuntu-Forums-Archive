---
title: "ubuntu server 6 quota problem"
date: 2010-01-03
forum: Server Platforms
---

### Post by bluedrakonis on 2010-01-03
if i have posted this in the wrong section i appologise

here is my problem:
I am following this guide:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

 when i run quotaon -avug i get cant stat () mounted device /dev/sda1: no such file or directory         

any ideas or suggestion, and please explain it simply i am more used  to windows than this thanks

---

### Post by sylvester_0 on 2010-01-03
Hmm, please post the output of these commands for further help:

```
mount
```

```
cat /etc/fstab
```

```
ls -l /q*
```

---

### Post by bluedrakonis on 2010-01-05
thanks for the help but i ended up scrapping this project and started one with an ubuntu 9 server

---

