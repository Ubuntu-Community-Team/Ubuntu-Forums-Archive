---
title: "Apache Redirect, http://site.org to http://www.site.org"
date: 2012-05-21
forum: Server Platforms
---

### Post by vavr on 2012-05-21
Hi @ All,

I have set up a LAMP Server in Ubuntu 12.04 with a production site.

The A record for my domain points local in my server and the www using a CNAME points in the AKAMAI networks (for load balance-reliability etc).
e.g [http://site.org](http://site.org) - Local Server (Public IP Address)
     [http://www.site.org](http://www.site.org) - AKAMAI Network

In which way can i configure apache so all the http traffic will go/redirect in the www? 


thanks

---

### Post by volkswagner on 2012-05-21
In your apache2 virtual host file you will want to add the alias directive.

```
ServerAlias www.site.org
```

Then create a 301 redirect using .htaccess.

Here is some info for the [301 redirect]("http://w3schools.in/article/301-redirect-in-PHP-and-.htaccess/")

---

### Post by vavr on 2012-05-21
I've got it, thank you so much

---

### Post by Lars Noodén on 2012-05-21
It's not necessary to use .htaccess if you yourself already have access to the Apache configuration files.  Those are only needed if you do not have access to the web server itself.  If you do have access, you can put the redirect rules directly in the configuration file. 

Here is Apache's solution:
[https://httpd.apache.org/docs/2.2/rewrite/remapping.html#canonicalhost](https://httpd.apache.org/docs/2.2/rewrite/remapping.html#canonicalhost)

---

### Post by vavr on 2012-05-22
Hil i dit it by modify the .htaccess file and it seems to work because when the firefox loads the site is reading data from the [http://www.site.org](http://www.site.org) but the address bar still stays on the [http://site.org](http://site.org). How can i change that so the address bar will so [http://www.site.org?](http://www.site.org?)
thanks

---

### Post by Lars Noodén on 2012-05-22
The address will change if you are doing the redirect correctly.  If you have access to the configuration file, then you can skip .htaccesss and edit the configuration file directly.  That will make things much easier to maintain by having all the changes in one place.  See the link above to the Apache projects advice on how to set canonical host names.

---

### Post by LHammonds on 2012-05-22
hehehe.  I kinda have a similar problem.  I setup a dedicated wiki server and once I got it online for internal use, I added a DNS entry in our domain so we could access the site as wiki.mydomain.com but when we type that inside the address bar and press enter, it finds the site but trades out the domain name for the IP address.  I thought this was a DNS problem but it turns out that this is probably related to the apache server configuration.

I think the links presented here point directly at the solution but I'm too new to how apache works to figure out what to do exactly to fix it. (e.g. every change I make breaks the site lol)  I'm sure I'll get it sometime but it is not high on my priority list at the moment.

LHammonds

---

### Post by SeijiSensei on 2012-05-23
If you make domain.name an alias for [www.domain.name](www.domain.name) using the ServerAlias directive in Apache mentioned above, you shouldn't see any changes in the address bar at all.

```

<VirtualHost *:80>
    ServerName  www.example.com
    ServerAlias example.com

    DocumentRoot /path/to/the/site/directory

    [stuff]

</VirtualHost>

```

You shouldn't need a Redirect at all as long as there are DNS A or CNAME records for both example.com and [www.example.com](www.example.com) that point to your server.

---

### Post by rubylaser on 2012-05-23
> **SeijiSensei said:**
> If you make domain.name an alias for [www.domain.name](www.domain.name) using the ServerAlias directive in Apache mentioned above, you shouldn't see any changes in the address bar at all.

```

<VirtualHost *:80>
    ServerName  www.example.com
    ServerAlias example.com

    DirectoryRoot /path/to/the/site/directory

    [stuff]

</VirtualHost>

```

You shouldn't need a Redirect at all as long as there are DNS A or CNAME records for both example.com and [www.example.com](www.example.com) that point to your server.

+1. This is a great and easy way to get this done.

---

### Post by LHammonds on 2012-05-24
> **SeijiSensei said:**
> 
    DirectoryRoot /path/to/the/site/directory

Did you mean "DocumentRoot"?

I configured this file (which was empty) this way and it still turns the site URL into an IP:

/etc/apache2/httpd.conf
```

<VirtualHost *:80>
  ServerName wiki.mydomain.com
  ServerAlias mydomain.com
  DocumentRoot /var/www
</VirtualHost>

```When I type **ping wiki** from the DOS prompt on my Win7 PC, I get a response back from the correct IP:
```

Pinging wiki.work.mydomain.com [192.168.107.23] with 32 bytes of data:
Reply from 192.168.107.23: bytes=32 time=1ms TTL=63
Reply from 192.168.107.23: bytes=32 time=2ms TTL=63

```When I type **ping wiki.mydomain.com**, I also get the correct IP:
```

Pinging wiki.mydomain.com [192.168.107.23] with 32 bytes of data:
Reply from 192.168.107.23: bytes=32 time=2ms TTL=63
Reply from 192.168.107.23: bytes=32 time=2ms TTL=63
```However, when I type **wiki** or **[http://wiki](http://wiki)** or **wiki.mydomain.com** or **[http://wiki.mydomain.com](http://wiki.mydomain.com)** in the address bar of a web browser, it turns into **[http://192.168.107.23/index.php/Main_Page](http://192.168.107.23/index.php/Main_Page)**

---

### Post by SeijiSensei on 2012-05-25
Thanks for pointing out that error, LHammonds.  I fixed the original post.

Do you have a DNS server or just using hosts files?  All my sites have DNS resolution enabled (they are on the public Internet), and I don't get the conversion to the IP address in the browser's address bar.

Also your server appears to be called wiki.work.mydomain.com, not wiki.mydomain.com.  So it may be that you need:

```

ServerName wiki.work.mydomain.com
ServerAlias wiki.mydomain.com mydomain.com
...

```

Did you remove the 000-default symlink from /etc/apache2/sites-enabled?  If not, then any request regardless of its URL will return the contents of /var/www, since that's the Ubuntu default.  If [http://192.168.107.23/](http://192.168.107.23/) returns your site, that's because of the default configuration, not your virtualhost configuration.

---

### Post by LHammonds on 2012-05-25
> **SeijiSensei said:**
> 
Do you have a DNS server or just using hosts files?

The DNS servers I have are Windows-based.  All servers point to my internal DNS servers as part of the network configuration.

For Linux servers (since they do not "join" the domain), we manually add records to the DNS servers so our PCs can find them by name irregardless of how I have the actual server named.  In this case, the Ubuntu name is "srv-wiki" but the DNS record is "wiki"

> **SeijiSensei said:**
> 
Also your server appears to be called wiki.work.mydomain.com, not wiki.mydomain.com.  
```

ServerName wiki.work.mydomain.com
ServerAlias wiki.mydomain.com mydomain.com

```
Made the change but it made no difference.  Site still worked but URL turned into IP.

> **SeijiSensei said:**
> 
Did you remove the 000-default symlink from /etc/apache2/sites-enabled?

No.  But when I removed it and restarted apache, the site broke.  I moved it back to get it working again.  000-default --> ../sites-available/default

sites-available/default
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
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
        ErrorLog ${APACHE_LOG_DIR}/error.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

```

Everything is pretty-much Ubuntu default.  About the only thing different from the standard package install is that I deleted the default index file before copying MediaWiki files to the root.

Thanks,
LHammonds

---

### Post by SeijiSensei on 2012-05-25
> /etc/apache2/httpd.conf

Ah, I see now that you put the virtual host definition in httpd.conf.  That approach probably doesn't work with Ubuntu.  If you look at /etc/apache2/apache2.conf, you'll see that httpd.conf is read before both ports.conf and the section of apache2.conf that includes the NameVirtualHost directive.  So if you put a <VirtualHost *:80> stanza in httpd.conf, there won't be a NameVirtualHost declaration to match it against.  The virtual host is ignored; I bet an error is logged in /var/log/apache2/error.log, too.

Ubuntu prefers you to put each <VirtualHost> definition in a separate file in /etc/apache2/sites-available/ then enable them using a2ensite or manually creating a symlink to the definition file in /etc/apache2/sites-enabled/.  That's how the default file is set up.  

This also explains why removing the default file breaks your site.  It's that file that is providing access to /var/www, not the vhost declaration you placed in httpd.conf.  sites-available/default provides a "catch-all" virtual host that will respond to any requests that don't match a name-based virtual host.  These requests can result in an IP-based URL because there was no ServerName or ServerAlias that matched the requested URL.

So here's what you should try.  Create a file in sites-available and put the <VirtualHost> stanza you wrote for httpd.conf in there.  Next make sure that the ServerName is the one that will be commonly used to reach the site, with any ServerAlias declarations as needed.  Make sure all these names have corresponding DNS records.  

You might want to move the DocumentRoot from /var/www to another location on the server and recreate /var/www with just the Ubuntu default "It Works!" page.  That way you'll know whether you've successfully connected to the name-based virtual host or if you've used a unmatched URL.

Once you have saved the configuration file, create a symlink to it in sites-enabled, or use the a2ensite command (see "man a2ensite" for details).  After restarting Apache you should try URLs with and without server names matching those in the ServerName and ServerAlias declarations.  Matching ones should give you your wiki with the server name appearing unchanged in the browser's address bar.  Unmatched names will display the "It Works!" page and show the IP address in the browser.  In case you lost the default page, here it is:

/var/www/index.html

```
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
```

---

### Post by LHammonds on 2012-05-25
Thanks for the clarification.  I have a better understanding of how sites are linked up.  However, it still turns it into the IP.

I created a /var/www-default and placed the "it works" file there.  Then had the wiki site placed under /var/www-wiki

I updated the default and default-ssl to reference the www-default folder.

I copied the default to a file called wiki and updated the path to www-wiki.

I then typed a2ensite wiki which correctly created a link to the site info file.

Going directly to the IP address, it showed the "it works" page.  Going to wiki, or wiki.mydomain.com or wiki.work.mydomain.com went to the wiki site but still converted the URL into an IP.

I'm guessing the solution is elsewhere in the setup.

---

