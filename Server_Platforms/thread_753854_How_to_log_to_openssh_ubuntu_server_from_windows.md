---
title: "How to log to openssh ubuntu server from windows???"
date: 2008-04-13
forum: Server Platforms
---

### Post by rado3105 on 2008-04-13
Hi I have just installed ubuntu server 7.10. I am new to linux servers. I want to log to that server(it is running openssh) from windows(computer(I want to log from is in the same subnet like server). Computer ip is 192.168.76.99, server ip is 192.168.76.4. How can I log there and  what I need to install in windows to do that. Sorry for guestioning but I have no idea where to find some basics.

---

### Post by hyper_ch on 2008-04-13
(1) on the linux box install openssh server
```

sudo apt-get install openssh-server

```

(2) Download Putty for windows
- use as address the server's IP address
- use as username your normal user name
- use as password your normal user password

if you want to transfer files then download winscp from [http://www.winscp.com](http://www.winscp.com) --> use same credentials as above you can can confortably transfer files.

---

### Post by rado3105 on 2008-04-13
Thanks it helped me a lot. 
Is possible to log in there from some  windows computer on internet(not from that local network), I have public IP on the network the ubuntu server is.

---

### Post by hyper_ch on 2008-04-13
it is, if you are behind a router you just need to forward port 22 from the router to your linux box in your lan.

---

### Post by rado3105 on 2008-04-13
Thanks everything works

---

### Post by A$h X on 2008-04-14
You could also use NXclient to control ubuntu from XP. See here:

[http://ubuntuforums.org/showthread.php?t=736509](http://ubuntuforums.org/showthread.php?t=736509)

---

### Post by hyper_ch on 2008-04-15
nx is just too slow ;)

---

