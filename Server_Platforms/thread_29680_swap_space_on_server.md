---
title: "swap space on server"
date: 2005-04-25
forum: Server Platforms
---

### Post by paulfox on 2005-04-25
First of all, I'm sorry this isn't an ubuntu problem, it's one of our
servers acting up - running red hat 9, so i hope it's ok to pick your
brains here, you've always been a knowledgeable bunch for my ubuntu
desktop problems...
we have a server running a script every night, and every night our
memory usage jumps after it's run, eventually forcing the machine to
crash when there's no swap space left.
the script calls tar,gzip, postgres db_dumb and vacuumdb, then backs
up the files to a tape.
The memoy leaks are also occuring rarely even without the script being
called, which is the cause of the confusion.
I think it may be postgres leaking memory, but i don't know where.
does anybody have experience of this?

the main memory intensive process on the box is python(it's running zope).
postgres 7.4.5
zope 2.7.5
python 2.3.4
kernel 2.4.20 custom build.

i'd really appreciate any thoughts!

---

### Post by HungSquirrel on 2005-04-25
Not related to your problem, but I'd suggest upgrading those boxes to something else.  RH9 has plenty of remote exploits.  I should know, someone rooted my cousin's RH9 box.  ;)

---

### Post by jdodson on 2005-04-25
so your running redhat 9.0?  i would recommend : [http://fedoralegacy.org/](http://fedoralegacy.org/)

they provide support for old releases of unsupported redhat products.  i believe they still support redhat 9.0.

strike that, i actually recommend upgrading to the latest fedora, centos or better yet, ubuntu.  however, if you require redhat 9.0, [http://fedoralegacy.org/](http://fedoralegacy.org/) is your best option.  i would recommend patching it with the legacy patches if you have not already.

---

