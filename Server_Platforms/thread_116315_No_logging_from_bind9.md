---
title: "No logging from bind9"
date: 2006-01-12
forum: Server Platforms
---

### Post by shadowman on 2006-01-12
Hi all

I am setting up a new dns server using bind 9 from the repositories on ubuntu 5.10.  For some reason reason I am not gettng any logging in syslog or anywhere else that I can find.  Can anyone steer me in the right direction to get logging started?  I was under the impression that there would be some default logging at least but maybe not..

Thanks

---

### Post by bluefrog on 2006-01-16
This might help  you

[http://en.tldp.org/HOWTO/Chroot-BIND-HOWTO-4.html#ss4.2](http://en.tldp.org/HOWTO/Chroot-BIND-HOWTO-4.html#ss4.2)


james

---

### Post by ametade on 2006-01-16
Have you tried the following command?

```
sudo grep "named" /var/log/syslog
```

---

