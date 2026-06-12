---
title: "add on domains"
date: 2007-07-24
forum: Server Platforms
---

### Post by alaskns2 on 2007-07-24
Ok, here goes, I have a server in my store that I host my own web site.  I just purchased two more domain names and I would like to ad them to the server.  I know I should be able to host more than one domain name on my server.  When I type in the new domain name to the address bar on the browser, I only come up with my original web page.  How do I get ubuntu to recognize the new domains and separate them.  Thanks  Alasknsw:confused:

---

### Post by Mr. C. on 2007-07-24
You need two things:

a) an A record at your registrar the points to your IP address
b) a virtual name based host in apache that has as its ServerName the host name from (a) above.

Add to your httpd.conf file (**locate httpd.conf** to find it)

```
NameVirtualHost *:80
 
<VirtualHost *>
ServerName name_in_a_above
DocumentRoot /var/www/your_sites_path
</VirtualHost>

```
and then reload apache.  See the examples in other config files for other virtual hosts.

MrC

---

