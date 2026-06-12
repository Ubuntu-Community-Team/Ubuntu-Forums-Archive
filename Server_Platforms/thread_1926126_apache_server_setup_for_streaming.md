---
title: "apache server setup for streaming"
date: 2012-02-15
forum: Server Platforms
---

### Post by falconator on 2012-02-15
This my first attempt at setting up a server in Ubuntu 11.10.  I have been using ubuntu for about a year now and still have tons to learn.  
I am trying to get apache setup to be able to run a server to stream my local video/music content to my roku.  I have tried roConnect, roksbox, and plex.  I run into the same basic problem with each one.  
With roConnect, When I go to the setup page, it will not recognize the location where my video content is.  It will accept the /media/drive location but when I list the folders as well (/media/drive/folder) it says it isn't a valid location.  The same problem exists with plex.  
With roksbox, I had trouble getting the alias set correctly.  I edited the httpd.conf file for the alias but I must not have done it correctly as I kept getting the "it works" page but nothing else.  
I am assuming this is a permission issue with the drive and folder they are located in.  This is because if I do the same thing in Winxp, the setup works perfectly.  I am dual-booting ubuntu 11.10 and winxp.  
I am listing the alias as
alias /movies /media/C8D4A489D4A47B78/FolderName/movies

any direction would be appreciated.

---

### Post by nsnidanko on 2012-02-27
I am not familiar with any of these application and don't know how they run (either as as deault apache2 user: www-data) or have their own user. Just for test try to run the following
**chmod -R 777 /movies/media**

But as it seems roConnect accepts location, just doesn't have permissions to access anything there.

---

