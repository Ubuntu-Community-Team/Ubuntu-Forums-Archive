---
title: "ServerAlias not working"
date: 2006-11-25
forum: Server Platforms
---

### Post by General Moskovich on 2006-11-25
I'm trying to figure out this virtualhost stuff and server aliases. [I using 6.06 with Apache 2.0.55.] 

Here is my default file inside sites-available. 

[PHP]
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName new.<MY COMPANY>.com.tw
        ServerAlias www.new.<MY COMPANY>.com.tw

        DocumentRoot /space/www/direct
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /space/www/direct/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
        #       RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

        <Location />
                AuthType        Basic
                AuthName        "New Business Main Site"
                AuthUserFile    /space/www/htpasswd
                Require         valid-user
        </Location>

</VirtualHost>
[/PHP]

I can acess http://new.<MY COMPANY>.com.tw but cannot access http://www.new.<MY COMPANY>.com.tw.

Any help would be awesome!

-Sean

---

### Post by MJN on 2006-11-25
Well Sean, it ought to be working! Nowt wrong with that config.

Have you reloaded/restarted Apache after putting the ServerAlias directive in? And what do your access/errors logs say? Indeed, what does your client say when trying to access www.new.<MY COMPANY>.com.tw?

If you'd given your actual domain name (why hide it?) then we could also check the DNS config - that's all in place is it?

Mathew

---

### Post by stickboy2642 on 2006-11-26
Just curious, is www.new.<mycompany>.com.tw set up in DNS?  If not, then that is your problem.  If it is, make sure it points to the same ip address as new.<mycompany>com.tw, otherwise traffic won't get sent to the right server.

---

### Post by MJN on 2006-11-26
If people didn't hide their domain names we'd be able to nail things like this in an instant! I've never understood why someone would want to hide something that resides in a public database... (particularly when they're asking for help as to why it's not working!)

Mathew

---

