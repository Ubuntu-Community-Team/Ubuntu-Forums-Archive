---
title: "mysql 5.1.3 on 8.10?"
date: 2009-01-15
forum: Server Platforms
---

### Post by mr.generic.user on 2009-01-15
hope i'm in the correct category (actually running desktop ver 8.10 AMD64).  i am a web app developer, but for dev i use my computer as a LAMP server instead of using the production server.

is there a repos i can add to sources.list that has mysql server 5.1.3 or does anyone know all the packages i would need and have instructions or link that explains installing 5.1.3 with all of the default packages and extensions needed to get it running on 8.10 AMD64 just like the 5.0 package?  i need the ExtractValue() function that comes with the new version.  my production servers run 5.1.3, and i am trying to kickstart a new unified and integrated version of our apps with an XML-centric design to use as a proof of concept and initial proposal.  this one function would allow me to store my data in xml sets per row, and still be able to make the proper joins for complex queries.

any help would be appreciated.  thanks in advance...

---

### Post by mr.generic.user on 2009-01-16
does anyone know how to get mysql-server 5.1.3 (newest version) running on ubuntu 8.10, configured the same way as the 5.0.67 package in the repository?

i'm willing to do a make dance, but i need to know what options and packages i need to get the same funcitonality and config file layout...

anyone...?

---

### Post by mr.generic.user on 2009-01-17
thank you to all that read this thread.  i got it!!!  hopefully this will help some others.  i'm sure this is NOT the recommended way, but after some weeks of searching i found some repositories that allowed me to do this!

here they are:

deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all

---

### Post by fwolf on 2012-02-07
> **mr.generic.user said:**
> thank you to all that read this thread.  i got it!!!  hopefully this will help some others.  i'm sure this is NOT the recommended way, but after some weeks of searching i found some repositories that allowed me to do this!

here they are:

deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
I'm looking for this too, thanks for sharing .

---

