---
title: "Ubuntu server"
date: 2009-06-03
forum: Server Platforms
---

### Post by rajitha on 2009-06-03
Hi,

I am working on a project for one of my papers at university and I need a server set up with Apache 2, PHP 5 and PostreSQL 8. I have actually never dealt with PostgreSQL before but I _have_ to use it because the department for that paper only supports that database. But I have used MySQL before.

So they set me up with a virtual machine with Ubuntu server installed and SSH access. I typed "lsb_release -a" and here is what I got:
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy
```

But the problem is that they only installed the system and did not configure the Apache or PostgreSQL server. i.e. the *httpd.conf* file is blank :S (and other files that need to be written, which I don't know about). I am used to programming on Windows with XAMPP and just uploading my websites to a server which is already configured.

_Just some information on the website being built_
It is a system which provides students with learning material and questions to test their knowledge. If it's successful it is to be used in the university in that department so it has to be secure. And the IT support people are not willing to configure the server so I have to do it myself.

I am using the Zend Framework so I would need **mod_rewrite** enabled.

So here is what I need to get done:
[LIST]
[*]I need to restore the OS back to the state it was in when it was first installed. Because I stupidly installed gedit without remembering there was no GUI and it installed lots of other packages. I have very limited space so I don't want packages that I don't need.
[*]I need to know how to install and configure the Apache and PostgreSQL servers so that it is secure. I also need to have PHP 5 support added to the server.
[*]I would also like to have some sort of web control panel (like the ones web hosting companies provide you with) to easily change things later on.
[/LIST]

Thanks,
Rajitha

---

### Post by LepeKaname on 2009-06-03
First, do you know how to use aptitude?

If so, you can easily get rid of any graphic package that was installed. For example. just inside the "Installed Packages section" remove all packages inside the category of "x11", "kde", "gnome", "games".

If you need more space, go through the installed packages and remove all those you know don't need.

> i.e. the httpd.conf file is blank :S

In apache2 the httpd.conf is shipped blank by default. The configuration file is now distributed in several files, for example, look at /etc/apache2/apache2.conf, /etc/apache2/sites-available/default, etc.

Just install apache2, libapache2-mod-php5, postgresql and php5-pgsql. Then just edit your apache2 and postgres configuration files and you are ready to run.

> I would also like to have some sort of web control panel (like the ones web hosting companies provide you with) to easily change things later on.

Maybe you could search on plesk. There are many for that, but... I have no experience setting them up. Using the console is not that hard...

---

### Post by Iowan on 2009-06-03
I did LAMP install on Hardy server - one of the options included PostgreSQL. Dunno if you want/need to re-install to that level.

---

### Post by rajitha on 2009-06-04
Hey LepeKaname,

Well I know how to use "apt-get" and that is just to install programs. e.g. "apt-get install gedit".

I tried what you said about removing the packages and thanks it worked. I will look at the example configuration files like you mentioned and try get it working.

And about the control panels, I heard one called "webmin" and it looked good from the demos. I might try that out.

Thanks for the reply.

Thanks,
Rajitha

---

### Post by HermanAB on 2009-06-04
Howdy,

If you are green and doesn't have much of a clue yet, then you should use an easier distribution with proper wizards, such as Mandriva or Suse.  Ubuntu is not an easy Linux - it is kinda intermediate.

---

