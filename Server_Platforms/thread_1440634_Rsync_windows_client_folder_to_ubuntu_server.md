---
title: "Rsync windows client folder to ubuntu server"
date: 2010-03-27
forum: Server Platforms
---

### Post by rgotten on 2010-03-27
i have an ubuntu server 4 windows client..i use putty or webmin. would like to copy some folders for example: "My houses"to be backup everynigth to the ubuntu server..can somebody give me an easy way for doing this with rsync and smb or cifs

Thanks

---

### Post by Iker Etxebarria on 2010-03-27
Have you tried doing something?

---

### Post by kgatan on 2010-03-28
Share the folder in windows and mount it with samba in ubuntu, take backup with rsync and set schedule with cron.

Just google the each of them, tons of guides out there.

---

### Post by koenn on 2010-03-28
> **kgatan said:**
> Share the folder in windows and mount it with samba in ubuntu, take backup with rsync and set schedule with cron.

Just google the each of them, tons of guides out there.

this, 

or look at DeltaCopy (rsync for windows)
[http://users.telenet.be/mydotcom/howto/linux/rsyncservers.htm](http://users.telenet.be/mydotcom/howto/linux/rsyncservers.htm)

---

### Post by jrssystemsnet on 2010-03-28
> **kgatan said:**
> Share the folder in windows and mount it with samba in ubuntu

Bad idea.  If you're going to be using rsync, you're much better off using a daemon on the remote end than trying to do a "local" rsync across a network mount.

For the Windows boxes, you can use cwrsync (google it), or from what I understand (though I haven't used it myself) "deltacopy".

---

