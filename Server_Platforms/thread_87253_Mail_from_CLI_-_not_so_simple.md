---
title: "Mail from CLI - not so simple?"
date: 2005-11-07
forum: Server Platforms
---

### Post by basher on 2005-11-07
I'm a FreeBSD admin and I'm checking out Ubuntu for a desktop distro. So far I think it is one of, if not the best one I've tested.  I want to email myself from this desktop certain log files. In BSD it only takes a mail -s $address < $logfilename  and I receive the mail.

In Ubuntu I'm having problems.  I run the command from above but never receive the email, what am I missing here?  It must be a syntax issue or do I need to modify main.cf for Postfix.

Any help would be greatly appreciated.

Thanks

---

### Post by az on 2005-11-07
[http://www.ubuntuforums.org/showthread.php?t=15128](http://www.ubuntuforums.org/showthread.php?t=15128)

I cannot comment on Breezy, since I am not in front of a breezy box at the moment...

---

### Post by basher on 2005-11-07
Ok.. I changed my /etc/mailname to my fqdn mail server and now it worked. I was getting rejected msgs because it couldn't resolve the IP of my Ubuntu server (which is internal LAN only)

It works now, using mail -s commands. Hope that helps someone else.

---

