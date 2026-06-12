---
title: "lockal worpress -- setup error"
date: 2015-07-15
forum: Server Platforms
---

### Post by erok2 on 2015-07-15
I has installed mysql, apache and downloaded wordpress and try to get wordpress locally in my computer, when I try to reach for setup  my wordpress config. (to finish my config.)with the command :

```
http://localhost/wordpress/wp_admin/setup-config.php
```

I get the error 403 Frobidden, like this

```
**Forbidden**

 You don't have permission to access /wp-admin/setup-config.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80

```

I has tried to google the problem but not found  to solve the problem, what should I try to do for solve this problem??

---

### Post by nerdtron on 2015-07-15
What are the permissions of the word press files in the document root? They should be owned by apache and are world readable.

---

### Post by limbenjamin on 2015-07-16
apache does not have the permissions to access the file.

Assuming that your web root is at /var/www/html/wordpress/, execute the following commands to grant the permissions.

```

cd /var/www/html/wordpress/
chown www-data:www-data -R *          # Let apache be owner
find . -type d -exec chmod 755 {} \;  # Change directory permissions rwxr-xr-x
find . -type f -exec chmod 644 {} \;  # Change file permissions rw-r--r--

```

---

### Post by CharlesA on 2015-07-16
> **limbenjamin said:**
> apache does not have the permissions to access the file.

Assuming that your web root is at /var/www/html/wordpress/, execute the following commands to grant the permissions.

```

cd /var/www/html/wordpress/
chown www-data:www-data -R *          # Let apache be owner
find . -type d -exec chmod 755 {} \;  # Change directory permissions rwxr-xr-x
find . -type f -exec chmod 644 {} \;  # Change file permissions rw-r--r--

```

This pretty much covers it, but if you want to learn more about hardening Wordpress, you can check out their Codex here:
[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

They have a section for file permissions. :)

---

### Post by erok2 on 2015-07-17
Thanks, get this now:

```
sudo chown -R www-data:www-data /var/www
```

```
erok@eriks-dator:/var/www/html/wordpress$ sudo ls -l /var/www
total 212
drwx-w----  5 www-data www-data  4096 Jul  9 14:47 html
-rw-rw-r--  1 www-data www-data   418 Sep 25  2013 index.php
-rw-rw-r--  1 www-data www-data    87 Oct 27  2013 info.php
-rw-rw-r--  1 www-data www-data 19930 Apr  9  2014 license.txt
-rw-rw-r--  1 www-data www-data 14280 Sep  4  2014 licens-sv_SE.txt
lrwxrwxrwx  1 www-data www-data    21 Oct 27  2013 phpMyAdmin -> /usr/share/phpmyadmin
-rw-rw-r--  1 www-data www-data  9893 Sep  4  2014 readme.html
lrwxrwxrwx  1 www-data www-data    20 Oct 27  2013 wordpress -> /usr/share/wordpress
-rw-rw-r--  1 www-data www-data  4951 Aug 20  2014 wp-activate.php
drwx-w----  9 www-data www-data  4096 Sep  4  2014 wp-admin
-rw-rw-r--  1 www-data www-data   271 Jan  8  2012 wp-blog-header.php
-rw-rw-r--  1 www-data www-data  4946 Jun  5  2014 wp-comments-post.php
-rw-rw-r--  1 www-data www-data  2742 Jul  7 18:18 wp-config.php
-rw-rw-r--  1 www-data www-data  2742 Jul  7 11:27 wp-config.php~
-rw-rw-r--  1 www-data www-data  2788 Sep  4  2014 wp-config-sample.php
drwx-w----  8 www-data www-data  4096 Sep  4  2014 wp-content
-rw-rw-r--  1 www-data www-data  2956 May 13  2014 wp-cron.php
drwx-w---- 12 www-data www-data  4096 Sep  4  2014 wp-includes
-rw-rw-r--  1 www-data www-data  2380 Oct 24  2013 wp-links-opml.php
-rw-rw-r--  1 www-data www-data  2714 Jul  7  2014 wp-load.php
-rw-rw-r--  1 www-data www-data 33043 Aug 27  2014 wp-login.php
-rw-rw-r--  1 www-data www-data  8252 Jul 17  2014 wp-mail.php
-rw-rw-r--  1 www-data www-data 11115 Jul 18  2014 wp-settings.php
-rw-rw-r--  1 www-data www-data 26256 Jul 17  2014 wp-signup.php
-rw-rw-r--  1 www-data www-data  4026 Oct 24  2013 wp-trackback.php
-rw-rw-r--  1 www-data www-data  3032 Feb  9  2014 xmlrpc.php
erok@eriks-dator:/var/www/html/wordpress$
```

when I try this:

```
http://localhost/wordpress/wp-admin/setup-config.php
```

I get this (403 Forbidden):

```
**Forbidden**

 You don't have permission to access /wordpress/wp-admin/setup-config.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80

```

Restarting mysql and apache,

```
erok@eriks-dator:/$ sudo /etc/init.d/mysql start 
 * Starting MySQL database server mysqld    [ OK ] 

erok@eriks-dator:/$ sudo service apache2 restart
 * Restarting web server apache2 
AH00558: apache2: Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message   [ OK ]
erok@eriks-dator:/$
```

?? ip 127.0.1.1 not 127.0.0.1 is that right??

What shall i try next time?

---

### Post by CharlesA on 2015-07-17
What are the permissions inside the wp-admin directory?

I see three folders that do not have read permission for the group.

---

### Post by erok2 on 2015-07-18
**CharlesA wrote:**
```
What are the permissions inside the wp-admin directory?

I see three folders that do not have read permission for the group.
```

You mean this?

```
erok@eriks-dator:/$ sudo ls -l /home/erok/wordpress/wp-admin
total 912
-rw-rw-r-- 1 erok erok  7599 Sep  4  2014 about.php
-rw-rw-r-- 1 erok erok  3405 Jul 15  2014 admin-ajax.php
-rw-rw-r-- 1 erok erok  2349 Mar  8  2014 admin-footer.php
-rw-rw-r-- 1 erok erok   403 Dec 24  2013 admin-functions.php
-rw-rw-r-- 1 erok erok  6648 Jul 14  2014 admin-header.php
-rw-rw-r-- 1 erok erok 10344 Jul 17  2014 admin.php
-rw-rw-r-- 1 erok erok  1681 May 18  2014 admin-post.php
-rw-rw-r-- 1 erok erok  4140 Aug  2  2014 async-upload.php
-rw-rw-r-- 1 erok erok  9154 May 18  2014 comment.php
-rw-rw-r-- 1 erok erok  6844 Sep  3  2014 credits.php
drwxrwxr-x 3 erok erok  4096 Sep  4  2014 css
-rw-rw-r-- 1 erok erok 17067 Aug  9  2014 custom-background.php
-rw-rw-r-- 1 erok erok 44247 Aug  9  2014 custom-header.php
-rw-rw-r-- 1 erok erok  9380 Aug 25  2014 customize.php
-rw-rw-r-- 1 erok erok 11661 Mar 27  2014 edit-comments.php
-rw-rw-r-- 1 erok erok 29414 Sep  2  2014 edit-form-advanced.php
-rw-rw-r-- 1 erok erok  6364 May 19  2014 edit-form-comment.php
-rw-rw-r-- 1 erok erok  5992 May 18  2014 edit-link-form.php
-rw-rw-r-- 1 erok erok 14411 Jun 10  2014 edit.php
-rw-rw-r-- 1 erok erok  6948 Jan 24  2014 edit-tag-form.php
-rw-rw-r-- 1 erok erok 20308 May  6  2014 edit-tags.php
-rw-rw-r-- 1 erok erok  8332 Mar  8  2014 export.php
-rw-rw-r-- 1 erok erok  3367 Aug 28  2014 freedoms.php
drwxrwxr-x 2 erok erok  4096 Sep  4  2014 images
-rw-rw-r-- 1 erok erok  5265 Mar  8  2014 import.php
drwxrwxr-x 2 erok erok  4096 Sep  4  2014 includes
-rw-rw-r-- 1 erok erok  5989 Mar  8  2014 index.php
-rw-rw-r-- 1 erok erok  5446 Jul 17  2014 install-helper.php
-rw-rw-r-- 1 erok erok 11888 Sep  4  2014 install.php
drwxrwxr-x 2 erok erok  4096 Sep  4  2014 js
-rw-rw-r-- 1 erok erok   712 Sep 25  2013 link-add.php
-rw-rw-r-- 1 erok erok  3468 Mar  8  2014 link-manager.php
-rw-rw-r-- 1 erok erok  1990 Jul 17  2014 link-parse-opml.php
-rw-rw-r-- 1 erok erok  2625 Jul 17  2014 link.php
-rw-rw-r-- 1 erok erok  2818 Jul  7  2014 load-scripts.php
-rw-rw-r-- 1 erok erok  3149 Jul  3  2014 load-styles.php
drwxrwxr-x 2 erok erok  4096 Sep  4  2014 maint
-rw-rw-r-- 1 erok erok  3137 Mar  8  2014 media-new.php
-rw-rw-r-- 1 erok erok  5229 Jul 17  2014 media.php
-rw-rw-r-- 1 erok erok  3146 Jul 17  2014 media-upload.php
-rw-rw-r-- 1 erok erok  8011 Jul 17  2014 menu-header.php
-rw-rw-r-- 1 erok erok 12835 Jul 17  2014 menu.php
-rw-rw-r-- 1 erok erok   320 Sep 25  2013 moderation.php
-rw-rw-r-- 1 erok erok   211 Sep 25  2013 ms-admin.php
-rw-rw-r-- 1 erok erok  3695 Mar 28  2014 ms-delete-site.php
-rw-rw-r-- 1 erok erok   231 Sep 25  2013 ms-edit.php
-rw-rw-r-- 1 erok erok   236 Sep 25  2013 ms-options.php
-rw-rw-r-- 1 erok erok   228 Sep 25  2013 ms-sites.php
-rw-rw-r-- 1 erok erok   230 Sep 25  2013 ms-themes.php
-rw-rw-r-- 1 erok erok   232 Sep 25  2013 ms-upgrade-network.php
-rw-rw-r-- 1 erok erok   228 Sep 25  2013 ms-users.php
-rw-rw-r-- 1 erok erok  4676 Mar  8  2014 my-sites.php
-rw-rw-r-- 1 erok erok 38583 Jul 17  2014 nav-menus.php
drwxrwxr-x 2 erok erok  4096 Sep  4  2014 network
-rw-rw-r-- 1 erok erok 26492 Jul 17  2014 network.php
-rw-rw-r-- 1 erok erok 13677 Apr 12  2014 options-discussion.php
-rw-rw-r-- 1 erok erok 14240 Sep  3  2014 options-general.php
-rw-rw-r-- 1 erok erok   492 Mar  1  2013 options-head.php
-rw-rw-r-- 1 erok erok  5831 Mar  8  2014 options-media.php
-rw-rw-r-- 1 erok erok 15251 Mar 15  2014 options-permalink.php
-rw-rw-r-- 1 erok erok 10439 Aug 26  2014 options.php
-rw-rw-r-- 1 erok erok  9352 Mar  8  2014 options-reading.php
-rw-rw-r-- 1 erok erok  9876 Apr 12  2014 options-writing.php
-rw-rw-r-- 1 erok erok 11402 May  6  2014 plugin-editor.php
-rw-rw-r-- 1 erok erok  4513 Aug 27  2014 plugin-install.php
-rw-rw-r-- 1 erok erok 19763 May 31  2014 plugins.php
-rw-rw-r-- 1 erok erok  2458 Jul 25  2014 post-new.php
-rw-rw-r-- 1 erok erok  8856 Aug 22  2014 post.php
-rw-rw-r-- 1 erok erok 26776 Aug  1  2014 press-this.php
-rw-rw-r-- 1 erok erok   296 Sep 25  2013 profile.php
-rw-rw-r-- 1 erok erok  8321 May 19  2014 revision.php
-rw-rw-r-- 1 erok erok 13054 Sep  4  2014 setup-config.php
-rw-rw-r-- 1 erok erok 10192 Jul 17  2014 theme-editor.php
-rw-rw-r-- 1 erok erok 11080 Aug 27  2014 theme-install.php
-rw-rw-r-- 1 erok erok 16570 Aug 25  2014 themes.php
-rw-rw-r-- 1 erok erok  4167 Mar  8  2014 tools.php
-rw-rw-r-- 1 erok erok 27572 Aug 16  2014 update-core.php
-rw-rw-r-- 1 erok erok 10163 Aug 27  2014 update.php
-rw-rw-r-- 1 erok erok   338 Dec 24  2013 upgrade-functions.php
-rw-rw-r-- 1 erok erok  4198 Jun 29  2014 upgrade.php
-rw-rw-r-- 1 erok erok 12005 Aug 28  2014 upload.php
drwxrwxr-x 2 erok erok  4096 Sep  4  2014 user
-rw-rw-r-- 1 erok erok 21788 Jul  8  2014 user-edit.php
-rw-rw-r-- 1 erok erok 18757 Jul 18  2014 user-new.php
-rw-rw-r-- 1 erok erok 15932 Sep  4  2014 users.php
-rw-rw-r-- 1 erok erok 15687 Jul 17  2014 widgets.php
erok@eriks-dator:/$
```

Or this?

```
erok@eriks-dator:/$ sudo ls -l /usr/share/wordpress/wp-admin
total 876
-rw-r--r-- 1 www-data www-data  9931 Nov 22  2014 about.php
-rw-r--r-- 1 www-data www-data  3280 Apr  9  2014 admin-ajax.php
-rw-r--r-- 1 www-data www-data  2143 Apr  9  2014 admin-footer.php
-rw-r--r-- 1 www-data www-data   401 Apr  9  2014 admin-functions.php
-rw-r--r-- 1 www-data www-data  6585 Apr  9  2014 admin-header.php
-rw-r--r-- 1 www-data www-data 10399 Apr  9  2014 admin.php
-rw-r--r-- 1 www-data www-data  1045 Apr  9  2014 admin-post.php
-rw-r--r-- 1 www-data www-data  4003 Apr  9  2014 async-upload.php
-rw-r--r-- 1 www-data www-data  9190 Apr  9  2014 comment.php
-rw-r--r-- 1 www-data www-data  6763 Apr  9  2014 credits.php
drwxr-xr-x 3 www-data www-data  4096 Jul  9 14:47 css
-rw-r--r-- 1 www-data www-data 15966 Apr  9  2014 custom-background.php
-rw-r--r-- 1 www-data www-data 35468 Apr  9  2014 custom-header.php
-rw-r--r-- 1 www-data www-data  7902 Apr  9  2014 customize.php
-rw-r--r-- 1 www-data www-data 11651 Apr  9  2014 edit-comments.php
-rw-r--r-- 1 www-data www-data 28424 Apr  9  2014 edit-form-advanced.php
-rw-r--r-- 1 www-data www-data  6400 Apr  9  2014 edit-form-comment.php
-rw-r--r-- 1 www-data www-data  6008 Apr  9  2014 edit-link-form.php
-rw-r--r-- 1 www-data www-data 14309 Apr  9  2014 edit.php
-rw-r--r-- 1 www-data www-data  4218 Apr  9  2014 edit-tag-form.php
-rw-r--r-- 1 www-data www-data 20303 Apr  9  2014 edit-tags.php
-rw-r--r-- 1 www-data www-data  8331 Apr  9  2014 export.php
-rw-r--r-- 1 www-data www-data  3348 Apr  9  2014 freedoms.php
drwxr-xr-x 2 www-data www-data  4096 Jul  9 14:47 images
-rw-r--r-- 1 www-data www-data  5318 Apr  9  2014 import.php
drwxr-xr-x 2 www-data www-data  4096 Jul  9 14:47 includes
-rw-r--r-- 1 www-data www-data  5980 Apr  9  2014 index.php
-rw-r--r-- 1 www-data www-data  5590 Apr  9  2014 install-helper.php
-rw-r--r-- 1 www-data www-data 10752 Nov 22  2014 install.php
drwxr-xr-x 2 www-data www-data  4096 Jul  9 14:47 js
-rw-r--r-- 1 www-data www-data   712 Apr  9  2014 link-add.php
-rw-r--r-- 1 www-data www-data  3467 Apr  9  2014 link-manager.php
-rw-r--r-- 1 www-data www-data  2482 Apr  9  2014 link-parse-opml.php
-rw-r--r-- 1 www-data www-data  2649 Apr  9  2014 link.php
-rw-r--r-- 1 www-data www-data  2859 Apr  9  2014 load-scripts.php
-rw-r--r-- 1 www-data www-data  3172 Apr  9  2014 load-styles.php
drwxr-xr-x 2 www-data www-data  4096 Jul  9 14:47 maint
-rw-r--r-- 1 www-data www-data  3136 Apr  9  2014 media-new.php
-rw-r--r-- 1 www-data www-data  5240 Apr  9  2014 media.php
-rw-r--r-- 1 www-data www-data  1750 Apr  9  2014 media-upload.php
-rw-r--r-- 1 www-data www-data  7533 Apr  9  2014 menu-header.php
-rw-r--r-- 1 www-data www-data 12452 Apr  9  2014 menu.php
-rw-r--r-- 1 www-data www-data   320 Apr  9  2014 moderation.php
-rw-r--r-- 1 www-data www-data   211 Apr  9  2014 ms-admin.php
-rw-r--r-- 1 www-data www-data  3669 Apr  9  2014 ms-delete-site.php
-rw-r--r-- 1 www-data www-data   231 Apr  9  2014 ms-edit.php
-rw-r--r-- 1 www-data www-data   236 Apr  9  2014 ms-options.php
-rw-r--r-- 1 www-data www-data   228 Apr  9  2014 ms-sites.php
-rw-r--r-- 1 www-data www-data   230 Apr  9  2014 ms-themes.php
-rw-r--r-- 1 www-data www-data   232 Apr  9  2014 ms-upgrade-network.php
-rw-r--r-- 1 www-data www-data   228 Apr  9  2014 ms-users.php
-rw-r--r-- 1 www-data www-data  4701 Apr  9  2014 my-sites.php
-rw-r--r-- 1 www-data www-data 38451 Apr  9  2014 nav-menus.php
drwxr-xr-x 2 www-data www-data  4096 Jul  9 14:47 network
-rw-r--r-- 1 www-data www-data 26009 Nov 22  2014 network.php
-rw-r--r-- 1 www-data www-data 13786 Apr  9  2014 options-discussion.php
-rw-r--r-- 1 www-data www-data 13420 Apr  9  2014 options-general.php
-rw-r--r-- 1 www-data www-data   492 Apr  9  2014 options-head.php
-rw-r--r-- 1 www-data www-data  5895 Apr  9  2014 options-media.php
-rw-r--r-- 1 www-data www-data 14889 Apr  9  2014 options-permalink.php
-rw-r--r-- 1 www-data www-data 10122 Apr  9  2014 options.php
-rw-r--r-- 1 www-data www-data  9416 Apr  9  2014 options-reading.php
-rw-r--r-- 1 www-data www-data  9957 Apr  9  2014 options-writing.php
-rw-r--r-- 1 www-data www-data 11146 Apr  9  2014 plugin-editor.php
-rw-r--r-- 1 www-data www-data  4099 Apr  9  2014 plugin-install.php
-rw-r--r-- 1 www-data www-data 19571 Apr  9  2014 plugins.php
-rw-r--r-- 1 www-data www-data  2067 Apr  9  2014 post-new.php
-rw-r--r-- 1 www-data www-data  8842 Apr  9  2014 post.php
-rw-r--r-- 1 www-data www-data 26430 Nov 22  2014 press-this.php
-rw-r--r-- 1 www-data www-data   296 Apr  9  2014 profile.php
-rw-r--r-- 1 www-data www-data  8131 Apr  9  2014 revision.php
-rw-r--r-- 1 www-data www-data 12056 Apr  9  2014 setup-config.php
-rw-r--r-- 1 www-data www-data 10206 Apr  9  2014 theme-editor.php
-rw-r--r-- 1 www-data www-data  4435 Apr  9  2014 theme-install.php
-rw-r--r-- 1 www-data www-data 16277 Apr  9  2014 themes.php
-rw-r--r-- 1 www-data www-data  4166 Apr  9  2014 tools.php
-rw-r--r-- 1 www-data www-data 27172 Apr  9  2014 update-core.php
-rw-r--r-- 1 www-data www-data  9996 Apr  9  2014 update.php
-rw-r--r-- 1 www-data www-data   336 Apr  9  2014 upgrade-functions.php
-rw-r--r-- 1 www-data www-data  4183 Apr  9  2014 upgrade.php
-rw-r--r-- 1 www-data www-data  9577 Apr  9  2014 upload.php
drwxr-xr-x 2 www-data www-data  4096 Jul  9 14:47 user
-rw-r--r-- 1 www-data www-data 21827 Apr  9  2014 user-edit.php
-rw-r--r-- 1 www-data www-data 18123 Apr  9  2014 user-new.php
-rw-r--r-- 1 www-data www-data 15691 Apr  9  2014 users.php
-rw-r--r-- 1 www-data www-data 15680 Apr  9  2014 widgets.php
erok@eriks-dator:/$ 


```

---

### Post by CharlesA on 2015-07-18
The permissions look ok, but how did you install wordpress? If it is in /usr/share it usually means it was installed via a package management tool.

Can you check the web server's error logs to see what the specific error is?

---

### Post by erok2 on 2015-07-18
**CharlesA wote:**
```
The permissions look ok, but how did you install wordpress? If it  is in /usr/share it usually means it was installed via a package  management tool.

Can you check the web server's error logs to see what the specific error is?
```

I did downloaded latest wordpress and unzipped to my home folder and then I followed instructions from some website I found.


I hope you mean any of these error-(logs) ??

```

erok@eriks-dator:/var/log$ sudo tail -f /var/log/apache2/error.log
[Sat Jul 18 11:32:34.198826 2015] [mpm_event:notice] [pid 25991:tid 140285372008320] AH00491: caught SIGTERM, shutting down
[Sat Jul 18 11:32:35.273320 2015] [mpm_event:notice] [pid 27001:tid 139860122376064] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Sat Jul 18 11:32:35.273414 2015] [core:notice] [pid 27001:tid 139860122376064] AH00094: Command line: '/usr/sbin/apache2'
[Sat Jul 18 11:32:49.906896 2015] [authz_core:error] [pid 27005:tid 139860038317824] [client 127.0.0.1:35739] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php
[Sat Jul 18 11:32:51.527038 2015] [authz_core:error] [pid 27005:tid 139860029925120] [client 127.0.0.1:35739] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php
[Sat Jul 18 11:35:34.991838 2015] [authz_core:error] [pid 27005:tid 139860021532416] [client 127.0.0.1:35744] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php
[Sat Jul 18 11:37:08.486361 2015] [authz_core:error] [pid 27005:tid 139860013139712] [client 127.0.0.1:35749] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php
[Sat Jul 18 11:37:09.935548 2015] [authz_core:error] [pid 27005:tid 139860004747008] [client 127.0.0.1:35749] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php
[Sat Jul 18 11:37:24.643216 2015] [authz_core:error] [pid 27005:tid 139859996354304] [client 127.0.0.1:35750] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php
[Sat Jul 18 11:37:38.272044 2015] [authz_core:error] [pid 27004:tid 139860038317824] [client 127.0.0.1:35751] AH01630: client denied by server configuration: /var/www/wordpress/wp-admin/setup-config.php

```

```

erok@eriks-dator:/$ sudo tail -f /var/log/apache2/access.log
127.0.0.1 - - [18/Jul/2015:11:32:07 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 527 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:32:08 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 526 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:32:13 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 526 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:32:49 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 527 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:32:51 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 526 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:35:34 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 527 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:37:08 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 527 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:37:09 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 526 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:37:24 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 527 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"
127.0.0.1 - - [18/Jul/2015:11:37:38 +0200] "GET /wordpress/wp-admin/setup-config.php HTTP/1.1" 403 527 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0"

```

```

empty mysql.error file??
erok@eriks-dator:/var/log$ sudo tail -f mysql.err


```


```

empty mysql.log file??
erok@eriks-dator:/var/log$ sudo tail -f mysql.log


```

---

### Post by CharlesA on 2015-07-18
Ok, so it is an issue with the web server configuration, not the file permissions.

Did you create a separate virtualhost for wordpress?

---

### Post by erok2 on 2015-07-18
**CharlesA wrote:**
```
Ok, so it is an issue with the web server configuration, not the file permissions.

Did you create a separate virtualhost for wordpress?
```

OK, I followed some link I found, downloaded wordpress and unzipped it to my home directory and then  I installed and configured only mysql and apache2, so I don't think so?

I wanted it locally on my computer only

---

### Post by CharlesA on 2015-07-18
Something isn't set up right. What link did you use?

I found this one and it seems decent, but I haven't bothered with wordpress myself.
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04)

---

### Post by erok2 on 2015-07-18
Ok, shall I start over from start and try again?
with these codes, perhaps? and  try with your link

```

sudo apt-get remove --purge apache2

```

and

```

sudo apt-get remove --purge mysql-server

```

---

### Post by CharlesA on 2015-07-18
You might have to purge some more packages than those, but it is a start.

---

### Post by erok2 on 2015-07-19
After that changes "/etc/apache2/apache2.conf" file to this

```

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

#<Directory /var/www/>
#        Options Indexes FollowSymLinks
#        AllowOverride None
#        Order allow,deny
#        allow from all
#</Directory>

```

And with the command on firefox
```

http://localhost/wordpress/wp-admin/setup-config.php

```


I get this (picture), but I don't know what to try next time for resolve this problem??

[IMG][[IMG]http://i794.photobucket.com/albums/yy222/erland100/lockalhost.png[/IMG]]("http://s794.photobucket.com/user/erland100/media/lockalhost.png.html")[/IMG]

---

### Post by CharlesA on 2015-07-19
You need to create and populate the database before you can do the install.

The digital ocean howto should have had the steps required.

---

### Post by erok2 on 2015-07-19
**CharlesA wrote:**
```
You need to create and populate the database before you can do the install.

The digital ocean howto should have had the steps required.
```

Can't create database 'wordpress'; database exists

```
 erok@eriks-dator:/$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 55
Server version: 5.5.43-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CREATE DATABASE wordpress;
ERROR 1007 (HY000): Can't create database 'wordpress'; database exists
mysql> 

```

Shall I purge mysql? if it is the best way?
Or create a new database with other name?

```
sudo apt-get remove --purge mysql-server
 
```

---

### Post by CharlesA on 2015-07-19
Easier way is to login to mysql as root and run this:

```
mysql -u root -p
```

```
drop database wordpress;
```

---

### Post by erok2 on 2015-07-19
**ChalesA wrote:**

```

Easier way is to login to mysql as root and run this:
mysql -u root -p
drop database wordpress; 

```

I had "drop" database and the user, created those again, but no change (same picture come up) when I try to setup with this command on firefox
```

http://localhost/wordpress/wp-admin/setup-config.php

```

I'm completely stuck on  this problem, I hope you have more ideas I can try? or can it be a bug?

---

### Post by CharlesA on 2015-07-20
I really don't know. I've never seen a screen like that before.

If the database is gone and it is still doing it. Maybe you can download wordpress again and see if it still happens.

Also, out of curiosity, do you get anything when you run this:
```
dpkg -l | grep wordpress
```

---

### Post by erok2 on 2015-07-20
**CharlesA wrote:**
```

Also, out of curiosity, do you get anything when you run this:

dpkg -l | grep wordpress

```

```

erok@eriks-dator:/$ dpkg -l | grep wordpress
ii  wordpress                                             3.8.2+dfsg-1ubuntu0.1                               all          weblog manager
ii  wordpress-l10n                                        3.8.2+dfsg-1ubuntu0.1                               all          weblog manager - language files
ii  wordpress-theme-twentyfourteen                        3.8.2+dfsg-1ubuntu0.1                               all          weblog manager - twentyfourteen theme files
ii  wordpress-theme-twentytwelve                          3.8.2+dfsg-1ubuntu0.1                               all          weblog manager - twentyttwelve theme filess
erok@eriks-dator:/$ 

```

Maybe shall I purge everything, how does to do it?
This is perhaps is not enough?

```

sudo apt-get remove --purge mysql-server mysql-client mysql-common
sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -rf /var/lib/mysql
sudo rm -rf /etc/mysql

```

---

### Post by CharlesA on 2015-07-20
If you have been downloading wordpress, you can remove the version that was installed with apt-get.

```
sudo apt-get purge wordpress
```
```
sudo apt-get autoremove
```

That is probably the cause of the problem.

---

### Post by erok2 on 2015-07-21
Ok, I have "purged" everything and install wordpress again, but have a same problem, in firefox after following code:

```

http://localhost/wordpress/wp-admin/setup-config.php

```


"wp-config.php" location on my hard drive:

```

/var/www 

/home/erok/wordpress

/usr/share/wordpress

/opt/lampp/htdocs

/opt/lampp/htdocs/wordpress

```


This happens in firefox then
See the screen dump below, delete wp-config.php, but where?

[[IMG]http://i794.photobucket.com/albums/yy222/erland100/setup_config_php_1.png[/IMG]]("http://s794.photobucket.com/user/erland100/media/setup_config_php_1.png.html")

---

### Post by CharlesA on 2015-07-21
Good question.

Was this an existing install or could you wipe it and install from scratch?

It looks like you tried to install wordpress a few different ways and I don't know if they are conflicting or what the deal is.

---

### Post by erok2 on 2015-07-21
[B]CharlesA wrote:
> It looks like you tried to install wordpress a few different ways and I don't know if they are conflicting or what the deal is.[/B]


I have followed this link below

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)


And I also downloaded the latest wordpress and followed some lines in beginning from this link below:

[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04)


probably this that has created the problem, right? and seems I really do not know what I had done?

---

### Post by CharlesA on 2015-07-21
> **erok2 said:**
> [B]CharlesA wrote:
[/B]


I have followed this link below

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)


And I also downloaded the latest wordpress and followed some lines in beginning from this link below:

[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04)


probably this that has created the problem, right? and seems I really do not know what I had done?

Yeah, it looks like you tried to install the version of wordpress that is in the Ubuntu repos as well as install it manually, so it's all messed up.

If you want to keep using the version you installed from the repos, you would need to work with the files in /usr/share/wordpress

With that said, I tend to do manual installs of web applications since the versions in the ubuntu repo (if they exist) could be out of date.

It is up to you though.

---

### Post by erok2 on 2015-07-22
Ok,  I "purged" wordpress and mysql and followed this link now:

I have Ubuntu 14.04 LTS

[URL="https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04"]https://www.digitalocean.com/communi...n-ubuntu-12-04

[/URL]

but when everything are finished, and tried this in firefox.

```

http://localhost/wordperss/wp-admin/setup-config.php

```

I get this "403 Forbidden" again

**Forbidden**

 You don't have permission to access /wordperss/wp-admin/setup-config.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80


This command gets:

```

erok@eriks-dator:/$ ls -l /var/www
total 216
drwx-w----  5 erok www-data  4096 Jul 19 16:39 html
-rw-rw-r--  1 erok www-data   418 Sep 25  2013 index.php
-rw-rw-r--  1 erok www-data    87 Oct 27  2013 info.php
-rw-rw-r--  1 erok www-data 19930 Apr  9  2014 license.txt
-rw-rw-r--  1 erok www-data 14280 Sep  4  2014 licens-sv_SE.txt
lrwxrwxrwx  1 erok www-data    21 Oct 27  2013 phpMyAdmin -> /usr/share/phpmyadmin
-rw-rw-r--  1 erok www-data  9893 Sep  4  2014 readme.html
lrwxrwxrwx  1 erok www-data    20 Oct 27  2013 wordpress -> /usr/share/wordpress
-rw-rw-r--  1 erok www-data  4951 Aug 20  2014 wp-activate.php
drwxrwxr-x  9 erok www-data  4096 Sep  4  2014 wp-admin
-rw-rw-r--  1 erok www-data   271 Jan  8  2012 wp-blog-header.php
-rw-rw-r--  1 erok www-data  4946 Jun  5  2014 wp-comments-post.php
-rw-rw-r--  1 erok www-data  2742 Jul 22 10:45 wp-config.php
-rw-rw-r--  1 erok www-data  3342 Jul 21 05:48 wp-config.php~
-rw-rw-r--  1 erok www-data  2998 Jul 21 05:49 wp-config.php.bak
-rw-rw-r--  1 erok www-data  2788 Sep  4  2014 wp-config-sample.php
drwxrwxr-x  8 erok www-data  4096 Sep  4  2014 wp-content
-rw-rw-r--  1 erok www-data  2956 May 13  2014 wp-cron.php
drwxrwx--- 12 erok www-data  4096 Sep  4  2014 wp-includes
-rw-rw-r--  1 erok www-data  2380 Oct 24  2013 wp-links-opml.php
-rw-rw-r--  1 erok www-data  2714 Jul  7  2014 wp-load.php
-rw-rw-r--  1 erok www-data 33043 Aug 27  2014 wp-login.php
-rw-rw-r--  1 erok www-data  8252 Jul 17  2014 wp-mail.php
-rw-rw-r--  1 erok www-data 11115 Jul 18  2014 wp-settings.php
-rw-rw-r--  1 erok www-data 26256 Jul 17  2014 wp-signup.php
-rw-rw-r--  1 erok www-data  4026 Oct 24  2013 wp-trackback.php
-rw-rw-r--  1 erok www-data  3032 Feb  9  2014 xmlrpc.php
erok@eriks-dator:

```

And this command gave nothing now:

```

erok@eriks-dator:~$ dpkg -l | grep wordpress
erok@eriks-dator:~$

```


Phuu, but why, what did I do wrong this time?

---

### Post by CharlesA on 2015-07-22
What does the apache log say this time?

The default web root for Apache 2.4 is /var/www/html if I am not mistaken.

The digital ocean howto did not mention creating your own Apache virtualhost to handle Wordpress but it is based off of Apache 2.2, and there have been some changes since then.

---

### Post by erok2 on 2015-07-22
Root permission and "/var/www/html" directory, looks like this

```

root@eriks-dator:/var/www/html# ls
index.php         wordpress           wp-comments-post.php  wp-content         wp-load.php      wp-signup.php
license.txt       wp-activate.php     wp-config.php         wp-cron.php        wp-login.php     wp-trackback.php
licens-sv_SE.txt  wp-admin            wp-config.php~        wp-includes        wp-mail.php      xmlrpc.php
readme.html       wp-blog-header.php  wp-config-sample.php  wp-links-opml.php  wp-settings.php
root@eriks-dator:/var/www/html# 

```


Do you mean "wp-config.php"? which is same on my home directory, like this


```

 GNU nano 2.2.6                                  File: wp-config.php                                                                           

<?php

// ** MySQL-inst&#65533;llningar - MySQL-uppgifter f&#65533;r du fr&#65533;n ditt webbhotell ** //
/** Namnet p&#65533; databasen du vill anv&#65533;nda f&#65533;r WordPress */
define('DB_NAME', 'wordpress');

/** MySQL-databasens anv&#65533;ndarnamn */
define('DB_USER', 'erok');

/** MySQL-databasens l&#65533;senord */
define('DB_PASSWORD', 'my password');

/** MySQL-server */
define('DB_HOST', 'localhost');

/** Teckenkodning f&#65533;r tabellerna i databasen. */
define('DB_CHARSET', 'utf8');

/** Kollationeringstyp f&#65533;r databasen. &#65533;ndra inte om du &#65533;r os&#65533;ker. */
define('DB_COLLATE', '');

/**#@+


```

I don&#8217;t know if you meant some of this above? and what shall I to do next??

---

### Post by erok2 on 2015-07-22
Now it works with "wordpress" locally on my computer, it was difficult problem to get it work with 14.04 LTS ! - I started over again and "purged" everything again and then followed this link

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

And the finally "fix" was this:

> To install PHP and PHP support for Apache, just write the following in console:




```

$>sudo apt-get install php5 libapache2-mod-php5



```

**Thanks for taking your time to help me "CharlesA"!**

---

### Post by CharlesA on 2015-07-22
Glad you were able to get it working.

I'm surprised it didn't throw more errors that actually related to PHP instead of the access forbidden message.

At least it is fixed. :)

---

