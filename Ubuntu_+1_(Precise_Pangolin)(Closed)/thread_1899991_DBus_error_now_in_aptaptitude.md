---
title: "DBus error now in apt/aptitude"
date: 2011-12-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-25
DBus problems now affect apt/aptitude for me. These apps were unaffected by it until recently (or, at least, there was no DBus error message in their outputs).

```

Fetched 22.3 MB in 12s (1,774 kB/s)
**Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.**
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by ventrical on 2011-12-28
Par for the course on all my Precise installs.

---

### Post by ventrical on 2011-12-28
Maby there are some answers here.

[http://ubuntuforums.org/showthread.php?t=1036024&page=4](http://ubuntuforums.org/showthread.php?t=1036024&page=4)

---

### Post by ventrical on 2011-12-28
Yeah.. after running this:

sudo update-apt-xapian-index

you will get the true time out.

[http://ubuntuforums.org/showpost.php?p=10661166&postcount=43](http://ubuntuforums.org/showpost.php?p=10661166&postcount=43)

 but how can we fix it for good?

---

### Post by effenberg0x0 on 2011-12-28
It's weird cause this post talks about **rebuilding **this xapian package, not reinstalling it or updating it. You think he really meant that or just select the word badly?

**Edit:** Forget it, I'm sleepy. Running this thing **rebuilds** the xapian index, just saw the man page.

---

### Post by ventrical on 2011-12-28
zzzzzzzzzzzzzz.......

me 2

---

