---
title: "PHP and Ubuntu Folder permission"
date: 2013-11-06
forum: Server Platforms
---

### Post by a.chaudhari on 2013-11-06
Hi,
 M trying to create new directory in var/ww/project/report folder.
But m not able to create due to permssion access.
I want to change the directory(report) permission through php code itself.

I have tried to use following code :
$rep_fold = getcwd().'/report/';
chmod($rep_fold,0755);

$dirnamere= getcwd().'/report/test';
mkdir($dirnamere, 0777);

But it doesnt work, can anybody guide me..
Thanks in Advance!

---

### Post by koenn on 2013-11-06
what errors are you getting ?

---

### Post by SeijiSensei on 2013-11-07
PHP scripts run with the same permissions as the Apache web server.  That means that any write operations must take place in directories writable by the "www-data" user that the web server runs as.

---

