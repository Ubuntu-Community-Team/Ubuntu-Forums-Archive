---
title: "PHP files are prompt for download..."
date: 2008-09-22
forum: Server Platforms
---

### Post by fistuks on 2008-09-22
Hey,

I've set up lamp on my hardy desktop.
all works great beside the fact that when ever i try to reach a php that's on the server, the browser (any browser on any os/computer) prompt for download the file and ask for appropriate app to run it.

any clues?...

---

### Post by cb951303 on 2008-09-22
is php module for apache installed correctly?

---

### Post by mbeach on 2008-09-22
from the command line, post the output of:
```
a2enmod php5
```

---

### Post by hyper_ch on 2008-09-22
and prepend the command given by mbeach with "sudo"

---

### Post by mbeach on 2008-09-22
whoops.  thanks for the review!!  this forum is great.

---

### Post by ene_dene on 2008-11-18
I have the same problem, I don't know was it the LAMP or something else, but my php5 is not working:
```
sudo a2enmod php5
```
gives:
```
This module does not exist!
```
I've tried removing apache and php by:
```
sudo aptitude --purge remove apache2 libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php5-imagick php5-mcrypt php5-memcache php5-mhash php5-mysql php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl
```
And then reinstalling them all, but it didn't work.
Is there a solution to this?

---

### Post by hyper_ch on 2008-11-18
you also need to install the php5 module for apache2:

```

libapache2-mod-php5

```

---

### Post by cb951303 on 2008-11-18
best way to install LAMP is ```

sudo tasksel install lamp-server
```

---

### Post by ene_dene on 2008-11-18
> **hyper_ch said:**
> you also need to install the php5 module for apache2:

```

libapache2-mod-php5

```
I have that installed but it's not working.

---

### Post by cb951303 on 2008-11-18
> **ene_dene said:**
> I have that installed but it's not working.

did you do ```
 sudo a2enmod php5 
``` again after reinstalling?

---

### Post by ene_dene on 2008-11-18
> **cb951303 said:**
> did you do ```
 sudo a2enmod php5 
``` again after reinstalling?
Yes, I had that installed all the time.
Now I've removed it, and wanted to install it again and here is one interesting msg:
```

Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.3) ...
Not replacing deleted config file /etc/php5/apache2/php.ini

```
I haven't been deleting anything. I was trying before reinstalling everything, so after I removed apache and php, I also deleted the directories. And then the fresh install, but I only did that because it said that no php5 module was installed.

---

### Post by ene_dene on 2008-11-18
This is quite frustrating, I tried removing, than installing again, nothing works.
Could someone give me instructions how to clean it all, step by step, and then install apache and php5. The only program that could be making the problems is webmin, although I don't know how,I'll remove that one too.

---

### Post by ene_dene on 2008-11-18
I've succeeded in making the module work, by removing every component instead:
```
sudo aptitude --purge remove xxx
```
by
```
 sudo apt-get remove --purge xxx
```
Now I get:
```
 sudo a2enmod php5
This module is already enabled!

```
But now I have another problem, when trying to open file from server with firefox (I've cleaned cache), it want's to download php file, it's not run on server. How do I solve that?

---

### Post by ene_dene on 2008-11-18
I'm really sorry about spam but it was a little crazzy. It works now, apparently it was some kind of firefox problem, php worked fine after apt-get remove --purge, and reinstall.

---

### Post by hyper_ch on 2008-11-18
after enabling php on apache you need to restart apache

---

### Post by ene_dene on 2008-11-18
> **hyper_ch said:**
> after enabling php on apache you need to restart apache
I did that, works fine now. Thank you.

---

### Post by kracekumar on 2010-01-18
i ve installed lamp,and tried sudo php5 also it shows php is enabled already,but when i tried to open php still firefox propmptd download option and i ve cleared cache too.

---

### Post by ene_dene on 2010-01-18
> **kracekumar said:**
> i ve installed lamp,and tried sudo php5 also it shows php is enabled already,but when i tried to open php still firefox propmptd download option and i ve cleared cache too.
Try:
```
sudo /etc/init.d/apache2 restart
```
And then refresh in firefox.

---

### Post by xbyte1024 on 2010-12-05
Worked for me in ubuntu 10.10
Cleaning cache is important as I concluded :p

---

### Post by varom on 2011-01-02
Thanks for this thread,

that has been a long journey to work it out !!! if you all install in correct way and still firefox wants to safe default.php, just  [COLOR=Red]**cleaning**[/COLOR] firefox cache is clue. Thats weird.

---

### Post by jaesun on 2011-11-30
Sorry to resurrect this thread, but I am having this problem.  

I installed Ubuntu 10.10 Server 64-bit, barebones install, using a Virtual Machine (VirtualBox).

Installed lamp server via:
```
sudo tasksel install lamp-server
```

I then setup apache2 VirtualDirectories (apache2/sites-available, etc).  I do have /home/.../public_html/ as a symbolic link to a networked computer.

I disabled php5 via (just to be sure):
```
sudo a2dismod php5
sudo apache2 restart
```

Then re-enabled php:
```
sudo a2enmod php5
sudo apache2 restart
```

Cleared the cache in both firefox, IE, and Chrome.

I still get the php download prompt.  What gives?  

I added in apache2.conf (even tried httpd.conf):
```
<FilesMatch \.php$>
    SetHandler application/x-httpd-php
</FilesMatch>
```

Not sure what I am missing here.  I can view html files just fine, and I can view the php via CLI (php /public_html/test.php)

---

### Post by SeijiSensei on 2011-12-01
Make sure the **libapache2-mod-php5** package is installed.  It adds the needed FilesMatch directives to the Apache configuration.  This problem seems to crop up here recently.  I've browsed launchpad and see similar bugs reported in earlier Ubuntu versions where this package was not correctly installed, but the developers seem to think the bugs have been quashed.  I'm not so sure myself.

---

### Post by jaesun on 2011-12-01
> **SeijiSensei said:**
> Make sure the **libapache2-mod-php5** package is installed.  It adds the needed FilesMatch directives to the Apache configuration.  This problem seems to crop up here recently.  I've browsed launchpad and see similar bugs reported in earlier Ubuntu versions where this package was not correctly installed, but the developers seem to think the bugs have been quashed.  I'm not so sure myself.

I did a sudo apt-get install libapache2-mod-php5 and it says the latest version is already installed.  I also added the FilesMatch directive in the httpd.conf and/or apache2.conf.

I was messing around with it more (more in depth thread I posted here:  [http://ubuntuforums.org/showthread.php?t=1889020](http://ubuntuforums.org/showthread.php?t=1889020)) and found that if I put my documentroot in /home/jaesun/public_html , php prompts for a download.  But if I change it to /var/www or any directory in /var/www, php works fine.

Friend told me it might be permissions.  So yesterday, I was trying to change the owner:group to apache, but there is no such user in ubuntu (at least with checking the htpasswd file, there no entry).  I tried changing the /home/jaesun/public_html to root:root, but wouldnt let me (even if i was root user) ... could it be the permissions on the public_html sym-link or the permissions on /home/jaesun itself?  I assumed /home/jaesun/public_html would be fine, since many webhosts use /home/USER/public_html

---

