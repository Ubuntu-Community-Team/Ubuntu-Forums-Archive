---
title: "MD5 routine to reveal a compromize"
date: 2014-04-04
forum: Security
---

### Post by ant2ne on 2014-04-04
Here is an idea I had, but I’m sure someone else has already thought of it before. There probably already is such a script/program, although my limited googling hasn’t uncovered it.

Suppose there was a script that did an md5 recursively on all files in certain directories like /etc /bin /sbin /usr (etc. any directory which limited users don’t have access and do not change) and wrote those sums to a file. Then that file could then be stored external to the system or wrote to CD. Of course, every time the system administrator installs or updates programs this script would need to be run. But, if someone suspected a compromise then one could run a second script which re md5s all the files, but instead of writing to the file it compares the results of the files and report back which files don’t match. If a compromise was to have happened the system administrator would know what files were modified.

A particularly skilled script writer could set it up all automated via cron and sshkeys. Cron executes the file write script at midnight the last line of that script writes the md5 file to another storage server using sshkeys. At about 2am that other storage server sends yesterday’s md5 file back to the first server who runs the second comparor script and the last line of that script sendmails the system admin the results including which files got changed.

What is your opinion of such a technique?

---

### Post by untrustytahr on 2014-04-04
Sounds like [Tripwire]("https://apps.ubuntu.com/cat/applications/tripwire/")

---

### Post by unspawn on 2014-04-04
Even better: Samhain for  0) checking integrity *actively* (in contrast with AIDE or tripwire),  1) checking efficiently using *inotify*, 2) allowing signed config and databases and 3) adhering to the client - server paradigm (see Yule).   [http://www.la-samhna.de/samhain/](http://www.la-samhna.de/samhain/)

---

### Post by CharlesA on 2014-04-05
I just use csf, which has an integrity check builtin. If a file's hash has changed, I get an email about it.

---

### Post by ant2ne on 2014-04-07
csf?

---

### Post by CharlesA on 2014-04-07
> **ant2ne said:**
> csf?

This thing:
[http://www.configserver.com/cp/csf.html](http://www.configserver.com/cp/csf.html)

---

