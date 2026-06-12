---
title: "Subdomain on LAN"
date: 2008-04-24
forum: Server Platforms
---

### Post by dmhtong on 2008-04-24
Hi all,

I am new to this and have installed Ubuntu Server 7.10 i386 edition. I am trying to create subdomains to be accessible by other computers on the network.

I have the following setup:
- PC with Ubuntu Server 7.10 i386 installed
- Laptops, both Windows and Mac's

I can:
- From the laptops access the server through [http://192.168.2.200](http://192.168.2.200) and it directs me to my index.htm that i setup.

I want to:
- From the laptops access subdomains on the server, [http://diamonds.192.168.2.200](http://diamonds.192.168.2.200) ??? If this is fundamentally wrong, what alternative do I have to produce something of similar results? When i attempt to access [http://diamonds.192.168.2.200](http://diamonds.192.168.2.200) I get "Server not found" message

I don't want to:
- Have subfolders, EG. [http://192.168.2.200/diamonds](http://192.168.2.200/diamonds), [http://192.168.200/pearls](http://192.168.200/pearls) etc

What I have tried:
- [http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/")
- [http://ubuntuforums.org/showthread.php?t=592456&highlight=%2Fetc%2Fapache2%2Fsites-available+subdomain]("http://ubuntuforums.org/showthread.php?t=592456&highlight=%2Fetc%2Fapache2%2Fsites-available+subdomain")

What is all this for?
- I am trying to make a few websites that will be accessed through subdomains, eg [http://diamonds.domainname.com](http://diamonds.domainname.com) and [http://pearls.domainname.com](http://pearls.domainname.com), however, i don't yet have a domain name registered. I intend on purchasing this AFTER i get my websites up and running.

What am I doing wrong guys? A pointer in the right direction and any help will be greatly appreciated.

My current settings:
Directory: /etc/apache2/sites-available$
Files: default  websites
default
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webhost@gmail.com

        DocumentRoot /var/www/domain.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
       </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
                   "/usr/lib/cgi-bin">
        DocumentAllowOverride None
        <DirectoOptions +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        ErrorLog /var/log/apache2/error.lognks MultiViews
                AllowOverride None
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.rom all
        LogLevel warns directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
        CustomLog /var/log/apache2/access.log combined
        ServerSignature On
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        DenyOverride None
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>  AllowOverride None



                # in /apache2-default/, but still have / go to the right place

```

websites
```
# localhost
<VirtualHost 127.0.0.1>
        DocumentRoot /var/www/domain.com/
</VirtualHost>

# pearls
<VirtualHost 127.0.0.2>
        DocumentRoot /var/www/pearls/
</VirtualHost>

# diamonds
<VirtualHost 127.0.0.3>
        DocumentRoot /var/www/diamonds/
</VirtualHost>

```

directory: /etc/apache2/sites-enabled$
files: 000-default  domain.com  pearls  diamonds

domain.com
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webhost@gmail.com
        ServerName domain.com
        ServerAlias www.domain.com

        DocumentRoot /var/www/domain.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
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
        ServerSignature On

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

pearls
```
<VirtualHost *> 
        DocumentRoot /var/www/pearls/
        ServerName pearls.localhost

        <Directory /var/www/pearls/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

diamonds
```
<VirtualHost *>
        DocumentRoot /var/www/diamonds/
        ServerName diamonds.localhost

        <Directory /var/www/diamonds/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

directory: /etc/apache2$

httpd.conf
```
<VirtualHost *>
ServerName localhost
DocumentRoot /var/www/domain.com
</VirtualHost>

<VirtualHost *>
ServerName pearls.localhost
DocumentRoot /var/www/pearls/
</VirtualHost>

<VirtualHost *>
ServerName diamonds.localhost
DocumentRoot /var/www/diamonds/
</VirtualHost>

```

Directory: /var/www$
Folders: apache2-default  diamonds  domain.com  pearls


Thanks in advance,

David

---

### Post by geertn on 2008-04-24
First of all, using subdomains depends on the request the browsers sends to the webserver. 

Try to setup a fictive domain name on your webserver and your clients.

Steps:
Edit your hosts file on the clients to trick them into thinking the domain and subdomains really exist and point to 192.168.2.200.

On Windows:

- find your hosts file: [http://lunarsoft.net/forum/index.php?showtopic=1153](http://lunarsoft.net/forum/index.php?showtopic=1153)
- Edit it and add entries for your subdomains, eg:

192.168.2.200 pearl.domain.com
192.168.2.200 subdomain2.domain.com

If you have this working you will be able to setup your subdomains in your apache config using the ServerName directive.


Example:
NameVirtualHost 192.168.2.200:80

<VirtualHost 192.168.2.200>
   ServerName pearls.domain.com
   DocumentRoot /var/www/pearls/
</VirtualHost>

---

### Post by dmhtong on 2008-04-24
geertn,

Thanks so much.

I added the following entries to my client host files:
```
192.168.2.200 domain.com
192.168.2.200 pearls.domain.com
192.168.2.200 diamonds.domain.com
```

I then changed my httpd.conf to look like:
```
<VirtualHost *>
ServerName ephalent.com.au
DocumentRoot /var/www/ephalent.com.au
</VirtualHost>

<VirtualHost *>
ServerName pearls.ephalent.com.au
DocumentRoot /var/www/pearls/
</VirtualHost>

<VirtualHost *>
ServerName diamonds.ephalent.com.au
DocumentRoot /var/www/diamonds/
</VirtualHost>

```

However, I didn't understand the reasons for the additional content you asked me to put in and removed them because I received the following errors:
Additional content
```
NameVirtualHost 192.168.2.200:80
<VirtualHost 192.168.2.200>
```
Errors
```
[Fri Apr 25 10:20:39 2008] [error] VirtualHost 192.168.2.200:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Apr 25 10:20:39 2008] [error] VirtualHost 192.168.2.200:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Apr 25 10:20:39 2008] [error] VirtualHost 192.168.2.200:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Apr 25 10:20:39 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Fri Apr 25 10:20:49 2008] [error] VirtualHost 192.168.2.200:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Apr 25 10:20:49 2008] [error] VirtualHost 192.168.2.200:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Apr 25 10:20:49 2008] [error] VirtualHost 192.168.2.200:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Apr 25 10:20:49 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
```

I will try and dig up what I can find about these before I lodge another post though. Might have to read up on the Apache2 manual ;)

Thanks for your help once again.

Kind regards,
David

---

### Post by Wim Sturkenboom on 2008-04-25
Below my vhosts config (from a Slackware 12 server)
```

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

# catch-all
<VirtualHost *:80>
    ServerAdmin admin@btd-techweb
    DocumentRoot /srv/httpd/htdocs
    ServerName btd-techweb02
</VirtualHost>

# site 1
<VirtualHost *:80>
    ServerAdmin admin@btd-techweb
    DocumentRoot /home/wim/www/site1/web
    ServerName site1.btd-techweb02
    ErrorLog /var/log/httpd/error_log
    CustomLog /var/log/httpd/access_log common

#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site1/web">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

# site2
<VirtualHost *:80>
    ServerAdmin admin@btd-techweb
    DocumentRoot /home/wim/www/site2/web
    ServerName site2.btd-techweb02
    ErrorLog /var/log/httpd/error_log
    CustomLog /var/log/httpd/access_log common

#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site2/web">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

```

Hope it helps

---

### Post by babajc on 2008-05-04
Did you solve your NameVirtualHost error message problem?  If not, see if this solution helps:
[http://apachehelp.blogspot.com/2008/05/named-virtual-hosts-in-apache2.html](http://apachehelp.blogspot.com/2008/05/named-virtual-hosts-in-apache2.html)

---

