---
title: "sudden Forbidden errors - apache2"
date: 2012-06-17
forum: Server Platforms
---

### Post by mons00n on 2012-06-17
Hey guys, 

I'm having a serious problem with my apache 2.2.22 server on Ubuntu 12.04 x64.  I recently reinstalled my entire server (LAMP) and everything was working *perfect* (for roughly 2 weeks) until a few days ago.  Suddenly, without ANY changes, I am getting '403 Forbidden - You don't have permission to access / on this server.'  The SAME problem [happened to me 2 weeks ago (link to thread)]("http://ubuntuforums.org/showthread.php?t=1993407") and I thought it was because of an apache update, but now I'm starting to think it is something else.  

My website resides in a folder in my home directory, but that has never posed a problem in the past.  I can still access things that are outside of my home directory such as phpMyAdmin, and Mumble-django, but nothing whose files reside within my home directory.  Again NOTHING has been changed...I haven't even rebooted the machine until this morning.  I've examined my apache logs and everything seems fine (other than random PHP errors) until it just starts spitting out '(13) Access Denied' errors.  

Has anyone had something like this happen to them in the past?  It's quite aggravating and I'd rather not have to reinstall again =(  Thanks for your time.

---

### Post by SeijiSensei on 2012-06-17
The top of your home directory needs, at a minimum, 711 permissions so the Apache pseudo-user, called "www-data", can see the website directory.  If you run:

```

cd /
ls -l home

```

what permissions does /home/username have?  By default, Ubuntu sets all home directories to 700 (user read/write/execute, everyone else gets nothings).  If you only see permissions like "drwx-------", then you need to run 

```
sudo chmod 711 /home/username
```

If the permissions are correct at the top of your directory, continue to browse down through all the subdirectories above your website directory and make sure they all have at least 711 permissions as well.

---

### Post by mons00n on 2012-06-17
> **SeijiSensei said:**
> The top of your home directory needs, at a minimum, 711 permissions so the Apache pseudo-user, called "www-data", can see the website directory.  If you run:

```

cd /
ls -l home

```

what permissions does /home/username have?  By default, Ubuntu sets all home directories to 700 (user read/write/execute, everyone else gets nothings).  If you only see permissions like "drwx-------", then you need to run 

```
sudo chmod 711 /home/username
```

If the permissions are correct at the top of your directory, continue to browse down through all the subdirectories above your website directory and make sure they all have at least 711 permissions as well.

I'll double check the permissions when I get home, but it doesn't make sense that it worked perfectly for 2 weeks then suddenly stopped without changing a thing.  Would there be any reasoning for that?  The box is a simple web/file/mumble/arma2 server that is on 24/7 with very little interaction.

---

### Post by SeijiSensei on 2012-06-17
Another possibility is that you no longer have the "Indexes" option enabled for the directory where the site resides. Do you have 

```

DocumentRoot  /home/me/mysite

<Directory "/home/me/mysite">
    Options Indexes
</Directory>

```

or "Options All" specified in the VirtualHost definition for the site?  If you use an .htaccess file, does the <Directory> stanza in the VirtualHost definition include "AllowOverride Indexes" or "AllowOverride All"?  More details [here](http://httpd.apache.org/docs/2.2/mod/core.html#directory).

---

### Post by mons00n on 2012-06-17
> **SeijiSensei said:**
> Another possibility is that you no longer have the "Indexes" option enabled for the directory where the site resides. Do you have 

```

DocumentRoot  /home/me/mysite

<Directory "/home/me/mysite">
    Options Indexes
</Directory>

```

or "Options All" specified in the VirtualHost definition for the site?  If you use an .htaccess file, does the <Directory> stanza in the VirtualHost definition include "AllowOverride Indexes" or "AllowOverride All"?  More details [here](http://httpd.apache.org/docs/2.2/mod/core.html#directory).

Would those just disappear without any changes on my side?  Last time I checked all of those were present.  Again I'll double check in a few hours when I get home - but again, everything worked 100% for two weeks.

---

### Post by mons00n on 2012-06-18
All of the home directory permissions were fine.  I had to move my folders out of my home directory and things started working again.  Still baffles me why it would just stop out of no where.

---

