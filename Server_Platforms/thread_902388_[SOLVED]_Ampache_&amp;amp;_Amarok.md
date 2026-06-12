---
title: "[SOLVED] Ampache &amp;amp; Amarok"
date: 2008-08-27
forum: Server Platforms
---

### Post by TDragon on 2008-08-27
Yesterday, I installed Apache2 (w/ PHP5; I already had mySQL installed from Amarok) first and then attempted to install Ampache using the default web location, /var/www/ampache. And getting frustrated that i couldn't load the site, I found a .deb file to install the second latest version of the program, which worked after testing [http://localhost/ampache/](http://localhost/ampache/). I configured the program and when I went to save the config file, I discovered that the site is running from /usr/share/ampache/www/... 
 
Is there anyway of telling Apache to look in the default folder for it (after I physically move the directory)? I know that Apache is already looking in that directory (/var/www/) because I created a test php file in that directory and was able to successfully run it.
 
 
My second question is there any way I can get Amarok to use the ampache DB so I don't have to maintain and populate a second DB? I know that Amarok2 is stupposed to have support for it, but I don't know to what extent (playing streams, intergration, etc).

---

### Post by TDragon on 2008-09-10
I found the link file in the apache directory that was pointing to the /usr/share location, edited it to point back to the default wwwroot directory, and restarted apache2. It now works properly.

I still however have not figured out how to get Amarok & Ampache to play together. Oh well, I guess I'll have to wait for Amarok2.

---

### Post by cjssmo on 2009-03-05
As you know Ubuntu is based on Debian, the package installed ampache correctly according to Debian policy (/usr/share/ampache/www), but since it is your system you are allowed to do what you will with it.  

Amarok2 when it is released, will support ampache's XML API

---

### Post by dasbooter on 2009-05-09
> **cjssmo said:**
> As you know Ubuntu is based on Debian, the package installed ampache correctly according to Debian policy (/usr/share/ampache/www), but since it is your system you are allowed to do what you will with it.  

Amarok2 when it is released, will support ampache's XML API
  
Old thread but just wondering if this has any ramifications if I want to upgrade to the latest stable ampache? 3.5 in this case.

---

