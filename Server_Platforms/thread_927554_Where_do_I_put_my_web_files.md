---
title: "Where do I put my web files?"
date: 2008-09-23
forum: Server Platforms
---

### Post by botfish on 2008-09-23
Hi,

I've just installed Ubuntu server and I see that home directories are not created for user.

Where do I put my web files?

I want to run a number of virtual hosts do I need to create a user for each virtual host?

Thanks for any help.

---

### Post by isync on 2008-09-23
As far as I know the usual location for Debian-like systems (ubuntu) is to place webfiles under the /var/www/... branch of dirs. That is also the location where apache would look (at least you find it in many example apache config files).

So you could build dirs like that:

/var/www/example.com
/var/www/sub1.example.com
/var/www/sub2.example.com
etc.

---

### Post by leg on 2008-09-23
To create virtual hosts you need to set each one up. Firstly you will find a directory called /etc/apache2/ and there is a directory in there called available hosts (or something very similar). Open the file named default and copy it to a file named the same as the virtual host you want. Open the file and change the settings to set the directory for your host. When you have done that you need to add the host name to your hosts file. then you (re)start apache and you should be able to access your virtual host.

There is also a package that enables you to set up per user directory hosts but I can't remember what it is called.

[This page]("https://help.ubuntu.com/community/ApacheMySQLPHP") should help I am fairly sure it contains a section on virtual hosting.

---

### Post by Iowan on 2008-09-23
The referenced page also gives advice on changing/adding/copying "sites-available" to "sites-enabled' via **a2ensite**

---

