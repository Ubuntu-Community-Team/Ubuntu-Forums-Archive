---
title: "How can I downgrade Apache2"
date: 2006-12-12
forum: Server Platforms
---

### Post by computec on 2006-12-12
I am a real Linux newbie, and need some help with Apache.
I have Apache2 running with perl and webmin but I can't seem to find anyone who can tell me how to get FrontPage Server ext. working on Apache2.
I would like to keep Apache2 but I will be forced to downgrade to Apache 1.x if I can't get FrontPage to work. I searched the forums and found one place where someone had a problem trying to downgrade from Apache2 to 1.x.
Can anyone tell me how to get FrontPage to work with Apache2 or how to downgrade to Apache 1.x.

Thanks,

Alan

---

### Post by computec on 2006-12-12
Update.....

     I have tried installing the ext to Apache 2.0 but the script fails because I don't have httpd-devel package installed. I have tried to find it but can't. Does anyone know where to download or how to install the httpd-devel package?

Thanks,


Alan

---

### Post by gnaunited on 2006-12-12
Make sure all repositories are enabled by default (probably not multiverse though)

Do a search for apache2 devel:

sudo apt-cache search apache2 dev

See what it pulls up.

---

### Post by computec on 2006-12-13
Thanks,... already did that with all rep enabled and already have it installed... when I run the fp_install.sh it fails because it tells me that it doesn't support 2.0.55 I know it supports 2.0, and I read that if I had httpd-devel installed it would work with 2.0.55 I am guessing that httpd-devel is apache2-dev. If so I have that installed and it still doesn't work... 

When running sudo apt-cache search apache2 dev
I get these results:

apache2-mpm-perchild - experimental high speed perchild threaded model for Apache2
apache2-prefork-dev - development headers for apache2
**apache2-threaded-dev - development headers for apache2**
libapache2-mod-perl2-dev - Integration of perl with the Apache2 web server - development files
libapache-mod-php4 - server-side, HTML-embedded scripting language (apache 1.3 module)
libapache2-mod-php4 - server-side, HTML-embedded scripting language (apache 2.0 module)
php4-cgi - server-side, HTML-embedded scripting language (CGI binary)
torrus-apache - Universal front-end for Round-Robin Databases (for apache 1.x)
torrus-apache2 - Universal front-end for Round-Robin Databases (for apache 2.x)
torrus-common - Universal front-end for Round-Robin Databases (common files)
**libapache2-mod-php5 - server-side, HTML-embedded scripting language (apache 2.0 module)**
php5-cgi - server-side, HTML-embedded scripting language (CGI binary)

Does this look right? The ones in BOLD are already installed.

What next? and other ideas?...


Thanks,

ALan

---

### Post by MJN on 2006-12-13
<snip post>

---

### Post by computec on 2006-12-13
What does that mean?

---

### Post by MJN on 2006-12-14
Sorry, it meant I wrote something but later realised it wasn't going to help you so deleted it! ;)
 
Unfortunately you can't delete posts on here (or at least I don't know how to!)...

---

### Post by computec on 2006-12-14
Ok thanks... I went ahead and uninstalled Apache2 and installed Apache 1.3.34 
It works but now I still have all the old Apache2 files and folders in the file system.
How do I get rid of them?

---

### Post by forethought on 2006-12-14
How exactly did you uninstall Apache2?

If you did it through apt or Synaptic, and if you're absolutely sure you don't need any of Apache2's leftover files/directories (though I am curious what it left) you can do:

sudo rm -Rf /directory/you/want/to/delete

But before you do that, tell us how you uninstalled it, and what was left on your system.

---

### Post by computec on 2006-12-14
I used sudo aptitude and went to the installed section and uninstalled it.

I still have all the Apache2 folder and files in /etc/apache2/ and I still have apache2ctl and apache2-ssl-certificate in the /usr/sbin/ folder.
I also still have /usr/lib/apache2/modules/ with files in it.

I'm not sure but I think that's all I have left.

---

### Post by gnaunited on 2006-12-15
sudo apt-get remove --purge apache2

You will have to reinistall apache1 because there are a lot of inter dependencies between the two.

---

### Post by computec on 2006-12-16
I guess I just have to run autoremove and get rid of all the dependencies and then uninstall Apache 1.x and reinstall Apache 1.x

Right?

---

