---
title: "Webdav Access"
date: 2010-03-26
forum: Server Platforms
---

### Post by Spectre5 on 2010-03-26
Hello all.  I'm having a problem with my webdav share.  I've read countless sites and threads to try to resolve my problem, but I've yet to find a solution.

I have a secure webdav folder that gets accessed via a non-standard port and requires basic authentication.  I can connect and interact with it fine via cadaver.  However, when I try to connect from nautilus, it says "Access was denied."  To make it even stranger, sometimes I can click on the folder in nautilus (it still mounts) and access it.  Sometimes not (just repeats the error message and won't show me the contents).  I may not even un-mount it, but just look at other folder, then click it again and be able to access it, but again - only rarely.

I asked a friend to try connecting from his windows vista computer and it would not work.  It would not work from my windows XP virtual computer either.  However, it mounts and works just find from my work computer (also Windows XP).

So it seems to be a 50/50 chance that the drive will mount on any given computer/system and work.  Do anyone know what the problem may be?  I'm guessing user permissions, but I can't figure out what.

I've made sure the webdav folder is owned by www-data and www-data has read access to the password file as well.

When I try connecting from nautilus, I get this in the log file:
```
... "OPTIONS /webdav HTTP/1.1" 401 1264 "-" "gvfs/1.4.1"
... "OPTIONS /webdav HTTP/1.1" 200 - "-" "gvfs/1.4.1"
... "PROPFIND /webdav HTTP/1.1" 207 310 "-" "gvfs/1.4.1"
... "OPTIONS / HTTP/1.1" 200 - "-" "gvfs/1.4.1"
... "PROPFIND /webdav HTTP/1.1" 403 1021 "-" "gvfs/1.4.1"
... "PROPFIND /webdav HTTP/1.1" 403 1021 "-" "gvfs/1.4.1"
```

Here is one of the (many) sites I've tried looking at:
[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10")

---

### Post by Spectre5 on 2010-03-28
Any ideas?

---

### Post by volkswagner on 2010-03-28
Sorry I don't recognise those exact logs.

I do recall while playing with WebDav myself there is some sort of bug in Nautilus.

Try connecting from your desktop using the "connect to server" under the "places" shortcut.

Select WebDav as the service type, try variations using ip address, port, user name and also no user name(wait for prompt).

Sorry can't be more help.

Good luck.

---

### Post by Spectre5 on 2010-03-28
Ya, I've tried it like that as well as several others ways!  I think it may be a problem in nautilus, but the reason I also considered the permissions is because windows seems to have problems as well, so it isn't just nautilus.

Also, it doesn't seem to allow any connections to edit files I place.  I have to copy the file to the local hard drive, edit it, then delete the file on the webdav server, then copy the edited file to webdav.

It won't let me just copy over the old one either, I have to actually delete the copy on webdav, then upload the new one.

---

### Post by volkswagner on 2010-03-29
Where are your WebDav directives located?

Have you seen [my thread]("http://ubuntuforums.org/showthread.php?t=1240886")?

I believe the how to we both used is not correct on the directive location for apache2 and Ubuntu.

---

