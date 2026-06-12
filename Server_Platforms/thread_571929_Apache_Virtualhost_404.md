---
title: "Apache Virtualhost 404"
date: 2007-10-09
forum: Server Platforms
---

### Post by usbsnowcrash on 2007-10-09
I have a wierd problem.  I have 1 file in my directory called index.html.  I can get it to display by typing in the url [http://www.example.com/index.html](http://www.example.com/index.html).  However if I type in [http://www.example.com/](http://www.example.com/) I get a 404 error.

Here is configuration for [www.example.com:](www.example.com:)
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin jeffery.yeary@gmail.com
        ServerName example.com
        ServerAlias *.example.com
        DocumentRoot /home/www-example-com/public_html/
        <Directory /home/www-example-com/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                SetHandler mono
                DirectoryIndex index.html index.htm index.aspx default.aspx
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /home/www-example-com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

</VirtualHost>


```

This might be related, I get this when I start apache
```


root@example:~# /etc/init.d/apache2 reload

 * Reloading apache 2.0 configuration... 
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

---

### Post by hangthedj on 2007-10-09
after looking at my apache configuration i don't even have a virtualhost directive for a main site.  just Documentroot and listen and <Directory.

try taking the slash off the end of the DocumentRoot and check to make sure public_html is readable by the web server.

---

### Post by twistedtwig on 2007-10-10
could it be something silly like it is looking for .htm rather than .html files as the index... I think its something like directory-index or something that you can set the options for what time of files can be used as an index / default file type.

---

### Post by hangthedj on 2007-10-10
he's got DirectoryIndex in there, i'm pretty sure its looking for 
public_html//index.html instead of public_html/index.html

on all my servers there is no extra backslash. after DocumentRoot

---

### Post by MJN on 2007-10-10
The trailing slash won't matter - multiples are ignored anyway (try sticking a load of ///// into a URL or filepath).

Usbsnowcrash (man, these usernames getter weirder and weirder! ;)), post the output of your Apache error log as this ought to push us in the right direction towards finding what's wrong.

Mathew

---

### Post by usbsnowcrash on 2007-10-10
I figured out my issue.  Basically since I had this line in my config

```

SetHandler mono

```

All requests were being sent to mono-server process first which was failing because of a bad configuration. I ended up creating the following file  **/etc/mono-server2/example.com.webapp**
```

<apps>
        <web-application>
                <name>Test</name>
                <vpath>/</vpath>
                <path>/home/www-example-com/public_html</path>
                <vhost>www.example.com</vhost>
        </web-application>
</apps>


```

What kind of goofy person runs asp .net on linux anyway?

---

