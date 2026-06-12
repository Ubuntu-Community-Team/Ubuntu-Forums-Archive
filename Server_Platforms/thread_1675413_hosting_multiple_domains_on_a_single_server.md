---
title: "hosting multiple domains on a single server"
date: 2011-01-25
forum: Server Platforms
---

### Post by tangerine0469 on 2011-01-25
ok, after a bit of light reading in the forums and in the tech documents that go with 10.04lts i came up short...

i am trying to host two domains on the same server i have them setup using apache as virtual hosts. i am able to see my first domain properly and the second one is just the "It works!" page.

the document roots are correct 

computer spec's aside here are the details:
john-stapleton.com
computercrasherz.com

/etc/apache2/sites-available/john-stapleton.com

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName john-stapleton.com
        ServerAlias *.john-stapleton.com
        DocumentRoot /var/www/john-stapleton.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/john-stapleton.com>
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

</VirtualHost>

/etc/apache2/sites-available/computercrasherz.com

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName computercrasherz.com
        ServerAlias *.computercrasherz.com
        DocumentRoot /var/www/computercrasherz.com
.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/computercrasherz.com>
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
</VirtualHost>


how do i get the second one to point to the index.html page which is located in /var/www/john-stapleton.com?

---

### Post by wongo888 on 2011-01-25
When someone opens computercrasherz.com you want them to redirect to john-stapleton.com?

That would be done via a redirect. The way I usually do that is via mod_rewrite. You can read about it here:

[http://httpd.apache.org/docs/current/mod/mod_rewrite.html](http://httpd.apache.org/docs/current/mod/mod_rewrite.html)

Tons to practical tutes online. Google "301 redirect mod_rewite" assuming you want the 301 permanent redirect.

---

### Post by tangerine0469 on 2011-01-26
i didn't think of a redirect but i was under the impression that the server could use host names to resolve which folder tree to point the http requests at. i can do it on my works windows 2008 server no problem.

edit:domain name, not host name.

---

### Post by wongo888 on 2011-01-27
I'm not sure that I understand your issue. Is your browser not opening the right web root?

Name virtual hosting requires that your browser send a host header. It is part of HTTP/1.1. You can read about it here:

[http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.23](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.23)

Apache then uses that bit of info to figure out which directory to use to serve docs.

If this server is a virtual machine running on your workstation, you need to configure your hosts file to resolve the domain to an IP. Your browser will handle the rest.

If you are just wanting to serve the exact same content, I would do a redirect, or if this was a link farming exercise, just symlink the second webroot to the first.

Finally, ensure that your site is enabled using *a2ensite* and that the correct symlink is in the */etc/apache2/sites-enabled* directory.

---

### Post by tangerine0469 on 2011-02-02
scratch my question the problem turned out to be with my a record with godaddy... thanks for the help trying to solve this.

---

