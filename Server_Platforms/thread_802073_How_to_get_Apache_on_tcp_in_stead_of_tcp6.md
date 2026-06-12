---
title: "How to get Apache on tcp in stead of tcp6"
date: 2008-05-21
forum: Server Platforms
---

### Post by comunica2 on 2008-05-21
I use Ubuntu 6.06 as VPS under OpenVz. I did apt-get install apache2 and when I look at netstat -l I see:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
```

Since OpenVZ works virtual networking is only tcp, the Apache has become invisible to the outside world. My question is how you can reconfigure that is works with tcp, just like the ssh?

---

### Post by windependence on 2008-05-21
You need to turn off IPV6 support. I am not sure where to do this as i always turn it off when I install.

-Tim

---

### Post by MJN on 2008-05-21
It might actually be that Apache is listening on both Ipv4 and v6. Can you post the output of **netstat -tn** and also confirm what happens if you browse locally to [http://127.0.0.1/](http://127.0.0.1/)
 
Mathew

---

### Post by n0d on 2008-07-17
I just ran into this same problem.  I am starting tomcat via a startup script in rc2.d.  However, using netstat -plant I can only see the listener on tcp6 8080.  However, I can connect via telnet/netcat on 8080 without problem, so I know the daemon is running and listening.  Also, if I try to start another service on 8080, it can't bind to 8080.  Even if I run netstat as root, 8080 will not show up as "tcp".  Was a change made to imply tcp6 as both tcp and tcp6?  I personally think this is a bug.  

So, to the original poster of this thread, I think you're Apache is probably listening on both ipv6 tcp and ipv4 tcp, but netstat is telling you it's only listening on ipv6 tcp.  

Again, this seems like netstat is broken to me.  I just spent half a day debugging a problem, because I couldn't tell that 8080 tcp was actually listening -- because it wasn't visible to me!

---

### Post by Bpa on 2011-03-06
> **n0d said:**
> I just ran into this same problem.  I am starting tomcat via a startup script in rc2.d.  However, using netstat -plant I can only see the listener on tcp6 8080.  However, I can connect via telnet/netcat on 8080 without problem, so I know the daemon is running and listening.  Also, if I try to start another service on 8080, it can't bind to 8080.  Even if I run netstat as root, 8080 will not show up as "tcp".  Was a change made to imply tcp6 as both tcp and tcp6?  I personally think this is a bug.  

So, to the original poster of this thread, I think you're Apache is probably listening on both ipv6 tcp and ipv4 tcp, but netstat is telling you it's only listening on ipv6 tcp.  

Again, this seems like netstat is broken to me.  I just spent half a day debugging a problem, because I couldn't tell that 8080 tcp was actually listening -- because it wasn't visible to me!

Ever figure out what the deal was here? I am seeing the same weirdness where netstat is only reporting apache running on tcp6, but I can connect just fine from the internet using ipv4, so is it doing some implicit conversion or tunneling from ipv4 to ipv6 or is netstat lying?

---

