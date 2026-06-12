---
title: "upgraded apache 2.2 to 2.4, some sites return 403 error"
date: 2013-12-15
forum: Server Platforms
---

### Post by FabianN on 2013-12-15
I upgraded my install of Ubuntu server from 12.10 to 13.10. After the upgrade I found that my sites configured in apache were not working and with research found that it was due to changes in the config files from apache 2.2 to apache 2.4. I found the following information and made changes where they seemed to apply:
[http://httpd.apache.org/docs/current/upgrading.html](http://httpd.apache.org/docs/current/upgrading.html)
[http://stackoverflow.com/questions/9127802/munin-server-with-apache-you-dont-have-permission-to-access-munin-on-this-se/12058057#12058057](http://stackoverflow.com/questions/9127802/munin-server-with-apache-you-dont-have-permission-to-access-munin-on-this-se/12058057#12058057)
[http://tfountain.co.uk/blog/2013/10/18/fixing-apache-ubuntu-13-10](http://tfountain.co.uk/blog/2013/10/18/fixing-apache-ubuntu-13-10)

This fixed up most of the sites, but there are three that are giving me 403 errors and I am at the end of my rope of trying to figure out how to get it working again. The sites that are returning 403 errors is my munin install, my gitlab install, and my gitlab-ci install. I figure they are all having simular issues and the solution for one is likely the solution for others, but I've tried everything I can think of and no success.

Here are various files that would help diagnosing this issue.

Munin related files:

/etc/munin/apache.conf
```
[COLOR=#000000]# Enable this for template generation[/COLOR]Alias /munin /var/cache/munin/www

# Enable this for cgi-based templates
#Alias /munin-cgi/static /var/cache/munin/www/static
#ScriptAlias /munin-cgi /usr/lib/munin/cgi/munin-cgi-html
#<Location /munin-cgi>
#    Order allow,deny
#    Allow from localhost 127.0.0.0/8 ::1
#    AuthUserFile /etc/munin/munin-htpasswd
#    AuthName "Munin"
#    AuthType Basic
#    require valid-user
#</Location>

<Directory /var/cache/munin/www>
        #Order allow,deny
        #Allow from localhost 127.0.0.0/8 ::1
        Options All
        AllowOverride All
        Require all granted
        #Options FollowSymLinks SymLinksIfOwnerMatch

    # This file can be used as a .htaccess file, or a part of your apache
    # config file.
    #
    # For the .htaccess file option to work the munin www directory
    # (/var/cache/munin/www) must have "AllowOverride all" or something 
    # close to that set.
    #

    # AuthUserFile /etc/munin/munin-htpasswd
    # AuthName "Munin"
    # AuthType Basic
    # require valid-user

    # This next part requires mod_expires to be enabled.
    #
    
    # Set the default expiration time for files to 5 minutes 10 seconds from
    # their creation (modification) time.  There are probably new files by
    # that time. 
    #

    <IfModule mod_expires.c>
        ExpiresActive On
        ExpiresDefault M310
    </IfModule>

</Directory> 

# Enables fastcgi for munin-cgi-html if present
#<Location /munin-cgi>
#    <IfModule mod_fastcgi.c>
#        SetHandler fastcgi-script
#    </IfModule>
#</Location>

#<Location /munin-cgi/static>
#    SetHandler None
#</Location>

# Enables fastcgi for munin-cgi-graph if present
ScriptAlias /munin-cgi/munin-cgi-graph /usr/lib/munin/cgi/munin-cgi-graph
<Location /munin-cgi/munin-cgi-graph>
    #Order allow,deny
    #Allow from localhost 127.0.0.0/8 ::1
    Options All
    Require all granted
    # AuthUserFile /etc/munin/munin-htpasswd
    # AuthName "Munin"
    # AuthType Basic
    # require valid-user
    <IfModule mod_fcgid.c>
        SetHandler fcgid-script
    </IfModule>
    <IfModule !mod_fcgid.c>
        SetHandler cgi-script
    </IfModule>
</Location>

ScriptAlias /munin-cgi/munin-cgi-html /usr/lib/munin/cgi/munin-cgi-html
<Location /munin-cgi/munin-cgi-html>
    #Order allow,deny
    #Allow from localhost 127.0.0.0/8 ::1
    Options All
    Require all granted
    # AuthUserFile /etc/munin/munin-htpasswd
    # AuthName "Munin"
    # AuthType Basic
    # require valid-user
    <IfModule mod_fcgid.c>
        SetHandler fcgid-script
    </IfModule>
    <IfModule !mod_fcgid.c>
        SetHandler cgi-script
    </IfModule>
</Location>
```[COLOR=#222222][FONT=Verdana]
/var/log/apache2/munin/error.log:
[/FONT][/COLOR]```
[FONT=Verdana][Sat Dec 14 21:35:38.581644 2013] [authz_core:error] [pid 29141] [client 192.168.1.1:57415] AH01630: client denied by server configuration: /usr/lib/munin/cgi/munin-cgi-html
[/FONT][FONT=Verdana][Sat Dec 14 21:35:38.939689 2013] [authz_core:error] [pid 29141] [client 192.168.1.1:57415] AH01630: client denied by server configuration: /etc/munin/static/favicon.ico
[/FONT][FONT=Verdana][Sat Dec 14 21:35:39.607071 2013] [authz_core:error] [pid 29141] [client 192.168.1.1:57415] AH01630: client denied by server configuration: /usr/lib/munin/cgi/munin-cgi-html
[/FONT][FONT=Verdana][Sat Dec 14 21:35:40.002671 2013] [authz_core:error] [pid 29141] [client 192.168.1.1:57415] AH01630: client denied by server configuration: /etc/munin/static/favicon.ico
[/FONT][FONT=Verdana][Sat Dec 14 21:39:37.822173 2013] [authz_core:error] [pid 29398] [client 192.168.1.1:57527] AH01630: client denied by server configuration: /usr/lib/munin/cgi/munin-cgi-html
[/FONT][FONT=Verdana][Sat Dec 14 21:39:38.283179 2013] [authz_core:error] [pid 29398] [client 192.168.1.1:57527] AH01630: client denied by server configuration: /etc/munin/static/favicon.ico
[/FONT][FONT=Verdana][Sat Dec 14 21:42:11.890270 2013] [authz_core:error] [pid 29896] [client 192.168.1.1:57620] AH01630: client denied by server configuration: /usr/lib/munin/cgi/munin-cgi-html
[/FONT][FONT=Verdana][Sat Dec 14 21:42:12.289243 2013] [authz_core:error] [pid 29896] [client 192.168.1.1:57620] AH01630: client denied by server configuration: /etc/munin/static/favicon.ico
[/FONT][FONT=Verdana][Sat Dec 14 21:42:12.840027 2013] [authz_core:error] [pid 29896] [client 192.168.1.1:57620] AH01630: client denied by server configuration: /usr/lib/munin/cgi/munin-cgi-html
[/FONT][FONT=Verdana][Sat Dec 14 21:42:13.184672 2013] [authz_core:error] [pid 29896] [client 192.168.1.1:57620] AH01630: client denied by server configuration: /etc/munin/static/favicon.ico
[/FONT][FONT=Verdana][Sat Dec 14 21:42:13.458130 2013] [authz_core:error] [pid 29896] [client 192.168.1.1:57620] AH01630: client denied by server configuration: /usr/lib/munin/cgi/munin-cgi-html
[/FONT][FONT=Verdana][Sat Dec 14 21:42:13.865968 2013] [authz_core:error] [pid 29896] [client 192.168.1.1:57620] AH01630: client denied by server configuration: /etc/munin/static/favicon.ico[/FONT]
```

For gitlab/gitlab-ci, since it is a ruby app, I have the passenger module for apache loaded. They both have nearly the same config files, only differences being the directory location for the app.

And then these are the relevant apache files:
/et/apache2/sites-available/gitlab.conf:
```
[COLOR=#000000]# require apache module mod_proxy and mod_proxy_http[/COLOR]<VirtualHost *:80>
    ServerAdmin gitlab@tevorta.com
    ServerName gitlab.tevorta.com
    ServerAlias git.tevorta.com

    DocumentRoot /home/git/gitlab/public    
      <Directory /home/git/gitlab/public>
         # This relaxes Apache security settings.
         AllowOverride all
         Require all granted
         # MultiViews must be turned off.
         Options -MultiViews
      </Directory>

    # Uncomment if you want redirect from HTTP to HTTPS
    #RewriteEngine   on
    #RewriteCond     %{SERVER_PORT} ^80$
    #RewriteRule     ^(.*)$ https://%{SERVER_NAME}$1 [L,R]
    
    #ProxyPass / http://127.0.0.1:3000/
    #ProxyPassReverse / http://127.0.0.1:3000/
    #ProxyPreserveHost On

    CustomLog /var/log/apache2/gitlab/access.log combined
    ErrorLog  /var/log/apache2/gitlab/error.log
</VirtualHost>
<VirtualHost *:443>
    ServerName gitlab.tevorta.com
    ServerAlias git.tevorta.com
    ServerAdmin gitlab@melchior.tevorta.com

    DocumentRoot /home/git/gitlab/public    
      <Directory /home/git/gitlab/public>
         # This relaxes Apache security settings.
         AllowOverride all
         Require all granted
         # MultiViews must be turned off.
         Options -MultiViews
      </Directory>

    SSLEngine On
    SSLProtocol all -SSLv2
    SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM:+LOW
    SSLCertificateFile    /etc/ssl/certs/gitlab.tevorta.com.crt
    SSLCertificateKeyFile /etc/ssl/private/gitlab.tevorta.com.key
    #SSLCertificateChainFile /etc/apache2/ssl/cacert.pem

    #ProxyPass / http://127.0.0.1:3000/
    #ProxyPassReverse / http://127.0.0.1:3000/
    #ProxyPreserveHost On

    CustomLog /var/log/apache2/gitlab/access.log combined
    ErrorLog  /var/log/apache2/gitlab/error.log

    <FilesMatch "\.(cgi|shtml|phtml|php)$">
        SSLOptions +StdEnvVars
    </FilesMatch>
    <Directory /usr/lib/cgi-bin>
        SSLOptions +StdEnvVars
    </Directory>

    BrowserMatch "MSIE [2-6]" \
        nokeepalive ssl-unclean-shutdown \
        downgrade-1.0 force-response-1.0
    # MSIE 7 and newer should be able to use keepalive
    BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
 [COLOR=#000000]</VirtualHost>[/COLOR]
```

/var/logs/apache2/gitlab/error.log
```
[Sat Dec 14 20:53:42.937601 2013] [authz_core:error] [pid 19980] [client 192.168.1.11:56222] AH01630: client denied by server configuration: /home/git/gitlab/public/, referer: http://melchior.tevorta.com/
[Sat Dec 14 20:53:43.189605 2013] [authz_core:error] [pid 19980] [client 192.168.1.11:56222] AH01630: client denied by server configuration: /home/git/gitlab/public/favicon.ico
[Sat Dec 14 20:53:45.204103 2013] [authz_core:error] [pid 19980] [client 192.168.1.11:56222] AH01630: client denied by server configuration: /home/git/gitlab/public/, referer: http://melchior.tevorta.com/
[Sat Dec 14 20:53:45.641012 2013] [authz_core:error] [pid 19980] [client 192.168.1.11:56222] AH01630: client denied by server configuration: /home/git/gitlab/public/favicon.ico
[Sat Dec 14 20:57:46.759168 2013] [authz_core:error] [pid 19980] [client 66.249.74.95:42147] AH01630: client denied by server configuration: /home/git/gitlab/public/direwolf20
[Sat Dec 14 21:04:54.535283 2013] [authz_core:error] [pid 20005] [client 180.76.5.65:24107] AH01630: client denied by server configuration: /home/git/gitlab/public/direwolf20
[Sat Dec 14 21:20:25.640136 2013] [authz_core:error] [pid 25983] [client 192.168.1.11:56945] AH01630: client denied by server configuration: /home/git/gitlab/public/, referer: http://melchior.tevorta.com/
[Sat Dec 14 21:20:26.015333 2013] [authz_core:error] [pid 25983] [client 192.168.1.11:56945] AH01630: client denied by server configuration: /home/git/gitlab/public/favicon.ico
[Sat Dec 14 21:20:31.788902 2013] [authz_core:error] [pid 25979] [client 192.168.1.11:56946] AH01630: client denied by server configuration: /home/git/gitlab/public/favicon.ico
[Sat Dec 14 21:26:14.038344 2013] [autoindex:error] [pid 26947] [client 192.168.1.11:57110] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive, referer: http://melchior.tevorta.com/
[Sat Dec 14 21:31:50.115765 2013] [autoindex:error] [pid 28550] [client 192.168.1.11:57264] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive, referer: http://melchior.tevorta.com/
[Sat Dec 14 22:43:04.801232 2013] [autoindex:error] [pid 5661] [client 192.168.1.11:59256] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive, referer: http://munin.tevorta.com/
[Sat Dec 14 22:57:44.152715 2013] [autoindex:error] [pid 5866] [client 192.168.1.11:59676] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive, referer: http://melchior.tevorta.com/
[Sun Dec 15 01:21:01.162199 2013] [autoindex:error] [pid 14947] [client 202.46.62.97:61160] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 01:22:35.053686 2013] [autoindex:error] [pid 14940] [client 119.63.193.195:1805] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 07:18:00.240021 2013] [autoindex:error] [pid 19020] [client 202.46.58.23:17431] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 07:19:26.795230 2013] [autoindex:error] [pid 19016] [client 119.63.193.132:40122] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 13:20:30.111945 2013] [autoindex:error] [pid 13933] [client 202.46.61.32:38818] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 13:22:03.882468 2013] [autoindex:error] [pid 13785] [client 119.63.193.130:60435] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 16:20:39.630363 2013] [autoindex:error] [pid 9379] [client 192.168.1.11:57209] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 16:52:44.824098 2013] [autoindex:error] [pid 15544] [client 192.168.1.11:58202] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 16:52:45.208589 2013] [autoindex:error] [pid 15544] [client 192.168.1.11:58202] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 17:54:11.245529 2013] [autoindex:error] [pid 25863] [client 192.168.1.11:60303] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[Sun Dec 15 17:54:11.545378 2013] [autoindex:error] [pid 25863] [client 192.168.1.11:60303] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive
[COLOR=#000000][Sun Dec 15 17:57:13.794691 2013] [autoindex:error] [pid 26537] [client 192.168.1.11:60370] AH01276: Cannot serve directory /home/git/gitlab/public/: No matching DirectoryIndex (index.html,index.cgi,index.pl,index.php,index.xhtml,index.htm) found, and server-generated directory index forbidden by Options directive[/COLOR]
```


Is there anyone out there that can help? I've already tried doing a clean re-install of munin (since I didn't care that much about the history). Just getting one of these fixed would be great.

---

