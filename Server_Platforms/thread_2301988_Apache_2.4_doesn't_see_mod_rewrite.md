---
title: "Apache 2.4 doesn't see mod_rewrite"
date: 2015-11-06
forum: Server Platforms
---

### Post by mefimess on 2015-11-06
[FONT=Verdana]Hello everyone ! 

[/FONT]At the beginning I'm sorry for my English - I hope everything will be undersandable.

I have a big problem with configure mod_rewrite on my local Ubuntu 14.04. Apache version is 2.4 . When I type in console 

**sudo a2enmod rewrite**

It says that module mod_rewrite is loaded, moreover - phpinfo() says the same. I've created the simplest .htaccess file I could: 

```

[B][COLOR=#465584][FONT=Courier]RewriteEngine On
RewriteRule ^index\.html$ index.php [L][/FONT][/COLOR]
[/B]
``` 

But unfortunately when I type in address bar my site with index.html there is 404 error... Inside 

[B]/etc/apache2/sites-available/default 

there is code:

```

[COLOR=#465584][FONT=Courier]<Directory /var/www/>
    Options Indexes FollowSymLinks
    Require all granted
    AllowOverride All
</Directory>
[/FONT][/COLOR]

```

I've google many of similar problems but nothing helped...

Could anyone help me ?

Thanks in advance.[/B]

---

### Post by matt_symes on 2015-11-06
You should get more help in this forum.

Thread moved to **Server Platforms**

BTW: Why apache 2.4 ?

---

### Post by mefimess on 2015-11-06
Thanks and sorry for problem.

I don't know why this version of apache - it probably has upgraded one time during system updates and it stayed like this. What do you recommend ? Uninstall this version and install earlier ?

---

### Post by matt_symes on 2015-11-06
> **mefimess said:**
> Thanks and sorry for problem.

It's no problem. I'm trying to help you.

> I don't know why this version of apache - it probably has upgraded one time during system updates and it stayed like this. What do you recommend ? Uninstall this version and install earlier ?

Don't worry. Somewhere between my eyes, brain and fingers, i thought you were on 2.2.

---

### Post by mefimess on 2015-11-07
thanks...

hmm ... so that looks that nobody has the same problem ? Maybe downgrade apache to lower level will help ?

Greetings

---

### Post by SeijiSensei on 2015-11-07
In 2.4 the default web root is /var/www/html, not /var/www.  What is the DocumentRoot in the default configuration?

---

### Post by mefimess on 2015-11-07
Okay, I changed this line in default file. Now is :

```

<Directory /var/www/html>
    Options Indexes FollowSymLinks
    Require all granted
    AllowOverride All
</Directory>

```

This is my file **/etc/apache2/sites-available/default**

but it doesn't help ...

---

### Post by SeijiSensei on 2015-11-07
And you are sure there is an index.php in /var/www/html and no index.html?

I presume you restarted Apache after making the earlier change.

---

### Post by mefimess on 2015-11-07
Hmmm... please wait. So I have to create ALL my websites in /var/www/html folder ? not in /var/www ? I have my website in /var/www/testpage

Previously I had all my websites in /var/www folder and .htaccess has worked for me

---

### Post by pqwoerituytrueiwoq on 2015-11-07
can you confirm your .htaccess file is operating?
just drop this line in it 
```
ErrorDocument 404 http://media.boingboing.net/wp-content/uploads/2011/12/404.jpg
```
and make make up a file name in your browser
i think 2.4 defaults to /var/www if you upgraded from 2.2, but that is not the point

also check if rewrite.load is in /etc/apache2/mods-enabled/
that is required for the rewrite model to work

also take a look at the error log
cat /var/log/apache2/error.log

---

### Post by mefimess on 2015-11-07
> **pqwoerituytrueiwoq said:**
> can you confirm your .htaccess file is operating?
just drop this line in it 
```
ErrorDocument 404 http://media.boingboing.net/wp-content/uploads/2011/12/404.jpg
```


yes, I put this line in my .htaccess file and opened localhost/testpage/blablabla.html and it didn't redirect me to media.boingboing. So probably .htaccess doesn't work at all.

> **pqwoerituytrueiwoq said:**
> also check if rewrite.load is in /etc/apache2/mods-enabled/
that is required for the rewrite model to work

I checked it - there is rewrite.load in mods-enabled. Apache says that mod_rewrite is enabled.

> **pqwoerituytrueiwoq said:**
> 
also take a look at the error log
cat /var/log/apache2/error.log

in logs I've plenty of errors but nothing connected with htaccess and mod_rewrite

---

### Post by SeijiSensei on 2015-11-07
1) By default, .htaccess is ignored.  It will be used if
```
AllowOverride On
```
is enabled in the <Directory> stanza for the website directory.  The relevant directory is defined by DocumentRoot which needs to have a corresponding <Directory> stanza for the same directory.

2) Bump up logging with "[LogLevel]("http://httpd.apache.org/docs/current/mod/core.html#loglevel") debug" or "LogLevel trace1".

---

### Post by mefimess on 2015-11-07
Uhm ... I put 
```

AllowOverride On

```

but now I'am completly lost. Where should I put my dir with webpage ? into /var/www or into /var/www/html ? These paths which you say should be in /etc/apache2/sites-available/default or /etc/apache2/sites-available/000-default.conf ? 

Thanks for patience and help

---

### Post by pqwoerituytrueiwoq on 2015-11-07
/var/www or /var/www/html is defined in your config file
your active config file is defied by the symlinks in this folder
```
readlink /etc/apache2/sites-enabled/*
```
i have one setup similar to this:
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www
        <Directory /var/www/>
                Require all granted
                Options FollowSymLinks
                Options +Indexes
                AllowOverride All
        </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
you can change /var/www to anyplace you want, just be sure www-data has read access to it, personally i like /home/www-data/ in that i keep several sites which i have managed to assigned to each a subdomain in what i am sure is a sloppy manner

---

### Post by SeijiSensei on 2015-11-07
Let's start from scratch.

Configurations are stored in /etc/apache2/sites-available/.  They are "enabled" by creating a symbolic link in /etc/apache2/sites-enabled/ like this:
```
sudo a2ensite 000-default
```
That site should be enabled by default when you install apache2.

If you have left-over configuration files from Apache 2.2, then remove the old Apache and reinstall 2.4 with
```

sudo apt-get remove --purge apache2
sudo rm -rf /etc/apache2
sudo apt-get install apache2

```
Make a backup of /etc/apache2 before you do this to be safe.

Now let's look at the content of /etc/apache2/sites-available/000-default.conf, the configuration file itself:

```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

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

```

The DocumentRoot directive shows where the default website files are stored.  In Apache 2.4 that is the directory /var/www/html.  This is a very stripped-down configuration, especially if you are used to seeing the one from version 2.2.  You can add the appropriate directives in a <Directory> container within the <VirtualHost> container:

```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

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

[B]        # add this to get debugging info; disable it when things are working correctly
        # if debug isn't sufficiently detailed, use "trace1" instead
        LogLevel debug
 
        # here is the definition for the DocumentRoot directory       
        <Directory "/var/www/html">
            RewriteEngine On
            RewriteRule ^index\.html$ index.php [L]
            
            Options Indexes FollowSymLinks
            Require all granted
        </Directory>        
[/B]</VirtualHost>

```
Don't use AllowOverride and remove any .htaccess file from /var/www/html.  If you have full control over the server configuration, you should put all the directives inside a relevant <Directory> stanza and not in .htaccess.  

Put the website files in /var/www/html.  Restart Apache with "sudo service apache2 restart".

---

### Post by mefimess on 2015-11-08
Thanks SeijiSensei for help. I did all you've written but now I have a problem that apache doesn't see my website. In 000-default.conf file there are paths to /var/www/html and there I have my testpage (/var/www/html/testpage/). When I try to open my site there is 404 error. When I change path in this file to /var/www there is no 404 error but PHP doesn't work - apache shows all my code. Can you help me with this one ?

Greetings

@edit
Ok, previous message is bad. I have paths /var/www/html in 000-default.conf. When I copy my website to /var/www/html there is visible in localhost, but when I open it there is no PHP running (all code is visible).

@edit2
I have done something bad I think. I tried to install :
```

sudo apt-get install apache2 php5 libapache2-mod-php5

```

but now when I try to restart apache I get the error 

```

AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message

```

Arghhh my last chance is probably to totally uninstall LAMP and install as new. This is very, very, very annoying, as I tried everything from official sources from ubuntu and I can't solve this damn problem of ServerName ...

---

### Post by mefimess on 2015-11-08
Nothing helped. After reinstall php5, mysql, phpmyadmin and apache2 there is exactly the same error. After installing 

```

[COLOR=#465584][FONT=Courier]sudo apt-get install libapache2-mod-php5[/FONT][/COLOR]

```

everything crash. I tried to add ServerName localhost in few places and apache now doesn't say about this error but still not wake-up. After 20 sec there is information that I have to check error.log file. 

```

[COLOR=#465584][FONT=Courier][Sun Nov 08 14:26:21.034899 2015] [mpm_event:notice] [pid 31490:tid 140162427312000] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:26:21.035022 2015] [core:notice] [pid 31490:tid 140162427312000] AH00094: Command line: '/usr/sbin/apache2'[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:28:56.111874 2015] [mpm_event:notice] [pid 31490:tid 140162427312000] AH00491: caught SIGTERM, shutting down[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:28:57.188752 2015] [mpm_event:notice] [pid 6066:tid 140177483171712] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:28:57.188861 2015] [core:notice] [pid 6066:tid 140177483171712] AH00094: Command line: '/usr/sbin/apache2'[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:30:25.612088 2015] [mpm_event:notice] [pid 6066:tid 140177483171712] AH00491: caught SIGTERM, shutting down[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:30:26.713257 2015] [mpm_event:notice] [pid 9958:tid 139966135859072] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:30:26.713385 2015] [core:notice] [pid 9958:tid 139966135859072] AH00094: Command line: '/usr/sbin/apache2'[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:30:59.018105 2015] [mpm_event:notice] [pid 9958:tid 139966135859072] AH00491: caught SIGTERM, shutting down[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:31:00.092657 2015] [mpm_prefork:notice] [pid 12101] AH00163: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:31:00.092777 2015] [core:notice] [pid 12101] AH00094: Command line: '/usr/sbin/apache2'[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier][Sun Nov 08 14:31:01.441796 2015] [mpm_prefork:notice] [pid 12101] AH00169: caught SIGTERM, shutting down[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier]PHP Fatal error:  [ionCube Loader] The Loader must appear as the first entry in the php.ini file in Unknown on line 0[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier]PHP Fatal error:  [ionCube Loader] The Loader must appear as the first entry in the php.ini file in Unknown on line 0[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier]PHP Fatal error:  [ionCube Loader] The Loader must appear as the first entry in the php.ini file in Unknown on line 0[/FONT][/COLOR]
[COLOR=#465584][FONT=Courier]PHP Fatal error:  [ionCube Loader] The Loader must appear as the first entry in the php.ini file in Unknown on line 0[/FONT][/COLOR]

```

I don't know how to repair it ... I need apache to work but I can't start it

---

### Post by SeijiSensei on 2015-11-08
In /etc/hosts on my machine there is the line
```

127.0.1.1     myhostname

```
That is the name I gave to the machine during installation.  The installer uses that name and adds the entry for 127.0.1.1 in /etc/hosts.  It also stores that name in /etc/hostname, where the host's name is specified.  That name is returned if you run the "hostname" command at a terminal prompt.  Some on a standard installation the /etc/hostname and /etc/hosts files are consistent, and Apache knows what name is attached to the 127.0.1.1 address. If you don't have an entry for 127.0.1.1 in /etc/hosts, or a "ServerName" directive in 000-default.conf, you will get the error you report.  

If I visit [http://myhostname/](http://myhostname/), I get the "Apache2 Ubuntu Default Page" which is contained in /var/www/html/index.html. I also get that page with [http://127.0.1.1/](http://127.0.1.1/).  

If you don't have an entry for 127.0.1.1 in /etc/hosts, try adding it and restarting Apache.  Now use that name in a URL as I did.  That should bring up index.html or index.php if the rewrite rule is working.

If this server is intended to accept requests from the public Internet, there's more to deal with.  Let's start with the basics first.

---

