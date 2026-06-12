---
title: "Webmin Apache Default server problems"
date: 2012-02-06
forum: Server Platforms
---

### Post by Yourname on 2012-02-06
Hello,

I recently got a2billing (a VoIP billing software) installed by a consultant on my server. He installed it so a2billing runs as the "Default Server" of apache. 

I don't want it to be like that because not only does it feel naked, but also anyone from anywhere can access the server via http and boom, there's the login screen.

Long story short, I want to move it to it's own virtual host on apache (billing.domain.com). That way I can point all new domains I purchase and have them go to /var/www/index.html as a placeholder without needing to create a new virtual host each time I buy a domain. I'd rather have THAT as my default server and not a2billing.

I know how virtual hosts work but this "Default Server" is a little too complicated once you click on it.

This is the [first screen]("http://screencast.com/t/s0guY0fuBiYq") on Apache server on Webmin. When you click through into "Default Server", you see all of these [new things]("http://screencast.com/t/Ep695iXd") whereas I was hoping to see something [like this]("http://screencast.com/t/LEEormcR2Rf") which you see when you click into the "Virtual Server".

Either way, you get the drift. I want this to be a virtual host. I can't simply create a new virtual host with Server Name = billing.domain.com and Document Root = /usr/share/a2billing/1-current/stable/admin/ which seems to be very easy and should get the job done. 

Basically, I want that ^^ to be the virtual host and I want default server to be "Any" server name and "/var/www" as Document Root. 

Any help would be great. Thanks!!

---

### Post by volkswagner on 2012-02-06
I have not used webmin in years.  From my limited experience, I recall the process of creating vhost not overly intuitive.  I also remember having unexpected results at times, especially if  I created vhosts by hand vs. via webmin.

I recommend following the steps in the [Sticky]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") at the top of this forum.

The key to making a "default" vhost is not calling it default.  The way Apache2 works, is by reading the vhost files in alpha/numeric order.  The first file that has a match to the request is served.  If there are not matches to the request, the first vhost file is served.

Therefore to have a default site just make sure it comes first alpha/numerically.  This is why a clean install has the default named 000-default.  The leading zero's get in in the top of the list.

---

### Post by Yourname on 2012-02-06
My apologies. I forgot to attach the screenshots along with the post and that's why it was hard for you to understand where I'm coming from. Please take a look at it and you'll see why I find it difficult.

---

### Post by Yourname on 2012-02-07
lol
Now that the screenshots are in, everybody's stumped?

---

### Post by volkswagner on 2012-02-07
You may get some insight by examining the actual vhost files.

```
ls /etc/apache2/sites-available
```

```
cat /etc/apache2/sites-available/default
```

```
cat /etc/apache2/sites-available/site2
```

Obviously you will need to change the file names.  I think webmin also has a file viewer built in if you don't want to use the command line.

Again, I highly  recommend staying away from Webmin for Apache2 administration.  I really don't like the way it handles some of the config options.

I have very limited experience with Webmin.  If you don't get more solid advice you can try copying the default config file to a diff file name, change the directive for both vhost files, and make sure your viopsite file name comes alpha numerically after the site you want to make default. 

Make backups of everything so you can revert if it goes sour. 

Would go something like this.

```
cd /etc/apache2/sites-available
```

```
sudo cp default default.bak
```
```
sudo cp site2 site2.bak
```
```
sudo cp default viopSite
```
```
sudo nano viopSite
```
Change the virtual host directive so it is like:
```
<VirtualHost *>
```

```
sudo nano site2
```
Change the virtual host directive so it is like:
```
<VirtualHost *>
```

disable the default site and enable it's replacement

```
sudo a2dissite default
```
```
sudo a2ensite voipSite
```

Cross your fingers and reload apache2

```
sudo service apache2 reload
```

---

### Post by Yourname on 2012-02-07
> **volkswagner said:**
> You may get some insight by examining the actual vhost files.

```
ls /etc/apache2/sites-available
```

```
cat /etc/apache2/sites-available/default
```

```
cat /etc/apache2/sites-available/site2
```

Obviously you will need to change the file names.  I think webmin also has a file viewer built in if you don't want to use the command line.

Again, I highly  recommend staying away from Webmin for Apache2 administration.  I really don't like the way it handles some of the config options.

I have very limited experience with Webmin.  If you don't get more solid advice you can try copying the default config file to a diff file name, change the directive for both vhost files, and make sure your viopsite file name comes alpha numerically after the site you want to make default. 

Make backups of everything so you can revert if it goes sour. 

Would go something like this.

```
cd /etc/apache2/sites-available
```

```
sudo cp default default.bak
```
```
sudo cp site2 site2.bak
```
```
sudo cp default viopSite
```
```
sudo nano viopSite
```
Change the virtual host directive so it is like:
```
<VirtualHost *>
```

```
sudo nano site2
```
Change the virtual host directive so it is like:
```
<VirtualHost *>
```

disable the default site and enable it's replacement

```
sudo a2dissite default
```
```
sudo a2ensite voipSite
```

Cross your fingers and reload apache2

```
sudo service apache2 reload
```

Hey,

Thanks. Going to try this now.

---

### Post by Yourname on 2012-02-08
Webmin said "File or directory to add virtual servers to" -> /etc/apache2/sites-available

So, obviously, /etc/apache2/httpd.conf is unavailable for comment.

```

root@phantom:~# cd /etc/apache2/sites-
sites-available/ sites-enabled/
root@phantom:~# cd /etc/apache2/sites-available/
root@phantom:/etc/apache2/sites-available# ls
a2billing_admin.conf  a2billing_customer.conf  default      freepbx.conf              a2billing_agent.conf  a2billing_index.conf     default-ssl  
root@phantom:/etc/apache2/sites-available# less default
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

Then there's...

```
root@phantom:/etc/apache2# cd sites-enabled/
root@phantom:/etc/apache2/sites-enabled# ls
000-default  a2billing_admin.conf  a2billing_agent.conf  a2billing_customer.conf  a2billing_index.conf  freepbx.conf  kasbahmanila.com.ph.conf  kasbahmanila.ph.conf  utang.ph.conf
root@phantom:/etc/apache2/sites-enabled# less 000-default
root@phantom:/etc/apache2/sites-enabled#


```

So, naturally, I went into 000-default...

```
root@phantom:/etc/apache2/sites-enabled# cat 000-default
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
root@phantom:/etc/apache2/sites-enabled#



```

So, now I don't understand how Webmin shows [SO MANY]("http://screencast.com/t/Ep695iXd") symlinks :S

---

### Post by volkswagner on 2012-02-08
Too many symbolic links....
The way Virtual hosts works is when you enable it, a link gets created in sites-enabled from sites-available.  You can enable it using 'a2ensite' or create the link by hand.  This makes it easy to enable/disable sites without actually touching config files.

The reason default has a link like 000-default is to make sure requests for domains not listed in other vhost files will be served by 000-default because the file comes early alphanumerically.  I believe this is the way apache is installed in Ubuntu/debian.

I did not realize you had so many vhost files.  Are all this vhosts working as expected?

Please locate the vhost file that has /usr/share/a2billing/1-current/stable/admin as the document root.  Please post the config of this vhost.

Your goal is to have all new sites inside /var/www.  Are you going to have an index page in /var/www with links to all new sites?  This will work well if you new sites all have the same domain name and you use a folder structure like... mydomain.com, mydomain.com/site2, mydomain.com/site2.

If you want to use subdomains, you will still want to create vhost files so the subdomain is found by apache2.  One way around this is if your default vhost file lists all your new subdomains as aliases.  Then you can use the sub folder structure within /var/www.  So you would still need to edit a vhost file each time you add a subdomain.  Otherwise you will be relying on the fact that apache2 will serve the subdomain based on not being found and expecting the vhost file with the highest priority (earliest alphaNumerically).  This will work, but may not be a good practice.

---

### Post by Yourname on 2012-02-09
> **volkswagner said:**
> Too many symbolic links....
The way Virtual hosts works is when you enable it, a link gets created in sites-enabled from sites-available.  You can enable it using 'a2ensite' or create the link by hand.  This makes it easy to enable/disable sites without actually touching config files.

The reason default has a link like 000-default is to make sure requests for domains not listed in other vhost files will be served by 000-default because the file comes early alphanumerically.  I believe this is the way apache is installed in Ubuntu/debian.

I did not realize you had so many vhost files.  Are all this vhosts working as expected?

Please locate the vhost file that has /usr/share/a2billing/1-current/stable/admin as the document root.  Please post the config of this vhost.

Your goal is to have all new sites inside /var/www.  Are you going to have an index page in /var/www with links to all new sites?  This will work well if you new sites all have the same domain name and you use a folder structure like... mydomain.com, mydomain.com/site2, mydomain.com/site2.

If you want to use subdomains, you will still want to create vhost files so the subdomain is found by apache2.  One way around this is if your default vhost file lists all your new subdomains as aliases.  Then you can use the sub folder structure within /var/www.  So you would still need to edit a vhost file each time you add a subdomain.  Otherwise you will be relying on the fact that apache2 will serve the subdomain based on not being found and expecting the vhost file with the highest priority (earliest alphaNumerically).  This will work, but may not be a good practice.

For clarity: 
Thing is I buy lots of domains every now and then. But host only a handful with more than one page. 
So, my mindset was when I buy a domain I don't want to have to always set up a virtual host for them as most of them will go to /var/www/index.html which is the placeholder. 

Every now and then I'd get a domain that I want to have a couple more pages, and for that a virtual host is fine. This whole dynamic got messed up when a2billing came into /var/www/. 

And yes, those symlinks are what I'm afraid of. Don't wanna screw something up.

---

### Post by volkswagner on 2012-02-09
I understand.

If you want to get to the bottom of the issue, it would be very helpful if you could post the config file of the site webmin is calling default.

Please locate the vhost file that has /usr/share/a2billing/1-current/stable/admin as the document root. Please post the config of this vhost.

---

### Post by Yourname on 2012-02-10
> **volkswagner said:**
> I understand.

If you want to get to the bottom of the issue, it would be very helpful if you could post the config file of the site webmin is calling default.

Please locate the vhost file that has /usr/share/a2billing/1-current/stable/admin as the document root. Please post the config of this vhost.

Here you go:```


root@phantom:/etc/apache2/sites-available# cat a2billing_admin.conf

                        Alias /a2b_admin /usr/share/a2billing/1-current/stable/admin/

                        DocumentRoot /usr/share/a2billing/1-current/stable/admin/

                        <directory /usr/share/a2billing/1-current/stable/admin>
                        AllowOverride all
                        Options Indexes FollowSymLinks
                        order allow,deny
                        allow from all
                        AuthName "A2Billing Admin"
                        AuthType Basic
                        AuthUserFile /dev/null
                        AuthBasicAuthoritative off
                        Auth_MySQL on
                        Auth_MySQL_Authoritative on
                        Auth_MySQL_Username asteriskuser
                        Auth_MySQL_Password amp109
                        Auth_MySQL_DB asterisk
                        Auth_MySQL_Password_Table ampusers
                        Auth_MySQL_Username_Field username
                        Auth_MySQL_Password_Field password_sha1
                        Auth_MySQL_Empty_Passwords off
                        Auth_MySQL_Encryption_Types SHA1Sum
                        Require valid-user
                        </directory>

                        <IfModule mod_php5.c>
                        php_flag magic_quotes_gpc Off
                        php_flag track_vars On
                        php_flag register_globals Off
                        </IfModule>

                <IfModule mod_auth_mysql.c>


root@phantom:/etc/apache2/sites-available#

```

---

### Post by volkswagner on 2012-02-10
As you see there are no VirtualHost directive and no servername.  The lack of <VirtualHost> tags is what I believe causes this file to act as "default".

If you have the inclination you can copy the contents of a2billing_admin.conf to the clipboard.  Then by your choice use webmin or manually create a new virtual host file with a different file name.  If you create the file by hand you will want to wrap the contents in <Virtualhost *:80> </VirtualHost> tags.
 
This will allow you to either delete the original or copy the contents of 000-default and replace the contents of webmin's default.

Always create backups for the files before editing.    ;)

---

