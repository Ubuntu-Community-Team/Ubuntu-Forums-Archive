---
title: "apache woes"
date: 2009-06-23
forum: Server Platforms
---

### Post by johnh10000 on 2009-06-23
Hi gang

I am running so far sucessfully my website:
here goes through a virgin media inet connection
through a netgear wgr614 router
via a dynadns name
to my ubuntu jaunty box

all was fine.

I setup another name ebassy.isa-geek.org on dynadns.  They suggested using
virtualhosts or web-hop.  I think web-hop is untidy.
 
So I setup virtualhosts one for tux.isa-geek.org and one for
ebassy.isa-geek.org.

Apache starts, then try to goto either of them it says something like it looks alright but I can't do it. (With web-hop off)

heres my configs:

###virtual.conf
    I A  virtual.conf.l (c)(Read onl  Row 1    Col 1    5:40  Ctrl-K H for help
#
#  We're running multiple virtual hosts.
#
NameVirtualHost *

#########

#####
sites enabled
#####
#
#  ebasssy.isa-geek.org (/etc/apache2/sites-available/www.example.com)
#
<VirtualHost *>
        ServerAdmin [email]webmaster@example.com[/email]
        ServerName  ebassy.isa-geek.org
        ServerAlias ebassy.isa-geek.org

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/www/ebassy.isa-geek.org/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/ebassy.isa-geek.org/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/ebasssy.isa-geek.org/logs/error.log
        CustomLog /home/www/ebassy.isa-geek.org/logs/access.log combined
</VirtualHost>

#####
default
######
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
#####
any ideas?

---

### Post by Bachstelze on 2009-06-23
You have a vhost for your first site, ebassy.isa-geek.org. Now you must create another one for your second site, tux.isa-geek.org. Something like that:

```

<VirtualHost *>
    ServerAdmin webmaster@example.com
    ServerName tux.isa-geek.org

    # Indexes + Directory Root.
    DirectoryIndex index.html
    DocumentRoot /home/www/tux.isa-geek.org/htdocs/

    # CGI Directory
    ScriptAlias /cgi-bin/ /home/www/tux.isa-geek.org/cgi-bin/
    <Location /cgi-bin>
        Options +ExecCGI
    </Location>


    # Logfiles
    ErrorLog /home/www/tux.isa-geek.org/logs/error.log
    CustomLog /home/www/tux.isa-geek.org/logs/access.log combined
</VirtualHost>
```

---

### Post by johnh10000 on 2009-06-23
[QUOTE=HymnToLife;7504491]You have a vhost for your first site, ebassy.isa-geek.org. Now you must create another one for your second site, tux.isa-geek.org. Something like that:

Yeah, I did that already, but :-


root@tux:/etc/init.d# ./apache2 start
 * Starting web server apache2                                                  [Tue Jun 23 18:34:35 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Jun 23 18:34:35 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [fail]

---

### Post by johnh10000 on 2009-06-23
> **johnh10000 said:**
> [QUOTE=HymnToLife;7504491]You have a vhost for your first site, ebassy.isa-geek.org. Now you must create another one for your second site, tux.isa-geek.org. Something like that:

Yeah, I did that already, but :-


root@tux:/etc/init.d# ./apache2 start
 * Starting web server apache2                                                  [Tue Jun 23 18:34:35 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Jun 23 18:34:35 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [fail]

Failed to Connect

      

      
      
      

      
        
        

          

The connection was refused when attempting to contact ebassy.isa-geek.org.

        


        
        


Though the site seems valid, the browser was unable to establish a connection.




    *  Could the site be temporarily unavailable? Try again later.


    *  Are you unable to browse other sites?  Check the computer's network connection.


    *  Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

---

### Post by Bachstelze on 2009-06-23
Change

```
NameVirtualHost *
```

to

```
NameVirtualHost *:80
```

and all occurrences of

```
<VirtualHost *>
```

to

```
<VirtualHost *:80>
```

---

### Post by johnh10000 on 2009-06-23
> **HymnToLife said:**
> Change

```
NameVirtualHost *
```

to

```
NameVirtualHost *:80
```

and all occurrences of

```
<VirtualHost *>
```

to

```
<VirtualHost *:80>
```

ok done that same result but starting apache was differant

root@tux:/etc/init.d# ./apache2 start
 * Starting web server apache2                                                  [Tue Jun 23 18:59:37 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [fail]

---

### Post by Bachstelze on 2009-06-23
What does your config file look like now?

---

### Post by johnh10000 on 2009-06-23
> **HymnToLife said:**
> What does your config file look like now?

As far as i know what you recomended:  I've even tried to removing the default one, to the same effect.

Having my tea now, so .. Ill post back about 8ish in the uk

#
#  We're running multiple virtual hosts.
#
NameVirtualHost *:80

----
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
----------
#
#  ebasssy.isa-geek.org (/etc/apache2/sites-available/www.example.com)
#
<VirtualHost *:80>
        ServerAdmin [email]webmaster@example.com[/email]
        ServerName  ebassy.isa-geek.org
        ServerAlias ebassy.isa-geek.org

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/www/ebassy.isa-geek.org/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/ebassy.isa-geek.org/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/ebasssy.isa-geek.org/logs/error.log
---------

#
#  ebasssy.isa-geek.org (/etc/apache2/sites-available/www.example.com)
#
<VirtualHost *:80>
        ServerAdmin [email]webmaster@example.com[/email]
        ServerName  tux.isa-geek.org
        ServerAlias tux.isa-geek.org

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/www/tux.isa-geek.org/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/tux.isa-geek.org/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/tux.isa-geek.org/logs/error.log

---

### Post by johnh10000 on 2009-06-24
Thanks gang, whoever suggested look at the logs.  Duh from my side.  one stupid extra "s" remove it, and it now works!

I know it shoudn't make that much diff but it did.

Thanks again.

---

