---
title: "More Apache+PHP problems"
date: 2005-11-10
forum: Server Platforms
---

### Post by ceph_systems on 2005-11-10
I've seen this problem numerous times in various threads and spent an entire night going through and trying everything under the sun(the moon, literally the whole night) contained in them but to no avail.  

Problem:
I've installed the LAMP architecture but I can't open a .php file in a browser without getting a download window popping up.  

I checked all the config files and even reinstalled Apache2/PHP5  An important fact is that once upon a time I had Apache1.3.  

Data:

I have installed:

apache2-server, 
apache2-common
apache2-utils
libapache2-mod-php5
php5
php5-common 

APACHE2:  
httpd.conf-->everything commented out
apache2.conf-->DirectoryIndex directive contains index.html and index.php
        -->AddType directive has application/x-httpd-php .php and
                                                 application/x-httpd-php-source .phps 
mods-enabled--> contains sym links to php5.conf and php5.load in mods-available.
mods-available/php5.load points where it should  i.e. /usr/lib/apache2/modules/libphp5.so

After reinstalling php5, I sudoed a2enmod php5 and restarted the server.

if I try opening a test file, [http://localhost/test.php](http://localhost/test.php), which is sits in /var/www or anywhere else, with permissions fully set (chmod 777 test.php) I still get the download window.

Please help!  Thanks in advance.

---

### Post by mcewen98 on 2005-11-10
I'm not sure if this makes a difference, but you may want to check /etc/mime.types and make sure that the x-httpd-php lines are not commented out.  Maybe try running  'a2enmod include' too?

---

### Post by LordHunter317 on 2005-11-10
First, fix your permissions.  That file should be 644 at most.  Don't do anything util you fix it.

Did you clear your browser cache and press 'F5' to force a reload of the page?

---

### Post by ceph_systems on 2005-11-10
Hello again,

I've tried both people's suggestion and still no luck.....the mime types are already uncommented and also I changed the permissions to 644 and cleared the cache and reloaded the page.  

Any other ideas?
Thanks!

---

### Post by dbee on 2005-11-10
You might want to try just putting your .so file in httpd.conf and see if that works
```

LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

```
... never mind about the mods_enabled bit.

---

### Post by LordHunter317 on 2005-11-11
No, it's doubtful that's it.   I'd be interested in seeing a tcpdump of the output, as lots of people are having this issue.  I'm wondering if it's locale related.

---

### Post by MatthewMetzger on 2005-11-11
Hello, I'm having the same problem. Completely fresh install as I want to use Ubuntu on Mac for a local intranet server. I followed the directions exactly as they appeared in ubuntuguide.org (I also have done this before and know mostly what I'm doing), but with the same results. Any .php file I try to view ([http://localhost/testphp.php](http://localhost/testphp.php)) just pops up a download window instead of viewing the file.

Any help would be greatly appreciated. I'm in the United States, running the very latest Ubuntu for mac on a G3 tower.

---

### Post by joselin on 2005-11-11
Same problem here, but with a little difference. I can open lots of php files, but some specific ones pops up the download window. And, of course, perms are right for all the files, and rights are the same for all of them, and there isn't .htaccess or something like this.

Regards,
Jose

---

### Post by MatthewMetzger on 2005-11-11
I figured out a solution for me, that may work for others having this problem.

It only worked for me once I installed libapache2-mod-php4. My guess is that most people have the trouble php files not parsing in apache is that they need to install this package.

Also, make sure that these two lines are uncommented in your apache2.conf file:

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

---

### Post by joselin on 2005-11-11
[QUOTE=MatthewMetzger]I figured out a solution for me, that may work for others having this problem.

It only worked for me once I installed libapache2-mod-php4. My guess is that most people have the trouble php files not parsing in apache is that they need to install this package.

Also, make sure that these two lines are uncommented in your apache2.conf file:

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps[/QUOTE]

Does not work for me. I have this package instaled and neither if i comment or uncoment this two lines, the server do the same.

Regards.

---

### Post by SuperMike on 2005-11-25
You weren't having a problem with your libapache2-mod-php(x) file, were you? I was. I think there's a bug. I finally got it to work after multiple attempts to uninstall and reinstall. Here's my story and I hope it helps...

I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue. The net effect of this is that even though you have installed Apache2, PHP(x), and libapache2-mod-php(x), and have cleared your Firefox cache, you find that Firefox still asks you what to do with the PHP file, instead of Apache2 pre-processing it at the server. This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 framework -- even though you can clearly see the various .conf files are properly updated and the libphp(x).so file is in the proper place.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced. Just upgrade from Hoary (with a loaded PHP4 install) to Breezy, and then uninstall completely the PHP4 and/or PHP5. Then, reboot. Then, try to install PHP4 again with Universe option enabled. Or, for that matter, try on a separate PC to install PHP5 again. Both PHP4 and PHP5 will intermittently have the same issue of not compiling the libapache2-mod-php(x) file properly.

I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.

P.S. There's been some discussion about uncommenting some Mime type info in the /etc/apache2/apache2.conf file. You don't have to do that. Here's the real story...

If the Mime type is not uncommented in the apache2.conf file, there's another way to make the conf file look in another directory for adding extra stuff. You'll find the uncommented version in:

/etc/apache2/mods-enabled/php4.conf

or

php5.conf in the same dir.

The installer is supposed to do this for you. However, like I said, it only intermittently compiles the libphp4.so or libphp5.so file (libapache2-mod-php(x)) properly -- you have to fight with the process of uninstallation and reinstallation, along with reboots, until it finally just "takes".

---

