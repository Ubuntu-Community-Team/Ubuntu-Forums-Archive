---
title: "Problems with virtual hosts LAMP"
date: 2018-10-09
forum: Server Platforms
---

### Post by dam034 on 2018-10-09
Dear users,

I have a VPS with LAMP, the default virtual host is this:
```
<Directory /srv/sites/main/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

<IfModule mod_autoindex.c>
        IndexOptions FancyIndexing HTMLTable FoldersFirst IconWidth=16 IconHeight=16 IgnoreCase SuppressDescription SuppressRules VersionSort XHTML
        IndexStyleSheet "/def-list.css"
</IfModule>

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin me@vps
        DocumentRoot /srv/sites/main

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

And now I'm trying to add another virtual host to 2 others that already exist:
```
<Directory /srv/sites/music/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

<IfModule mod_autoindex.c>
        IndexOptions FancyIndexing HTMLTable FoldersFirst IconWidth=16 IconHeight=16 IgnoreCase SuppressDescription SuppressRules VersionSort XHTML
        IndexStyleSheet "/def-list.css"
</IfModule>

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName music.local
        ServerAlias mydns.ga *.mydns.ga

        ServerAdmin me@vps
        DocumentRoot /srv/sites/music

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

When I try to activate the virtual host with:
```
root@myvps:/# a2ensite music.conf
root@myvps:/# service apache2 reload
```

In the default virtual host all .htaccess don't work anymore, in music virtual host I can see the default website, not the music website, as DocumentRoot doesn't work.

How can I fix this issue?

Thanks

---

### Post by SeijiSensei on 2018-10-10
Usually I put the <Directory> stanzas inside the <VirtualHost> stanza.  I've never seen the <Directory> stand alone outside of a VirtualHost container.

---

### Post by dam034 on 2018-10-10
I tried to edit, but I have the same problem.

Help!

---

### Post by SeijiSensei on 2018-10-10
Have you studied the logs in /var/log/apache2?

Are you using [http://music.local/](http://music.local/) for the URL?  [http://music/](http://music/) will not match the ServerName.  If you want to use "music" you'll need to make it a ServerAlias.

---

### Post by dam034 on 2018-10-11
The logs are all in one file, so I can't understand much.
Now I tried to re-a2ensite the second VH.
Using [http://192.168.1.15](http://192.168.1.15) (default VH) or [http://music.local](http://music.local) (music VH), I can see music VH website in both cases.

I have 2 other VHs but they are working correctly, with ServerName and ServerAlias directives.

Why music VH conflicts with default VH, giving me problems?

Thanks

---

### Post by SeijiSensei on 2018-10-12
The error log is separate:

"ErrorLog ${APACHE_LOG_DIR}/error.log"

Should be /var/log/apache2/error.log

Also you shouldn't ever use .htaccess files if you control the server.  Put any directives in an .htaccess file into the corresponding <Directory> container in the virtual host definition.  .htaccess is a kludge for people who run hosting companies and need to give their customers some limited control over the server for their sites.

---

### Post by dam034 on 2018-10-12
I realized that there is priority in alphabetical order on the names of the conf files in the sites-available folder. Can this be the problem?

Thanks

---

### Post by SeijiSensei on 2018-10-12
Yes.  

If I were you, I'd rename the 000-default.conf file to something else.  It has the "000-" prefix so it is read in before the others.  I believe Apache matches ServerName/Alias in the order in which they appear in the files.

---

### Post by dam034 on 2018-10-13
You're right.

Until now, in the sites-available folder, the default VH was the second in alphabetical order, and for this reason it didn't work.
Now I renamed the default VH re-adding the 000- prefix and now it works again.

Thanks for help :D

---

