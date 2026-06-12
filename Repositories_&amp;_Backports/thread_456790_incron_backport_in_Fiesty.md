---
title: "incron backport in Fiesty"
date: 2007-05-28
forum: Repositories &amp; Backports
---

### Post by thelonecabbage on 2007-05-28
is it even possible to backport incron to Fiesty?

I've compiled it from source following the instructions at: 
[http://inotify.aiken.cz/?section=incron&page=doc&lang=en](http://inotify.aiken.cz/?section=incron&page=doc&lang=en)

but I'm unable to get any of my incron-tables to stick.   

ie: 

sudo incrond
incrontab -e 
>> in the editor
/home/me/testcron/*  IN_CLOSE_WRITE  touch /home/me/testcron/$#.didit
<<

no effect can be noticed when testing and running icrontab -e again just gives an empty editor.

---

