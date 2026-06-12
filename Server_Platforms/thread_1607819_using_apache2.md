---
title: "using apache2"
date: 2010-10-28
forum: Server Platforms
---

### Post by oren tal on 2010-10-28
Hello

I have just installed ubuntu server and I have installed on this apache2.

I started to read the documentation of it in:
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)
[http://httpd.apache.org/docs/2.2/invoking.html](http://httpd.apache.org/docs/2.2/invoking.html)


Now before I lost myself in this documentation, I thought that if it is not complicated if can someone explain to me who I just define the apache to load a specific file when someone call the ip of the server with http protocol.
I mean that if he wrote in his browser [http://192.168.50.123](http://192.168.50.123), from within the internal network, that he will get a specific page.

Thanks a lot.

---

### Post by linux-hack on 2010-10-28
I'm not rely shure how but take a look at the alias option in apache.

---

### Post by Ryan Dwyer on 2010-10-28
Edit the /var/www/index.html file.

---

### Post by SeijiSensei on 2010-10-28
By default, Ubuntu serves up files stored in the /var/www directory.  The configuration for the default server is in /etc/apache2/sites-enabled/000-default.

---

### Post by oren tal on 2010-10-28
thank you both.

---

