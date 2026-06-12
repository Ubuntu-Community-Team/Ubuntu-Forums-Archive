---
title: "Ubuntu advance Squid"
date: 2010-06-07
forum: Server Platforms
---

### Post by jfkati on 2010-06-07
Hi all,


i'm using ubuntu 9.4  and i would like to monitor the users of my 
networks by checking
how much bandwidth they use and wich protocols they are using and how 
much Download/upload traffic they do everyday.
i thought about squid proxy, which permits to know which url my users 
are accessing but i don't know how to get  further informations.
also when i set up my proxy , my users can uncheck the proxy checkbox on 
their browser easily to  get rid my monitoring, how can i avoid that?

---

### Post by expatCM on 2010-06-08
I think you need to set up Squid as a headless or transparent proxy.  That means all the browser traffic goes through Squid whether or not it is set up in the client machine settings.

For the traffic you need to install a stats package to collect the data for you.  There is a package called Squid Report Generator and another called SARG.
[http://sarg.sourceforge.net/](http://sarg.sourceforge.net/)

---

### Post by jfkati on 2010-06-08
Thanks you very much

---

