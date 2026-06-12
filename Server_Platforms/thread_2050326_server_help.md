---
title: "server help"
date: 2012-08-30
forum: Server Platforms
---

### Post by FatPaulie on 2012-08-30
Hello

First of all I must tell you that I'm new with all this stuff, but I try to learn as much as possible.. 
So here's the thing. The goal was to setup a preview Wordpress blog for a firend of mine. I installed xubunut, than installed apache2, than php5 and mysql and in the end Wordpress. So now Wordpress is working fine when when I tyoe localhost/wordpress in browser.
But when I tried to reach the blog from an outside connection it gets blocked since my ISP block port 80 on the inside. So by reading further I learn that I should change port in Apache2 configuration. I access the config file and after "Listen 80" line add "Listen 1234". After saving accesing through 80 works, but through 1234 does not. I've tried on default apache index.html file and I get 
"**Not Found** 
The requested URL / was not found on this server.
 Apache/2.2.22 (Ubuntu) Server at localhost Port 1234" message.

I also forwarded ports on my Netgear router on the correct IP, which happens to be 192.168.1.4, but when accessing localhost:1234 I still get the same message.

I would be glad if someone helps me with this or explaining me how to change ports and became visible from outside connections.

---

### Post by darkod on 2012-08-30
The port forwarding on the router should have an option to use different public and private ports, so that would probably be the easiest way.

For example, set the port forwarding to forward port 8080 to 192.168.1.4 port 80 (where your apache is listening to).

But from the outside you would need to enter with something like xxx.xxx.xxx.xxx:8080 or xxx.xxx.xxx.xxx:8080/wordpress

The point is the connection to arrive on 8080 (hopefully the ISP is not blocking that) and the router to divert it to 80.

---

### Post by FatPaulie on 2012-08-30
Thx darkod, but when setting port 1234 to trigger on port 80 (or the other side around), my router notices me that i should use port from number 1 to number 65535 excluding port 80.

what really bothers me is that i can connect using localhost:80 adress, but with adress localhost:1234 i can't. On the other hand, I've installed glftpd  listening on port 64553 and connecting with "ftp localhost 64553" works ok.

So, IMO, that means that the problem isn't in router, but there's something wrong with Apache. I'll try also setting port 8080, maybe something will change.

---

### Post by kennethconn on 2012-08-30
Have you reloaded Apache after you made changes (and exactly what are the changes you made)?
 
There seems to be two problems here.

---

### Post by BrianBlaze on 2012-08-30
> **FatPaulie said:**
> Thx darkod, but when setting port 1234 to trigger on port 80 (or the other side around), my router notices me that i should use port from number 1 to number 65535 excluding port 80.

what really bothers me is that i can connect using localhost:80 adress, but with adress localhost:1234 i can't. On the other hand, I've installed glftpd  listening on port 64553 and connecting with "ftp localhost 64553" works ok.

So, IMO, that means that the problem isn't in router, but there's something wrong with Apache. I'll try also setting port 8080, maybe something will change.

I would try 8080 or basically any port after 49152 since everything before it is either registered or well-known [http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers) ... but if you are having problems getting to it from outside your network I would definitely say it's a router problem or the fact you havent restarted the service ;)

---

### Post by FatPaulie on 2012-08-30
@kennethconn Yes, I've restarted it. Few times I rebooted the computer aswell.. Changes that I made are in ports.conf which looks like this
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 8080
listen 80
Listen 64551

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

```and in httpd.conf which was by default blank, but now contains 
```
ServerName localhost

```suggested by this ( [http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu](http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu) )article.

@BrianBlaze Well, I've also tried port 8080 and 64551 and the results are the same. [http://localhost:8080](http://localhost:8080) gives error 404 while on port 80 works ok. At any other port that I didn't include in ports.conf Firefox returns me "Unable to connect" error. So at the moment I'm not worying about outside connections since even connecting from local machine doesn't work as it should. :( 
Thats why I'm botherd by the fact that glftpd works fine on random port.

---

### Post by darkod on 2012-08-30
Don't bother with adding ports to apache. At least in my limited knowledge.

The point of the router changing the port is that to apache it will arrive on port 80, which is configured correctly and working.

If using 8080 doesn't work, either:
- it's also blocked
- the router is not configured correctly to pass 8080 to 80

Apache doesn't need to know anything about the port you select to use. The router already changed it before the packet got to apache. At least that's how I understand the process.

---

### Post by kennethconn on 2012-08-30
Wouldn't normally advocate this, but in your situation I would be tempted to test external access first by following what darkod said in first post. The web server is working for port 80 so a simple port forward rule on router should suffice.
 
As to getting it to work on an alternative port (locally or otherwise):
 
1) Did you investigate this:
 
```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
```
 
2) Ensure apache is listening (as opposed to not listening or another service listening) on the specified port.
 
This is what I meant by two different problems.

---

### Post by sandyd on 2012-08-31
> **FatPaulie said:**
> @kennethconn Yes, I've restarted it. Few times I rebooted the computer aswell.. Changes that I made are in ports.conf which looks like this
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 8080
listen 80
Listen 64551

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

```and in httpd.conf which was by default blank, but now contains 
```
ServerName localhost

```suggested by this ( [http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu](http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu) )article.

@BrianBlaze Well, I've also tried port 8080 and 64551 and the results are the same. [http://localhost:8080](http://localhost:8080) gives error 404 while on port 80 works ok. At any other port that I didn't include in ports.conf Firefox returns me "Unable to connect" error. So at the moment I'm not worying about outside connections since even connecting from local machine doesn't work as it should. :( 
Thats why I'm botherd by the fact that glftpd works fine on random port.
You will have to change your NameVirtualHost/VirtualHost statements to match the port changes.

Aside, leave it on port 80, and pick a port that your ISP does not block. Forward THAT port to ip-address-of-computer:80

---

### Post by FatPaulie on 2012-08-31
So today I reinstalled Xubuntu, installed apache2, php, mysql again, followed your advices and the problem persisted. Then i figured that error 404 pops out also on myphpadmin. So I googled that and applied this [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_Phpmyadmin_.26_mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_Phpmyadmin_.26_mysql-admin)
Now everything bworks fine, even the port trigering. Thx everybody for help.

---

