---
title: "IspConfig3 Mysql php login details"
date: 2010-05-27
forum: Server Platforms
---

### Post by finnj6 on 2010-05-27
Hi I'm using ispconfig3 to manage my web server. I'm creating a website which will access a mysql database and I want to keep the database details secret. I want to have a file mydbconfig

[PHP]
$db = array(
'hostname' => 'host',
'username' => 'usr',
'password' => 'pw',
'database' => 'mydb',
); [/PHP]

and have it located outside the browser accessible folders, is there a way of doing this inside ispconfig ?

Id like to have this file accessible only to the relevant account. So client on can only see it's db config file and client 2 can't see it so i don' want to leave it in /var/ and the clients only seem to be in /var/www

Thanks in advance for any help.

---

