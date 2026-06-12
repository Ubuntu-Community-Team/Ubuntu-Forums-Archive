---
title: "Apache Multiple hosts defined only one page is served."
date: 2010-12-30
forum: Server Platforms
---

### Post by zbenta on 2010-12-30
Hi there you guys,

I have a server that host's several sites, recently I had to create a new server because the old one isn't good enough for me.
Ive installed apache2 on the new server and moved all the files from one server to the other.
I'm making tests in my local lan so I've edited my computer's hosts file to point to the name of each site to the local ip of the new server:

...
192.168.1.85 [www.mypage.com]("http://www.mypage.com")
192.168.1.85 svn.mypage.com
192.168.1.85 trac.mypage.com
...

I have all the site definition files in /etc/apache2/sites-available
I also have the used a2ensite to enable each page.

Whenever o use my browser to try and access each of the sites I always get the svn.mypage.com page and none of the others.

here is some debug info:
```

 sudo apache2ctl -S
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:*                    svn.mypage.com (/etc/apache2/sites-enabled/svn.mypage.com:1)
*:*                    trac.mypage.com (/etc/apache2/sites-enabled/trac.mypage.com:1)
*:*                    www.mypage.com (/etc/apache2/sites-enabled/www.mypage.com:1)
Syntax OK

```vi ports.conf

```

Listen 80
<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

I've tried enabling each site separately and they work fine, when I enable more than one site at the same time apache only returns one site.
I've googled around for tutorials to make sure I didn't miss anything while configuring apache and they all do as I've done.
Can anyone give me a hand on this one?

---

### Post by zbenta on 2010-12-30
I have found the solution for my problem.

I've edited /etc/apache2/httpd.conf and added the following:

NameVirtualHost 192.168.1.85:80

I also edited every virtual host and added the ip address of the server as follows:

<VirtualHost 192.168.1.85:80>

The following link helped me.
[http://superuser.com/questions/189012/apache2-2-2-14-setup-multiple-virtual-hosts-for-local-testing-configuration-err](http://superuser.com/questions/189012/apache2-2-2-14-setup-multiple-virtual-hosts-for-local-testing-configuration-err)

Will this still work when I move this server to our company datacenter and change the locla ip address with the external ip address of the server?

I believe that the moderators can close this thread.

---

