---
title: "very slow server"
date: 2008-04-26
forum: Server Platforms
---

### Post by ezacon on 2008-04-26
I have just installed an Ubuntu Sever on an Intel DG965RY based machine with 4gb Ram and 2 Sata drives. With default kernel (2.0.24-16-server), the system runs extremely slow. It takes more than 30 min. to boot to login prompt and 10 min to apt-get update. If i start with 2.0.24-16-generic, everything runs at normal speed.
Is it any know problem with this kernel?

Thanx

---

### Post by p_quarles on 2008-04-26
Well, first of all, I'm assuming you mean 2.6.24-16, and are not running some incredibly old custom kernel ;)

Anyway, the generic kernel is really okay for server use, but if you want to find out what's the problem with the server kernel, I would recommend looking at the output of top and dmesg.

---

### Post by ezacon on 2008-04-26
Oops. Yes its 2.6...
I have looked at /var/log/syslog and dmesg but i cant find anything abnormal.
Will boot to server kernel again and chech compare logs.

---

### Post by ezacon on 2008-04-27
Finaly the problem is a bad firmware with this board.
[http://www.avsforum.com/avs-vb/showthread.php?t=857100](http://www.avsforum.com/avs-vb/showthread.php?t=857100)
There is no bios update to solve this problem.
It works with generic kernel because the memory management in this kernel dont use all 4gb memory. The system work fine with 3Gb, even with the server kernel.
I will replace this piece of shee... with a working board.
Any recomendation for 4gb and more?

Thanks

---

