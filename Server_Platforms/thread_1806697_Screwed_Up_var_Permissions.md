---
title: "Screwed Up /var Permissions"
date: 2011-07-18
forum: Server Platforms
---

### Post by fullmoonguru on 2011-07-18
I have 10.04 server with a few web apps installed.  I was trying to load a new one & having errors with not havig permissions for certain files.  So i had the great idea of changing the file permissions for the /var folder.  now I can't connect to mysql.  I tried changing permissions there (mysql:mysql) but it's not working.  I also triedremoving/reinstalling sql server but still the same.

One very strange thing tha hapened during all this is that the msql log files are empty.  They're all still there, just nothing in them?  Anyway, how can I resolve these permission errors?

---

### Post by SeijiSensei on 2011-07-18
If you ran "chown someuser.somegroup -R /var" you're pretty much screwed.  /var has a number of different directories and subdirectories with a number of different owners and permissions.  Your best bet is to reinstall.

Alternatively you could build another server from scratch (virtual machines are good for this) then reproduce the permission structure from that server on the real one.  This is an arduous and pain-staking task, though.

---

### Post by fullmoonguru on 2011-07-18
That's kind of what I figured.  Was thinking of reinstalling anyway since this was my first server & it's kind of polluted with experiments.  Thanks-

---

### Post by SeijiSensei on 2011-07-18
> **fullmoonguru said:**
> That's kind of what I figured.  Was thinking of reinstalling anyway since this was my first server & it's kind of polluted with experiments.  Thanks-

Might I recommend, if you're going to be reinstalling anyway, that you consider placing /home on a separate partition, and maybe /boot as well?  This approach lets you replace the OS while not disturbing users' files.  Having a separate /boot is useful if you might be installing multiple Linux versions or distros on the same machine.

---

