---
title: "How to create a virtual host??"
date: 2011-07-04
forum: Server Platforms
---

### Post by mvivekc on 2011-07-04
**Ubuntu 11.04** installed with **apache2** and all the relevant packages installed
 
**[SIZE=4]Tried most of the blogs[/SIZE]** and made google and other forums my best friends,yet unable to solve this issue.

Need to setup a named virtual host on my local system for development.

Created the directory "vivek" in /var/www and copied the default index.html and edited some elements.

added the file "vivek.com" in /etc/apache2/sites-available
 
The contents of the file "vivek.com" are as follows 
[SIZE=3][COLOR=Red]----------------------------->>[/COLOR][/SIZE]

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek.com](www.vivek.com)
DocumentRoot /var/www/vivek

# Other directives here
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
     <Directory /var/www/vivek/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>



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


[SIZE=3][COLOR=Red]--------------------------------------------->>>>>>>>>>
[/COLOR][/SIZE]

I.e i've added these following lines ---->>

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek.com](www.vivek.com)
DocumentRoot /var/www/vivek

# Other directives here
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
     <Directory /var/www/vivek/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>


  ---------------->>
to the default file which was already present in "**sites-available**" folder(took the back up of default file before editing it)

added this in the hosts file present in /etc/hosts

127.0.0.1       localhost
127.0.1.1       vivek-PC
127.0.0.1       [www.vivek.com](www.vivek.com)

Performed the following operations with no errors:

root@vivek-PC:~# a2ensite vivek.com 
Enabling site vivek.com.
Run '/etc/init.d/apache2 reload' to activate new configuration!
root@vivek-PC:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2 

When i entered [www.vivek.com,it](www.vivek.com,it) gave me the default index.html in /var/www but not one present in the folder /var/www/vivek which is edited.

Later,i edited the index.html from /var/www but still i was getting the same index.html(default-before editing). all the index.html's've been edited but apache seems to have some hidden one which keeps coming up when i request for [www.vivek.com](www.vivek.com)

and the ironic thing is,once after restart -- Apache came up fine but my site -- [www.vivek.com](www.vivek.com) failed to show up (even with the index.html which's hidden god knows where!!).. now,my browser is showing "Unable to connect " .. :( 


Please help.I've been trying to set this up since a week with no successful result.

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> **Ubuntu 11.04** installed with **apache2** and all the relevant packages installed
 
**[SIZE=4]Tried most of the blogs[/SIZE]** and made google and other forums my best friends,yet unable to solve this issue.

Need to setup a named virtual host on my local system for development.

Created the directory "vivek" in /var/www and copied the default index.html and edited some elements.

added the file "vivek.com" in /etc/apache2/sites-available
 
The contents of the file "vivek.com" are as follows 
[SIZE=3][COLOR=Red]----------------------------->>[/COLOR][/SIZE]

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek.com]("http://www.vivek.com")
DocumentRoot /var/www/vivek

# Other directives here
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
     <Directory /var/www/vivek/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>



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


[SIZE=3][COLOR=Red]--------------------------------------------->>>>>>>>>>
[/COLOR][/SIZE]

I.e i've added these following lines ---->>

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek.com]("http://www.vivek.com")
DocumentRoot /var/www/vivek

# Other directives here
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
     <Directory /var/www/vivek/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>


  ---------------->>
to the default file which was already present in "**sites-available**" folder(took the back up of default file before editing it)

added this in the hosts file present in /etc/hosts

127.0.0.1       localhost
127.0.1.1       vivek-PC
127.0.0.1       [www.vivek.com]("http://www.vivek.com")

Performed the following operations with no errors:

root@vivek-PC:~# a2ensite vivek.com 
Enabling site vivek.com.
Run '/etc/init.d/apache2 reload' to activate new configuration!
root@vivek-PC:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2 

When i entered [www.vivek.com,it]("http://www.vivek.com,it") gave me the default index.html in /var/www but not one present in the folder /var/www/vivek which is edited.

Later,i edited the index.html from /var/www but still i was getting the same index.html(default-before editing). all the index.html's've been edited but apache seems to have some hidden one which keeps coming up when i request for [www.vivek.com]("http://www.vivek.com")

and the ironic thing is,once after restart -- Apache came up fine but my site -- [www.vivek.com]("http://www.vivek.com") failed to show up (even with the index.html which's hidden god knows where!!).. now,my browser is showing "Unable to connect " .. :( 


Please help.I've been trying to set this up since a week with no successful result.

I'm not sure if the name makes a difference but try renaming your vivek.com file to vivek-com.conf.  Then run:

```
sudo a2ensite vivek-com
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by mvivekc on 2011-07-04
Changed it.
But could not execute "a2ensite vivek-com" as it gave me an error ---->>
root@vivek-PC:~# a2ensite vivek-com
ERROR: Site vivek-com does not exist!

------->>

But,changed the parameter and  --->>

root@vivek-PC:~# a2ensite vivek-com.conf
Enabling site vivek-com.conf.
Run '/etc/init.d/apache2 reload' to activate new configuration!
root@vivek-PC:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2  

---------------->>

No result !!.. neither does vivek.com not vivek-com.conf is giving any proper output..!!

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> Changed it.
But could not execute "a2ensite vivek-com" as it gave me an error ---->>
root@vivek-PC:~# a2ensite vivek-com
ERROR: Site vivek-com does not exist!

------->>

But,changed the parameter and  --->>

root@vivek-PC:~# a2ensite vivek-com.conf
Enabling site vivek-com.conf.
Run '/etc/init.d/apache2 reload' to activate new configuration!
root@vivek-PC:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2  

---------------->>

No result !!.. neither does vivek.com not vivek-com.conf is giving any proper output..!!

Can you tell us what you mean by No results!!?

I just clicked on [www.vivek.com](www.vivek.com) and it appears to bring up your page.  I can't say I understand what's not working.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by mvivekc on 2011-07-04
Lol.. :P .. that's not my site.I'm trying to build a local virtual host,i.e on giving vivek.com which is an alias to 127.0.0.1  -- i'm trying to bring up a local index.html page which is located in /var/www/vivek folder.

That folder should have index.html 

and the contents of the "vivek.com" file present within sites-available is given above.

That about site is not mine.just replace "vivek" with "example".so,on typing of [www.example.com](www.example.com) --- my browser was showing me the result of the default "index.html" which comes with apache2 instead of the index.html present in the vivek(example) folder..!!

now,as i said earlier -- its not even showing me the default index page,instead the browser says -- unable to connect!! :(

---

### Post by mvivekc on 2011-07-04
okay,let me change some parameters to avoid confusion !!..

the contents of the file --  "/etc/apache2/sites-available/vivek123.com"  is as follows

________________________________________________________________________________

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek123.com](www.vivek123.com)
DocumentRoot /var/www/vivek

# Other directives here
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/vivek/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

</VirtualHost>



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


________________________________________________________________________________

Contents of the file /ets/hosts is as follows
________________________________________________________________________________

127.0.0.1       localhost
127.0.1.1       vivek-PC
127.0.0.1       vivek123.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


________________________________________________________________________________


The local file structure is as given below !!

root@vivek-PC:/var/www/vivek# pwd
/var/www/vivek
root@vivek-PC:/var/www/vivek# ls
index.html

________________________________________________________________________________

I'm enabling the site as follows !!

root@vivek-PC:~# a2ensite vivek123.com
Enabling site vivek123.com.
Run '/etc/init.d/apache2 reload' to activate new configuration!
root@vivek-PC:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2  

________________________________________________________________________________


on giving the URL vivek123.com
i get this from the browser :(
________________________________________________________________________________


Unable to connect
      
      
      
      
      
        
        
          Firefox can't establish a connection to the server at vivek123.com.
        

        
        

  The site could be temporarily unavailable or too busy. Try again in a few
    moments.
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> Lol.. :P .. that's not my site.I'm trying to build a local virtual host,i.e on giving vivek.com which is an alias to 127.0.0.1  -- i'm trying to bring up a local index.html page which is located in /var/www/vivek folder.

That folder should have index.html 

and the contents of the "vivek.com" file present within sites-available is given above.

That about site is not mine.just replace "vivek" with "example".so,on typing of [www.example.com]("http://www.example.com") --- my browser was showing me the result of the default "index.html" which comes with apache2 instead of the index.html present in the vivek(example) folder..!!

now,as i said earlier -- its not even showing me the default index page,instead the browser says -- unable to connect!! :(

Looking back at your original message, it's kind of confusing what you have in the vivek-com.conf file.  Can you show us again exactly what is in your vivek-com.conf file putting the content between [ code ] tags?

The configuration is very simple.  But from what you posted before, I can't tell where your vivek-com.conf text start and where it ends.  Using the 

[ code ] 
code here 
[ /code ] 

tags (without the spaces will make it easier to decipher.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by mvivekc on 2011-07-04
since that solution didnt work,i restored it to my original configuration,i.e the vivek123.com 

who's contents are as follows
```

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek123.com]("http://www.vivek123.com")
DocumentRoot /var/www/vivek

# Other directives here
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/vivek/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

</VirtualHost>



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

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> okay,let me change some parameters to avoid confusion !!..

the contents of the file --  "/etc/apache2/sites-available/vivek123.com"  is as follows

________________________________________________________________________________

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek123.com]("http://www.vivek123.com")
DocumentRoot /var/www/vivek

# Other directives here
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/vivek/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

</VirtualHost>



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


________________________________________________________________________________

Contents of the file /ets/hosts is as follows
________________________________________________________________________________

127.0.0.1       localhost
127.0.1.1       vivek-PC
127.0.0.1       vivek123.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


________________________________________________________________________________


The local file structure is as given below !!

root@vivek-PC:/var/www/vivek# pwd
/var/www/vivek
root@vivek-PC:/var/www/vivek# ls
index.html

________________________________________________________________________________

I'm enabling the site as follows !!

root@vivek-PC:~# a2ensite vivek123.com
Enabling site vivek123.com.
Run '/etc/init.d/apache2 reload' to activate new configuration!
root@vivek-PC:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2  

________________________________________________________________________________


on giving the URL vivek123.com
i get this from the browser :(
________________________________________________________________________________


Unable to connect
      
      
      
      
      
        
        
          Firefox can't establish a connection to the server at vivek123.com.
        

        
        

  The site could be temporarily unavailable or too busy. Try again in a few
    moments.
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.

I see you were typing while I was typing.  Please look at my previous message along with this one.  Your message above is appearing to show too many <VirtualHost> blocks in your conf file.  Look at the default file and use it as an example.  You basically have to just copy that default file to a new file and specify the root directory and the name directive and you should be virtually set.

Again, please, if you're going to show us text examples please use the [ code ] tags.  It'll make your messages much easier to read and in turn make it easier for us to pick out the problem areas and give support.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> since that solution didnt work,i restored it to my original configuration,i.e the vivek123.com 

who's contents are as follows
<code>
# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.vivek123.com]("http://www.vivek123.com")
DocumentRoot /var/www/vivek

# Other directives here
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/vivek/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

</VirtualHost>



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

</code>

I see you attempted to use [ code ] tags.  However, you used greater than signs rather than brackets.  The tags are made with brackets "[" not greater than or less than signs.

If you follow the steps I provided you in my previous message I'm sure you won't have any problems.  If you do have problems, at least it'd be very easy to identify what you're doing wrong.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by mvivekc on 2011-07-04
I've used code tag on your request(did not know how to use it untill now -- my 1st request thread)

and will try changing the default file itself and get back to u right away.

---

### Post by mvivekc on 2011-07-04
here is my new code (edited the default file)
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName vivek123.com
    DocumentRoot /var/www/vivek
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/vivek/>
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

Contents of 

/etc/hosts

```

127.0.0.1    localhost
127.0.1.1    vivek-PC
127.0.0.1       vivek123.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```

Still the same problem,browsers throwing unable to connect :(

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> here is my new code (edited the default file)
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName vivek123.com
    DocumentRoot /var/www/vivek
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/vivek/>
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


```Contents of 

/etc/hosts

```

127.0.0.1    localhost
127.0.1.1    vivek-PC
127.0.0.1       vivek123.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```Still the same problem,browsers throwing unable to connect :(

Did you restart the server after editing your new code?

```
sudo service apache2 restart
```


Also, what did you type into your browser?  Was it, "vivek123.com", the way you have it in the conf file?


-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by mvivekc on 2011-07-04
Yup,i restarted apache2 and the url i typed is "vivek123.com" as specified in the /etc/hosts file.Browser says "unable to connect"

---

### Post by apollothethird on 2011-07-04
> **mvivekc said:**
> Yup,i restarted apache2 and the url i typed is "vivek123.com" as specified in the /etc/hosts file.Browser says "unable to connect"

Let's look at some test.

What do you get when you open [http://localhost](http://localhost) from the browser?

What do you get when you type these lines from a terminal window:

```
ls /var/www/vivek/*.htm*
ping -c1 vivek123.com
apache2 -D DUMP_VHOSTS
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by sparklypenguin on 2011-07-30
Did you ever get this sorted on you installation?

I have the same issues with my ubuntu 11.04 apache2 installation

I'm trying to run two sites from the same IP with dyndns redirecting two domains successfully pointing at my server. 
entering (eg) site1.com or site2.com in my browser within local network works fine but when i go outside and try it on the INTERNET i am redirected to the default page for apache2 - or i was until i disabled the VirtualHost file - then i am directed to site1.com .... but from both site1 and site2's URL.

truly frustrating 
I've been through many tutorials and although most are vary similar i have tried all the subtle differences but to no avail. 

heres my setup

ports.conf
```

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>


```within the sites-available folder
```

<VirtualHost *>
        ServerAdmin webmaster@site1.com
        ServerName  www.site1.com
        ServerAlias site1.com

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/site1.com/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/site1.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/site1.com/logs/error.log
        CustomLog /var/www/site1.com/logs/access.log combined
</VirtualHost>

```site2.com is exactly the same but with the expected changes
both sites are enabled

hosts.conf
```

127.0.0.1    localhost  site1.com site2.com
# 127.0.0.1    frank
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```this is the set up described in most of the tutorials and forum i've read but although it seems to work for others...it just wont work for me....?

I'm new to ubuntu and Linux and this is almost driving me back to XP...and i really dont want to go so any help would be greatly appreciated

---

### Post by apollothethird on 2011-07-31
> **sparklypenguin said:**
> Did you ever get this sorted on you installation? 
 
I have the same issues with my ubuntu 11.04 apache2 installation 
 
I'm trying to run two sites from the same IP with dyndns redirecting two domains successfully pointing at my server. 
entering (eg) site1.com or site2.com in my browser within local network works fine but when i go outside and try it on the INTERNET i am redirected to the default page for apache2 - or i was until i disabled the VirtualHost file - then i am directed to site1.com .... but from both site1 and site2's URL. 
 
truly frustrating 
I've been through many tutorials and although most are vary similar i have tried all the subtle differences but to no avail. 
 
heres my setup 
 
ports.conf 
```
 
NameVirtualHost *:80 
Listen 80 
 
<IfModule mod_ssl.c> 
    # If you add NameVirtualHost *:443 here, you will also have to change 
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl 
    # to <VirtualHost *:443> 
    # Server Name Indication for SSL named virtual hosts is currently not 
    # supported by MSIE on Windows XP. 
    Listen 443 
</IfModule> 
 
<IfModule mod_gnutls.c> 
    Listen 443 
</IfModule> 
 

```within the sites-available folder 
```
 
<VirtualHost *> 
        ServerAdmin webmaster@site1.com 
        ServerName  www.site1.com 
        ServerAlias site1.com 
 
        # Indexes + Directory Root. 
        DirectoryIndex index.html 
        DocumentRoot /var/www/site1.com/htdocs/ 
 
        # CGI Directory 
        ScriptAlias /cgi-bin/ /var/www/site1.com/cgi-bin/ 
        <Location /cgi-bin> 
                Options +ExecCGI 
        </Location> 
 
 
        # Logfiles 
        ErrorLog  /var/www/site1.com/logs/error.log 
        CustomLog /var/www/site1.com/logs/access.log combined 
</VirtualHost> 

```site2.com is exactly the same but with the expected changes 
both sites are enabled 
 
hosts.conf 
```
 
127.0.0.1    localhost  site1.com site2.com 
# 127.0.0.1    frank 
# The following lines are desirable for IPv6 capable hosts 
::1     ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 

```this is the set up described in most of the tutorials and forum i've read but although it seems to work for others...it just wont work for me....? 
 
I'm new to ubuntu and Linux and this is almost driving me back to XP...and i really dont want to go so any help would be greatly appreciated 
 
Hi, Sparklypenguin.  I find it very hard to phantom how moving to Windows, especially to Windows XP could be a resolution for running a serious web server.  I have never heard of anyone running a serious web server of any kind on XP.  I believe any attempt to run a web server on XP would present more problems that you can imagine.  I hardly think you'd get a lot of support.  I'm almost certain anywhere you posted a message about an X, you'd receiving a bombard of responses suggesting that you move to a platform that made more sense.  They'd probably suggest that you invest thousands of dollars and run Windows Server, or run do what more common, easier and economical (free), and run your server on the Linux platform. 
 
I see your message has gone a long time without a response.  A lot of the users are probably giving you an opportunity to test trying XP and come back to a better support platform. 
 
What is the name of your sites available files?  You gave the name of all the other files that you showed in your post, but you didn't give a name of the file of either of the two you said you created. 
 
Did you enable those sites by their names? 
 
You'll find running a web server is very easy on Linux, especially Ubuntu.  There many on the developer's team that has already run the server and make configuration a breeze.  There are also many thousands who has tested the configuration and reported on the ease or other ways to make it easier. 
 
You'll find that you have made a very simple oversight and your post to the forums will bring about a quick resolution. 
 
I don't know which tutorials you've been reading.  Reading information presented by users of the distro version is a good start.   
 
-- L. James 
 
--  
L. D. James 
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL] 
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by sparklypenguin on 2011-08-06
thanks for taking the time the reply.

I was only planning on going back to my XP Xampp server because i had i working fine but i really didn't want to 
Ubuntu is a new thing for me  and i was/am really enjoying it.

happy to say all is working fine now :D
and the only reason it wasn't was because I'm a bit of a twit

i was using my actual domain names as the ServerName  and ServerAlias entries
these domains have a framed redirect to two DynDns accounts both pointing at my server...
can you see the mistake..... well i couldn't and now it seem so obvious i'm ashamed to point it out
but i will for the benefit of other readers incase they are making the same mistake.

the ServerName and ServerAlias in the <VirtualHost> needed to be the DynDns addresses not my actual domain addresses

i was looking at the config files my previous installation on the XP machine (on another HD) when i noticed that on them i'd used the dyndns addresses 
gave it a go and happy camper

---

