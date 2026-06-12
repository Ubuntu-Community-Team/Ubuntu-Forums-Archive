---
title: "Adding storage function to a mail server"
date: 2008-01-04
forum: Server Platforms
---

### Post by satimis on 2008-01-04
Hi folks,


Ubuntu 7.04 server amd64
apache2-2.2.3
postfix-2.3.8
mysql  Ver 14.12
SquirrelMail version 1.4.11


I have a working Mail Server with above packages installed.  I'm prepared adding further function allowing users uploading files to the server for storage.  Please advise whether additional packages are needed?  OR just configure the installed packages?  Please shed me some light where to find relevant document.  TIA


Edit:-
==

Actually what I need is a file server allowing users who have accounts (Linux/shell) on the Mail Server to upload/download their files via browser on the Mail Server for storage.  That is what I expect to achieve.


SquirrelMail, Webmin and Usermin are also running on the Mail Server.  Users can send/receive webmails direct on any PC.  They can change their passwords either direct on SquirrelMail or via Usermin.  


At the beginning I was thinking whether I can make use Usermin allowing users to upload/download files to/from the Mail Server.  Therefore they can access them on any PC world-wide, borderless.  While googling around on Internet I found;

HFS ~ Http File Server
[http://www.rejetto.com/hfs/?f=dl](http://www.rejetto.com/hfs/?f=dl)
[http://www.rejetto.com](http://www.rejetto.com)


I expect folks on the forum who have experience on this project shed me some light.  OR are there better solutions?


TIA


B.R.
satimis

---

### Post by Miademora on 2008-01-06
Dont know much about it but maybe go for something simpler like:

[http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

maybe the filebased usermanagement isnt the greatest but since your mailserver seems mysqlbased you could just switch the authentication to ask the database easily.

just googled php file manager

---

### Post by HermanAB on 2008-01-06
There are a number of way to do it.  One way is to add FTP.  Usermin has a FTP up/download feature.

Another way is to install Citadel, since it supports mail, calendars, notes, webmail, forums - pretty much anything you can think of, right out of the box.  So to provide file up/download, simply create a forum (BBS/Chatroom) with public/private/list access and people can then exchange attachments using a browser with HTTP/HTTPS or a mail client using IMAP/IMAPS.

Cheers,

Herman

---

### Post by satimis on 2008-01-07
> **Miademora said:**
> Dont know much about it but maybe go for something simpler like:

[http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

Thanks for your advice and URL


> 
maybe the filebased usermanagement isnt the greatest but since your mailserver seems mysqlbased you could just switch the authentication to ask the database easily.

Please provide more detai how to make it.  TIA


> 
just googled php file manager
googling "php file manager" found many, such as;
PHP Filesystem Management Tool
[http://phpfm.sourceforge.net/](http://phpfm.sourceforge.net/)

PhpXplorer
[http://www.bigwebmaster.com/2846.html](http://www.bigwebmaster.com/2846.html)
[http://www.phpxplorer.org/phpXplorer/www/](http://www.phpxplorer.org/phpXplorer/www/)

Dolphin.php file manager
[http://www.hotscripts.com/Detailed/74948.html](http://www.hotscripts.com/Detailed/74948.html)

PHPfileNavigator v2.3.1
[http://pfn.sourceforge.net/index.php?opc=1&lg=ing](http://pfn.sourceforge.net/index.php?opc=1&lg=ing)

etc.

Which one shall I use.  Thanks


satimis

---

### Post by satimis on 2008-01-07
> **HermanAB said:**
> There are a number of way to do it.  One way is to add FTP.  Usermin has a FTP up/download feature.

Thanks for your advice.


I'm interested on this suggestion because FTP and usermin are running on this Mail Server.  Please provide more detail how to do it.  TIA.


> 
Another way is to install Citadel, since it supports mail, calendars, notes, webmail, forums - pretty much anything you can think of, right out of the box.  So to provide file up/download, simply create a forum (BBS/Chatroom) with public/private/list access and people can then exchange attachments using a browser with HTTP/HTTPS or a mail client using IMAP/IMAPS.

Whether you meant;

The Groupware Server for Web 2.0
[http://www.citadel.org/doku.php?id=start](http://www.citadel.org/doku.php?id=start)

Installing the pre-build packages
[http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian)


Thanks.


satimis

---

### Post by HermanAB on 2008-01-07
Well, FTP is really trivial.  Both proftpd and vsftpd will work right out of the box.  Just install it from Synaptic, start the service and you are done.  Well, OK, you got to allow FTP in your firewall too.

Citadel has custom Debian packages, but the Easy Install script works very well too: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)
and only takes about 20 minutes, plus another 20 for ClamAV and SpamAssassin.

The advantage of Citadel is that it takes care of everything.  For an equivalent modular system, you have to integrate postfix, mysql, dovecot, apache, roundcube, vBulletin, webcal, amavisd-new, spam assassin, clamav and jabber.  To get that fat lot to work together will take you at least 2 weeks and management will be a continual PITA, since whenever you create/delete a new account, you have to edit a bundle of different things.

Cheers,

Herman

---

### Post by satimis on 2008-01-07
> **HermanAB said:**
> Well, FTP is really trivial.  Both proftpd and vsftpd will work right out of the box.  Just install it from Synaptic, start the service and you are done.  Well, OK, you got to allow FTP in your firewall too.

Citadel has custom Debian packages, but the Easy Install script works very well too: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)
and only takes about 20 minutes, plus another 20 for ClamAV and SpamAssassin.

The advantage of Citadel is that it takes care of everything.  For an equivalent modular system, you have to integrate postfix, mysql, dovecot, apache, roundcube, vBulletin, webcal, amavisd-new, spam assassin, clamav and jabber.  To get that fat lot to work together will take you at least 2 weeks and management will be a continual PITA, since whenever you create/delete a new account, you have to edit a bundle of different things.

Hi Herman,


Thanks for your advice.

I have "usermin" running on the Mail Server.  Just discovered It is quite simple to upload/download files via it.  Except I haven't discovered natvigating the files download to the designated directory.


I'll try Citadel later.


B.R.
satimis

---

