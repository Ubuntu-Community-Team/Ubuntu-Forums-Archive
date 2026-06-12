---
title: "motd Shown Twice"
date: 2008-03-13
forum: Server Platforms
---

### Post by dataset on 2008-03-13
Hey everyone!
I'm having a problem where every time I login via SSH to my server the motd gets shown twice.
The motd file only has the message only once, but it shows it twice at login. There is also a file name motd.tail.
What is causing this problem?
Thanks in advanced!

---

### Post by tubezninja on 2008-03-14
motd.tail is the default motd file.  Whenever the server is reboot, a script runs that adds the output of uname -snrvm plus the contents of /etc/motd.tail to the motd.

The relevant script is in /etc/init.d/bootmisc.sh:

```
	# Update motd
	uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd


```

The question is, what's in your motd.tail?  can you cat this file and see if the contets are duplicated?

---

### Post by dataset on 2008-03-14
> **scaredpoet said:**
> motd.tail is the default motd file.  

The question is, what's in your motd.tail?  can you cat this file and see if the contets are duplicated?

Well the contents are duplicated. Does this mean I should delete the motd.tail? Or clear it? Or does the problem reside somewhere deep in configuration files?
BTW Thanks for replying so soon!

---

