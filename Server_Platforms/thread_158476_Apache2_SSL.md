---
title: "Apache2 SSL"
date: 2006-04-11
forum: Server Platforms
---

### Post by werty on 2006-04-11
Hi
Im using Apache2 and PHP5...
I setup a virtual directory under localhost.. i wanted a ssl site for 
that directory.. So i installed "apache-ssl" package and
"apache-common" packages in the synaptic manager and i also installed
the certificates. Now when i https the virtual directory ([https://localhost/emites)](https://localhost/emites)),
the php(index.php) file is being downloaded.. what should i do?

---

### Post by mlind on 2006-04-11
is php5 module enabled?
*sudo a2enmod php5*

---

### Post by werty on 2006-04-11
sujith@SUJITH:~$ sudo a2enmod php5
Password:
This module is already enabled!

---

### Post by gmclachl on 2006-04-11
Are you sure you have downloaded the apache2-ssl module, from the looks of it you have probably installed Apache1.3.x. I suppose they would both be running happily as they are on different ports. 

George

---

### Post by werty on 2006-04-11
ok.. htere is apache-ssl which seems to be installed
but no apache2-ssl. I dont see the module in the synaptic
thanks in advance

---

### Post by werty on 2006-04-11
ok.. there is apache-ssl which seems to be installed
but no apache2-ssl. I dont see the module in the synaptic.
thanks in advance

---

### Post by gmclachl on 2006-04-11
[http://www.ubuntuforums.org/archive/index.php/t-4466.html](http://www.ubuntuforums.org/archive/index.php/t-4466.html)

 Have a look 3-4 posts down there is a mini how to for apache2 

 George

---

### Post by s7eam on 2006-04-11
Take a look at this ubuntu server guide:

[http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html)

---

### Post by LordHunter317 on 2006-04-11
***You don't need to install any special packages for SSL support in Apache2.***

The design of Apache2 even makes this rather difficult and senseless.

Your issue is inarguably a site configuration issue, post the relevant vhosts and configuration directives.

---

### Post by werty on 2006-04-13
[QUOTE=LordHunter317]***You don't need to install any special packages for SSL support in Apache2.***

The design of Apache2 even makes this rather difficult and senseless.

Your issue is inarguably a site configuration issue, post the relevant vhosts and configuration directives.[/QUOTE]

eh.. what is a vhost and what conf files should i post here...

---

### Post by werty on 2006-04-14
[QUOTE=s7eam]Take a look at this ubuntu server guide:

[http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html)[/QUOTE]

Thanks it worked.
But when i wanted to start my server today it would say

sujith@SUJITH:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Apr 14 09:37:02 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
[Fri Apr 14 09:37:02 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address [::]:443
no listening sockets available, shutting down
Unable to open logs

whats wrong...

---

