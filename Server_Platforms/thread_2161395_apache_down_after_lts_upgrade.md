---
title: "apache down after lts upgrade"
date: 2013-07-10
forum: Server Platforms
---

### Post by ZenMasta on 2013-07-10
So I know I probably should have left well enough alone. But I decided to perform an in place upgrade from 10.04 to 12.04 and now I'm paying for it.

Generally everything else seems fine, except apache.

When I try to start (as root) this is what I get.
ve : /etc/init.d/apache2 start
 * Starting web server apache2                                                  mktemp: failed to create directory via template `/var/lock/apache2.XXXXXXXXXX': No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.


Thanks

---

### Post by rubylaser on 2013-07-10
Have you made sure that /var/lock exists and checked it's permissions?
```

mkdir -p /var/lock
ls -l /var/lock

```

---

### Post by ZenMasta on 2013-07-19
It already exists

ve ~: ls -l /var/lock
lrwxrwxrwx 1 root root 9 Jul  2 11:51 /var/lock -> /run/lock

---

### Post by ZenMasta on 2013-07-19
It already exists

ve ~: ls -l /var/lock
lrwxrwxrwx 1 root root 9 Jul  2 11:51 /var/lock -> /run/lock

---

### Post by SeijiSensei on 2013-07-19
Have you tried starting apache2 via upstart, which is the norm in 12.04?  Rather than /etc/init.d, use the command "sudo service apache2 start".  Work any better?

Does the www-data user than apache2 runs as have write privileges to /run/lock?  On my machine that directory is writable by everyone just like /tmp is:

```
drwxrwxrwt  3 root       root         60 Jul 11 21:25 lock
```

---

