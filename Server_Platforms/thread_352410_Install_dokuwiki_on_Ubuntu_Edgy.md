---
title: "Install dokuwiki on Ubuntu Edgy"
date: 2007-02-03
forum: Server Platforms
---

### Post by nick.allen on 2007-02-03
Hi,

I am trying to install dokuwiki on Ubuntu Edgy. I used synaptic to install the dokuwiki package which also installed all the necessary dependancies. Apache2 is running fine and I configured dokuwiki to be at [http://localhost/dokuwiki](http://localhost/dokuwiki). If I visit this URL in Firefox though I just get a dialog saying:

You have chosen to open

  which is a: PHTML file
  from: [http://localhost](http://localhost)

What should Firefox do with this file?

 Open with [Browse...]
 Save to Disc

Any ideas what I need to do. I searched the dokuwiki install docs and couldn't find any help there. It basically just says it's easy to install and that's about it! I don't find it too easy ;-) Any help greatly appreciated. Thanks,

Nicholas Allen

---

### Post by Gerard Barberi on 2007-02-03
I have Dokuwiki installed on my own system.  I can't find any phtml file in there.  I can tell you how I installed it.

I didn't go through the repositories; I honestly didn't think to look in there.

I downloaded it straight from [http://wiki.splitbrain.org/wiki:dokuwiki](http://wiki.splitbrain.org/wiki:dokuwiki)

unpacked the archive to Apache's web root
gave it write access

cd /var/www/dokuwiki/data/

sudo chmod 777 *

and ran the install script localhost/dokuwiki/install.php

oh, and I also renamed the folder to dokuwiki after I extracted the archive

---

### Post by mjrclark on 2007-03-26
I remember having trouble with this. If I remember correctly if you accessed the wiki using anything other than "http://localhost" the file was dealt with correctly. I might have reinstalled dokuwiki to fix it though. (apt-get remove dokuwiki --purge) to remove config. files.

---

### Post by vbhavsar on 2007-06-26
You probably don't have a php module for apache installed. Check /etc/apache2/mods-available for php*.conf. If you don't find anything, use synaptic to install a php (4 or 5) module. libapache2-mod-php5 for php5 and libapache2-mod-php4 for php4.

---

### Post by mogra on 2007-12-03
I badly need help for installing dokuwiki on my laptop for the personal use.

This going to my last attempt to install,  

Laptop : PowerBook G4 15"  , tiger 10.4

Things I tried so far :

Followed instructions from official dokuwiki forum :
[http://wiki.splitbrain.org/wiki:install](http://wiki.splitbrain.org/wiki:install)

But it didnt work , uninstalled three times and reinstalled.

Then friend of mine gave me following instructions : 
DokuWiki requires a Web server running PHP. These are the steps I followed to get DokuWiki set up on my Mac:

   1. Download DokuWiki from [http://www.splitbrain.org/projects/dokuwiki](http://www.splitbrain.org/projects/dokuwiki). I downloaded 
latest version
   2. I unpacked the DokuWiki archive and moved the contents to ~/Sites/dokuwiki.
   3. I enabled the Apache Web server. From System Preferences > Sharing, I checked the Personal Web Sharing checkbox. My Mac is running Apache version 1.3, and its URL is [http://localhost/](http://localhost/) or [http://127.0.0.1/](http://127.0.0.1/). Append “~myid” to the URL to get to the document root for user myid (fill in your own user name).
   4. I installed PHP 5.1.6 by following the instructions at [http://www.entropy.ch/software/macosx/php/#install](http://www.entropy.ch/software/macosx/php/#install).
   5. I set the permissions for the dokuwiki directory (and all enclosed items) to read and write, for Owner, Group, and Others. This can be easily done in the Finder via File > Get Info on dokuwiki.
   6. The URL of your Wiki is [http://127.0.0.1/~myid/dokuwiki](http://127.0.0.1/~myid/dokuwiki).


But hard luck it still doesnt work  for me. 

I get following error
Forbidden
You don't have permission to access /~myid/dokuwiki on this server.
Apache/1.3.33 Server at mogra.local Port 80


Can anybody please help me? 

I am not much familiar with all the permissions issues.  This forum is my last hope.

Thanks   a lot

---

### Post by sethvath on 2007-12-03
I would go with [XAMPP]("http://www.apachefriends.org/en/xampp.html") I've had success installing drupal, wordpress and a variety of other software with it.

EDIT: only took me a minute to install dokuwiki on xampp. Make sure you have the permissions of the dokuwiki folder in /opt/lampp/htdocs/ set to 777. You can do that by right clicking on the folder>permissions and selecting "read and write" access for everyone

---

