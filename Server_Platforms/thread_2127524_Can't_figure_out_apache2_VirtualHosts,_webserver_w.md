---
title: "Can't figure out apache2 VirtualHosts, webserver won't even start"
date: 2013-03-20
forum: Server Platforms
---

### Post by DerpishCat on 2013-03-20
Hello once again Ubuntu forums, I need help, again.
This time it's about apache2, and VirtualHosts.

Going to jump straight into the problem:
So I want [www.derpnet.nu]("http://www.derpnet.nu") (and just derpnet.nu) to send the visitor to one place, and map.derpnet.nu to another.
I tried following [this]("http://www.debian-administration.org/articles/412") guide, only leading to me breaking everything...

I have no clue what I'm doing wrong, so I'll just paste the configs.

```
<VirtualHost *:80>
        ServerAdmin derpishcat@derpnet.nu
        ServerName  www.derpnet.nu
        ServerAlias derpnet.nu

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/website/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/website/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/website/logs/error.log
        CustomLog /var/www/website/logs/access.log combined
</VirtualHost>
```
```
<VirtualHost *:80>
        ServerAdmin derpishcat@derpnet.nu
        ServerName  map.derpnet.nu
        ServerAlias derpnet.nu

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/map/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/map/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/map/logs/error.log
        CustomLog /var/www/map/logs/access.log combined
</VirtualHost>
```
The error I'm getting:
```
derpishcat@DerpNet:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Mar 20 15:08:24 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Wed Mar 20 15:08:24 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Wed Mar 20 15:08:24 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
Action 'start' failed.
The Apache error log may have more information.
                                                                                                                                                                 [fail]


```

If you need to see any more configs, let me know, I appreciate all help!

**EDIT:** Crap, I just realized I misspelled apache2, can a mod rename the thread please?

---

### Post by sandyd on 2013-03-20
You have a ServerAlias line that is not needed.

Can you also make sure that you are specifying your ip address in your virtualhosts (don't post the ips here!), so that it looks like

```

<VirtualHost ip-address-here:80>
```
You likely have a
```

<NameVirtualHost ip-address-here:80>
``` which can't be mixed with
```

<VirtualHost *:80>
```

---

### Post by DerpishCat on 2013-03-20
Thanks for the reply, while typing this I just figured out one of the problems, I simply had forgot to type in :80 in my virtual.conf (in conf.d)
Sadly the problem with the server not wanting to start, is remaining.

```
derpishcat@DerpNet:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Mar 20 16:34:04 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
Action 'start' failed.
The Apache error log may have more information.
                                                                                                                                                                 [fail]
```
I have no idea what to do, I'm just doing trial and error on this, and failed quite hard :/ (The webserver has "just worked" until now, so this is pretty much the first time I actually try do something advanced)

**EDIT:** After fighting with this for hours, and finding out that it isn't even working if I copy over the entire default config, I just give up.
I've had enough of this, and I'll just go back to what I had before, so I can get my website working.

---

### Post by koenn on 2013-03-20
just a couple of hours and you're ready to give up ?  

it's fairly easy.

the basic config is this :
```

NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.domain.tld
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
ServerName www.otherdomain.tld
DocumentRoot /www/otherdomain
</VirtualHost>

```
(straight from [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) - 0.18 sec google search :) no need for hours of blind trial and error )

try and see  if you can get the above (adapted for your  paths and names) to work. If it doesn't, then give up.

---

### Post by cariboo on 2013-03-21
I'd suggest you check the logs, as the error message said, they are located in /var/log/apache2

---

### Post by DerpishCat on 2013-03-21
> **koenn said:**
> just a couple of hours and you're ready to give up ?  

it's fairly easy.

the basic config is this :
```

NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.domain.tld
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
ServerName www.otherdomain.tld
DocumentRoot /www/otherdomain
</VirtualHost>

```
(straight from [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) - 0.18 sec google search :) no need for hours of blind trial and error )

try and see  if you can get the above (adapted for your  paths and names) to work. If it doesn't, then give up.
Oh crap, was I supposed to add stuff into httpd.conf? I thought I were supposed to make files in sites-available and then link them...
Urgh, I'll try this and then return...

**EDIT:**
I edited httpd.conf, the stuff marked with bold is the newly added stuff.
```
[B]NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.derpnet.nu
DocumentRoot /var/www
</VirtualHost>

<VirtualHost *:80>
ServerName map.derpnet.nu
DocumentRoot /home/derpishcat/test
</VirtualHost>[/B]

<FilesMatch "\.(gif|jpg|png)$">
ErrorDocument 404 /stuff/404.png
</FilesMatch>
```
(Thought it'd be better if I just paste it all, seeing how I seem to fail with much else :()

It still tells me "NameVirtualHost *:80 has no VirtualHosts", but at least starts up with "OK".
But it does work, should I just remove NameVirtualHost?

---

### Post by SeijiSensei on 2013-03-21
The NameVirtualHost directive is included in /etc/apache2/ports.conf by default, and httpd.conf is deprecated.  The correct method as you describe is to create the sites in /etc/apache2/sites-available and use a2ensite to create the appropriate symlinks in /etc/apache2/sites-enabled.

Do you see any more detailed error information in /var/log/apache2/error.log?

---

### Post by DerpishCat on 2013-03-21
> **SeijiSensei said:**
> The NameVirtualHost directive is included in /etc/apache2/ports.conf by default, and httpd.conf is deprecated.  The correct method as you describe is to create the sites in /etc/apache2/sites-available and use a2ensite to create the appropriate symlinks in /etc/apache2/sites-enabled.

Do you see any more detailed error information in /var/log/apache2/error.log?
As everything (except that error on startup, but I'll deal with it later) seems to be working, and I'm currently working on adding more virtualhosts (which seems to work just fine), I'll just be using this method instead.
And no, I could only find 404 errors for stuff that I had linked and then removed from the site.

Thanks for all the help guys, I'll mark this as solved now.

**EDIT:** It seems I cannot mark this as solved, I guess I'll have to ask a mod to do that...

---

