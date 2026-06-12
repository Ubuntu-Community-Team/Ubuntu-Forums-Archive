---
title: "Eskuel or Phpmyadmin on Edgy"
date: 2007-01-16
forum: Repositories &amp; Backports
---

### Post by HercuLeeZ on 2007-01-16
Greetings all,

I have installed Edgy on a new laptop that will be travelling to our various branch offices with a consultunt who will be performing workstation audits using WinAudit.

My goal was to install a MySQL 4 database for WinAudit to dump its inventory to.  To make the process of checking and verifying the data easier, I wanted to provide the consultant with a GUI or Web interface to easily view and query the database.

Sadly, mysql-server 4 nor mysql-admin, phpmyadmin, or eskuel seem to be available according to 'apt-cache search'.

Are their any backports or backport servers I could add to my source.list file to provide these applications?

Thanks!
Herc

---

### Post by bapoumba on 2007-01-17
hi,

```
~ $ aptitude search mysql-server
p   mysql-server                    - mysql database server (current version)   
p   mysql-server-4.1                - mysql database server binaries            
p   mysql-server-5.0                - mysql database server binaries            
v   virtual-mysql-server            -                    
```
```
~ $ aptitude show mysql-server
Package: mysql-server
State: not installed
Version: 5.0.24a-9
Priority: optional
Section: misc

```
```
~ $ aptitude show phpmyadmin
Package: phpmyadmin
State: not installed
Version: 4:2.8.2-0.2
Priority: extra
Section: universe/web

```
```
~ $ aptitude show eskuel
Package: eskuel
State: not installed
Version: 1.0.6-1
Priority: optional
Section: universe/web

```
```
~ $ aptitude show mysql-admin
Package: mysql-admin
State: not installed
Version: 1.1.10-1
Priority: optional
Section: universe/admin

```

Looks like you have to enable universe repositories.
You can also search for packages here : [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

