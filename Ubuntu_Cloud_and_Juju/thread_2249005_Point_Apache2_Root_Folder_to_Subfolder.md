---
title: "Point Apache2 Root Folder to Subfolder"
date: 2014-10-18
forum: Ubuntu Cloud and Juju
---

### Post by j-adoin-d on 2014-10-18
This topic has been covered in the past, but I am posting it again, because none of the solutions work for me.

I have run chmod 755 on the folder that I want to serve as the root. It is a subfolder of /var/www/html/ The folder I want to be the root is /var/www/html/lvf/public_html/ .

In /etc/apache2/sites-available/ I copied 000-default.conf to lvf.conf. Here is the file:
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost 
    ServerName lvf.org
    ServerAlias www.lvf.org
    DocumentRoot /var/www/html/lvf/public_html
    <Directory />
    Options FollowSymLinks
    AllowOverride None
    </Directory>
    <Directory /var/www/html/lvf/public_html/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

Posts have also mention editing a file called default in sites-available/ . Here is the file:
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
    <Directory />
        Options Follow SymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/html/>
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

    Alias /python/ "/var/www/html/lvf/public_html/p-app/"
    <Directory "/var/www/html/lvf/public_html/p-app/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

I have enabled default and lvf.conf, and disabled 000-default.conf.

I have run sudo service apache2 restart.

When I check [http://localhost](http://localhost), I get the Index of /var/www/html/ .

What am I missing?

---

### Post by SeijiSensei on 2014-10-18
This looks like another change from 12.04 to me.  To make name-based virtual hosts work, there needs to be this directive
```
NameVirtualHost  *:80
```
somewhere in the Apache configuration.  I thought it used to be in /etc/apache2/ports.conf by default, but I don't see it there any longer.  So I'd add that line to ports.conf and restart Apache.

Why this isn't a default is beyond me.  It's hardly a security issue.

Even with that enabled, however, it still won't work if you visit [http://localhost/](http://localhost/), because that URL doesn't match the "ServerName" [www.lvf.org](www.lvf.org).  You must make sure that hostname points to an interface on the computer, and use [http://www.lvf.org/](http://www.lvf.org/) or [http://lvf.org/](http://lvf.org/) (the ServerAlias) to invoke the virtual host.  Apache determines which virtual host to use based on the server name in the URL.

As always, it's best to read the official documentation, in this case: [http://httpd.apache.org/docs/2.4/vhosts/name-based.html](http://httpd.apache.org/docs/2.4/vhosts/name-based.html)

---

### Post by j-adoin-d on 2014-10-19
I added it to ports.conf, but it still doesn't work.

---

### Post by SeijiSensei on 2014-10-20
> **j-adoin-d said:**
> I added it to ports.conf, but it still doesn't work.

And what about this:
> **SeijiSensei said:**
> Even with that enabled, however, it still won't work if you visit [http://localhost/](http://localhost/), because that URL doesn't match the "ServerName" [www.lvf.org](www.lvf.org).  You must make sure that hostname points to an interface on the computer, and use [http://www.lvf.org/](http://www.lvf.org/) or [http://lvf.org/](http://lvf.org/) (the ServerAlias) to invoke the virtual host.  Apache determines which virtual host to use based on the server name in the URL.

Did you read the documentation I pointed you to?

---

### Post by Doug S on 2014-10-21
I have a test 14.04 server on my internal network. I access the Apache web server via s15.smythies.com (only works on my LAN).
I left 000-default.conf alone. The older name of default was for before 14.04.
I added a file named bla.conf, made a sub-directory. /var/www/html/bla and added an A record to my list for bind, pointing to the same place as s15:```
epson-wp2       IN      A       192.168.111.111
s15             IN      A       192.168.111.112
[COLOR=#ff0000]bla             IN      A       192.168.111.112[/COLOR]
s16             IN      A       192.168.111.113
```I never added "NameVirtualHost  *:80" to anywhere (but I do see on my 12.04 server that it used to be there).
It works as expected, serving a test page from /var/www/html/bla/index.html if I enter bla.smythies.com. Bla.conf:```
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
        ServerName bla.smythies.com
        ServerAlias www.bla.smythies.com
        DocumentRoot /var/www/html/bla

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/html/bla>
                Options Indexes FollowSymLinks MultiViews Includes
                AllowOverride All
                Order allow,deny
                allow from all
                DirectoryIndex index.html
        </Directory>

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

---

### Post by SeijiSensei on 2014-10-21
> **Doug S said:**
> I never added "NameVirtualHost  *:80" to anywhere (but I do see on my 12.04 server that it used to be there).

Apparently the directive has been [removed]("http://httpd.apache.org/docs/current/mod/core.html#namevirtualhost") in Apache 2.4.  

> In 2.3.11 and later, any time an IP address and port combination is used in multiple virtual hosts, name-based virtual hosting is automatically enabled for that address.

---

### Post by burnsmicro2 on 2014-10-21
Aside from understanding very little about apache2 configuration, I am having a devil of a time being able to load html files from a user folder through localhost. The more I read, the more confusing it gets. I seem to lack the critical mass of knowledge to allow me to fully grasp how things work.

 What I am trying to do is to display files and folders on my FF browser and these files/folders are located in a local folder: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/. In the past, I seem to recall I managed this with a symlink in /var/ww to the target folder. But, I am no longer able to do that and I gather, it is dangerous. Instead, I followed advice on the web to set up a VirtualHost.

 I do not mess with apache2.conf. I do attempt to set up a VirtualHost through solvoj.conf which is dutifully a2dissite'ed and a2ensite'ed before restarting apache2 and testing my localhost connection.

 ```
<VirtualHost *:80> 
         ServerAdmin bob.chambers@doodle.com
         ServerName solvoj 
         ServerAlias www.solvoj.com 
         DocumentRoot /home/robert/Development/mCRefactor/gAppGUI-1 
  
         <Directory /> 
                 Options FollowSymLinks 
                 AllowOverride None 
         </Directory> 
  
  <Directory /home/robert/Development/mCRefactor/gAppGUI-1> 
     Options Indexes FollowSymLinks 
     AllowOverride None 
     Require all granted 
  </Directory> 
      LogLevel trace8 
  
         ErrorLog ${APACHE_LOG_DIR}/error.log 
         CustomLog ${APACHE_LOG_DIR}/access.log combined 
  </VirtualHost> 
  
 # vim: syntax=apache ts=4 sw=4 sts=4 sr noet
``` 

 Two problems arise:
 
 1. the ServerName, solvoj, is appended to the TargetPath <Directory TargetPath> and, so is the url entered from the target. For instance, if the Directory is set as:
 
  <Directory /home/robert/Development/mCRefactor/gAppGUI-1>
 
 Then, after attempting to connect to [http://localhost]("http://localhost/"), the trace8 tells me  
 ...[client 127.0.0.1:40384] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/
 
 ..and, after attempting to connect to [http://localhost]("http://localhost/")/solvoj, the trace8 tells me  
 ...[client 127.0.0.1:40411] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/solvoj
 
 2. The other problem is that even when I fall back to a bare localhost and the right path is generated, I get an error 403 “You don't have permission to access /solvoj on this server.”. In this regard, every folder in the path has permissions set to 755.

---

### Post by burnsmicro2 on 2014-10-21
Aside from understanding very little about apache2 configuration, I am having a devil of a time being able to load html files from a user folder through localhost. The more I read, the more confusing it gets. I seem to lack the critical mass of knowledge to allow me to fully grasp how things work.

 What I am trying to do is to display files and folders on my FF browser and these files/folders are located in a local folder: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/. In the past, I seem to recall I managed this with a symlink in /var/ww to the target folder. But, I am no longer able to do that and I gather, it is dangerous. Instead, I followed advice on the web to set up a VirtualHost.

 I do not mess with apache2.conf. I do attempt to set up a VirtualHost through solvoj.conf which is dutifully a2dissite'ed and a2ensite'ed before restarting apache2 and testing my localhost connection.

 ```
<VirtualHost *:80> 
         ServerAdmin bob.chambers@doodle.com
         ServerName solvoj 
         ServerAlias www.solvoj.com 
         DocumentRoot /home/robert/Development/mCRefactor/gAppGUI-1 
  
         <Directory /> 
                 Options FollowSymLinks 
                 AllowOverride None 
         </Directory> 
  
  <Directory /home/robert/Development/mCRefactor/gAppGUI-1> 
     Options Indexes FollowSymLinks 
     AllowOverride None 
     Require all granted 
  </Directory> 
      LogLevel trace8 
  
         ErrorLog ${APACHE_LOG_DIR}/error.log 
         CustomLog ${APACHE_LOG_DIR}/access.log combined 
  </VirtualHost> 
  
 # vim: syntax=apache ts=4 sw=4 sts=4 sr noet
``` 

 Two problems arise:
 
 1. the ServerName, solvoj, is appended to the TargetPath <Directory TargetPath> and, so is the url entered from the target. For instance, if the Directory is set as:
 
  <Directory /home/robert/Development/mCRefactor/gAppGUI-1>
 
 Then, after attempting to connect to [http://localhost]("http://localhost/"), the trace8 tells me  
 ...[client 127.0.0.1:40384] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/
 
 ..and, after attempting to connect to [http://localhost]("http://localhost/")/solvoj, the trace8 tells me  
 ...[client 127.0.0.1:40411] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/solvoj
 
 2. The other problem is that even when I fall back to a bare localhost and the right path is generated, I get an error 403 “You don't have permission to access /solvoj on this server.”. In this regard, every folder in the path has permissions set to 755.

---

### Post by burnsmicro2 on 2014-10-21
Aside from understanding very little about apache2 configuration, I am having a devil of a time being able to load html files from a user folder through localhost. The more I read, the more confusing it gets. I seem to lack the critical mass of knowledge to allow me to fully grasp how things work.

 What I am trying to do is to display files and folders on my FF browser and these files/folders are located in a local folder: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/. In the past, I seem to recall I managed this with a symlink in /var/ww to the target folder. But, I am no longer able to do that and I gather, it is dangerous. Instead, I followed advice on the web to set up a VirtualHost.

 I do not mess with apache2.conf. I do attempt to set up a VirtualHost through solvoj.conf which is dutifully a2dissite'ed and a2ensite'ed before restarting apache2 and testing my localhost connection.

 ```
<VirtualHost *:80> 
         ServerAdmin bob.chambers@doodle.com
         ServerName solvoj 
         ServerAlias www.solvoj.com 
         DocumentRoot /home/robert/Development/mCRefactor/gAppGUI-1 
  
         <Directory /> 
                 Options FollowSymLinks 
                 AllowOverride None 
         </Directory> 
  
  <Directory /home/robert/Development/mCRefactor/gAppGUI-1> 
     Options Indexes FollowSymLinks 
     AllowOverride None 
     Require all granted 
  </Directory> 
      LogLevel trace8 
  
         ErrorLog ${APACHE_LOG_DIR}/error.log 
         CustomLog ${APACHE_LOG_DIR}/access.log combined 
  </VirtualHost> 
  
 # vim: syntax=apache ts=4 sw=4 sts=4 sr noet

``` 

 Two problems arise:
 
 1. the ServerName, solvoj, is appended to the TargetPath <Directory TargetPath> and, so is the url entered from the target. For instance, if the Directory is set as:
 
  <Directory /home/robert/Development/mCRefactor/gAppGUI-1>
 
 Then, after attempting to connect to [http://localhost]("http://localhost/"), the trace8 tells me  
 ...[client 127.0.0.1:40384] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/
 
 ..and, after attempting to connect to [http://localhost]("http://localhost/")/solvoj, the trace8 tells me  
 ...[client 127.0.0.1:40411] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/solvoj
 
 2. The other problem is that even when I fall back to a bare localhost and the right path is generated, I get an error 403 “You don't have permission to access /solvoj on this server.”. In this regard, every folder in the path has permissions set to 755.

---

### Post by SeijiSensei on 2014-10-22
I'd start by removing "Require all granted".  See this: [http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html](http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html)

---

### Post by burnsmicro2 on 2014-10-22
Is there an Apache2 Config 101 that clearly explains the basic configuration directives to a newby?

> **SeijiSensei said:**
> I'd start by removing "Require all granted".  See this: [http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html](http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html)

This doc tells me "The following examples will grant or deny     access to all requests: Require all granted,    Require all denied". Is that not what I am after, to resolve what trace8 calls an authentication failure?

In any event, I commented out "Require all granted". Then, when I tried to connect with localhost, I got a 403 error and trace8 showed:
   ```
..[pid 14240] mod_authz_core.c(802): [client 127.0.0.1:40863] AH01626: authorization result of Require all denied: denied 
..[pid 14240] mod_authz_core.c(802): [client 127.0.0.1:40863] AH01626: authorization result of <RequireAny>: denied 
 ..[pid 14240] [client 127.0.0.1:40863] AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/
```

When I tried to connect with localhost/solvoj, trace8 showed:
```
...AH01630: client denied by server configuration: /home/robert/Development/mCRefactor/gAppGUI-1/solvoj/solvoj/
```
Note the ".../solvoj/solvoj/" at the end of the path string.

Then, I found that apachet2.conf had a "Request all denied" for <Directory />. On changing this to "Request all granted", and, attempt to connect to localhost, which dug up and displayed an html page burried in the bowels of my PC (???).

In short, I am flailing in the dark and desperately need to learn the basics like:

[LIST]
[*]what does ServerName really mean? How is this reflected in the VirtualHost's URL? 
[*]what does ServerAlias really mean? How is this reflected in the VirtualHost's URL? 
[*]what does DocumentRoot really mean? How is this reflected in the VirtualHost's URL? 
[*]what do the <Directory ..> directives really mean? 
[*]does <Directory /> mean, apply these rules to anyone attempting to connect to [http://192.168.2.123?](http://192.168.2.123?) 
[*]then, what does <Directory /var/www/> mean? 
[/LIST]

---

### Post by burnsmicro2 on 2014-10-22
Doh!

I just stumbled upon apache2 [Getting Started]("http://httpd.apache.org/docs/2.4/getting-started.html"). I have no idea why Mr. Google never found this for me. So far, it seems to be exactly what I need.

---

