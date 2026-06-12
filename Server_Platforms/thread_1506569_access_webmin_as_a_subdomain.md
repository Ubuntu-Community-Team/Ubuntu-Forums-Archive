---
title: "access webmin as a subdomain"
date: 2010-06-10
forum: Server Platforms
---

### Post by Zynon on 2010-06-10
Hello, I am using webmin pannel as a way to administer my box and works really good. I am able to access it great from any external IP out side of the home network but not able to from work. I assume it has to do with the firewall that we have here.
 
So what I am trying to do is to use webmin as a subdomain on port 80 like any other website that I have on my box uses.
 
I found a site from google that explains how to do this but I get an error when restarting apache. I dont have very much experiance with apache to know what this is refering to.
 
Here is the steps that i took.

[INDENT]$ sudo a2enmod proxy
[/INDENT]Create a configuration file at /etc/apache2/sites-available/webmin and paste the following code in:
[INDENT]<IfModule mod_proxy.c><VirtualHost *:80> **# Don't forget to customise the following line to your actual subdomain:** ServerName webmin.example.com **# The following URLs are for your Webmin server. If Webmin is on a different machine, change these:** ProxyPass / [http://localhost:10000/](http://localhost:10000/) ProxyPassReverse / [http://localhost:10000/](http://localhost:10000/) <Proxy *> Order Allow,Deny Allow from all </Proxy></VirtualHost></IfModule>
[/INDENT]Then, enable the Virtual Host configuration you have just created:
[INDENT]$ sudo a2ensite webmin
[/INDENT]Now restart Apache:
[INDENT]$ sudo invoke-rc.d apache2 restart Now when I go to restart the apache server I get this error message.brent@kcpcrepair:~$ sudo invoke-rc.d apache2 restart
[sudo] password for brent:
* Restarting web server apache2 [Thu Jun 10 12:54:06 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
... waiting [Thu Jun 10 12:54:07 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results 
[/INDENT]

---

### Post by duceduc on 2010-12-29
I, too, would like to access webmin using a subdomain. I have tried the above suggestion but when I access the link I get a 500 internal error.

I have webmin setup using ssl connection and this may be my problem but I don't know how to remedy it.

Here is my virtual host file.

```
<IfModule mod_proxy.c>
<VirtualHost *:80>
ServerName sub.domain.com
ProxyPass / https://localIP:10000/
ProxyPassReverse / https://localIP:10000/

 <Proxy *>
   Order Allow,Deny
   Allow from all
 </Proxy>

  </VirtualHost>
 </IfModule>

```

---

### Post by James78 on 2010-12-29
I'm guessing the order allow,deny stuff is what's giving you the 500 internal error.

Remove the <Proxy *> block. Does it work fine after? It's probably related to that then. Try this afterward (notice the case):
```
<Proxy *>
  Order allow,deny
  allow from all
</Proxy>
```

Does it still not work? Still a 500 internal server error? It might be related to webmin. Check the apache and webmin error logs, they might state something useful.

---

### Post by duceduc on 2010-12-29
james78,

Thanks for your reply. I've deleted the code suggested and I get a 'Forbidden-You don't have permission to access / on this server' error.

I've tried your code (lower case) and I get the internal error once again.

---

### Post by James78 on 2010-12-29
It's probably Webmin. Check /var/log/apache2/error.log and /var/webmin/miniserv.error

If you find any errors regarding this in there, please post the related part(s).

From [this]("http://www.virtualmin.com/node/7334") thread, I've gathered you might need to do something in Webmin. Try ...
> ... you need one IP address dedicated to Webmin. In the Webmin Ports and Addresses page, you can set which address Webmin listens on. Make it the IP of "panel.example.com", and put no virtual servers on this IP address.

---

### Post by duceduc on 2010-12-29
I see no log pertaining to my issue in the miniserv.error. In the apache erorr.log, I see this.

> 
[Thu Dec 30 12:35:09 2010] [error] [client 192.168.1.1] client denied by server configuration: proxy:[http://192.168.1.135:10000/favicon.ico](http://192.168.1.135:10000/favicon.ico), referer: [http://sub.domain.com/](http://sub.domain.com/)
[Thu Dec 30 12:35:10 2010] [error] [client 192.168.1.1] client denied by server configuration: proxy:[http://192.168.1.135:10000/](http://192.168.1.135:10000/)
[Thu Dec 30 12:35:10 2010] [error] [client 192.168.1.1] client denied by server configuration: proxy:[http://192.168.1.135:10000/favicon.ico](http://192.168.1.135:10000/favicon.ico), referer: [http://sub.domain.com/](http://sub.domain.com/)


---

### Post by James78 on 2010-12-29
Can you go to Webmin Configuration -> Webmin Ports and Addresses, and set which address Webmin listens on to the IP of your sub.domain.com? Also, for some reason they said not to put any virtual servers on this IP address.

---

### Post by duceduc on 2010-12-29
I am confused at this point. That quote is asking for a static ip I don't have. 
My ip is dynamic. If I set that ip address to the subdomain it is on, when it changes, it will not resolve to the new ip, correct?

---

### Post by James78 on 2010-12-29
Correct. There are ways to get around this however. You could use a service like NoIP or DynDNS. They provide a static IP which redirects all traffic to your IP. You install a client program on your computer which continurally updates the IP they point to. For a basic thing like this, you won't have to pay anything (free).

---

### Post by blaguman on 2011-02-07
Hi guys,

I was stuck on the same problem, and it's now FIXED for me.

In the available Apache's modules, there's more than "proxy". Enabling proxy_http fixed the problem for me :)

```
a2enmode proxy_http
```

Hope that helps!

---

