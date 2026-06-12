---
title: "Correct User/Apache/FTP folder permissions"
date: 2008-03-20
forum: Server Platforms
---

### Post by Poleh on 2008-03-20
ok so I have apache running vhosts and vsftpd installed for ftp access. Folder structure as follows:

/home/www-domain-com/public_html/
/home/www-domain-com/logs/

/home/www-domain2-com/public_html/
/home/www-domain2-com/logs/

The vhost configs point directly to the user home folders' public_html and logs folders.

The problem I am encountering now is one of permissions. If I create the public_html/logs folders with sudo mkdir they're owned by root and the web server serves the vhost files fine, but the users can't do anything with ftp.

If the folders are owned by the user, apache appears to not be able to read the files/ignores them completely with the usual "You do not have permission to ..." However in this configuration the ftp clearly works fine.

I have tried adding the users supplemental group to www-data and then chown the public_html folders to www-data but that didn't seem to help much.

Samples of apache config files below, any help would be much appreciated:
```
<VirtualHost *>
        ServerAdmin webmaster@localhost
        
        DocumentRoot /home/www-swaziboy-com/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/www-swaziboy-com/public_html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /home/www-swaziboy-com/logs/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /home/www-swaziboy-com/logs/access.log combined
        ServerSignature On

</VirtualHost>

```

---

