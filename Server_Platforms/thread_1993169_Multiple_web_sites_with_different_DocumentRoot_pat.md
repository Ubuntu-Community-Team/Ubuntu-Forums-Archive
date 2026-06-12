---
title: "Multiple web sites with different DocumentRoot paths"
date: 2012-06-01
forum: Server Platforms
---

### Post by JackTheKnife on 2012-06-01
Hi,

I have set staging web server with multiple local domains set at /home for particular users, but unfortunately /home is set as separate partition which is almost full (I have try to resize it but it went into problems).

Question is can I put some of those web sites to /var/www? If yes then what steps I should to take?

Thanks

---

### Post by galvatron408 on 2012-06-03
You have a few options.

You could sym link your root dir to /var/www or you could just reconfigure apache to serve its pages from /var/www.

Anyway, to your concern about /home being full... umm, these files are served by apache, so even if the /home partition is full, apache isn't going to stop working. You do have a separate partition for /var right? and /var/log is on it right?

---

### Post by lisati on 2012-06-03
*Thread moved to **Server Platforms**.*

---

### Post by volkswagner on 2012-06-03
You can have an unlimited number of document root folders.

Choose a partition with sufficient space and move some sites to that location.

This is easily accomplished with NameVirtualHosts.

For info on how to create multiple vhost files check the server docs/sticky at the top of this forum.  Here's the link for [Apache]("https://help.ubuntu.com/10.04/serverguide/httpd.html").

---

### Post by JackTheKnife on 2012-06-08
> **volkswagner said:**
> You can have an unlimited number of document root folders.

Choose a partition with sufficient space and move some sites to that location.

This is easily accomplished with NameVirtualHosts.

For info on how to create multiple vhost files check the server docs/sticky at the top of this forum.  Here's the link for [Apache]("https://help.ubuntu.com/10.04/serverguide/httpd.html").

So if I have vhost file like that one:

```

# domain: xyz.local
# public: /home/xyz/html

<VirtualHost *:80>

    ServerName xyz.local
    ServerAlias www.xyz.local
    ServerAdmin me@null.com

    
    # Index file and Document Root
    # DirectoryIndex index.html
    DocumentRoot /home/xyz/html
    <Directory /home/xyz/html>
	Options FollowSymLinks
	AllowOverride All
    </Directory>

    # Custom log file location
    LogLevel warn
    ErrorLog /home/xyz/log/error.log
    CustomLog /home/xyz/log/access.log combined

</VirtualHost>

```

and I will move site from /home/xyz/html to /var/www/xyz/html and change vhost file to


```

# domain: xyz.local
# public: /var/www/xyz/html

<VirtualHost *:80>

    ServerName xyz.local
    ServerAlias www.xyz.local
    ServerAdmin me@null.com

    
    # Index file and Document Root
    # DirectoryIndex index.html
    DocumentRoot /var/www/xyz/html
    <Directory /var/www/xyz/html>
	Options FollowSymLinks
	AllowOverride All
    </Directory>

    # Custom log file location
    LogLevel warn
    ErrorLog /var/www/xyz/log/error.log
    CustomLog /var/www/xyz/log/access.log combined

</VirtualHost>

```

Is should work? What about FTP/SVN access in that case?

Thanks

---

### Post by volkswagner on 2012-06-08
I'm sorry but I'm not familiar with SVN.

As far as ftp goes, you will like likely need to change the config for the user's default or jailed directory.

The document root is solely for Apache2.  If you have other requirements they will need to be addressed individually.

Do you have multiple users and sites for each user?

Also moving from a /home to /var will may have some file permission differences also.

If your ftp server config has users jailed to their /home/username directory, you may be able to move that users directory to a partition with available space.

---

