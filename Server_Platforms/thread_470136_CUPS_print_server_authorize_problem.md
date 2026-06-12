---
title: "CUPS print server authorize problem?"
date: 2007-06-10
forum: Server Platforms
---

### Post by JasonPN on 2007-06-10
Hello.

I am trying to but a simple CUPS printer server for a small network.  I am using 6.06 (regular version) and I followed the directions for creating a print server on Linux Reality here:

[http://www.linuxreality.com/podcast/episode-59-home-servers-part-5-file-and-print-servers/](http://www.linuxreality.com/podcast/episode-59-home-servers-part-5-file-and-print-servers/)

which are based on the directions here

[http://forums.debian.net/viewtopic.php?t=10438](http://forums.debian.net/viewtopic.php?t=10438)

Everything works initially in the install until I tried to use the web-based CUPS control panel (on my server at 192.168.1.60:631).

Every time I try to make a change or add a printer, it asks me for a username and password.  It won't accept, however, the username/password I created at the install not the root user, which I added a password for.

Any ideas?

---

### Post by mitch.c on 2007-06-11
> **JasonPN said:**
> Every time I try to make a change or add a printer, it asks me for a username and password.  It won't accept, however, the username/password I created at the install not the root user, which I added a password for.

Make sure the user account you are using is a member of the 'lpadmin' group:
```
$ sudo adduser username lpadmin
```
Have you made changes to /etc/cups/cupsd.conf? If so, it might help to post.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

