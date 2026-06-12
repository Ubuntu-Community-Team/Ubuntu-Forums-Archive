---
title: "Apache Server Error “Forbidden: You don't have permission to access on this server.”"
date: 2013-07-19
forum: Server Platforms
---

### Post by masoodmx on 2013-07-19
I have a very weird problem with Apache server.
A kind of shell script file is running on the server. Before some modification which was needed to install awstats, everything was working properly, but after that always errors happen on the server to run that script file.


The error on the page is:


  ```
  Forbidden
    You don't have permission to access /factsage/ on this server.



```and error.log records:


    ```
client denied by server configuration: /var/www/factsage/factsage.sh

```

The content of sites-available/default:


   ```
 <VirtualHost *>
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
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch +FollowSymLinks
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

```


And the content of conf.d/factsage.conf


   ```
 #ScriptAlias /factsage/ /var/www/factsage/
    # Causes error: attempt to invoke directory as script
    
    Alias /factsage /var/www/factsage
    # Causes error: client denied by server configuration


    <Directory /var/www/factsage>
            Options +ExecCGI Multiviews +FollowSymLinks
    #       Options Indexes FollowSymLinks Includes ExecCGI  # no effect
            AddHandler cgi-script .cgi .sh
            DirectoryIndex factsage.sh
    
            AllowOverride None
            Order allow,deny
            Allow from All
    #       Require all granted  # causes Internal Server Error
    #       AuthType All  # no effect
    #       Require local   # causes Internal Server Error
    </Directory>

```

Any idea how to solve this problem?! I tried every possible way either I could find in web or test configuration myself.

---

### Post by TheFu on 2013-07-19
ScriptAlias is important for things to be run as scripts.  I recommend you read up on that and make certain a script-handler works for .sh files too.
I would have thought the execcgi option would make it work, but that doesn't appear to be the case.

In truth, I stopped using apache for anything complex years ago, so I'd need to carefully research any better answer.

Why not just restore from a backup with the settings that worked?

---

