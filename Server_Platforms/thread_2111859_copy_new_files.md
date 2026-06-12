---
title: "copy new files"
date: 2013-02-03
forum: Server Platforms
---

### Post by Surox on 2013-02-03
Hello,

i'm looking to create a (i think) very simple script, but i just started on ubuntu and haven't got a clue how to get it to work.

I have a folder which recieves new files from other parts in my network. I need to do some processing on those files but now and then something goes wrong in that process and i loose files. to be sure of my system i need to have a script which watches a directory and copies any new files in it to another directory. every file/folder just needs to be copied once (when it just got into the directory).
is there an easy way to do this?


it's on a fresh install of ubuntu server 12.04

---

### Post by howefield on 2013-02-03
Thread moved to the "*Server Platforms*" forum.

---

### Post by Surox on 2013-02-03
whohoo not beginner enough for the absolute beginners section apparently :p

---

### Post by sudodus on 2013-02-03
Welcome to the Ubuntu Forums :-)

I hope you are ready for ***rsync***. See the well written manual ```
man rsync
```, where you can find what you need.

```
rsync -avn source-directory/ target-directory
``` will list what is new (and needs to be copied)
```
rsync -av source-directory/ target-directory
``` will do the copying.

If you want it done automatically, make a ***cron*** job of it!

---

### Post by koenn on 2013-02-03
> **sudodus said:**
> 
If you want it done automatically, make a ***cron*** job of it!

if you want it done automatically on every change (triggered, rather than scheduled), you might want
this [http://linux.about.com/library/cmd/blcmdl1_watch.htm](http://linux.about.com/library/cmd/blcmdl1_watch.htm)
or 
this [http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/](http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/)

---

### Post by sudodus on 2013-02-03
***incron*** seems to be a very good alternative :KS

---

### Post by Surox on 2013-02-07
thnx for the help, got it working

---

