---
title: "questions about server"
date: 2008-11-26
forum: Server Platforms
---

### Post by hirohitosan on 2008-11-26
Hi there.

I have on my computer Ub server and desktop and I have some questions
1. Where should I add UserDir directive? In apache2.conf or in httpd.conf?
2. How can I add UserDir directive? I don't know if is already enabled or not
3. I tried to restart apache2 and I got:
```
sudo apache2 -k restart
apache2: bad user name ${APACHE_RUN_USER}
```

what is user name ${APACHE_RUN_USER}?

4. Where are network configurations?
my /etc/network/interfaces looks like:
```
auto lo
iface lo inet loopback

```
that's all

Many thanks

---

### Post by dantrevino on 2008-11-26
Userdir mod is available with a default install.  

```
sudo a2enmod userdir
```
```
sudo /etc/init.d/apache2 force-reload
```

should get you set up.

---

### Post by hirohitosan on 2008-11-26
I restarted and I get:

```
* Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.

```

what does it mean?

---

### Post by Titan8990 on 2008-11-26
It means you did not specify servername in the virtual host file.

Here is an example:

<VirtualHost MYDOMAINNAME.com>

ServerName MYDOMAINNAME.com
ServerAdmin [email]root@MYDOMAINNAME.com[/email]
ServerAlias MYDOMAINNAME.com
DocumentRoot /var/www/mail

</VirtualHost>

---

