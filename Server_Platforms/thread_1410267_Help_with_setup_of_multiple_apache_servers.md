---
title: "Help with setup of multiple apache servers"
date: 2010-02-18
forum: Server Platforms
---

### Post by melsen on 2010-02-18
Hello everyone...

I'm hoping any of you can help me here..

What I'm trying to accomplish is the following.

I have 1 outside IP

I have domains names pointing to that IP, and then the firewall routes the traffic to one ip.

Now, if THAT server hosted all the websites, that wouldn't be a problem... but here's what I'm trying to do.

Server 1 = Firewall

Server 2 = Apache route

Server 3 = Hosting 1 apache website

Server 4 = hosting another apache website.


So basically I want server 1 to point all web traffic to server 2. Server 2 then - based on which domain name it is - points to either server 3 or server 4 where the website is running.

I've tried a LOAD of various configuration... messing with the httpd.conf file on server 2.. but I just can't seem to get it right.

Can someone give me a rundown of how I do this.. Thanks.

- Melsen

---

### Post by mbehamin on 2010-02-19
why don't you use virtual hosting?! 
anyway if you need to separate your server based the website domain. i recommend you to install apache , nginx or lighthttpd as a proxy web server. so that it has virtual host per domains with the root directory of other web-server machine. (some how its type of cache only server).

---

### Post by melsen on 2010-02-19
Uhmmm... did you not read my post?

I _AM_ running apache.. it says so specifically... but I have websites that has different needs, and server 3 is much better performing than server 2 in my house... which is why I want some websites on that servers, and the not so important ones with a low load to be placed on the other.

---

### Post by melsen on 2010-02-19
Now I just tried this:

Using Virtual_host and mod_proxy together

The following example allows a front-end machine to proxy a virtual host through to a server running on another machine. In the example, a virtual host of the same name is configured on a machine at 192.168.111.2. The ProxyPreserveHost On directive is used so that the desired hostname is passed through, in case we are proxying multiple hostnames to a single machine.

<VirtualHost *:*>
ProxyPreserveHost On
ProxyPass / [http://192.168.111.2/](http://192.168.111.2/)
ProxyPassReverse / [http://192.168.111.2/](http://192.168.111.2/)
ServerName hostname.example.com
</VirtualHost> 

It does seem to go a little further.. but now I get a 403 on it.. hrmmm

---

