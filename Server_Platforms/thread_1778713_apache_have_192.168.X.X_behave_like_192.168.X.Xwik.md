---
title: "apache have 192.168.X.X behave like 192.168.X.X/wiki"
date: 2011-06-09
forum: Server Platforms
---

### Post by giuspen on 2011-06-09
Hi,
I have an ubuntu server with apache and a wiki installed that is triggered when I insert the server address 192.168.X.X/wiki.
When I just insert 192.168.X.X I obtain the page /var/www/index.html.
Is it possible to have 192.168.X.X show the same as 192.168.X.X/wiki?

---

### Post by ruffEdgz on 2011-06-09
Depending on how you actually setup your apache, something like this should be able to help:
[list]
[*]Go to /etc/apache2/sites-enabled/
[*]If 000-default is the only file there, edit that one. If not, open whatever config file that holds the VirtualHost *:80 or something similar
[*]Once in, find your DocumentRoot and it should be something like this: **DocumentRoot /var/www**
[*]Change it to something like this: **DocumentRoot /var/www/wiki/**
[*]Change anything else in this config file that might conflict with this new change
[*]Save document and reload service
[/list]
This should help if the wiki page is the only site you want to display on this server. If you have other sites/pages that you want to host on this box, you might want to revisit this and see if placing the DocumenRoot as /var/www/wiki/ will still work for you.

PS - Another idea is to have a 301 redirect in your config file. More information can be found at this link: [http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect)

Cheers!

---

### Post by giuspen on 2011-06-10
to ruffEdgz:

I tried both your tips but no luck.
The only working solution that I found so far is to edit:

sudo nano /var/www/index.html

writing:

<html>
<head>
<meta http-equiv="refresh" content="0;url=http://192.168.X.X/wiki" />
</head>
<body><h1>Redirecting...</h1></body>
</html>

Thanks for the help, cheers!

---

### Post by volkswagner on 2011-06-10
You can disable the default site.

```
sudo a2dissite default
```

Then restart Apache2.

```
sudo /etc/init.d/apache2 reload
```

Apache loads the sites alphabetically if all NameBased VirtualServers have equal priority.  AKA, if they all use the wildcard which means load "this" server if no others have a better match.

```
<VirtualHost *:80>
```

or

```
<VirtualHost *>
```

---

### Post by giuspen on 2011-06-10
to volkswagner:

the solution to disable the site default is not good for me because I have all sites handled in the default config:

```
sudo nano /etc/apache2/sites-available/default
```

I have trac, hg, moinmoin all in that text file...

---

### Post by volkswagner on 2011-06-10
> **giuspen said:**
> to volkswagner:

the solution to disable the site default is not good for me because I have all sites handled in the default config:

```
sudo nano /etc/apache2/sites-available/default
```

I have trac, hg, moinmoin all in that text file...

How do you access the other sites (trac, hg, moinmoin)?

I prefer to create an individual Vhost file as described in the [sticky]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html").

If you are happy with your workaround perhaps you should mark your thread as solved.  If you are seeking alternatives please give a little more detail about your setup and goals.

---

### Post by giuspen on 2011-06-11
Here's the apache "sites-available/default" which includes moinmoin, trac and hg:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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

        ### moin
        ScriptAlias /wiki "/usr/share/moin/mywiki/moin.cgi"
        alias /moin_static192 "/usr/share/moin/htdocs"
        <Directory /usr/share/moin/htdocs>
                Order allow,deny
                allow from all
        </Directory>
        ### end moin

        ### trac
        <Location "/trac">
                SetHandler mod_python
                PythonInterpreter main_interpreter
                PythonHandler trac.web.modpython_frontend
                PythonOption TracEnvParentDir /home/qsduser/trac
                PythonOption TracUriRoot /trac
        </Location>
        <LocationMatch "/trac/[^/]+/login">
                AuthType Basic
                AuthName "Trac"
                AuthUserFile /home/qsduser/trac/userpw
                Require valid-user
        </LocationMatch>
        ### end trac

        ### hg repos
        ScriptAlias /repository/qst/core "/home/qsduser/repository/qst/core/hgweb.cgi"
        <Location "/repository/qst/core">
        </Location>

        ScriptAlias /repository/qst/q_163a "/home/qsduser/repository/qst/q_163a/hgweb.cgi"
        <Location "/repository/qst/q_163a">
        </Location>

        ScriptAlias /repository/projects "/home/qsduser/repository/projects/hgweb.cgi"
        <Location "/repository/projects">
        </Location>

        ScriptAlias /repository/docs "/home/qsduser/repository/docs/hgweb.cgi"
        <Location "/repository/docs">
        </Location>
        ### end hg repos

</VirtualHost>
```

I would like to have moinmoin reached not only at /wiki but also at / just modifying the "sites-available/default"

---

### Post by volkswagner on 2011-06-11
You could try adding an Alias directive to your default file like:


```
# Make MoinMoin default site for /
Alias / "/var/www/wiki"
```

---

### Post by donniezazen on 2011-06-11
Should your web related stuff be in /var/www/ directory from security point of view? Ajaxplorer and rutorrent are in www folder which lets them resolve as myserver.com/ajaxplorer and myserver/rutorrent automatically without any change in virtual host. Webmin is installed in /usr/share/. I was wondering if i should create a link to www folder or direct DocumentRoot to /usr/share/webmin.

Thanks.

---

### Post by giuspen on 2011-06-13
I tried with:

```
Alias / "/usr/share/moin/mywiki"
```

and also just adding a symbolic link to /var/www but no luck

About put moinmoin wiki to /var/www for security reasons this is for my private network so no security issues.

Since adding the redirection inside of index.html satisfies my needs I will set this thread as solved, thanks to everybody replied.

---

### Post by volkswagner on 2011-06-13
> **giuspen said:**
> I tried with:

```
Alias / "/usr/share/moin/mywiki"
```

and also just adding a symbolic link to /var/www but no luck

About put moinmoin wiki to /var/www for security reasons this is for my private network so no security issues.

Since adding the redirection inside of index.html satisfies my needs I will set this thread as solved, thanks to everybody replied.


Are you sure that is the right path?

From your host file:
```
alias /moin_static192 "/usr/share/moin/htdocs"

```

Does MoinMoin have any info already in /var/www or is it all in /usr/share/moin...?

---

### Post by giuspen on 2011-06-15
> **volkswagner said:**
> Are you sure that is the right path?

From your host file:
```
alias /moin_static192 "/usr/share/moin/htdocs"

```

Does MoinMoin have any info already in /var/www or is it all in /usr/share/moin...?

/usr/share/moin/mywiki/moin.cgi is the key.

there are some generic settings also in /etc/moin/

about "/moin_static192" I didn't understand the reason for it since I reach the wiki with "/wiki" but if I change the number 192 (which is the version num) with another num it doesn't work

---

### Post by volkswagner on 2011-06-15
For kicks, perhaps you can try changing

```
alias /moin_static192 "/usr/share/moin/htdocs"
```

to 

```
alias /moin_static192/wiki "/usr/share/moin/htdocs"
```

I am not familiar with MoinMoin.  I have worked with Twiki and Foswiki, both of which have a configuration page where the alias could be set.  Perhaps you should be making the change outside of apache2.

---

