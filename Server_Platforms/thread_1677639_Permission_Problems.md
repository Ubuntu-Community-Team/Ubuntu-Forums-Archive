---
title: "Permission Problems"
date: 2011-01-29
forum: Server Platforms
---

### Post by ryannathans on 2011-01-29
Hey

Just ran into a bit of a small problem with my Joomla! 1.6 installation.

When trying to install a package I get an error about writing and permissions.

```
 * JFile: :write(/var/www/mga/tmp/install_4d41090f69224/index.php):  fopen(/var/www/mga/tmp/install_4d41090f69224/index.php): failed to open  stream: Permission denied
        * Unable to write entry
```I can't work out what the problem is and the guys at the Joomla! forum told me to post here as it was ubuntu related and not Joomla!

A couple of questions, what should the user be called and the group of the user account that is operational in the /var/www/mga folder? At the moment I have called it joomla in the nogroup what should it be?

Server is trying to install a joomla extension from the uploaded com_joomlaxplorer_1.6.3.zip (uploaded using the web control panel) but gets that permission error when it creates the other folder in tmp. (extracting it I believe)

```
ryannathans@UbuntuServer:/var/www/mga$ ls -l
total 96
drwxrwxr-x 10 joomla nogroup  4096 2011-01-27 10:22 administrator
drwxrwxr-x  2 joomla nogroup  4096 2011-01-27 10:22 cache
drwxrwxr-x 12 joomla nogroup  4096 2011-01-27 10:22 components
-rwxrwxr-x  1 joomla nogroup  2168 2011-01-29 14:13 configuration.php
drwxrwxr-x  4 joomla nogroup  4096 2011-01-27 10:22 images
drwxrwxr-x  2 joomla nogroup  4096 2011-01-27 10:22 includes
-rwxrwxr-x  1 joomla nogroup  1394 2011-01-09 10:40 index.php
-rwxrwxr-x  1 joomla nogroup  1273 2011-01-11 11:58 joomla.xml
drwxrwxr-x  4 joomla nogroup  4096 2011-01-27 10:22 language
drwxrwxr-x  6 joomla nogroup  4096 2011-01-27 10:22 libraries
-rwxrwxr-x  1 joomla nogroup 17816 2009-12-12 23:44 LICENSE.txt
drwxrwxr-x  2 joomla nogroup  4096 2011-01-27 10:22 logs
drwxrwxr-x  8 joomla nogroup  4096 2011-01-27 10:23 media
drwxrwxr-x 25 joomla nogroup  4096 2011-01-27 10:23 modules
drwxrwxr-x 10 joomla nogroup  4096 2011-01-27 10:23 plugins
-rwxrwxr-x  1 joomla nogroup  4493 2011-01-09 10:40 README.txt
-rwxrwxr-x  1 joomla nogroup   301 2009-08-13 01:12 robots.txt
drwxrwxr-x  6 joomla nogroup  4096 2011-01-27 12:59 templates
drwxrwxr-x  3 joomla nogroup  4096 2011-01-29 14:20 tmp
``````
ryannathans@UbuntuServer:/var/www/mga/tmp$ ls -l
total 476
-rwxrwxrwx 1 joomla nogroup 480836 2011-01-29 14:23 com_joomlaxplorer_1.6.3.zip
drwxr-xr-x 2 joomla nogroup   4096 2011-01-29 14:23 install_4d43b26cae769
```What permissions and owners/groups should everything be set to for it to work?

I believe it is using FTP layer to do everything with the user joomla in group nogroup

-thanks
ryannathans

EDIT: just reinstalled joomla in that directory and remade all the mysql databases and everything + set the user to mga Set permissions of everything to 777 and still it gets this error. (I know 777 is unsafe)

```

    
[LIST]
[*]JFile:  :write(/var/www/mga/tmp/install_4d43cbb080ce7/admin.joomlaxplorer.php):  fopen(/var/www/mga/tmp/install_4d43cbb080ce7/admin.joomlaxplorer.php):  failed to open stream: Permission denied
[*]Unable to write entry
[/LIST]

``` 
And proof.
```

ryannathans@UbuntuServer:/var/www/mga$ ls -l
total 96
drwxrwxrwx 10 mga nogroup  4096 2011-01-29 16:03 administrator
drwxrwxrwx  2 mga nogroup  4096 2011-01-29 16:03 cache
drwxrwxrwx 12 mga nogroup  4096 2011-01-29 16:03 components
-rwxrwxrwx  1 mga nogroup  1772 2011-01-29 16:10 configuration.php
drwxrwxrwx  4 mga nogroup  4096 2011-01-29 16:03 images
drwxrwxrwx  2 mga nogroup  4096 2011-01-29 16:03 includes
-rwxrwxrwx  1 mga nogroup  1394 2011-01-29 16:03 index.php
-rwxrwxrwx  1 mga nogroup  1273 2011-01-29 16:03 joomla.xml
drwxrwxrwx  4 mga nogroup  4096 2011-01-29 16:04 language
drwxrwxrwx  6 mga nogroup  4096 2011-01-29 16:04 libraries
-rwxrwxrwx  1 mga nogroup 17816 2011-01-29 16:03 LICENSE.txt
drwxrwxrwx  2 mga nogroup  4096 2011-01-29 16:04 logs
drwxrwxrwx  8 mga nogroup  4096 2011-01-29 16:04 media
drwxrwxrwx 25 mga nogroup  4096 2011-01-29 16:04 modules
drwxrwxrwx 10 mga nogroup  4096 2011-01-29 16:03 plugins
-rwxrwxrwx  1 mga nogroup  4493 2011-01-29 16:03 README.txt
-rwxrwxrwx  1 mga nogroup   301 2011-01-29 16:03 robots.txt
drwxrwxrwx  6 mga nogroup  4096 2011-01-29 16:03 templates
drwxrwxrwx  3 mga nogroup  4096 2011-01-29 16:11 tmp

```

---

### Post by ryannathans on 2011-01-30
*bump* 

I need this site functional ASAP

---

### Post by James78 on 2011-01-30
Well, first I'd suggest you set those files to user www-data and group www-data. That's Apache's user, and that's the user that needs correct access to those files; permission wise.

Secondly, I may be wrong, but when you're uploading the file, whatever it's copying to /var/www/mga/tmp may not be owned by Apache or have the proper permissions. My guess is that you have a file with user mga and group nogroup, with permissions 777, and the new files it copies over inherit the user and group, BUT, the new files it makes aren't going to be 777; they're probably going to be -rw-r----- at the most, and Apache can't access that.

As I said earlier, you might try setting everything to www-data, so Apache can access it properly. You could also add www-data to your users group (sudo adduser www-data mga), then have your files owned by user mga and group mga, but newly created files would not very likely be writable by Apache; only readable (that may not even be a problem however). The first idea is the best shot at the moment though.

---

### Post by ryannathans on 2011-01-30
> **James78 said:**
> Well, first I'd suggest you set those files to user www-data and group www-data. That's Apache's user, and that's the user that needs correct access to those files; permission wise.

Secondly, I may be wrong, but when you're uploading the file, whatever it's copying to /var/www/mga/tmp may not be owned by Apache or have the proper permissions. My guess is that you have a file with user mga and group nogroup, with permissions 777, and the new files it copies over inherit the user and group, BUT, the new files it makes aren't going to be 777; they're probably going to be -rw-r----- at the most, and Apache can't access that.

As I said earlier, you might try setting everything to www-data, so Apache can access it properly. You could also add www-data to your users group (sudo adduser www-data mga), then have your files owned by user mga and group mga, but newly created files would not very likely be writable by Apache; only readable (that may not even be a problem however). The first idea is the best shot at the moment though.

EDIT: Just installed 2 packages fine, it works! thanks

```
root@UbuntuServer:/var/www/tmp/install_4d45717c843a4# ls -l
total 148
-rw-r--r-- 1 www-data www-data  8977 2011-01-30 22:11 admin.joomlaxplorer.php
-rw-r--r-- 1 www-data www-data  6322 2011-01-30 22:11 CHANGELOG.txt
drwxr-xr-x 2 www-data www-data  4096 2011-01-30 22:11 config
-rw-r--r-- 1 www-data www-data   649 2011-01-30 22:11 configuration.jx.php
drwxr-xr-x 2 www-data www-data  4096 2011-01-30 22:11 ftp_tmp
drwxr-xr-x 2 www-data www-data  4096 2011-01-30 22:11 images
drwxr-xr-x 2 www-data www-data  4096 2011-01-30 22:11 include
-rw-r--r-- 1 www-data www-data    44 2011-01-30 22:11 index.html
-rw-r--r-- 1 www-data www-data   656 2011-01-30 22:11 install.joomlaxplorer.php
-rw-r--r-- 1 www-data www-data  3720 2011-01-30 22:11 joomlaxplorer.init.php
-rw-r--r-- 1 www-data www-data 17178 2011-01-30 22:11 joomlaxplorer.list.php
-rw-r--r-- 1 www-data www-data  3377 2011-01-30 22:11 joomlaxplorer.php
-rw-r--r-- 1 www-data www-data 14880 2011-01-30 22:11 joomlaxplorer.xml
drwxr-xr-x 2 www-data www-data  4096 2011-01-30 22:11 languages
drwxr-xr-x 5 www-data www-data  4096 2011-01-30 22:11 libraries
-rw-r--r-- 1 www-data www-data 25753 2011-01-30 22:11 LICENSE
-rw-r--r-- 1 www-data www-data  5497 2011-01-30 22:11 README.txt
-rw-r--r-- 1 www-data www-data  2796 2011-01-30 22:11 RELEASE.txt
drwxr-xr-x 3 www-data www-data  4096 2011-01-30 22:11 scripts
drwxr-xr-x 2 www-data www-data  4096 2011-01-30 22:11 style

```

---

### Post by ryannathans on 2011-01-30
what would I do if I wanted another joomla installation? (like i will do soon)

---

### Post by James78 on 2011-01-30
I've never tried this method, but I'd imagine it should work. Just upload a new Joomla copy to /var/www/anotherfolder, then configure it and whatever else. I think it should be fairly straightforward. :) You can create another database for the new installation, or you can use the same database only with different table prefixes, e.g. jos2_

---

### Post by ryannathans on 2011-01-30
> **James78 said:**
> I've never tried this method, but I'd imagine it should work. Just upload a new Joomla copy to /var/www/anotherfolder, then configure it and whatever else. I think it should be fairly straightforward. :) You can create another database for the new installation, or you can use the same database only with different table prefixes, e.g. jos2_

still using the www-data user?

only problem I had when using that user operating in /var/www/mga/ was that when I saved that as root in joomla config it kept defaulting back to /var/www/ and of course wouldn't find any of my files.

---

### Post by James78 on 2011-01-30
> **ryannathans said:**
> still using the www-data user?

only problem I had when using that user operating in /var/www/mga/ was that when I saved that as root in joomla config it kept defaulting back to /var/www/ and of course wouldn't find any of my files.
Ya, still using the www-data user (anything under the webroot /var/www = www-data:www-data)

---

