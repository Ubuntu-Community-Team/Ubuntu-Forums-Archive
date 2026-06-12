---
title: "RivetTracker v0.1 Beta Test"
date: 2007-06-09
forum: The Cafe
---

### Post by firefly2442 on 2007-06-09
edit: See latest post.

---

### Post by Iarwain ben-adar on 2007-06-09
I'd like to say that, if i had the possibility to run a tracker, i'd like to run it with this program.

Seems quite organized for me (although i'm really chaotic)

Good job i'd say!


Iarwain

---

### Post by firefly2442 on 2007-06-09
Thanks!  Yeah, the original PHPBTTracker program was an excellent base to start from but I added in some admin pages, authentication, more detailed user statistics, etc.

---

### Post by firefly2442 on 2007-07-03
Version 0.8 has been released with many feature enhancements:

[http://www.rivetcode.com/software/rivettracker/](http://www.rivetcode.com/software/rivettracker/)

---

### Post by firefly2442 on 2007-08-29
RivetTracker version 0.9 has been released. This version has many security enhancements, code optimizations, RSS feeds, and an improved installer. Because of changes in the database, previous users of RivetTracker will have to perform a complete reinstall. This is the last version before the 1.0 release and it will be considered off beta status.

If you have any suggestions or bug reports please let me know. I want this to be polished and ready to go for the next release. The one technical question I have revolves around how the speed calculations are done. I did some tests and this method is not accurate at all. All the speed updating and calculations are in the tracker.php file. Does anyone have a suggestion for an alternative method for determining the speed of the torrent? Thanks. :)

[http://www.rivetcode.com/software/rivettracker/](http://www.rivetcode.com/software/rivettracker/)

---

### Post by firefly2442 on 2007-11-20
A beta release of v0.99 has been released.

[http://rivetcode.com/software/rivettracker/](http://rivetcode.com/software/rivettracker/)

This version adds a lot of stuff, including HTTP seeding which is pretty sweet.  If people could test it out and give me feedback that would be awesome.  Thanks! :)

---

### Post by firefly2442 on 2008-02-13
A new version of RivetTracker has been released:

v0.999

[http://www.rivetcode.com/software/rivettracker/](http://www.rivetcode.com/software/rivettracker/)

Old versions should be considered obsolete and need to be updated. If you are upgrading, zip up all the torrents you have and do a complete reinstall. Then use the zip upload page to reinitialize your torrents into the database. This version changed a lot of code and as such I am looking for bugs and security vulnerabilities. If you find any, please let me know.

Changelog:

---Version 0.999---

-Fixed bug where RSS feed was being displayed in header when it was disabled
-Fixed rounding error in statistics.php where user was being shown as 100% done when they are only almost done (99.6%)
-Changed display of bytes transferred on index.php page to correct units, before it defaulted to GB
-Added check for stalled download in runSpeed() function
-Fixed error where speed was set to 0 if seeders == 0, not always the case, can still be downloading even if there are no seeders (partial d/l)
-took out repair statement in sanity.php and sanity_no_output.php
-Added CSS page where you can change/swap/create CSS files and examine colors with the color picker
-Added batch upload of torrents via ZIP file
-Added help link to index.php
-Used htmlspecialchars on inputs in order to prevent code injection
-Added javascript row select in delete page
-Fixed delete bug, URL bug
-Added MySQL table prefix option
-Sanitized some inputs (still more?), this way if someone gets your admin password they won't be able to execute malicious code

---

### Post by firefly2442 on 2008-02-18
New release is out:

[http://www.rivetcode.com/software/rivettracker/](http://www.rivetcode.com/software/rivettracker/)

A major install bug managed to sneak into the previous release.  Thanks for those that are testing! :)

---

### Post by firefly2442 on 2008-03-01
It's finally here.  RivetTracker v1.0 has been released after months of work.  Any updates from here on will probably be bug fixes.  Please report all problems either on the forums or the contact page.

[http://www.rivetcode.com/software/rivettracker/](http://www.rivetcode.com/software/rivettracker/)

Latest changes:
> 
-Changed database engine from default MyISAM to InnoDB, hopefully this will prevent table crashes
-Changed CSS files
-Changed session authentication to more secure method, does not store username or MD5 anymore
-Passwords are now no longer stored in cleartext in the config.php file, they are computed as md5(username.password)


---

