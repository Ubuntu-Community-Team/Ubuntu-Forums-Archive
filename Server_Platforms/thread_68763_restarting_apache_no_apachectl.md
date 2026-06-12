---
title: "restarting apache: no apachectl?"
date: 2005-09-24
forum: Server Platforms
---

### Post by jnoreiko on 2005-09-24
I'm RTFMing, and TFM says: 

```
apachectl -k graceful
``` 
(at [http://httpd.apache.org/docs/2.0/stopping.html](http://httpd.apache.org/docs/2.0/stopping.html))

But ubuntu says:

```
  bash: apachectl: command not found

``` 

I've found on the forums I can do

```
 sudo /etc/init.d/apache2 restart
``` 

but why doesn't it work as in the manual?

---

### Post by jnoreiko on 2005-09-24
It seems

```
sudo apache2ctl restart
``` 

works.

---

### Post by esaym on 2007-01-28
Its apache2ctl?  Thank you!

---

### Post by crouton on 2007-01-31
FYI, it's useful to know the /etc/init.d/<program> nomenclature, as it's used for a wide variety of system services.

---

### Post by MJN on 2007-02-01
Indeed, use **sudo /etc/init.d/apache2 start|stop|restart **as this is essentially an 'intelligent' frontend to apache2ctl. Whilst at the moment it doesn't do all that much extra in the future it could well do - best to get in the right habit now!
 
Mathew

---

### Post by esaym on 2007-02-17
> **crouton said:**
> FYI, it's useful to know the /etc/init.d/<program> nomenclature, as it's used for a wide variety of system services.


True.  But can it do graceful reboots so it will not kill all the child procs?


apache2ctl -k graceful :p

---

### Post by MJN on 2007-02-18
Sure - **sudo /etc/init.d/apache2 reload**

Mathew

---

### Post by esaym on 2007-02-18
> **MJN said:**
> Sure - **sudo /etc/init.d/apache2 reload**

Mathew

....oohhhhhh:oops:

---

### Post by MJN on 2007-02-19
I'll concede that it's not necessarilly intuitive that this is what it does so you can be forgiven...

---

### Post by balbir97 on 2007-02-27
> **MJN said:**
> I'll concede that it's not necessarilly intuitive that this is what it does so you can be forgiven...

hey thanks...u all even mine problem in apache got solved. :)

---

