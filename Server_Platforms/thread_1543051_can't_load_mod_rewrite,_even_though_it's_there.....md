---
title: "can't load mod_rewrite, even though it's there...."
date: 2010-07-31
forum: Server Platforms
---

### Post by pythonscript on 2010-07-31
I'm running Ubuntu server, 10.04, with the LAMP package installed. I'm trying to install the mod_rewrite module, but even though it's there... (mod_rewrite.so is in the /usr/lib/apache2/modules/ directory) apache says it can't find it. 

Here's what I've added to /etc/apache2/apache2.conf

```

LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
AddModule mod_rewrite.c

```I've tried removing the /usr/lib/apache2/ from the first line, all of it, but I still get this error:

```

user@webserver:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
  apache2: Syntax error on line 208 of /etc/apache2/apache2.conf: 
Syntax error on line 2 of /etc/apache2/httpd.conf: 
Cannot load /etc/apache2/modules/mod_rewrite.so into server:
 /etc/apache2/modules/mod_rewrite.so: cannot open shared object file:
 No such file or directory   [COLOR=Red][fail][/COLOR]
user@webserver:~$ 

```

This is 100% critical for my web server, as the packages I'm using simply will NOT install without mod_rewrite enabled. I installed the LAMP package during the installation of Ubuntu server, and I was hoping that this was already configured....

Any help here?

---

### Post by pythonscript on 2010-08-01
Any ideas? I'm trying to set up elgg, an open source engine for social networking, and it actually *requires* this to run...

---

### Post by cob on 2010-08-02
If the file is there, I would believe that apache is unable to access it due to file permissions.

---

### Post by Ryan Dwyer on 2010-08-02
For reference, here's the correct permissions:

-rw-r--r-- 1 root root   58664 2010-07-28 18:58 mod_rewrite.so

Although you shouldn't have to play around with permissions if you did everything correctly. Assuming you installed Apache from the repo, you should have been able to run sudo a2enmod rewrite to enable it.

---

