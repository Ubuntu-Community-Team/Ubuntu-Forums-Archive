---
title: "Changing Apache DocumentRoot to Home directory"
date: 2009-08-23
forum: Server Platforms
---

### Post by a_bains on 2009-08-23
Hello,

I have Ubuntu 9.04 Server edition. This is my first post ever about linux. I've been using Windows all my life.  I have Apache, mySQL, PHP installed. 

The default apache documentroot is var/www. Things worked fine in there but once I changed the sites-available/default file to the below, then I had the Forbidden error message. I check apache error log and it is (13) Permission denied. Wierd thing is that it works fine when I SSH into the server and login as : Aaron. The server is run on a standalone machine and trying to access the web server in the browser. There is also an index.html file in the aaron/www/html directory. If i was to just restart the server and not login as: aaron in ubuntu then I get this forbidden error message when I try to access the web server from another computer on the network. I really appreciate your help! :)

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/aaron/www/html/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/aaron/www/html/>
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

---

### Post by a_bains on 2009-08-23
I have a feeling that this has to do with the fact that I chose to encrypt my home directory during the Ubuntu installation. Because, I have played around with permissions for hours I don't know what else it could be. If anyone knows how to unencrypt my home directory without reinstalling Ubuntu that would be great. Thanks :)

---

