---
title: "PostgreSql and Ubuntu"
date: 2006-06-09
forum: Server Platforms
---

### Post by jitesh on 2006-06-09
Can anyone tell me how to install postgresql on a ubuntu server.

---

### Post by OneSeventeen on 2006-06-09
[QUOTE=jitesh]Can anyone tell me how to install postgresql on a ubuntu server.[/QUOTE]
If you are using Dapper, just use:
```
sudo apt-get install postgresql-8.1
```

Then again, I haven't installed the Dapper server yet, so I'm not sure if you need "sudo" or if you just log in as root...  Either way, apt-get install postgresql-8.1 should work.

To find out what package to install, I just went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and searched for "Postgresql" in the Dapper distribution.

(for Breezy, use postgresql-8.0)
I'll be installing postgresql-8.1 and setting up some users and databases on the Desktop version of Dapper today, so I'll post a guide somewhere and link to it from here.

Hope this helps!

---

### Post by jitesh on 2006-06-12
I'v tried the command, unfortunatly I get an error returned "E: could'nt find package postgres-8.0". This is the install package of postgres on ubuntu breeezy badger, what do i do?

---

### Post by LordHunter317 on 2006-06-12
Because the package isn't postgres-8.0  It's postgres**ql-8.0** and I'm pretty sure you'll need universe anyway.

But if you're running breezy, what you really want to do is setup a dapper source and pull down 8.1.

---

### Post by jitesh on 2006-06-12
Don't have an internet connection yet configured on the server, is it possible to install postgresql via a CD?

---

### Post by schurtek on 2006-08-11
I used dapper (6.06) and found that postgresql-8.1 was on the CD. I type sudo apt-get install postgresql-8.1

problem with my case is I needed 7.4.7 cos 8.0 and 8.1 has known issue with the software I am using... ](*,)

---

