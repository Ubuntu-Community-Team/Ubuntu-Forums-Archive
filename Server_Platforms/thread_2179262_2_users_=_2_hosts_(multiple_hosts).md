---
title: "2 users = 2 hosts (multiple hosts)"
date: 2013-10-07
forum: Server Platforms
---

### Post by alfirdaous on 2013-10-07
Good day to you,

I am trying to do a multiple hosts on my local ubuntu, 1st host is "alfirdaous" and the 2nd one is "tests".

once I go to the URLs:

+ [http://localhost/~alfirdaous](http://localhost/~alfirdaous) ==> It works
+ [http://localhost/~tests](http://localhost/~tests) ==> It shows 500 error page

The thing the error page e-mail address is the one belongs to alfirdaous host:

> 
Please contact the server administrator,  **** and inform them of the time the error occurred, and anything you might have done that may have caused the error.




```

root@ubuntu:/etc/apache2/sites-available# ls -l
total 15
-rw-r--r-- 1 root root 1178 Oct  7 12:09 alfirdaous
-rw-r--r-- 1 root root  692 Jul  5 02:44 default
-rw-r--r-- 1 root root 7251 Jul  5 02:44 default-ssl
-rw-r--r-- 1 root root 1146 Oct  7 13:31 tests
root@ubuntu:/etc/apache2/sites-available# vim alfirdaous 
root@ubuntu:/etc/apache2/sites-available# vim tests 

```

alfirdaous virtual host:
```

<VirtualHost *:80>
        ServerAdmin alfirdaous@gmail.com
        ServerName http://localhost/~alfirdaous
        DocumentRoot /home/alfirdaous/www

#       DirectoryIndex index.php 
        <Directory />
                Options FollowSymLinks
               AllowOverride None
        </Directory>
       <Directory /home/alfirdaous/www/>

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
</VirtualHost>

```

tests virtual host:
```

<VirtualHost *:80>
        ServerAdmin tests@gmail.com
        ServerName http://localhost/~tests
        DocumentRoot /home/tests/www

#       DirectoryIndex index.php 
        <Directory />
                Options FollowSymLinks
               AllowOverride None
        </Directory>
       <Directory /home/tests/www/>

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
</VirtualHost>

```

Activation:

```

root@ubuntu:/etc/apache2/sites-available# a2ensite alfirdaous
Site alfirdaous already enabled
root@ubuntu:/etc/apache2/sites-available# a2ensite tests
Site tests already enabled

```


Why I cannot access the 2nd host, and showing the 500 error page for alfirdaous.

Thanks in advance

---

### Post by Lars Noodén on 2013-10-07
I think you may have gotten hosts confused with per-user directories.  Two different hosts would be [http://host1.example.com/](http://host1.example.com/) and [http://host2.example.com/](http://host2.example.com/)  Specifically that example is of name-based virtual hosts, if you are running both off of the same web server.  

To get various user directories on the web using the short cut of a tilde (~) and the user name, you should restore the vhost back to its defaults and look instead at [per-user web directories](http://httpd.apache.org/docs/2.2/howto/public_html.html).

---

### Post by alfirdaous on 2013-10-07
this is what I am doing:

[http://localhost/~user1](http://localhost/~user1)
[http://localhost/~user2](http://localhost/~user2)

but for user2 shows an error 500

---

### Post by Lars Noodén on 2013-10-07
You have two virtual hosts, but without unique names to distinguish them from each other.  If you're going to try to have two different virtual hosts, then you need unique names (set in /etc/hosts or elsewhere) to work from.  Those would be "name-based" virtual hosts.  But that does not look like what you are trying to do.

What you seem to be trying with the tilde (~) looks like per-user directories.  For that you need to eliminate one of your virtual host configuration files and then enable the module *userdir*

```

sudo a2enmod userdir
sudo  service apache2 restart

```

But before that, /etc/apache2/mods-available/userdir.conf should have the following line changed

```

[s] UserDir www /var/html [/s]
 UserDir www 

```

and this line

```

<Directory /home/*/www>

```

That will make [http://localhost/~alfirdaous/](http://localhost/~alfirdaous/) go to /home/alfirdaous/www/ and make [http://localhost/~test/](http://localhost/~test/) go to /home/test/www/ and [http://localhost/~user2](http://localhost/~user2) go to /home/user2/www/ and so on.

I think that is what you are trying to do.  So erase the extra vhost file and look at Per-user web directories.

---

### Post by alfirdaous on 2013-10-07
userdir.conf:

```

<IfModule mod_userdir.c>
#        UserDir www
UserDir /home/*/www
        UserDir disabled root

        <Directory /home/*/www>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>


```

and

```

root@ubuntu:/etc/apache2/sites-available# sudo a2enmod userdir
Module userdir already enabled

```

All steps are already done, so accessing to:

[http://localhost/~alfirdaous](http://localhost/~alfirdaous) => works
[http://localhost/~tests](http://localhost/~tests) => error 500

---

### Post by Lars Noodén on 2013-10-08
The line where you have **UserDir /home/*/www** should read ** UserDir www ** instead.  Change that and the when your changes are saved, reload the configuration.

```

sudo service apache2 restart

```

---

### Post by Lars Noodén on 2013-10-08
Also, be sure you fixed [ServerName](http://httpd.apache.org/docs/2.2/mod/core.html#servername) in your main configuration file.  It should only be the hostname and no protocol or paths.

---

### Post by alfirdaous on 2013-10-08
I only remove the <VirtualHost></VirtualHost> from the config file, and now it works, because it is local host

---

### Post by Lars Noodén on 2013-10-09
You'll need those <VirtualHost></VirtualHost> tags later.

---

### Post by alfirdaous on 2013-10-09
Thanks [**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643")

---

