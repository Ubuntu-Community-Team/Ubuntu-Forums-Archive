---
title: "Subdomains in Apache"
date: 2010-05-26
forum: Server Platforms
---

### Post by Zeophlite on 2010-05-26
Okay so my server (small box under the bench) is running apache nicely on lucid.  I can type in my IP address and browse pages, and that works easily.

Currently if I want to get show /var/www/<dir>/<pathtofile> I type in http://<IP>/<dir>/<pathtofile> and if I want /home/<user>/<pathtofile> I type in http://<IP>/~<user>/<pathtofile>

I'm using this:
```

[B]daniel@Mustrum:/etc/apache2/sites-available$ cat default
[/B]<VirtualHost *:80>
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

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error,  crit,
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

    RailsEnv production
    RailsBaseURI /redmine
    <Directory "/var/www/redmine/">
        Allow from all
        Options -MultiViews
    </Directory>

</VirtualHost>

```

I just registered a domain name, say www.<domain>.com, and I want to be able to also do this:
If I want to get show /var/www/<dir>/<pathtofile> I  type in http://www.<domain>.com/<dir>/<pathtofile> as well as http://<dir>.<domain>.com/<pathtofile> and if I want  /home/<user>/<pathtofile> I type in  http://www.<domain>.com/~<user>/<pathtofile> as well as http://<user>.<domain>.com/<pathtofile> (with preference to the /var/www/<dir> subdomain over the <user> one).

I want to get it working on my end before telling my domain register'er to...

Once I get it working on my end (how do I do that first?), what do I ask them to change?

Cheers,

Daniel

---

### Post by Ryan Dwyer on 2010-05-26
That setup should work mostly, except for the dir.domain.com/path example. You'll need to set up a virtual host for each dir.

You can test by adding [www.domain.com](www.domain.com) to your local hosts file and browsing to it.

You'll need to forward port 80 on your router, then ask your ISP to change the A record to your external IP.

---

### Post by Zeophlite on 2010-05-26
Thanks for your quick reply.

I've already set up the port forwarding on my router, I can type in my external IP at uni, and my page shows up normally.  (As an aside, if I type in my external IP at home, it shows up my router's admin page - this is a problem with my router, which I'm trying to fix)

I changed the A record (thanks for that) to my external IP, but typing in my domain name at home brings up my router admin page.  Trying from anywhere else gives an error (I don't think the A record has propagated throughout the internet yet).  I'll inform you if its changed in a couple of days.

Wouldn't I also have to change something on in sites-available/default so that it knows about my domain name?  And about the subdomains for users?

Also, how would I set up the virtual hosts for the directories?  Or is there some automatic way to do that? (perhaps with mod_rewrite - I don't know how to use it, just found it on the apache documentation pages)

---

### Post by Ryan Dwyer on 2010-05-26
The router admin page is standard behavior. You can set up a local DNS server to make your local machines map the domain name to the private address.

Apache will serve the default host if it receives a request for a hostname it doesn't know about, which is what's going to happen here. You don't need to configure it with a domain name unless you're not going to run it on the default host.

You can set up dynamic subdomains for the directories, but it's far easier to do it manually. You would have to add a DNS A record for each subdomain anyway unless your host supports wildcard records, which is rare. If you still want to go the automatic way, ready the docs for mod_vhost_alias ([http://httpd.apache.org/docs/2.2/mod/mod_vhost_alias.html](http://httpd.apache.org/docs/2.2/mod/mod_vhost_alias.html)) or mod_rewrite.

---

### Post by cdenley on 2010-05-26
This should point you in the right direction.

[http://ubuntuforums.org/showpost.php?p=9227698&postcount=4](http://ubuntuforums.org/showpost.php?p=9227698&postcount=4)

That will internally redirect any subdomains besides www to /~subdomain. I don't know how you plan to redirect both usernames and subdirectories. What if a subdirectory has the same name as a user?

---

### Post by Zeophlite on 2010-06-16
Okay, so I'm using the following code, and it works for most things

Say I want to get /home/<user>/public_html/<pathtofile>
I can type in either
http://www.mydomain.com/~<user>/<pathtofile>
http://<user>.mydomain.com/<pathtofile>
and both work so that's awesome.

I'm using this:
```

**daniel@Mustrum:/etc/apache2$ cat sites-available/default**
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName www.mydomain.com
        ServerAlias *.mydomain.com

        RewriteEngine on
        RewriteCond %{REQUEST_URI} !^/~
        RewriteCond %{HTTP_HOST} !^www\.mydomain\.com$
        RewriteCond %{HTTP_HOST} ^(.*)\.mydomain\.com$
        RewriteRule /(.*) /~%1/$1 [PT]

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

    RailsEnv production
    RailsBaseURI /redmine
    <Directory "/var/www/redmine/">
        Allow from all
        Options -MultiViews
    </Directory>

</VirtualHost>
**daniel@Mustrum:/etc/apache2$**

```


**Q1**
I have registered both [www.mydomain.com](www.mydomain.com) and [www.mydomains.com](www.mydomains.com) - what do I change to get both to work?  Preferably I'd want to put something into the
RewriteCond %{HTTP_HOST} !^www\.mydomain\.com$
lines like an expression for an optional s.



**Q2**
Also, currently to access
/var/www/<dir>/<pathtofile>
I type in
http://www.mydomain.com/<dir>/<pathtofile>
I want to be able to also type in
http://<dir>.mydomain.com/<pathtofile>

In order to resolve conflicts, I'd want it to work like so:
[http://bob.mydomain.com/file.html](http://bob.mydomain.com/file.html) should try /var/www/bob/file.html first and if that doesn't exist then /home/bob/public_html/file.html

How do I get that to work using rewrite?  I don't want to set up a virtual host for each folder if I can get away with it, but if I have to, how would I do that?


I'd want the ruby on rails stuff to also work - right now I have RailsBaseURI /redmine and so if I 
 tried using [http://redmine.mydomain.com](http://redmine.mydomain.com) I don't think that'd work - I tried before by removing the ~ from
RewriteRule /(.*) /~%1/$1 [PT]
and it just gave a directory listing.





Thanks for your help

Daniel

---

### Post by Zeophlite on 2010-06-18
bump

---

