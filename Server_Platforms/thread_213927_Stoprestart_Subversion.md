---
title: "Stop/restart Subversion?"
date: 2006-07-12
forum: Server Platforms
---

### Post by aaronk on 2006-07-12
So I installed and configured SVN according to [this]("http://ubuntuforums.org/showthread.php?t=187739&highlight=eclipse+subversion") handy tutorial. But here's a crazy question:

I've got svnserve running as a daemon, now how to I stop it? I just want to restart the freaking thing without rebooting the whole server.

The Subversion website's FAQ says things like "Restart svnserve." Great. Thanks. That's so much help:p

---

### Post by DrSturgeon on 2006-07-12
Not too familiar with subversion, but there's probably a script to start and stop it in /etc/init.d.  Try looking in there: maybe it's called svnserve?

```
sudo /etc/init.d/svnserve start
sudo /etc/init.d/svnserve stop
sudo /etc/init.d/svnserve restart
```

Otherwise, maybe svn has a control utility (like apache's apachectl).  Try just typing svn and hitting tab a couple times and see what shows up.

---

### Post by aaronk on 2006-07-13
Yeah, that was the first thing I thought of, too. But no dice. I ended up just restarting the entire box. :roll: Thanks anyway, though.

---

### Post by nagilum on 2006-07-14
I'm not aware of a "proper" shutdown method either, but you can of course simply kill it (e.g. 'killall svnserve'), no need to restart your system.

---

### Post by alskor on 2008-03-18
so, is there a better way to restart subversion other than use "kill" command?
it does not look like "subversion restart" works.
I understand this relates to Subversion itself, not to Ubuntu. But still....

Thanks!

---

