---
title: "File versioning sistem"
date: 2012-06-07
forum: Server Platforms
---

### Post by sbrus on 2012-06-07
I am looking for solution that will cover file versioning. I tried to google it, but without any success. I am looking for something that will work like it was long time ago in Novell salvage.

---

### Post by rubylaser on 2012-06-07
What type of things are you trying to version (i.e. code, and whole filesystem, etc)?  Novell Salvage was a filesystem versioning system if I recall correctly.  You could do this simply with rsync called via ionotify or cron and hard links (or rsnapshot), or go with a ZFS filesystem and have it take snapshots on a specific interval.  There are many other ways to probably accomplish what you're wanting, but it would be nice to know more info.

---

### Post by LHammonds on 2012-06-07
I saw an awesome article on using automated versioning of files in your /etc folder and will incorporate it into all of my servers and documentation (see sig).

Article: [Using etckeeper with git on Ubuntu]("http://evilrouters.net/2011/02/18/using-etckeeper-with-git-on-ubuntu/")

---

### Post by sbrus on 2012-06-20
Well...

1. I am not searching for solution that will help me to track changes in my source code. I am searching for:

2. I have users that have shared folder where they create, edit, move and delete files. They do that from word processor. What Novel had (I think that it is now available on their suse servers), was that he could (extremely easy) show who was, what was, when was, done something with any file, and _salvage_ that version of file to any folder. In order to do that, users did not have to 1. learn how to, and 2. do that what have to do in order to accomplish to have history of file change.

LHammonds gave link to Using etckeeper with git on Ubuntu. I am reading that, but I am not sure that it is what I am looking. It might be useful because of:

"...The Ubuntu etckeeper package sets up a cronjob that will run daily and auto-commit any changes to files in or under the /etc directory that we haven’t explicitly committed..."

if that auto-commit means that this system is clever enough to work without intervention of users. But if it relies on scheduled time, that is not what I am looking for.

---

