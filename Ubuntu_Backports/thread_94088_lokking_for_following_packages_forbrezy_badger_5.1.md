---
title: "lokking for following packages forbrezy badger 5.10"
date: 2005-11-23
forum: Ubuntu Backports
---

### Post by xstation on 2005-11-23
Must build a package from source need the folowing deps

adduser
logrotate
python 2.3
libss 10.9.7

many thanks

xstation:???:

---

### Post by AgenT on 2005-11-23
First, you should look into using [http://packages.ubuntu.com](http://packages.ubuntu.com) where you would notice that every package you need is already available except libss version 10. This will not be backported because 1) it is a library and 2) because it is NOT in Dapper. In the introduction to the backports (which you should read) it states that the package must be in Dapper before it having any change of being backported (backport means it is ported back from the newest version which is Dapper now). Your option is 1) build from source or 2) get a deb file from somewhere else (note that as of now not even Debian has version 10).

---

### Post by imagine on 2005-11-23
[QUOTE=AgenT]Your option is 1) build from source or 2) get a deb file from somewhere else (note that as of now not even Debian has version 10).[/QUOTE]3) Try to get it into Dapper : )

---

### Post by xstation on 2005-11-23
my mistake 
should read openssl 0.9.7

not liss10. xyz


thanks to all :smile:

---

### Post by AgenT on 2005-11-23
You know, instead of asking us to search for you would it be that hard for you to click on the link that I have provided you and look up the current version of openssl? Needless to say, you made us search for you when all those packages you ask for are in Breezy already.

---

### Post by xstation on 2005-11-24
Yes I did make you search for me, my apologies perhaps I can do the same for you one day:smile: 

andrew

---

