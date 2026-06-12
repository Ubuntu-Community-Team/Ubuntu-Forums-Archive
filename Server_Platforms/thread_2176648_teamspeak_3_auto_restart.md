---
title: "teamspeak 3 auto restart"
date: 2013-09-25
forum: Server Platforms
---

### Post by joe672 on 2013-09-25
ive had teamspeak 3 runing for a while now, i was wanting to setup auto restart. i was watching this [http://dfgdesign.com/tutorials/article/53-how-to-install-a-teamspeak-3-server-on-vps-server-through-ssh/](http://dfgdesign.com/tutorials/article/53-how-to-install-a-teamspeak-3-server-on-vps-server-through-ssh/)

am using the part from about 11:35 as ive already moved teamspeak file into etc/init.d

when i try run chkconfig --add teamspeak

```
root@..:/# chkconfig --add teamspeak
/sbin/insserv: No such file or directory
teamspeak                 0:off  1:off  2:off  3:off  4:off  5:off  6:off
root@...:/#


```

server is runing unbuntu 12.04 lts

any help would be appreciated

---

### Post by adrian31 on 2014-07-13
hey bud sorry about late reply
check out vid easy way to setup auto start
[https://www.youtube.com/watch?v=sFOaYv_22go](https://www.youtube.com/watch?v=sFOaYv_22go)

---

