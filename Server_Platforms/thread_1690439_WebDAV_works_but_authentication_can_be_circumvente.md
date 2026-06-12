---
title: "WebDAV works but authentication can be circumvented"
date: 2011-02-18
forum: Server Platforms
---

### Post by lotus49 on 2011-02-18
I have been trying to setup a WebDAV server following various howtos on the net (none of them completely worked so I had to pick and choose until it appeared to work).

If I go to http://<server name>/webdav I get an authentication popup, the authentication process works and when the correct credentials are given, access is granted.  So far so good.

Unfortunately, if I go to http://<server name> I immediately get unauthenticated access to the same files.

I suspect the issue is with my /etc/apache2/sites-available/default file but, I have to confess that I do not fully understand what I have cobbled together so I am struggling to identify the problem.  The contents of that file are:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/webdav
        <Directory /var/www/webdav/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        Alias /webdav /var/www/webdav
        <Location /webdav>
                DAV On
                AuthType Digest
                AuthName "webdav"
                AuthDigestProvider file
                AuthUserFile /var/www/.passwd.dav
                Require valid-user
                DavMinTimeout 600
                <LimitExcept GET PUT HEAD OPTIONS POST>
                        Require valid-user
                </LimitExcept>
        </Location>

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

I don't know if it relevant (I don't think it is but you never know) this is running on an EC2 server with an official 10.10 AMI from Canonical.

I would very much appreciate a pointer from someone who understands this better than me (that is probably most of you out there).

---

### Post by SeijiSensei on 2011-02-18
Apache discriminates among virtual hosts using the ServerName directive.  Each virtual host should have a distinct ServerName that will be used in URLs.  

Since it sounds like you changed the 000-default host definition, you now have only one host configured.  Here's what I'd suggest:

1)  Back up your current vhost definition, then reinstall Apache.  You'll restore the default 000-default file to sites-enabled.  Leave that alone.

2)  Copy your backed-up webdav definition into /etc/apache2/sites-enabled with a new file name to distinguish it from the default.

3)  In the webdav file, add a ServerName directive with a unique name like webdav.example.com.  Now requests for [http://webdav.example.com/](http://webdav.example.com/) will get handled by the webdav configuration, and all other requests will get the Ubuntu default "It Works!" page.

4)  Restart Apache.

You'll need to configure your DNS or hosts files to point webdav.example.com to the same IP address as your current server.

You can also delete the stanza for /usr/share/doc in the webdav file.  It's not relevant to the webdav installation.  All it does is enable someone sitting at the console to view the server's documentation directory with a web browser.

---

### Post by lotus49 on 2011-02-18
Thank you very much for your help.

You were correct, I had changed the 000-default host definition but I hadn't actually deleted anything so I restored that having copied my default file to one called webdav.

I then put the real dns name into the ServerName directive in webdav, restarted apache and hey presto, it all works now.

I appreciate your taking the time to help me with this.

---

### Post by SeijiSensei on 2011-02-19
You're welcome.  Please mark this thread as "Solved."

---

