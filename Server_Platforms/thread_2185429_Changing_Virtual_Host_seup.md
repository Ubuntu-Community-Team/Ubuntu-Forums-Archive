---
title: "Changing Virtual Host seup"
date: 2013-11-02
forum: Server Platforms
---

### Post by giles1000 on 2013-11-02
Hi all, pleasure to meet you all.

I have a machine running Ubuntu 12.04 x32 with LAMP stack. I set up a virtual Host along the lines of

```

DocumentRoot /var/www/directory1

<Directory />
    Options FollowSymLinks
    AllowOverride All
</Directory>
<Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Order allow,deny
    allow from all
</Directory>
```

... which works fine. I then realised I need to make a change. For the sake of argument, lets say I needed to change the document root to /var/www/directory2. I changed files in both sites-available and sites-enabled, restarted apache with no difference. My domain was still pointing to  /var/www/directory1. Cut a long story short, I ended up deleting both files in sites-available and sites-enabled, but Apache is still forwarding to www/directory1. I guess there must be another config somewhere that Apache is looking at? Can I get your help on what might be happening?

many thanks

---

### Post by SeijiSensei on 2013-11-03
The default site is in /etc/apache2/sites-available/default.  It points all traffic to /var/www. 

Ubuntu activates sites by creating a symbolic link from the corresponding file in /sites-available/ to /sites-enabled/. (The a2ensite command creates these links.)  The order of files in /sites-available/ determines how requests are processed.  By default the link to the default site is 000-default.conf in /sites-available/ to ensure it runs first.

So to replicate this behavior, remove any symlinks in /sites-enabled/, then create a symlink to your file in /sites-available/ and call it 000-something.conf.  Restart Apache.

---

### Post by yowchuan on 2013-11-12
Just a question on the DocumentRoot.

When I check my /etc/apache2/sites-available/default, this is what I get:

```
        <VirtualHost *:80>
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

I am not sure what the DocumentRoot in this config file meant, but I am 100% sure my websites are not stored in that path- /var/www

The path to my websites is as follow:

```
/home/user_name/public/example.com/public

```

In the next few hours, I am about to point 2 domains to my linode hosting. I have done all the Virtual Host setup, but I still feel something is not quite right because when I type in the IP of my server, the IP points to the first domain's folder correctly. Correct me if I am wrong, but I thought since I now have 2 domains setup (the virtual host way) on the same IP, it shouldn't show anything. This is my first time setting up a virtual host on a VPS.

And I am not about to risk pointing the DNS to the new IP yet, because it's going to take time to propagate. If it doesn't go well, I am going to receive a lot of phone calls from the customers... :(

Please point me the light...

And I am now having my 3rd cup of black coffee... ](*,)

---

### Post by Alphonse_Cabaro on 2013-11-13
Create and edit file /etc/apache2/sites-available/site1

```
[COLOR=#000000][FONT=Ubuntu Mono]<VirtualHost *:80>[/FONT][/COLOR]        ServerAdmin webmaster@localhost
        ServerName site1.example.com

        DocumentRoot /var/www/site1
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/site1/>
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


        ErrorLog ${APACHE_LOG_DIR}/site1_error.log


        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn


        CustomLog ${APACHE_LOG_DIR}/site1_access.log combined

</VirtualHost>[COLOR=#222222][FONT=Verdana]
```
[/FONT][/COLOR]
Enable the newly created site with command:
```
a2ensite site1
```

Copy the contents of site1 to folder /var/www/site1
give apache the rights to this folder
```
chown -R www-data.www-data /var/www/site1
```

Do the same for site2, site3 etc. (change the address and sitename and folder names to your liking)

You can then test the site by adding the servers ip into your /etc/hosts file in the computer you are browsing from.

for example:
192.168.0.10 site1.example.com

You can then test the site without changes to nameservers.

ServerName is the key telling which virtualhost is used when browser comes to your server.

I have not tested the above right now, but the idea is basically as described above.

/cab

---

