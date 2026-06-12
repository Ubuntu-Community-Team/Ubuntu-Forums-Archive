---
title: "Way to gracefully uninstall postgresql?"
date: 2008-09-15
forum: Server Platforms
---

### Post by airjaw on 2008-09-15
hi there.. long story short.. I 'm looking for a way to gracefully uninstall postgresql.. I'm trying to make the setup on my desktop and laptop the same.  Desktop is using postgresql8.3 , my laptop has an older version which I configured to install somewhere in my home folder.. yea i know.. kinda ugly.  It looks like this /home/xxxx/psql 

I want to install postgresql 8.3 in the normal location however I also want to remove the old one.. is there a way besides sudo -rm -r the entire directory?  Or is that method acceptable?

Thanks.

---

### Post by pqrs541 on 2008-09-16
You just might be a Red Neck if You've ever used lard in bed. Your home has more miles on it than your car.[world of warcraft](http://www.mmoinn.com)There is a stuffed possum anywhere in your house.[cheap wow gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)[wow power leveling](http://www.mmoinn.com) [power leveling](http://www.mmoinn.com)

---

### Post by barry.yarl on 2009-09-07
try sudo apt-get autoremove postgresql
that should do

---

### Post by lykwydchykyn on 2009-09-07
> **airjaw said:**
> hi there.. long story short.. I 'm looking for a way to gracefully uninstall postgresql.. I'm trying to make the setup on my desktop and laptop the same.  Desktop is using postgresql8.3 , my laptop has an older version which I configured to install somewhere in my home folder.. yea i know.. kinda ugly.  It looks like this /home/xxxx/psql 

I want to install postgresql 8.3 in the normal location however I also want to remove the old one.. is there a way besides sudo -rm -r the entire directory?  Or is that method acceptable?

Thanks.

I'm assuming you compiled it from source, which is why it's in a non-standard location.  If that's the case, you can do a "make uninstall" from the original source directory (if you still have it), or just remove the directory as you indicated.  

Only you know if that will remove all the files, because it depends on how you set it up.

---

### Post by beatyou on 2011-04-16
This worked for me
```
apt-get remove postgresql*
```

Which removed the following packages:
```
postgresql-8.4 postgresql-client postgresql-client-8.4 postgresql-client-common postgresql-common postgresql-contrib postgresql-contrib-8.4 postgresql-doc postgresql-doc-8.4
```

---

### Post by SeijiSensei on 2011-04-16
The point is that the version that the OP wants to remove wasn't installed from the repositories.

If you installed from source, did you specify --prefix=/home/user/psql when you ran ./configure?  If so, then just delete that directory and all traces of PostgreSQL will be gone.

Do you have any data in that installation you need to save?  If so, run pg_dumpall first to create a plain-text backup.

---

### Post by lykwydchykyn on 2011-04-16
I do surely hope the OP is not still struggling to uninstall Postgresql after 2 1/2 years...

---

