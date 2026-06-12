---
title: "Does running this command compromise the security of Ubuntu?"
date: 2009-07-23
forum: Security
---

### Post by CEB2nd on 2009-07-23
Does running this command, sudo usermod -a -G lp username, compromise
the security of Ubuntu?  I'm fairly new to Linux, so I really don't
know.

See this [_thread_]("http://ubuntuforums.org/showthread.php?t=1158132")

Thanks in advance!

---

### Post by bodhi.zazen on 2009-07-23
I think you are fine =)

---

### Post by Trebaruna on 2009-07-23
It adds the user username to the group lp. It has something to do with printing. Do not add users you don't want to give access to printers, but otherwise you're safe.

In general, a good way to find out what a command does is checking the manual, e.g. in this case type "man usermod" into the terminal.

---

