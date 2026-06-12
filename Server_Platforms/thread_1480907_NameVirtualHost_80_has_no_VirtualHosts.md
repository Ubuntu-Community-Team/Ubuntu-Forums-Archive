---
title: "NameVirtualHost *:80 has no VirtualHosts"
date: 2010-05-12
forum: Server Platforms
---

### Post by tapas_mishra on 2010-05-12
I have 5 websites running in a reverse proxy environment.
On main server 
I am getting this error
```

NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 12:18:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

```Where as there is a ServerName directive in all vhosts.On internal webservers also this problem is coming.
To check if vhost is having any problem I typed httpd -S and it said command not found.What should I check ?
Where as in /etc/hosts on main site I have named all the internal servers on which sites
have been forwarded.

I did 
```

apache2ctl --configtest
[Wed May 12 13:12:33 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 13:12:33 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 13:12:33 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 13:12:33 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed May 12 13:12:33 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```
What should I look for?

---

### Post by tapas_mishra on 2010-05-12
Okay finally I have been able to solve this problem.I am posting what made it work it may help some one else.
[http://www.movingtofreedom.org/2007/05/09/how-to-wordpress-on-ubuntu-gnu-linux/](http://www.movingtofreedom.org/2007/05/09/how-to-wordpress-on-ubuntu-gnu-linux/)
[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

 I could get a single site running, but never multiple sites correctly.   As soon as I added a second site, again with the “NameVirtualHost  yada-yada has no VirtualHosts”. 

Found lots of other people out there struggling with this.
On the apache reverse proxy server which redirects multiple domains to internal IPs 

 I removed the line

 ```
NameVirtualHost *:80 
```from the sites-enabled/abc.com
and changed ```
VirtualHost *:80
``` to```
 VirtualHost *
```
and created a file virtual.conf on reverse proxy server
it contains 
```

#
#  We're running multiple virtual hosts.
#
NameVirtualHost *


```
and on the client servers i.e. I am referring to the ones where I had actually hosted the site
I removed the NameVirtualHost *:80 line from the file where you configured your site that is /etc/apache2/sites-enabled/yoursite

you do not need to make virtual.conf on this machine.

I was getting an error not able to find out fully qualified domain name so on /etc/hosts
added one entry.

---

### Post by cdenley on 2010-05-12
You should only use "NameVirtualHost *:80" once. The only reason to use another "NameVirtualHost" line would be if you want a vhost to listen on a different port. In ubuntu 8.04, this line was in /etc/apache2/sites-available/default. In newer versions, this was moved to /etc/apache2/ports.conf.

---

### Post by tapas_mishra on 2010-05-12
Oh you mean to say that among various vhost files in /etc/apache2/sites-enabled/

I should mention name virtual host only in one of them.

---

### Post by cdenley on 2010-05-12
> **tapas_mishra said:**
> Oh you mean to say that among various vhost files in /etc/apache2/sites-enabled/

I should mention name virtual host only in one of them.

Typically. If you have vhosts binding to different interfaces or different ports, then you would need more. Depending on your version of ubuntu, they shouldn't be anywhere in /etc/apache2/sites-enable, but in /etc/apache2/ports.conf.

---

### Post by tapas_mishra on 2010-05-12
Okay thanks a lot for pointing that out.

---

### Post by stevedove on 2011-12-10
Hi am having the same prob but the thing is that am trying to host multiple sites & also use a static ip address & for some sites not only using the port 80 but also the 443 port the source i have got this info is from [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412) so how do i do it??? thank you for your reply in advance

---

### Post by tapas_mishra on 2011-12-10
[http://mightydreams.blogspot.com/2011/03/running-multiple-applications-in-lan.html](http://mightydreams.blogspot.com/2011/03/running-multiple-applications-in-lan.html)

---

### Post by wmoreno3 on 2012-12-30
I think that the best way may be:
1- Comment
```
#NameVirtualHost *:80
```
2- Add
```
[FONT=Courier New]Listen x.x.x.1:80[/FONT]
[FONT=Courier New]Listen x.x.x.2:80[/FONT]
[FONT=Courier New]...[/FONT]

```
3- Set vhosts
```
<VirtualHost x.x.x.1:80>
    ServerAdmin [EMAIL="webmaster@dummy-host.example.com"]webmaster@dummy-host.example.com[/EMAIL]
    DocumentRoot "/usr/local/docs/dummy-host.example.com"
    ServerName dummy-host.example.com
    ErrorLog "/var/log/dummy-host.example.com-error_log"
    CustomLog "/var/log/dummy-host.example.com-access_log" common
</VirtualHost>
<VirtualHost x.x.x.2:80>
    ServerAdmin [EMAIL="webmaster@dummy-host2.example.com"]webmaster@dummy-host2.example.com[/EMAIL]
    DocumentRoot "/usr/local/docs/dummy-host2.example.com"
    ServerName dummy-host2.example.com
    ErrorLog "/var/log/dummy-host2.example.com-error_log"
    CustomLog "/var/log/dummy-host2.example.com-access_log" common
</VirtualHost>
...
```
4- In order to see at WEB
```
        Alias /dummy-host.example.com /usr/local/docs/dummy-host.example.com
                AcceptPathInfo On
                <Directory /usr/local/docs/dummy-host.example.com>
                AllowOverride None
                Order Allow,Deny
                Allow from all
        </Directory>
        Alias /dummy-host2.example.com /usr/local/docs/dummy-host2.example.com
                AcceptPathInfo On
                <Directory /usr/local/docs/dummy-host2.example.com>
                AllowOverride None
                Order Allow,Deny
                Allow from all
        </Directory>
```
5- See Apache IP-based Virtual Host Support [HTML]http://httpd.apache.org/docs/2.2/vhosts/ip-based.html[/HTML]

---

