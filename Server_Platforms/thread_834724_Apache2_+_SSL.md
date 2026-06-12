---
title: "Apache2 + SSL"
date: 2008-06-19
forum: Server Platforms
---

### Post by KingTermite on 2008-06-19
I'm working toward creating a subversion server with LDAP authentication, working from a few different tutorials. I have a fresh install of Ubuntu 7.10 on this machine.


from: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I have already installed Apache. I have not done anything with it yet, but it was install with the standard apt-get method. Specifically, I installed with the LAMP plugins as:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Now from this tutorial:
[http://www.tldp.org/HOWTO/Apache-WebDAV-LDAP-HOWTO/x153.html](http://www.tldp.org/HOWTO/Apache-WebDAV-LDAP-HOWTO/x153.html)

I skipped the PHP, MySql, etc.. as it was install above. But now I'm to the Apache and it has me downloading/compiling Apache and configuring it for the SSL (sec 3.3).

```
# cd /tmp/download
# gzip -d httpd-2.0.46.tar.gz 
# tar -xvf httpd-2.0.46.tar
# cd httpd-2.0.46
#./configure --enable-so  --with-ssl --enable-ssl  --enable-rewrite   --enable-dav

```

1. What I'm trying to figure out is if I can configure Apache2 this way as its already installed, or do I need to recompile with this configuration arguments.

2. If I do need to compile, do I need to add other arguments to make sure it uses PHP, MySql, WebDAV etc..??

---

### Post by KingTermite on 2008-06-20
Bump....anybody?

---

### Post by Poleh on 2008-06-20
if you installed apache with apt-get you should have a working apache install with SSL capabilities available. not sure why you are going down the track of downloading and installing it from source?

---

### Post by lodp on 2008-06-20
second that .. same goes for OpenSSL. You can get what you want without re-compiling. Just enable the modules you need.

mod_auth_ldap is installed by default, too (or at least it appears to be on my system).

So in this case you just have to run

> sudo a2enmod authnz_ldap
> sudo /etc/init.d/apache2 force-reload

.. and you're good.

---

### Post by KingTermite on 2008-06-20
> **lodp said:**
> second that .. same goes for OpenSSL. No can get what you want without re-compiling. Just enable the modules you need.

mod_auth_ldap is installed by default, too (or at least it appears to be on my system).

So in this case you just have to run




.. and you're good.

I was dong down that path because of the tutorial...however that tutorial was about 5 years old so I suspected some thing had to be different.

So you are saying ssl and mod_auth_ldap are installed/enabled by default? If so, that's great.

How can I check what is/is not enabled in apache?

---

### Post by lodp on 2008-06-20
Check the contents of /etc/apache2/mods-enabled.

You can switch on any mod that's in /etc/apache2/mods-available by typing 

> sudo a2enmod [module name]

and the restarting apache2 with 

> sudo /etc/init.d/apache2 force-reload

---

