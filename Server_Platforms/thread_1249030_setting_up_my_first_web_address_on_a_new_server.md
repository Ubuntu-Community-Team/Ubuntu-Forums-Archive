---
title: "setting up my first web address on a new server"
date: 2009-08-24
forum: Server Platforms
---

### Post by krraleigh on 2009-08-24
Hi I have web space over at rack space and I have just finished configuring the setup stage. I have a few questions on how to get my web address recognized when a user looks for it on the web. Now I was told that I had to change the name server space, as it was parked over a go daddy, and I did this, but I am not sure what the next steps would be. Can anyone point me to an article that will advise me?
 
thanx kevin

---

### Post by Jerry.S on 2009-08-24
Did you set up DNS to point to your site? Dns is the first stop on a request when someone types in your domain name. If you have not set up DNS no one will find you

Jerry

---

### Post by mbeach on 2009-08-25
This link pretty much seems to cover it:

[http://www.rackspace.com/apps/support/portal/1110/1138/1166/1174](http://www.rackspace.com/apps/support/portal/1110/1138/1166/1174)

Some more reference for you though:
[http://help.godaddy.com/article/664](http://help.godaddy.com/article/664)

EDIT:
The next step may be just to wait - it will take a while for the changes to propagate

---

### Post by krraleigh on 2009-08-25
I appreciate the help
I setup the domain name servers as instructed
I also setup the domains in the domain manager on the rack space control panel; had something to do with A Names, MX Names - email, and CNames.
 
The last step I think is to setup apache to see the names. I found an article, but I am a little unsure of what to do here. The reason is the file that I need to modify contains a lot of information that I don't know about. I backed the file up, but I could use some insight as to this one point!
 
The file in question is the default file, and it contains the follow information:
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
 
I need to add the following to the file:
<VirtualHost [www.1purposebethel.com]("mhtml:{E0FB9D54-8691-455A-8144-CE97AC34CBF5}mid://00001064/!x-usc:http://www.1purposebethel.com/")>
ServerAdmin [kraleigh@sbcglobal.net]("mhtml:{E0FB9D54-8691-455A-8144-CE97AC34CBF5}mid://00001064/!x-usc:mailto:kraleigh@sbcglobal.net")
DocumentRoot /var/www/1purposebethel
ServerName [www.1purposebethel.com]("mhtml:{E0FB9D54-8691-455A-8144-CE97AC34CBF5}mid://00001064/!x-usc:http://www.1purposebethel.com/")
ErrorLog /var/www/logs/error_log
TransferLog /var/www/logs/access_log
</VirtualHost>
 
<VirtualHost www.greateropportunities.com>
ServerAdmin [kraleigh@sbcglobal.net]("mhtml:{E0FB9D54-8691-455A-8144-CE97AC34CBF5}mid://00001064/!x-usc:mailto:kraleigh@sbcglobal.net")
DocumentRoot /var/www/greateropportunities
ServerName [www.greateropportunities.org]("mhtml:{E0FB9D54-8691-455A-8144-CE97AC34CBF5}mid://00001064/!x-usc:http://www.greateropportunities.org/")
ErrorLog /var/www//logs/error_log
TransferLog /var/www/logs/access_log
</VirtualHost>
 
The question is do I add the information outside the current info? Like the following example?
 
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
<VirtualHost [www.1purposebethel.com]("http://www.1purposebethel.com")>
    ServerAdmin [EMAIL="kraleigh@sbcglobal.net"]kraleigh@sbcglobal.net[/EMAIL]
    DocumentRoot /var/www/1purposebethel
    ServerName [www.1purposebethel.com]("http://www.1purposebethel.com")
    ErrorLog /var/www/logs/error_log
    TransferLog /var/www/logs/access_log
</VirtualHost>
<VirtualHost [www.greateropportunities.com]("http://www.greateropportunities.com")>
    ServerAdmin [EMAIL="kraleigh@sbcglobal.net"]kraleigh@sbcglobal.net[/EMAIL]
    DocumentRoot /var/www/greateropportunities
    ServerName [www.greateropportunities.org]("http://www.greateropportunities.org")
    ErrorLog /var/www//logs/error_log
    TransferLog /var/www/logs/access_log
</VirtualHost>

```
 
thanx kevin

---

