---
title: "apache2, bind, ftp autostart issue"
date: 2011-02-27
forum: Server Platforms
---

### Post by rajas on 2011-02-27
Hi,

I am struck with a strange problem.. whenever I reboot server, apache2 , bind9 and proftpd does not start automatically while mysql does.

I tried reinstalling and also by manually adding the run levels by

sudo update-rc.d –f apache2 remove
update-rc.d apache2 defaults

but no luck..

Can any one advice, what may be the reason? and where I need to check to trace out the issue?

---

### Post by t3r0 on 2011-02-27
Anything in the error logs of those apps?

---

### Post by rajas on 2011-02-27
Hi,

No, i am able to start them using

/etc/init.d/apache2 restart
/etc/init.d/bind9 

etc..

Problem is only with the automatic startup

---

### Post by rajas on 2011-02-28
No luck on this forum..

I have decided to try Debian now

thanks

---

