---
title: "Potential LAMP vulnerabilities???"
date: 2009-09-18
forum: Security
---

### Post by colinireland on 2009-09-18
Hello,

I just started a course in Software design in university and have set up a LAMP server on my laptop for our classes in web design and databases. I am wondering if I am leaving myself particularly vulnerable to hackers etc. Is it possible to turn it off when not in use so as not to leave more then the necessary amount of ports open.

Thanks
Colin

---

### Post by Sporkman on 2009-09-18
sudo /etc/init.d/apache2 stop

(...then "start" to start it back up")

Note it starts automatically if you reboot.

---

### Post by slakkie on 2009-09-18
If you make sure Apache binds only on 127.0.0.1 (same for mysql) then there is nothing to worry about.

In your Apache configuration:
```

Listen 127.0.0.1:80

```

Then restart:
```

/etc/init.d/apache2 restart

```

MySQL has a sane default of only listening to localhost, or you bind via a unix socket. So no real issues there.

---

### Post by phillw on 2009-09-18
> **colinireland said:**
> Hello,

I just started a course in Software design in university and have set up a LAMP server on my laptop for our classes in web design and databases. I am wondering if I am leaving myself particularly vulnerable to hackers etc. Is it possible to turn it off when not in use so as not to leave more then the necessary amount of ports open.

Thanks
Colin

If you are not using your laptop to connect to other computers at Uni as a server  - then, your laptop will **NOT** be accepting any **incoming** 'phone-calls' - It will only allow **outgoing** ones, such as your using FireFox.

FireStarter is an excellent little add-on - It will show & allow you to block / allow information from other computers onto your LAMP server. (The answer is allow none !!)

The tutorials in the stickys on this section can teach you lots about security. 

Having had my lap-top 'got-at' when I messed up SSH configuration - Just ensure your computer is not 'listening' for any **incomming** connections & you've nothing to worry about.

When you start apache2 manually  ```
 sudo /etc/init.d/apache2 restart
```you should always see a message saying that it cannot find the IP address of the server, so is using 127.0.0.1 - That is your own laptop.

Regards,

Phill.

---

