---
title: "Local network, multiple websites on ubuntu server box"
date: 2011-06-19
forum: Server Platforms
---

### Post by Nouman on 2011-06-19
Hey guys, thanks for reading.

So I just installed ubuntu server on a spare PC I had laying around, in hopes of using it to develop/test my sites more easily across multiple computers in house (switching from Mac, macbook, and windows machines--darn IE testing)

I got the server up and running, and I can access it across all my machines using [http://192.168.1.137/](http://192.168.1.137/)

Now, my question is how to I host multiple sites on this box, and even dedicate nice URL names for each (I'm fine with having to configure this on each machine)

Any direction is welcome, thanks again!

---

### Post by ian dobson on 2011-06-19
Hi,

You just need to add your virtual hosts to /etc/apache2/apache2.conf

```
    <VirtualHost *>
    ServerName xxxx
    ServerAdmin xxx
    DocumentRoot "/data/apache/clan-faog/htdocs"
    DirectoryIndex index.html index.htm index.php
    ErrorLog "/data/apache/clan-faog/logs/error.log"
    CustomLog "/data/apache/clan-faog/logs/access.log" combined
    CustomLog "/data/apache/clan-faog/logs/deflate.log" deflate
    ScriptAlias "/cgi-bin" "/data/apache/clan-faog/cgi-bin/"
    </VirtualHost>
```

Apache will then use the host name supplied by the client ([http://host-one](http://host-one), [http://host-two](http://host-two))

Regards
Ian Dobson

---

### Post by Nouman on 2011-06-19
Hey Ian, thanks for the help so far.

In my 'apache2.conf', it says :
> 
# Include the virtual host configurations:
Include sites-enabled/

That folder currently just holds a link to the default file located in sites-available

so I navigate to sites-available, and I created a file 'testsite.dev' with the following:

```
 <VirtualHost *>
    ServerName testsite.dev
    ServerAdmin nouman
    DocumentRoot "/var/www/testsite"
    DirectoryIndex index.html index.htm index.php
    ErrorLog "/data/apache/clan-faog/logs/error.log"
    CustomLog "/data/apache/clan-faog/logs/access.log" combined
    CustomLog "/data/apache/clan-faog/logs/deflate.log" deflate
    ScriptAlias "/cgi-bin" "/data/apache/clan-faog/cgi-bin/"
</VirtualHost>

``` 

then created a symbolic link from to the file in /etc/apache2/sites-enabled

after trying service restart, I get:

> [Sun Jun 19 12:13:07 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
Action 'start' failed.
The Apache error log may have more information.
   ...fail!


not sure what I'm doing wrong.

thanks!

---

### Post by ian dobson on 2011-06-19
Hi,

You need to make sure that the directories pointed to by ErrorLog ,CustomLog ,CustomLog ,ScriptAlias actually exist.

Regards
Ian Dobson

---

### Post by Nouman on 2011-06-19
Good point :) copying and pasting without reading!

I've changed it to just have:

```

<VirtualHost *>
        ServerName testsite.dev
        ServerAdmin nouman@me.com 
        DocumentRoot /var/www/testsite         
</VirtualHost>

```

Apache starts without issue now--thanks!

My next question would be: what's the best way to access this through another computer? The default url [http://192.168.1.137](http://192.168.1.137) works, and I can easily add a host record for this on other machines, but how I would point to testsite.dev?

thanks again!

---

### Post by drdos2006 on 2011-06-19
Here is how I did my development.
I put the CMS in /var/www/cms, HTML pages in /var/www/html and the PHPBB3 pages in /var/www/phpbb3. Using your IP address I would access each separate development with:
for the CMS 
[http://192.168.1.137/cms/index.php](http://192.168.1.137/cms/index.php) 
for the html 
[http://192.168.1.137/html/index.html](http://192.168.1.137/html/index.html) 
for the forum
[http://192.168.1.137/phpbb3/index.php](http://192.168.1.137/phpbb3/index.php) 

regards

---

### Post by Nouman on 2011-06-19
That's a good, but for general knowledge I'd love to know it's done through virtual hosts

---

### Post by ian dobson on 2011-06-20
Hi,

If add entries to your hosts file on the client, that all point to the ip address of your server, you can then access the virtual hosts through [http://virtual-host](http://virtual-host)

This'll work under windows and linux. You just need to findout where the hosts file is.

Regards
Ian Dobson

---

### Post by Nouman on 2011-06-20
Hey Ian,

so here is how I've written my hosts file (on client machine)

```

192.168.1.137 web-server
192.168.1.137 testsite.dev

```

visiting [http://web-server](http://web-server) works, but visiting [http://testsite.dev](http://testsite.dev) doesn't load the virtual host entry from the server, instead loads the same as web-server does.

I'm wondering how to have testsite.dev (on client) point to the virtual host entry for testsite.dev on the server:

> 
<VirtualHost *>
        ServerName testsite.dev
        ServerAdmin [email]nouman@me.com[/email]
        DocumentRoot /var/www/testsite
</VirtualHost>


thanks again!

---

### Post by ian dobson on 2011-06-21
Hi,

That should work, I'll have a look at my configuration tonight, so see if you need to change anything else.

Regards
Ian Dobson

---

### Post by Nouman on 2011-06-23
Ian, thanks for all your help. I had messed up my virtual host files and after deleting them all and starting fresh, it is working.

Summary for anyone interested:

create virtual host file for domain (example.com) in /etc/apache2/sites-available/example.com

in the file, put:

```
<VirtualHost *:80>
  DocumentRoot /var/www/example.com/
  ServerName  example.com
</VirtualHost>

```

copy file into /etc/apache2/sites-enabled

restart apache2 (service apache2 restart)

On your other computers, modify the hosts file and put:
ip-address-for-server example.com

and it works!

thanks again guys.

---

