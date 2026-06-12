---
title: "Ports Open !!"
date: 2006-10-31
forum: Server Platforms
---

### Post by wdbreen on 2006-10-31
Gday All,
I have a laptop that i installed dapper drake on, then updated to edgy last week.  I havent installed anything out of the ordinary (like apache, server packages etc) but my FTP and SMTP ports 21 and 23 respectively are open!

I was under the impression that ubuntu came with all ports closed by default so is there any reason why these maybe open!

How do i close them easily (iptables maybe?)

Any suggestions or advice is most welcome

Regards

Wayne

---

### Post by amo-ej1 on 2006-10-31
simply find out what daemons are running and shut them down ?

---

### Post by wdbreen on 2006-10-31
My apologies, port 23 is a telnet port!!

Amo, how do i find out what daemons are running against these ports (ps -ef ?)

Wayne

---

### Post by nocturn on 2006-10-31
> **wdbreen said:**
> My apologies, port 23 is a telnet port!!

Amo, how do i find out what daemons are running against these ports (ps -ef ?)

Wayne

As root:
netstat -lp

It gives you something like this:
```
tcp        0      0 *:imaps                 *:*                     LISTEN     5020/cyrmaster
```

---

