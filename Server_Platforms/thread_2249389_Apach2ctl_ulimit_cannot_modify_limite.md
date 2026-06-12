---
title: "Apach2ctl ulimit cannot modify limite"
date: 2014-10-21
forum: Server Platforms
---

### Post by juri.knjazev on 2014-10-21
Hi Guys, I'm struggling here.

I'm running Ubuntu Server 12.04 on VPS and Apach 2.2.22 July build. Everything I restart apache2 i get this error.
```
root@host:/# sudo service apache2 restart * Restarting web server apache2                                                /usr/sbin/apache2ctl: line 87: ulimit: open files: cannot modify limit: Operation not permitted
 ... waiting /usr/sbin/apache2ctl: line 87: ulimit: open files: cannot modify limit: Operation not permitted
                                                                         [ OK ]
root@host:/# 



```

I've tried changing the listening port to 8080, modifying the limits file. What could be the cause of this and how can I fix it.

I'm root and it make no difference whether a put sudo or not.

Can you please help me.

---

### Post by Thirtysixway on 2014-11-02
Doing some searching, try the following:

So to avoid getting an error when apache2ctl does that, adjust your system's settings in the /etc/security/limits.conf file by adding these two lines:

*               soft    nofile          8192
*               hard    nofile          8192


Perhaps root, or the www-data user has too many files open to perform the action. That's what it's checking with ulimit, if there are too many files open.

---

