---
title: "MySQL Cluster Edition"
date: 2012-03-29
forum: Server Platforms
---

### Post by djjudas21 on 2012-03-29
I'm having some difficulties setting up MySQL Cluster Edition (note: different from MySQL Server).

Starting with a blank Ubuntu Server 10.04 LTS installation, I installed mysql-cluster-server and this worked fine. But when I installed various other packages which depend upon libmysql, there was a conflict.

```

jg4461@db4:~$ sudo apt-get install nagios-plugins-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nagios-plugins-standard is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  nagios-plugins-standard: Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```I want to know if there is a way to allow regular packages to use the regular mysql-client but to also run a mysql-cluster-server node. Is there a compat package or some other workaround?

Cheers,
Jonathan

---

