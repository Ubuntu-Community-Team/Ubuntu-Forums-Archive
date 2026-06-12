---
title: "php pages load slow or not at all..."
date: 2008-06-18
forum: Server Platforms
---

### Post by sbinkerd1 on 2008-06-18
I copied my joomla site from a WIN XP system running Apache 1.3.3 and PHP 4.1. after changing the configuration.php file to reflect the correct file structure, it seems to want to load, but just sits there churning the "wheel".

I get no errors, and the browser acts like it is downloading the site. this can go on forever with no output to the browser.

If I try to go to the administrator backend of joomla, it will bring up the log in page perfect (this is in HTML). When I log in, it will eventually (after 15-20 minutes) show some of the amdin area, although not all the images load.

I tried a fully HTML site with no PHP and it loads fine, so obviously this is a php problem, but since I am getting no errors I have no clue where to start to rectify the EXTREMELY SLOW loading of the site.

Obviously I am running a lamp server on the latestest distro of Ubuntu server (hardy). all the software is new as of 2 days ago.

any help is greatly appreciated.

---

### Post by hyper_ch on 2008-06-18
make a simple
```

<php phpinfo(); ?>

```
and call that... how long does that take to load?

---

### Post by sbinkerd1 on 2008-06-18
hey thanks for the help!

I tried a simple hello world echo and your code also. both seem to load fine and in a split second. 

I guess it must be the joomla site then. something it doesn't like about coming from a windows apache and php setup.

I don't want to have to rebuild the site, but if I have to I have to.

any experience with moving joomla from windows to linux?

---

### Post by sbinkerd1 on 2008-06-18
I did find this in the apache error logs:

PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\\PHP/php_mysql.dll'

it appears that it is looking in C:\\. probably because this install of joomla came from a windows apache server. I need to find out where it is calling that from and change it to the correct directory.

any ideas before I stumble on?

---

### Post by hyper_ch on 2008-06-19
you did copy the apache conf from your windows installation?

---

### Post by mbeach on 2008-06-21
I forget exactly how joomla's file structure works (it's been a long time) you might want to go to the root of it in a terminal, and type:
```
grep -i -R c:\\\\php *
```
which should list the files which have c:\php in them - might be a place to start.  

quick references:
[http://gimbo.org.uk/blog/2008/01/23/the-great-escape/](http://gimbo.org.uk/blog/2008/01/23/the-great-escape/)

---

### Post by mbeach on 2008-06-21
or more cleanly:
```
grep -iFR 'c:\Php' *
```

---

### Post by sbinkerd1 on 2008-06-23
got it work now. I had some file permissions messed up for specific files related to joomla, and then had to redirect the configuration file to my current file structure rather than the windows file structure. all is good, except now I have to do that for all my sites...

---

### Post by molotov00 on 2008-06-23
I had a problem today with non-loading PHP pages when I moved a site. Turned out to be a bad mod_rewrite directive.

I agree that you should check for c:\php in your joomla files but if it's written correctly it shouldn't store that stuff in php files.

In addition, check your .htaccess and apache configuration files. (.htacces in particular and check for absolute paths that are no longer correct)

---

