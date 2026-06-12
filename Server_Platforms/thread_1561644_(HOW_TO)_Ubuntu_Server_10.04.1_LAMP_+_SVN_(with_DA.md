---
title: "(HOW TO) Ubuntu Server 10.04.1 LAMP + SVN (with DAV) + FTP Server"
date: 2010-08-26
forum: Server Platforms
---

### Post by max_power on 2010-08-26
[COLOR="Red"]**-Disclaimer:**[/COLOR] These are basic settings. Since its not using SSL don't trust it to be secure.


* This setup is for 2 or more users but could be easily adapted to 1 user *

* this assumes you already have apache2 installed. If you dont just do 'sudo apt-get install apache2' then begin.*

Here we go...

[SIZE="5"]1. users + groups[/SIZE]
```

# groupadd www-pub
# groupadd svn
# useradd userb --password 12345
# usermod -a -G www-pub usera
# usermod -a -G www-pub userb
# usermod -a -G svn usera
# usermod -a _G svn userb
# usermod -a -G svn www-data

```

Change the owner of /var/www to the www-pub group
```

# chown -R root:www-pub /var/www
# chmod 2775 /var/www

```

[SIZE="5"]2. Setting up proftpd[/SIZE]
```

# apt-get install proftpd
# nano /etc/proftpd/proftpd.conf

```

Make the following changes in proftpd.conf:
```

DefaultRoot        /var/www usera
DefaultRoot        /var/www userb

User               nobody
Group              nogroup

```

Allow your users to rwx via ftp
```
# chmod -R g+w /var/www
```

Restart proftpd
```
# /etc/init.d/proftpd restart
```

[SIZE="5"]3. Setting up SVN[/SIZE]

fist install subversion and libapache2-svn
```

# apt-get install subversion libapache2-svn
# svnadmin create /var/svn

```

Next, lets setup the DAV
```

# nano /etc/apache2/mods-enabled/dav_svn.conf

```

Make the following changes:
```

uncomment <location /svn>
uncomment DAV svn
change SNVpath          to SVNpath /var/svn 
uncomment AuthTypeBasic
uncomment AuthName "Subversion Repository"
uncomment AuthUserFile /etc/apache2/dav_svn.passwd
add       Require valid-user
uncomment </location>

```

After saving dav_svn.conf, a2enmod auth_basic and auth_file for good mesure
```

# a2enmod auth_basic
# a2enmod authn_file

```

Now we create our svn passwords for our users. *only user htpasswd -c once to create the pw file. *
```

# htpasswd -c /etc/apache2/dav_svn.passwd usera
# htpasswd /etc/apache2/dav_svn.passwd userb

```

restart apache and reload the settings
```

# /etc/init.d/apache2 restart
# /etc/init.d/apache2 force-reload

```

[SIZE="5"]4. Securing web space (optional)[/SIZE]
If you want to restrict the non users from viewing the files on your web server ([http://localhost/index.html](http://localhost/index.html) etc...) You have to configure .htaccess in Apache and create the .htaccess file.

* note that index.html will still render and be viewable but will not be accessible until the user logs in *

Fist edit /etc/apache2/sites-available/default to allow .htaccess over ride
```

# nano /etc/apache2/sites-available/default

```

Change AllowOverride None to All
```

AllowOverride All

```

Now create the .htaccess file
```

# nano /var/www/.htaccess

```

Put this in .htacess
```

AuthName "Section Name" # Change this to the name of the what you are protecting (ex: "My Server")
AuthType Basic
AuthUserFile /etc/apache2/dav_svn.passwd
Require valid-user

#this restricts viewing of the .htaccess file so people cannot find the location of your .passwd file.
<Files .htaccess>
order allow,deny
deny from all
</Files>

```

Finally lets set the permissions on the .htaccess file so it cannot be read
```

# chmod 644 /var/www/.htaccess

```

Now, only the svn users can view the files on the web server

[SIZE="5"]5. Testing[/SIZE]
1. Log into your FTP server as your user/s and try creating and deleting files. The users should automatically be placed in the /www folder.

2. In a web browser, go to your SVN server address (ex: [http://localhost/svn](http://localhost/svn)) and login in with your user and svn passwd. If all is well you should see "Rev:0"

3. In a web browser, go to your web server and verify that users must authenticate to view content. 

[SIZE="5"]The End[/SIZE] * for now xD

---

### Post by iKindred on 2011-03-24
Thanks, this is useful.

---

