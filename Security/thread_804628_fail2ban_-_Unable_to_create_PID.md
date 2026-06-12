---
title: "fail2ban - Unable to create PID"
date: 2008-05-23
forum: Security
---

### Post by brigux on 2008-05-23
there's a bug in fail2ban 0.8.2-2

ref:
[https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/223706](https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/223706)

resulting in:

```
host:/etc/init.d$ sudo fail2ban-client start
2008-05-22 12:22:27,411 fail2ban.server : INFO   Starting Fail2ban v0.8.2
2008-05-22 12:22:27,412 fail2ban.server : ERROR  Unable to create PID file: [Errno 2] No such file or directory: '/var/run/fail2ban/fail2ban.pid'
```

fixed in fail2ban v 0.8.2-3

Unfortunately the correct package is still not in the repository

In the mean time, just download the package from debian:
[http://debian.mirror.inra.fr/debian/pool/main/f/fail2ban/fail2ban_0.8.2-3_all.deb](http://debian.mirror.inra.fr/debian/pool/main/f/fail2ban/fail2ban_0.8.2-3_all.deb)

then install it:

```
sudo dpkg -i fail2ban_0.8.2-3_all.deb
```

thought it might help someone out there...

---

### Post by nynexman4464 on 2008-05-30
Thanks, I was wondering what was going on with this package.  Hopefully it'll be added to the repository soon...

---

