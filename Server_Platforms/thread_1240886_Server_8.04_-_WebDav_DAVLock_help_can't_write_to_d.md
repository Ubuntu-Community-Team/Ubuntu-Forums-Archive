---
title: "Server 8.04 - WebDav DAVLock help can't write to directory"
date: 2009-08-15
forum: Server Platforms
---

### Post by volkswagner on 2009-08-15
I have been struggling with setting up webdav on a virtual host.

I used [this 8.10]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10") how to.

The main problem I am having is with DAVLock file.  Although the how to does not mention it, googling my error has led me to a few hits.

My errors match [this thread]("http://ubuntuforums.org/showthread.php?t=448814"), yet the solution yields no change.

From apache2 error.log
```
[Sat Aug 15 08:12:06 2009] [error] [client xx.xxx.xx.xxx] The locks could not be queried for verification against a possible "If:" header.  [500, #0]
[Sat Aug 15 08:12:06 2009] [error] [client xx.xxx.xx.xxx] Could not open the lock database.  [500, #400]
[Sat Aug 15 08:12:06 2009] [error] [client xx.xxx.xx.xxx] (13)Permission denied: Could not open property database.  [500, #1]
```

I have tried several attempts at creating the DAVLock file.  I tried inside /var/lock/apache2/, inside the root directory of the webdav folder, and various other places (all while editing the DAVLockDB directive in the Vhost file).  No matter where I put the empty file, I get the same error.  Even setting permissions to 777 does nothing.

I have not found any other info, what I can put into the file.

Clients can connect to the server, (using username/passwd) view files, but can't write.

I am surprised that WebDav is not more popular.  I am guessing it is lacking in security.  It seems to be the best alternative to get my wife's iPhone to share files with free software.

I have attached my latest vhost file.

TIA


EDIT:  I also tried following the directions [here]("http://arvati.blogspot.com/2008/12/apache-webdav-no-ubuntu.html"), moving the DAVLockDB directive to http.conf and the file to /usr/share/apache2/var/DavLock.  Still no change.

---

### Post by volkswagner on 2009-08-19
Well, not sure why the lack of a response.  It seems I am on my own these days.  Glad the answer was right under my nose.  Perhaps this is the reason for no response.  LOL

The how to mentioned above is not working with 8.04 server.

WebDav directives need to be entered in the /etc/apache2/mods-enabled/dav_fs.conf file.  As in [audax321 how to]("http://ubuntuforums.org/showthread.php?t=119228&highlight=howto+WebDAV")

So since I wanted a virtual host running WebDav I moved the <location> directive along with DAVLock directive to /etc/apache2/mods-enabled/dav_fs.conf and my vhost file just added "Dav On" to the <directory> listing.

All is working with 8.04 server.

There still seems to be the bug with Nautilus for my client.  I am running 9.04 desktop... To log into Dav server I can't enter username and password in the connection window.  I need leave the fields blank and wait for the prompt after login attempt.

As always with Linux, there is more than one way to skin a cat.  It just depends if you don't mind fur in your sandwich.

---

