---
title: "Apach2 with subdomains and a reverse proxy for Subsonic"
date: 2012-02-11
forum: Server Platforms
---

### Post by Mykle87 on 2012-02-11
I just setup an Ubuntu 11.10 server with LAMP and am looking for a little help. My goal is to start hosting 2 websites using subdomains and eventually expand to more. When I browse to mydomain.com over the Internet, everything works fine. I see the first page I setup. In addition, mydomain.com:4040 goes to Subsonic. I would really like to have subsonic.mydomain.com resolve to my Subsonic application. I have added subsonic.mydomain.com as an A-record with my hosting company and edited my /etc/hosts file to include```
127.0.0.1 subsonic.localhost
```
When I browse to subsonic.mydomain.com, nothing loads.
Here is what my main website file looks like:
```
<VirtualHost *:80>
        ServerName localhost

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
And here is what my subsonic reverse proxy file looks like:
```
<VirtualHost *:80>
ProxyPass / http://127.0.0.1:4040/
ProxyPassReverse / http://127.0.0.1:4040/
ServerName subsonic.localhost
</VirtualHost>

```
Any help would be greatly appreciated. Thanks in advance.

---

### Post by volkswagner on 2012-02-11
You need to change the ServerName in you subsonic vhost file.

Should be:

```
 ServerName subsonic.mydomain.com
```

You may also need to allow access to the directory.

I made quick [how-to]("http://ubuntuforums.org/showthread.php?t=1920715") which may help.

Pay close attention to the <location /> directive.  Without it you may get an error like "can't access / on server..."

---

### Post by Mykle87 on 2012-02-11
This did the trick. Thanks for the help!

---

### Post by volkswagner on 2012-02-12
Glad  worked.  Please mark your thread as solved.... At the top of this thread, select thread tools > mark as solved.

---

