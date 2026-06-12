---
title: "Upgrade 10.04.1 to 10.04.4"
date: 2012-02-21
forum: Server Platforms
---

### Post by pjs_gsy on 2012-02-21
Hi,

OK, sorry if this is already posted somewhere, but for the life of me I can't find out where!  How to I do a release upgrade from 10.04.x LTS to 10.04.4?

Thanks.

---

### Post by junaid_572 on 2012-02-21
I guess 10.04.4 is actually 10.04 with all updates installed
[http://ubuntuper.wordpress.com/2010/08/23/10-04-vs-10-04-1-update-upgrade-reinstall/](http://ubuntuper.wordpress.com/2010/08/23/10-04-vs-10-04-1-update-upgrade-reinstall/)

---

### Post by pjs_gsy on 2012-02-21
Hi,

I'm not sure it is, unless I'm missing something.  Certainly the behavior of 10.04.4 is slightly different from 10.04.x for me. 

For instance, the way I noticed this was netcat.  NC is a different version or behaves differently on 10.04.1 to 10.04.4 and I have run apt-get update and update-get upgrade on the 10.04.1 box.  This specific issue is affecting some scripts I wrote.

---

### Post by pjs_gsy on 2012-02-21
OK, perhaps it is after all!  I find there is 2 version of nc.  openbsd and 'traditional'.  Seems openbsd in the detail perhaps on 10.4.3-4 and traditional on 10.04.1-2.

---

### Post by Elfy on 2012-02-21
I f you have updated and upgraded then you have 10.04.4.

If you have an issue with netcat and scripts I'd suggest starting a thread for it.

---

### Post by junaid_572 on 2012-02-21
current version of netcat was released in 2004, so it would be weird if i say that they have included newer version of netcat. Problem might be in something else.

---

### Post by spynappels on 2012-02-21
FYI
```
sudo apt-get dist-upgrade
``` 
took me from 10.04.3 to 10.04.4

---

