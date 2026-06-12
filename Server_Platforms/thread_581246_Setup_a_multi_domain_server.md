---
title: "Setup a multi domain server"
date: 2007-10-19
forum: Server Platforms
---

### Post by trymbill on 2007-10-19
I've been having trouble getting my head around my question; "How can I setup a multi domain server with 2 servers?"  One server is an Apache Ubuntu server and the other one a IIS Win2k3 server.  I need to be able to use the Ubuntu server to some how make the browser display a web page from the win2k3 server when the hostname is "mydomain.com" and from the Ubuntu server when the hostname is "mydomain2.com" ...

... how can I do this?  What is the best and easiest way?  Has anyone written a "Step by step on; How to setup a multi domain server with Ubuntu" ??

I hope some one can help me,
Magnus

---

### Post by bukwirm on 2007-10-19
You probably want to look at Apache virtual servers.

---

### Post by trymbill on 2007-10-19
I've tried that, but I can't seem to figure out how to.

Do you know of a good tutorial or something to get me started?

---

### Post by twistedtwig on 2007-10-19
proxypassreverse!!!

I have a similar setup.. ubuntu box is my main server... firewall dhcp, dns apache etc... my main website runs off of apache on the ubuntu server but I have an ASP.NET site on the windows box.  I don't want to port forward as that feels messy so I have used proxy pass reverse to make it "Look" like the site is coming from the ubuntu box.

say for example you want your example.com/windows/ folder to come from your windows box then you would do something like:

proxypass /windows/ [http://192.178.6.2/](http://192.178.6.2/)
proxypassreverse /windows/ [http://192.178.6.2/](http://192.178.6.2/)

(hope that is right as I am doing it from memory).

this assumes that your example.com/windows/ is on ubuntu but the folder will display the site from the windows box with is the default (root level) site there.  also the IP address is the IP of the windows box.

N.B. when putting the request into a browser you must have the trailing slash as apache wont know to put it in for you like it normally does.

Hope this makes some sense

---

### Post by trymbill on 2007-10-19
Where do I put this code in? : - /

---

### Post by twistedtwig on 2007-10-19
i put mine in apache.conf file originally.. then i put it in my own file in the same folder and just did an include... this was so if I did an upgrade I have all my changes seperated.

---

### Post by trymbill on 2007-10-22
Ok, that's clever :)

How did you include it?  From apache.conf or from another file?

Sincerely,
Magnus

---

### Post by twistedtwig on 2007-10-22
just did the include from the bottom of the apache.conf file

---

### Post by trymbill on 2007-10-22
> say for example you want your example.com/windows/ folder to come from your windows box then you would do something like:

proxypass /windows/ [http://192.178.6.2/](http://192.178.6.2/)
proxypassreverse /windows/ [http://192.178.6.2/](http://192.178.6.2/)

What if I want a domain name like "windowsrocks.com" to com from my windows machine (192.168.0.2) but "linuxrocks.com" to com from my linux machine?

I have my linux machine on port 80, it's displaying the web page and everything works great, but then I need to access Exchange and one website I have on my windows machine and I don't want to use port forwarding.  How can I configure apache to use my windows machine if the host header (domain) is windowsrocks.com ??

I have WebMin, so if you know how to do it there, that would be great :)

Thanks for all the replies!

---

### Post by twistedtwig on 2007-10-22
my guess would be to use a combination of proxypass reverse with virtualhosts....

someone with more experience than me could hopefully explain how to do it fully but I would assume that you would setup two virtual hosts.. one that points at linuxrocks and the other at windowsrocks, which would have the proxy pass reverse directive in it.

I think!!

---

### Post by KCPokes on 2007-10-22
> **twistedtwig said:**
> my guess would be to use a combination of proxypass reverse with virtualhosts....

someone with more experience than me could hopefully explain how to do it fully but I would assume that you would setup two virtual hosts.. one that points at linuxrocks and the other at windowsrocks, which would have the proxy pass reverse directive in it.

I think!!

You are correct.  Essentially your linuxrocks.com and windowsrocks.com would be virtual servers, each with a configuration entry in the virtual servers section of your httpd.conf.  For the windowsrocks.com, you'd utilize the proxy functionality to send the traffic to your windows server, whereas the linuxrocks.com requests would remain local.  

For example:

```

<VirtualHost 192.168.1.100>
    ServerAdmin you@windowsrocks.com
    DocumentRoot /var/www/
    ServerName www.windowsrocks.com
    ProxyPass / http://192.168.1.101/
    ProxyPassReverse / http://192.168.1.101/
    DirectoryIndex index.html
</VirtualHost>
<VirtualHost 192.168.1.100>
    ServerAdmin you@linuxrocks.com
    DocumentRoot /var/www/
    ServerName www.linuxrocks.com
    DirectoryIndex index.html
    ScriptAlias /cgi-bin/ "/var/www/cgi-bin/"
</VirtualHost>

```

---

### Post by trymbill on 2007-10-23
I got it working :)

Here is my vhosts.conf file:

```

<VirtualHost *>
ServerName coachingwomen.org
ServerAlias coachingwomen.org *.coachingwomen.org
ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass / http://192.168.0.2/
ProxyPassReverse / http://192.168.0.2/
</VirtualHost>

<VirtualHost *>
ServerName coachingwomen.biz
ServerAlias coachingwomen.biz *.coachingwomen.biz
ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass / http://192.168.0.2/
ProxyPassReverse / http://192.168.0.2/
</VirtualHost>

<VirtualHost *>
ServerName coachingwomen.info
ServerAlias coachingwomen.info *.coachingwomen.info
ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass / http://192.168.0.2/
ProxyPassReverse / http://192.168.0.2/
</VirtualHost>

<VirtualHost *>
ServerName test.trymbill.is
ServerAlias *.trymbill.is 192.168.0.21 localhost
ServerAdmin myemaill@trymbill.is
DocumentRoot /var/www
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

</VirtualHost>

```

Do you see anything wrong with this conf file?

The only thing that I have a problem with now is that exchange wont open like it did but I'll probably just fix that with port forwarding.

Thanks for the help!

---

### Post by twistedtwig on 2007-10-23
how do you mean it wont open?  is it that it looks funny?

I have had an issue with an ASP.NET treeview not displaying through proxypass.. don't really know how to fix that apart from just not using it!

---

