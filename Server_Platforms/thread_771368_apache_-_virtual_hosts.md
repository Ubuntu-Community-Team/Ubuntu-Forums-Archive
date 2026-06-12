---
title: "apache - virtual hosts"
date: 2008-04-27
forum: Server Platforms
---

### Post by jk111 on 2008-04-27
Hello all,

I have set up apache on ubuntu server edition. I have everything running but I am having a very hard time setting up virtual hosting. I am using ssh to get into the server and change all the configuration files.

First, in /etc/apache2/sites-available, I have my own (new) file that i called example.exampledomain.com.conf

That file looks like this:

<VirtualHost example.exampledomain.com>
ServerAdmin [email]example@example.com[/email]
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.example.com
ServerAlias [www.example.exampledomain.com](www.example.exampledomain.com)
DocumentRoot /home/myusername/public_html/example.exampledomain.com
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>

I have tried everything but still no luck. I have also tried the a2ensite but it says that site is already enabled. When I browse to my site, I get the normal, it works message instead of the index.html file I placed in my document root.

What am I doing wrong?

Thanks,

jk111

P.S. I also have a link to example.exampledomain.com.conf in /etc/apache2/sites-enabled

---

### Post by reedox.com on 2008-04-27
```

<VirtualHost *:80>
    ServerAdmin example@example.com
    DocumentRoot /home/myusername/public_html/example.exampledomain.com
    ServerName server.example.com
    ServerAlias dev.example.com www.dev.example.com
    ScriptAlias /awstats/ /usr/lib/cgi-bin/
    CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>

```
then
```
/etc/init.d/apache2 restart
```
if you have any problems check the log.

---

### Post by jk111 on 2008-04-27
I get the message:  _default_ virtualhost overlap on port 80, the first has precedence.

When i browse to both of my sites, the same index.html file is shown although they do differ in the document root.  

What did I do wrong?

Thanks

---

### Post by jasonbrisbane on 2008-04-27
Hi,

I found this works on my Ubuntu PC:
I copied the Default from the sites-available directory, 
removed the NameVirtualHost, 
added the Servername (and ServerAlias, in your case), 
changed DocumentRoot 
and restarted apache2. 

Works like a charm for me.
Juts thought I'd share.

---

### Post by jk111 on 2008-04-28
Although I do not get any errors, both my domains open to the same index file even though they differ and their document roots are different.

---

