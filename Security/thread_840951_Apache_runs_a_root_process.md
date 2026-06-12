---
title: "Apache runs a root process"
date: 2008-06-25
forum: Security
---

### Post by ridgerunner7 on 2008-06-25
I have a newly installed hardy server. Just installed apache with default settings--haven't changed anything.

run:
```
$ ps aux | grep apache
root      4499  0.0  1.3  10468  2624 ?        Ss   10:13   0:00 /usr/sbin/apache2 -k start
www-data  4500  0.0  0.9  10240  1792 ?        S    10:13   0:00 /usr/sbin/apache2 -k start
www-data  4501  0.0  1.2 231804  2408 ?        Sl   10:13   0:00 /usr/sbin/apache2 -k start
www-data  4504  0.0  1.2 231804  2412 ?        Sl   10:13   0:00 /usr/sbin/apache2 -k start
neo       4619  0.0  0.3   3004   756 pts/0    R+   10:23   0:00 grep apache
```neo is my user that grepped, fine.
www-data is expected, fine.

But why is there a root owned process? Isn't this a security risk?

---

### Post by madu on 2008-06-26
I think it's fine. Gives the same for me.
I also had this problem and asked here.
Seems Apache is a process owned by the root but dont not run as root ( or something like that.).
Anyway, until an expert answers you, don't worry. Its fine.

---

### Post by todb on 2008-06-26
> **madu said:**
> Seems Apache is a process owned by the root but dont not run as root ( or something like that.).

Apache must start as root in order to bind to port 80 (and 443 if you're SSL-happy). However, www-data is the user that actually listens to the socket. 

Asking how to avoid this is a more complicated question, but it is suffice to say, if you don't trust Apache to bind the socket, then you probably shouldn't be using Apache as your web server.

Do not fret. Lots of things run as root. My fairly vanilla installation at this moment:

```

todb@mazikeen:~$ ps -ef | grep "^root" | wc -l
74

```

---

### Post by ridgerunner7 on 2008-06-26
> **todb said:**
> 
Do not fret. Lots of things run as root. My fairly vanilla installation at this moment:


[edit] retracting ignorant statements. :) 

FYI, some persistent googling told me that the root process opens privileged port 80 but **doesn't actually listen** to it. The www-data process is the one that listens to port 80 and interacts with users. So apparently if someone hacked your website they wouldn't have access to that root process.[COLOR=#ff0000][/COLOR]

---

