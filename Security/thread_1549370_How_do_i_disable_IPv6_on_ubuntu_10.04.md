---
title: "How do i disable IPv6 on ubuntu 10.04?"
date: 2010-08-09
forum: Security
---

### Post by dogdo on 2010-08-09
Anyone know how to disable IPv6 but still use IPv4?

---

### Post by bodhi.zazen on 2010-08-09
> **dogdo said:**
> Anyone know how to disable IPv6 but still use IPv4?

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by dogdo on 2010-08-09
I did this command in the terminal gksudo gedit  /etc/modprobe.d/aliases
and all i got was empty window-see attachment...according to that link you sent me im supposed to find the line 'alias net-pf-10 ipv6' but its not there. Seeing as that article was written in 2007 is it possible that 10.04 has IPv6 configured somewhere else?

---

### Post by lovinglinux on 2010-08-09
> **dogdo said:**
> I did this command in the terminal gksudo gedit  /etc/modprobe.d/aliases
and all i got was empty window-see attachment...according to that link you sent me im supposed to find the line 'alias net-pf-10 ipv6' but its not there. Seeing as that article was written in 2007 is it possible that 10.04 has IPv6 configured somewhere else?

See method #3 in the same article.

---

### Post by dogdo on 2010-08-20
> **lovinglinux said:**
> See method #3 in the same article.


Just a afterthought-ive already done this via method 3 but is there some online test i can do to see if ipv6 has really been disabled? like the way shields up scans your firewall?

---

### Post by bodhi.zazen on 2010-08-20
> **dogdo said:**
> Just a afterthought-ive already done this via method 3 but is there some online test i can do to see if ipv6 has really been disabled? like the way shields up scans your firewall?

What do you want to test exactly ?

[http://testmyipv6.com/](http://testmyipv6.com/)

If you want a port scan , use nmap (zenmap if you want a graphical interface)

[http://nmap.org/bennieston-tutorial/](http://nmap.org/bennieston-tutorial/)

---

### Post by wacky_sung on 2010-08-20
Actually if your ISP does not support IPv6 and you do not even need to bother about disabling it.

---

