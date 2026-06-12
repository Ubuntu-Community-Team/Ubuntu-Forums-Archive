---
title: "localhost vs localhost.localdomain"
date: 2005-09-17
forum: The Cafe
---

### Post by blastus on 2005-09-17
I'm not sure if this is the correct place to post but what is the difference between localhost and localhost.localdomain? Why is there even a localhost.localdomain to begin with?

---

### Post by XQC on 2005-09-17
[QUOTE=blastus]I'm not sure if this is the correct place to post but what is the difference between localhost and localhost.localdomain? Why is there even a localhost.localdomain to begin with?[/QUOTE]
 Agreed, this host name really does look out of place, espicially for a new user of Linux.

---

### Post by jdong on 2005-09-17
localdomain is the domain that localhost belongs to... UNIX systems need a default domain in addition to just a name.

---

### Post by Keffin on 2005-09-18
Since I just answered a question relating to this... Is there a reason why localhost.localdomain comes before localhost on the first line of /etc/hosts? Because if not it would be nice to switch them as default, giving one less problem in connecting an app (Java at least) to a MySQL database.

---

### Post by blastus on 2005-09-18
I must say that MySQL makes this unnecessarily complicated and fragile. Let's say your hostname is "ubuntu" and your /etc/hosts file has this line...

```
127.0.0.1 localhost.localdomain localhost ubuntu
```

...then "localhost.localdomain", "localhost", and "ubuntu" should ALL resolve to 127.0.0.1 and they should ALL be equivalent hostnames. So in MySQL, if you have given permissions to root@localhost, then you should be able to login to MySQL or use any of the following as hostnames in a JDBC connection string; "127.0.0.1", "localhost", "localhost.localdomain", and "ubuntu."

Personally, I don't even know why MySQL bothers to use the /etc/hosts file since it can't even determine that...

```
localhost.localdomain = localhost = ubuntu
```

---

