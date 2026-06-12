---
title: "Is there any apt log-file?"
date: 2005-04-21
forum: Repositories &amp; Backports
---

### Post by kb00heda on 2005-04-21
Hi,

Under SuSE I had a /var/log/apt.log file which showed my what packages had been installed or removed, i.e., like the "History" in Synaptic. Is there such a log file in Ubuntu as well, and if so, there to find it?

The "History" in Synaptic doesn't seem to recognize apt modifications made from a terminal.

Regards,
David

---

### Post by mendicant on 2005-04-21
You could use aptitude instead, which does provide a log file, in addition to its other benefits:

[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

---

### Post by xpollux on 2008-02-03
I realize this is a very old question but it came up when I was searching for this.  I don't know if there is an apt log, but there is a dpkg log in /var/log/dpkg.log (or dpkg.log.1) which should be just as good.

---

### Post by NoBugs! on 2009-09-02
There's also /var/log/apt/term.log, it looks like this is the file synaptic is reading with the file-history command.

---

### Post by joep-vd on 2010-02-26
if i remember all correctly, then both what I did in Synaptic and through apt-get end up in /var/log/apt/term.log. Not very handy to compile a list of installed packages though...

---

### Post by dumpsterdiver on 2010-08-18
```
/var/log/apt/history.log
```

Seems to contain all changes regarding packages.

---

### Post by feeela on 2011-09-27
I've noticed that ```
/var/log/dpkg.log
``` is much more detailed than ```
/var/log/apt/history.log
```, but both contain a goog overview of changes via apt in terminal.

---

### Post by oldos2er on 2011-09-27
Closed for necromancy.

---

