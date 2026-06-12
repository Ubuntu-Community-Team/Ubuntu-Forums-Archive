---
title: "netstat shows a possible intrusion but?"
date: 2009-02-23
forum: Security
---

### Post by cb951303 on 2009-02-23
> 
**~$ sudo netstat**
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 none:37784              knightonlineworld.c:www ESTABLISHED
...


I have 3 services running on my server. Apache, Mysql and SSH
Logs shows no intrusion (although apache and ssh show a lot of unsuccessful try)

I'm doing SSH tunneling to this machine and connect some sites that my IPS doesn't allow through it. Just to be sure I killed apache/mysql, and quit firefox in the client machine. But netstat was still showing this.

Any ideas how this can be?

PS: obviously I never went to knightonlineworld.com :) This the first time I hear about this site.

---

### Post by cdenley on 2009-02-23
It looks like at outgoing connection to the web server at 206.82.206.80 on port 80, so it was probably a website you were visiting, not necessarily knightonlineworld.com. Perhaps [www.gamersfirst.com](www.gamersfirst.com)?

---

### Post by cb951303 on 2009-02-23
> **cdenley said:**
> It looks like at outgoing connection to the web server at 206.82.206.80 on port 80, so it was probably a website you were visiting, not necessarily knightonlineworld.com. Perhaps [www.gamersfirst.com](www.gamersfirst.com)?

but just to make sure I closed all the applications that use internet connection. only ssh client was open.

PS: and no I didn't visit that site :/
The first thing I thought is that someone tunneling through me but there is no such log.

---

### Post by cdenley on 2009-02-23
Figure out what process has that connection open.
```

sudo netstat -tnp|grep :80

```

---

### Post by cb951303 on 2009-02-23
Aww, too late :D
I don't see the connection anymore.
I'll try that if I see it again

Thanks

---

