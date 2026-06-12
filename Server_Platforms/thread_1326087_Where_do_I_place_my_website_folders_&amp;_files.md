---
title: "Where do I place my website folders &amp; files?"
date: 2009-11-14
forum: Server Platforms
---

### Post by Stolea on 2009-11-14
I am a complete newbie to this, so please indulge my ignorance.

I run a PHP based website for my business that is hosted on a server in the US. The commercial template software is written in PHP and Dreamweaver.
We are in the process of rewriting some interface parts of the website and need to test the modifications before uploading them to the live website.

I have followed the instructions for setting up Appache and all the bits that go with it according to this previous post [http://ubuntuforums.org/showthread.php?t=1322480]("http://ubuntuforums.org/showthread.php?t=1322480")

When I type 127.0.0.1, the server responds > It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.

I have created a test user and test database with PHPMyadmin.

Where do I put my website files?
My real live website server has this construction:
/
/stats
/backup
/awstats
/logs
/private
/www
/www/.www-root
/www/www (directory where all my folders and files live)

I copied the folders and files to /var/www/www but when I type 127.0.0.1, get the > It Works response.

I have read up on the documentation, but cant seem to get any information on this.

Can Anyone shed some light on this please.:oops:

---

### Post by TwiceOver on 2009-11-14
Try /var/www  That is Apache's default www file on Ubuntu.  It can be changed.

If you copied everything to /var/www/www then you should find it at 127.0.0.1/www/

---

### Post by Stolea on 2009-11-14
> Try /var/www That is Apache's default www file on Ubuntu. It can be changed.


Just tried that and got > Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

When I have a look with Nautilus at the files in the directory they all have a white X on the icons. The permissions are owner:root read/write, group:root read/write, others:none

---

### Post by Iowan on 2009-11-14
*/var/www* is (by default) owned by root - so you'd need to **sudo** to put files there.  You can change permissions or put the files elsewhere. [This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") help page provides some details.

---

