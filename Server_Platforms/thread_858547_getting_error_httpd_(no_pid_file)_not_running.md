---
title: "getting error httpd (no pid file) not running"
date: 2008-07-13
forum: Server Platforms
---

### Post by kustomjs on 2008-07-13
Hi Guys
I am getting this error httpd (no pid file) not running and also I am getting a error 98:

httpd (no pid file) not running
(98 Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs

so can anybody tell me how to fix this problem?

and I do got 2 sites under my server using one ip address.

here is some more help I got webmin installed also and here is how my sites are setup under virtual host/ /etc/apache2/sites-available/siteone
/etc/apache2/sites-available/sitetwo

site one
<VirtualHost *>
ServerName cbcperformance.net
DocumentRoot /var/www/cbcperformance/cart/catalog
</VirtualHost>

site two is setup as like for one

yes i do still got the default settings in there and this is the guide help me do this:
[http://www.tequilafish.com/2007/08/0...ost-on-ubuntu/](http://www.tequilafish.com/2007/08/0...ost-on-ubuntu/)

and I am using Ubuntu 8.04 LTS server edition

also I was trying to get SSL working and this is when I got that error httpd (no pid file) not running and the site's was working before I did sudo a2enmod ssl bc i copied the information from here: [http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html)

---

### Post by windependence on 2008-07-14
> **Why can't I use SSL with name-based/non-IP-based virtual hosts?**
The reason is very technical, and a somewhat "chicken and egg" problem. The SSL protocol layer stays below the HTTP protocol layer and encapsulates HTTP. When an SSL connection (HTTPS) is established Apache/mod_ssl has to negotiate the SSL protocol parameters with the client. For this, mod_ssl has to consult the configuration of the virtual server (for instance it has to look for the cipher suite, the server certificate, etc.). But in order to go to the correct virtual server Apache has to know the Host HTTP header field. To do this, the HTTP request header has to be read. This cannot be done before the SSL handshake is finished, but the information is needed in order to complete the SSL handshake phase. Bingo!

**Why is it not possible to use Name-Based Virtual Hosting to identify different SSL virtual hosts?**

Name-Based Virtual Hosting is a very popular method of identifying different virtual hosts. It allows you to use the same IP address and the same port number for many different sites. When people move on to SSL, it seems natural to assume that the same method can be used to have lots of different SSL virtual hosts on the same server.

It comes as rather a shock to learn that it is impossible.

The reason is that the SSL protocol is a separate layer which encapsulates the HTTP protocol. So the SSL session is a separate transaction, that takes place before the HTTP session has begun. The server receives an SSL request on IP address X and port Y (usually 443). Since the SSL request does not contain any Host: field, the server has no way to decide which SSL virtual host to use. Usually, it will just use the first one it finds, which matches the port and IP address specified.

[B]You can, of course, use Name-Based Virtual Hosting to identify many non-SSL virtual hosts (all on port 80, for example) and then have a single SSL virtual host (on port 443). But if you do this, you must make sure to put the non-SSL port number on the NameVirtualHost directive, e.g.

NameVirtualHost 192.168.1.1:80 [/B]
[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html)

You have to set up each virtual host using it's Ip and port number and set up only one using port 443 as the SSL host.

Yours is set up as a blanket 

```
<VirtualHost *>
```

It should be 

```
<VirtualHost serverIP:80>
```

for each regualr virtual host and 

```
<VirtualHost serverIP:443>
```

for the SSL host. Note that you can only have ONE SSL host using named virtual hosts.

-Tim

---

### Post by Phristen on 2008-07-14
I am actually having the same trouble.
I am using <VirtualHost *:80>, as suggested by some guide, and it still doesn't work.

Edit:
Actually, never mind, I changed some paths in vhost configs and it suddenly started working...
But my domain name aliases aren't working still :(

For example, "ServerName microsoft.com" will not redirect me to my local site, but will load the microsoft's.

---

### Post by kylemech on 2008-08-25
I have no idea what went wrong, but my errors were the same.  Here are the steps that I took to correct it.  I make no claim about this being the right way to do things.

[LIST=1]
[*]Check if anything is listening on port 80 already.[LIST][*]**lsof -i :80**[/LIST]Note the PID number.

[*]Kill the process.[LIST][*]**kill 4329** (replace 4329 with the PID number from above)[/LIST]

[*]Restart apache.[LIST][*]**sudo /etc/init.d/apache2 restart**[/LIST]
[/LIST]

---

