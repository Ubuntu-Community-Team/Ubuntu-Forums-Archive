---
title: "permission hell and php"
date: 2007-05-13
forum: Server Platforms
---

### Post by dozier768 on 2007-05-13
Hey im running and apache web server with feisty server edition, i set up some virtual hosts and whatnot and installed vsftpd, mysql and php5, everything woks great, however anytime php creates a file in my users directory "say im running a forum and the forum package installer uploads a file" it ends up getting owned by www-data and it cannot be chmodded via ftp because the file owner and group is www-data and not user1:user1 or whatever... can any one shed some light on who needs to belong to what group and all that its a real pain in the rear and im pulliongmy hair out. currently /var/www/user1 is chowned to user1:user1 and i tried adding user1 to the www-data group but that made no difference.  	](*,)

---

### Post by Frosty Cold Drink on 2007-05-13
> **dozier768 said:**
> Hey im running and apache web server with feisty server edition, i set up some virtual hosts and whatnot and installed vsftpd, mysql and php5, everything woks great, however anytime php creates a file in my users directory "say im running a forum and the forum package installer uploads a file" it ends up getting owned by www-data and it cannot be chmodded via ftp because the file owner and group is www-data and not user1:user1 or whatever... can any one shed some light on who needs to belong to what group and all that its a real pain in the rear and im pulliongmy hair out. currently /var/www/user1 is chowned to user1:user1 and i tried adding user1 to the www-data group but that made no difference.  	](*,)

This is the way it should be, annoying as it is.

You could set your directories to be set gid (2775 for example), and umask's to allow group writing (0002 perhaps). You still won't be able to change permissions, but you can encourage them to be what they need to be. Many packages will let you set what permissions to chagne uploaded files to. Shuffling groups isn't going to help.

Another solution is to use suexec and suphp. They will run user's code as the users instead of as the web server's user.

I wouldn't advise setuid anything ever (outside of the normal passwd, sudo, and such...)

---

### Post by dozier768 on 2007-05-13
well i installed suphp, suexec is already installed and enabled, what directives are necessary in my virtual hosts.... the second suphp is enabled ic craps out my virtual hosts and complains about a misconfiguration

here is my vhost config

> <VirtualHost *>
    ServerName myhost.com
    ServerAlias [www.myhost.com](www.myhost.com)
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/myhost
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/myhost>
        # pcw No directory listsings
        # Options Indexes FollowSymLinks MultiViews
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/myhost/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/myhost/access.log combined
    ServerSignature On

</VirtualHost>

it would seem to me that even with suphp mod enabled and no directives in my vhost it shouldnt imediately kill my vhost.... should it..or is that normal behavior, and every vhost must be configured properly when suphp is enabled?

---

### Post by Frosty Cold Drink on 2007-05-13
> **dozier768 said:**
> well i installed suphp, suexec is already installed and enabled, what directives are necessary in my virtual hosts.... the second suphp is enabled ic craps out my virtual hosts and complains about a misconfiguration

here is my vhost config



it would seem to me that even with suphp mod enabled and no directives in my vhost it shouldnt imediately kill my vhost.... should it..or is that normal behavior, and every vhost must be configured properly when suphp is enabled?

I woudn't know since I don't use suPHP :)

Try setting the proper config options for suPHP in your VirtualHost block. You will need suPHP_UserGroup. If you don't have PHP on globally, you will need to turn it on in the VirtualHost block using"suPHP_Engine On".

---

