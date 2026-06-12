---
title: "ProxyPassReverse not working..."
date: 2009-11-09
forum: Server Platforms
---

### Post by shirubia on 2009-11-09
Hello all, I'm a complete noob to Ubuntu and Apache.. and am trying to get ProxyPassReverse to work but with no luck. I've Googled but still can't seem to get it to work. This is what I have gotten so far...

1. I've got Ubuntu 9.10 running in a Virtual Machine
2. Installed Apache 2.2
3. Enabled Mod Proxy (sudo a2enmod proxy)
4. Restarted Apache (sudo init.d/etc/apache2 restart)
           I get this comment: 

Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

5. Insert the following at the very bottom (but before </VirtualHost> tag) of my default file (sudo gedit /etc/apache2/sites-available/default)

ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>
ProxyPass /test [http://www.google.com](http://www.google.com)
ProxyPassReverse /test [http://www.google.com](http://www.google.com)

6. I then save the file and go to [http://localhost/test](http://localhost/test)
7. I get the following message:

**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.

Any help is much appreciated!

---

### Post by cdenley on 2009-11-09
First of all, what exactly are you trying to accomplish? Why did you use "/mail" for ProxyPassReverse? Also, did you try
```

sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart

```

You don't want to insert anything at the very bottom of your site configuration. It should be within the "VirtualHost" tag, otherwise it will be a global setting and apply to all hosts.

---

### Post by shirubia on 2009-11-09
> **cdenley said:**
> First of all, what exactly are you trying to accomplish? Why did you use "/mail" for ProxyPassReverse? Also, did you try
```

sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart

```You don't want to insert anything at the very bottom of your site configuration. It should be within the "VirtualHost" tag, otherwise it will be a global setting and apply to all hosts.

I have a website (site a) hosted on another server (and another geographic location). I'm looking to host a section of that website (site b) on my home server, but I want this section to have the same url as the original site. After doing some googling i found this ProxyPassReverse. But I can't seem to get it to work.

I'm sorry,  that "/mail" is actually suppose to be "/test", I changed the original post. I also I meant to say I put the ProxyPassReverse stuff at the bottom, BUT before the </VirtualHost> tag.

I JUST TRIED a2enmod proxy_http AND IT WORKS~! wow, thank you so much man.

I've read on a couple forums and they all say to do a2enmod proxy_**html**, and not **http **and every time I tried html I would get a "module does not exist!" msg... such a simple mistake but you cleared it all up.

It works now, but images are not rendering correctly, links are also broken... any advice?

---

### Post by shirubia on 2009-11-09
I've installed libxml2 and mod proxy_html via Synaptic Package Manager. I've also enabled the proxy_html (a2enmod proxy_html) but have no idea where to insert ProxyHTMLURLMap... Any advice?

---

### Post by cdenley on 2009-11-10
> **shirubia said:**
> I've installed libxml2 and mod proxy_html via Synaptic Package Manager. I've also enabled the proxy_html (a2enmod proxy_html) but have no idea where to insert ProxyHTMLURLMap... Any advice?

It can be used anywhere, so it all depends what kind of scope you want it to have. You probably want to use it for a single site, so use it within the site's "VirtualHost" tag.

---

### Post by badger_fruit on 2009-11-10
I found this from the [email]users@apache.org[/email] mailing list; maybe it might help?

The question was:-

> We have a corporate site at: [http://www.example.com](http://www.example.com) We are 
> implementing a new webshop and our Marketing dep. decided om: 
> [http://www.example.com/order](http://www.example.com/order)
> 
> Due to the nature of the requests and for performance, I would like to host the web shop on two different webservers.
> I thought of mod_proxy to create a reverse proxy on the webservers of example.com.
> 
> Are there any other ways to achieve this?
> They do not want to expose a different name then [www.example.com/order](www.example.com/order)

and the reply was:-


```

<VirtualHost 0.0.0.0:80>
    ServerName    "www.example.com"
    DocumentRoot "/var/www/html"

    ProxyPass        /order/ http://backend-order-server/order/
    ProxyPassReverse /order/ http://backend-order-server/order/

    etc...

</VirtualHost>

```

---

### Post by shirubia on 2009-11-10
Thanks for all the replies... but still no luck. This is what I have in my default file (/etc/apache2/sites-available/default)

```
<VirtualHost *:80>    
    ServerAdmin webmaster@localhost
    
   [COLOR=Green] ServerName cs.prxypsrevse.com[/COLOR]
    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

[COLOR=Green]ProxyRequests Off
ProxyHTMLExtended On

<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /test/ http://www.google.com/
ProxyPassReverse /test/ http://www.google.com/
ProxyHTMLURLMap http://www.google.com /test

[COLOR=Black]</VirtualHost>[/COLOR][/COLOR]
```Lines in green are things I added.

---

### Post by cdenley on 2009-11-10
Why are you using mod_proxy_html?

---

### Post by shirubia on 2009-11-10
> **cdenley said:**
> Why are you using mod_proxy_html?

I'm using mod proxy_html because all the links, images, etc. are broken when navigating to the website (google). In the above code, the google page only renders txt. The google image doesn't show up. I thought mod proxy_html would fix the google image URL...

[http://apache.webthing.com/mod_proxy_html/](http://apache.webthing.com/mod_proxy_html/)

---

### Post by cdenley on 2009-11-10
I understand now. You need to alter the page so links such as "/path/to/file" are changed to "/test/path/to/file". You need something like this:
```

ProxyPass /test/ http://www.google.com/
ProxyPassReverse /test/ http://www.google.com/
SetOutputFilter INFLATE;proxy-html;DEFLATE
ProxyHTMLURLMap / /test/

```

---

### Post by shirubia on 2009-11-10
> **cdenley said:**
> I understand now. You need to alter the page so links such as "/path/to/file" are changed to "/test/path/to/file". You need something like this:
```

ProxyPass /test/ http://www.google.com/
ProxyPassReverse /test/ http://www.google.com/
SetOutputFilter INFLATE;proxy-html;DEFLATE
ProxyHTMLURLMap / /test/

```

**!!!!!~ THANK YOU~ it works perfectly~**

I'm pretty new to all of this stuff, and the jargon ([http://httpd.apache.org/docs/2.2/mod/core.html#setoutputfilter](http://httpd.apache.org/docs/2.2/mod/core.html#setoutputfilter)) makes it difficult for me to understand the underlying concepts.. do you think you can explain to me (as if i was 7yrs old), what SetOutputFilter INFLATE;proxy-html;DEFLATE is doing? 

I know that the SetOutputFilter Directive is changing the links to include /test/, (still a little confused..) but what about INFLATE, proxy-html, DEFLATE?

Just curious for future reference..

Thanks again!!

---

### Post by cdenley on 2009-11-10
> **shirubia said:**
> 
do you think you can explain to me (as if i was 7yrs old), what SetOutputFilter INFLATE;proxy-html;DEFLATE is doing? 


With mod_proxy_html < version 3.1, you have to use "SetOutputFilter" to actually tell apache to pass documents through mod_proxy_html. However, if the user's browser supports compression, then google's web server will serve the page compressed, which mod_proxy_html will not be able to understand. That line decompresses documents (if compressed), runs it through proxy-html, then recompresses it (if supported).

---

