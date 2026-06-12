---
title: "Apache - Can't connect to IP-based virtual server"
date: 2012-12-28
forum: Server Platforms
---

### Post by geoffm on 2012-12-28
Trying to setup an IP-based virtual server so that I can get my partner to connect on his drupal website I'm working on locally.
I've been following the little instructions there are in the official [Apache doc]("http://httpd.apache.org/docs/2.2/vhosts/ip-based.html") - to no avail. My browser always says can't connect to server.  Here are the relevant parts of config files.

/etc/apache2/sites-available/default
```
<VirtualHost <removedip>:80>
        ServerAdmin webmaster@localhost
        ServerName <removedip>
        DocumentRoot /var/www
        <Directory />

```

/etc/apache2/ports.conf
```
Listen 80
```

/etc/apache2/httpd.conf
```
ServerName <removedip>
```

I have another virtual host that's name-based, which works. I don't know why it won't connect; I'm doing as the manuals say. If someone can point out where I'm wrong it could prove quite helpful.

**All the <removedip> sections are just the OP's ip** -sandyd

---

### Post by thnewguy on 2012-12-28
Is it possible you are behind a router? If I try to connect to a machine on my LAN using my external (public) IP address then the router blocks the connection. Also, I think the "Listen" parameter is supposed to have a full IP address and port number for this sort of set up.

---

### Post by volkswagner on 2012-12-29
You should not post your public ip in this or any forum.

You say you have a working virtual host, is it accessible from outside your LAN?  Can you post the working file?

From inside your LAN go to canyouseeme.org and see if port 80 is open.  If port 80 is not open you need to check router settings or see if your ISP blocks port 80.

Do you have more than one public ip?  If you have only one public ip, how will ip based virtual hosts help?

I suggest basing your setup on your working vhost.  Use sub directories rather than virtual hosts.  If you have a working site at /var/www/site1 which is accessed by [http://site1](http://site1) or [http://192.xxx.xxx.xxx](http://192.xxx.xxx.xxx) create your second site a sub directory inside /var/www/site1/site2.  Then you can access the second site by specifying the sub dir in the url like [http://site1/site2](http://site1/site2) or [http://192.xxx.xxx.xxx/site2](http://192.xxx.xxx.xxx/site2).

---

