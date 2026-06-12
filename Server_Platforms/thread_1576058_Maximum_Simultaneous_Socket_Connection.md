---
title: "Maximum Simultaneous Socket Connection"
date: 2010-09-16
forum: Server Platforms
---

### Post by hosseinyounesi on 2010-09-16
Hi everyone,

I'm writing a client-server program. There are more than 500 clients. I start a thread to process and response to each client and the processing needs some MySQL query. I'm looking for any possible hazards on my server!
1- Any limitation on "Maximum Simultaneous Socket Connection"?
2- Any limitation on using mysql?
3- As socket on Linux are file, Any limitation on number of sockets or threads?

I'm using a Linux server (Centos or Fedora or Ubuntu) and clients are both Linux and Windows.

Any answer is appreciated

---

### Post by jbrown96 on 2010-09-16
1) Apache has a max clients setting that you should look into if you are making a web app
2) [http://dev.mysql.com/doc/refman/5.1/en/too-many-connections.html](http://dev.mysql.com/doc/refman/5.1/en/too-many-connections.html)
3) Not that you will hit. ```
cat /proc/sys/kernel/threads-max
``` You can change the value if you want.
I can't find anything particular about sockets.

All of these are really limited by the amount of memory you have.

---

### Post by hosseinyounesi on 2010-09-18
Thanks "jbrown96". How about "backlog" parameter of "listen" function? What should I set for that?

---

