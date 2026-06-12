---
title: "Upgrade to 20.04 LTS breaks website images"
date: 2020-06-05
forum: Server Platforms
---

### Post by caldwell on 2020-06-05
I upgraded a small webserver from Ubuntu 18.04 LTS to 20.04 LTS.  The upgrade seemed to go fine except for one issue.  All the images on the website are now broken!  I think it's some sort of MIME type issue, I can download the images with a web browser, but they are corrupt.  If I sftp the images they are fine.

I'm running out of bright ideas. Thoughts?

---

### Post by SeijiSensei on 2020-06-05
What kind of images?  Are they JPG, GIF, PNG, or something more exotic?

---

### Post by LHammonds on 2020-06-05
And, when you access the page with the images, do you see anything in the "access" or "error" log that indicates an issue with sending that mime type?

Default install of Apache can handle .jpg, .png or .gif out of the box.

LHammonds

---

### Post by caldwell on 2020-06-08
Good Morning, they are mostly JPG with some GIF and PNG mixed in to keep life interesting.

---

### Post by LHammonds on 2020-06-08
Was it an in-place upgrade or did you migrate the files to a different server?

My initial guess would be a permissions issue but I do not know what web server you are using.  If you installed Apache, what version are you running?  Version 2.4.41 is the current version for 20.04.

```
apache2 -v
```
```
Server version: Apache/2.4.41 (Ubuntu)
Server built:   2020-04-13T17:19:17
```

If running Apache, your web service account and group name is likely called "www-data" so make sure your permissions on the images are owned by "www-data:www-data" or at the very least readable to the "other" group.

```
chmod 444 *.jpg
```

Apache by itself, out of the box, can display html pages and the pictures inside img tags.  You don't even need to enable php or anything else (if you are using .htm pages).  But if you are using php includes and you don't have php enabled, then that might cause what you are seeing...but I have extremely little info to go on here because I have not ever had this problem you are describing...which might be misleading as to the true root cause (pardon the pun).

If your web pages are .php files, you might want to create a phpinfo page and see if that works and what modules are enabled:

Example:
```

sudo touch /var/www/html/phpinfo.php
sudo chown www-data:www-data /var/www/html/phpinfo.php
sudo chmod 0644 /var/www/html/phpinfo.php
sudo echo "<?php phpinfo(); ?>" >> /var/www/html/phpinfo.php
```

**EDIT #1**: After looking at the permissions, use a browser and plug in the direct url to an image and see if that image displays...which is nothing other than displaying an image and has nothing to do with html/php code.

Example: 
```
https://images.hammondslegacy.com/linux/Ubuntu_2004_Logo_ASCII.png
```

**EDIT #2**: If you truly think it is a mime-related issue, then check how mimes are used.

[list=1]
[*]Make sure the mime mod is enabled.
```
ls /etc/apache2/mods-enabled/mime*
```
[*]You should see a mime.conf and mime.load in there by default.
[*]If you look at mime.conf, you will see it pulls a list of mime types from /etc/mime.types
[*]If you look at /etc/mime.types, you should find image/jpeg, image/gif, image/png and others in there.
[/list]


If you did not see the mime files linked in the "mods-enabled" folder, then try enabling them and restart Apache:
```
sudo a2enmod mime
sudo systemctl restart apache2
```

LHammonds

---

### Post by caldwell on 2020-06-11
Hello,

Nothing odd in the logs.  I tried reinstalling all the mime-parts without success.  I've temporarily solved the problem by rolling back the upgrade (VMWare rocks at times like this).  It's back to 18.04 and is happily serving images again.  I am now debating if I should try another upgrade or do a full nuke-and-pave operation to eliminate 5 years of accumulated "stuff" from the machine.  

Thank you!!

---

### Post by LHammonds on 2020-06-11
Well, here's the thing, you don't really want to do an in-place upgrade until the first point release is out (20.04.1) but that migration is only tested for the base operating system, not all the various apps you can bolt on.  Since you have a virtual environment, I would STRONGLY recommend setting up a brand new 20.04 server and get it working with the software first.  Then copy over your data and get your sites working.  Once you have done this successfully, jot down the steps needed to make it all work.  Then wipe the new machine and start over....following those steps.  If you are able to get it done again following those steps, you now have a VERY solid upgrade/migration procedure.  Do it one more time and when you migrate the data and verify it is working, swap the IP addresses of the machines and let the new machine take over as the production box!

That is the exact way I upgrade every server of mine.  I NEVER do an in-place upgrade.  I just don't like potentially having extended downtime...especially if I can have it running on the new platform and working perfectly BEFORE switching the IPs.  The transition from old to new is difficult to beat doing it this way in terms of uptime service and peace of mind knowing that the upgrade will work because you have already done it and proven it will work without ever causing downtime on the production machine.

LHammonds

---

### Post by caldwell on 2020-07-06
Problem fixed!  New server had the same problem.  The source files for the web server live on a WinDFS cluster.  There appears to be bug between Apache and SMB.  This will fix it:

by default, apache uses mmap, so probably mmap is broken on cifs. A workaround should be to set EnableMMAP off in the apache
config.

[FONT=courier new]<Directory "/path-to-cifs-files">
   EnableMMAP Off
</Directory>
[/FONT]
# Documented here
[http://httpd.apache.org/docs/2.4/mod/core.html#enablemmap](http://httpd.apache.org/docs/2.4/mod/core.html#enablemmap)

Thank you!

---

