---
title: "[SOLVED] Apache 2.2.9, virtual hosts; two domains, one machine"
date: 2008-11-16
forum: Server Platforms
---

### Post by drodger on 2008-11-16
Hi--

I've browsed the set of virtual hosts related topics and followed the notes given within, and am still having problems.  I'd appreciate any pointers.

I have two domains: [www.netmeaning.org](www.netmeaning.org) and [www.revellecommunications.com](www.revellecommunications.com).  Both are pointing to the same IP address.  Currently, regardless of which I type into a browser, I see the content that is correctly hosted under the [www.netmeaning.org](www.netmeaning.org) Apache server, and the browser URL switches to [www.netmeaning.org](www.netmeaning.org) if I came in from the other address.

I'd like to define a new apache virtual host to put different content up on the revellecommunications.com domain.

So here's what I've got:
/etc/apache2/ports.conf:
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

(NOTE: There are no other NameVirtualHost references in the /etc/apache2 directory structure.)

Then I have:
/etc/apache2/sites-available/default:
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        ServerName [www.netmeaning.org](www.netmeaning.org)

        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
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

</VirtualHost>

Finally, I have:
/etc/apache2/sites-available/revellecommunications.com:
#
#  Example.com (/etc/apache2/sites-available/revellecommunications.com)
#
<VirtualHost *:80>
        ServerAdmin [email]dave@davidrodger.com[/email]
        ServerName  revellecommunications.com

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/www/revellecommunications/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/revellecommunications/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/revellecommunications/logs/error.log
        CustomLog /home/www/revellecommunications/logs/access.log combined
</VirtualHost>


As I see it, the port designation is correct in both places, but for some reason, even after ensuring that the sites are enabled, not just available, and restarting apache (with no errors on restart), all the traffic is routed to the default site.

Any ideas?

Thanks.

-dave

---

### Post by MJN on 2008-11-16
Add **ServerAlias [www.revellecommunications.com]("http://www.revellecommunications.com")** to your Revelle config, e.g.

```
ServerName revellecommunications.com
ServerAlias www.revellecommunications.com
```Mathew

---

### Post by randomstuff on 2008-11-16
I have had the same problem yesterday. What you need to do is the following. Inside the /etc/apache2/apache2.conf you should add the following directive:

```
NameVirtualHost *:80
```

I have put it almost at the end of the file, just before:

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

---

### Post by MJN on 2008-11-16
NameVirtualHost only needs specifying once - in this case it is in ports.conf and thus is parsed by the main config.

Mathew

---

### Post by drodger on 2008-11-16
Thanks; I was pretty sure that once was all that was needed, so I'm still stuck.

But thanks for trying, nevertheless.

I wonder if there's an issue with how i have the <Directory> stuff set up, perhaps?  Or a permissions issue?  But there are no apparent errors in error_log.

Thanks.

-d

---

### Post by drodger on 2008-11-16
> **MJN said:**
> Add **ServerAlias [www.revellecommunications.com](www.revellecommunications.com)** to your Revelleconfig, e.g.

```
ServerName revellceommunications.com
ServerAlias www.revellecommunications.com
```Mathew

Done; no joy.  And when I try to go to the site via: [http://revellecommunications.com](http://revellecommunications.com) or [http://www.revellecommunications.com](http://www.revellecommunications.com), same issue.

Other thoughts?  Thanks.

-d

---

### Post by MJN on 2008-11-16
It's working from where I'm standing!

(Hint: Restart your browser. Your 301 redirects are being cached)

Mathew

---

### Post by drodger on 2008-11-16
> **MJN said:**
> It's working from where I'm standing!

(Hint: Restart your browser. Your 301 redirects are being cached)

Mathew

You see two different bits of content?  I.e. on:
[http://www.netmeaning.org](http://www.netmeaning.org)

you see a blog,

and on:
[http://www.revellecommunications.com](http://www.revellecommunications.com)

you see an ugly plain HTML page?

I have restarted browser; still getting the blog content for both URLs.

Thanks for the help.

-d

---

### Post by drodger on 2008-11-16
> **MJN said:**
> It's working from where I'm standing!

(Hint: Restart your browser. Your 301 redirects are being cached)

Mathew

Well, I should know better than to disagree.  I dumped cache etc. (not just restarted browser) and all is well.

Thanks to Mathew for the assist.

-d

---

### Post by spiderbatdad on 2008-11-16
Yes, two different sites. Clear your browser cache. 

EDIT: lol you got it!

---

### Post by MJN on 2008-11-16
Phew!

---

