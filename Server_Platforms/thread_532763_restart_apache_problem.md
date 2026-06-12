---
title: "restart apache problem"
date: 2007-08-23
forum: Server Platforms
---

### Post by b06dqn on 2007-08-23
when i try to restart with putty i write this

sudo /etc/init.d/apache2 restart

and it returns this 
 * Forcing reload of web server (apache2)...           
                         httpd (no pid file) not running
(fail)

what to i have to do?
thank you

---

### Post by anubhavrocks on 2007-08-23
```
/etc/init.d/apache2 stop
/etc/init.d/apache2 start
```

also  check the logs ```
/var/log/apache2/error.log
```

---

### Post by heimo on 2007-08-23
> **b06dqn said:**
> when i try to restart with putty i write this

sudo /etc/init.d/apache2 restart

and it returns this 
 * Forcing reload of web server (apache2)...           
                         httpd (no pid file) not running
(fail)

what to i have to do?
thank you

It's probably failing to restart because it fails to start at all. I'd run 
```
sudo apache2ctl configtest
```

Is syntax ok?

---

### Post by b06dqn on 2007-08-23
Syntax OK
 
now what? :)

---

### Post by heimo on 2007-08-23
> **b06dqn said:**
> Syntax OK
 
now what? :)

Try starting and check if it's running. Did you just install it, or did this problem occur recently? What are you trying to achieve (in addition to restarting Apache)?

---

### Post by b06dqn on 2007-08-23
no it's not running, the server was ok it was installed a few weeks ago but today i rebooted the the computer and now apache is not starting, before i rebooted i installed postfix.

i need to start apache so i can install a php-based webmail addon for postfix

---

### Post by az on 2007-08-23
> **b06dqn said:**
> no it's not running, the server was ok it was installed a few weeks ago but today i rebooted the the computer and now apache is not starting, before i rebooted i installed postfix.

i need to start apache so i can install a php-based webmail addon for postfix

What does the apache error log say?  There must be a reason it is no longer starting.  I doubt it has anything to do with postfix.

---

