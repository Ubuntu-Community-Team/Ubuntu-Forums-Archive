---
title: "Accessing MsAccess db from Ubuntu through ODBC"
date: 2009-05-28
forum: Wine
---

### Post by gjosef on 2009-05-28
Hi,

Is this possible at all?
I have an MS Access db that I can open elegantly through Access 2000 running under Wine.
Now I would like to let linux apps in general access this same db, through ODBC. For example, I would like to be able to access the database through OOo's Base, or through a Java program. So I am wondering, is there a way to have MS Access' ODBC service registered so that it becomes available to applications running outside of Wine, or can it only be accessed from within Wine itself?


TIA

---

### Post by gwm on 2009-07-12
This is my special interest at the moment. So far I also haven't had any concrete results from my queries or from searching the web. I have just seen a link to winehq that said msaccess (xp) installs and runs fine under wine. I was thinking to do that in the hope that the installation will also give me what I need to make oledb work (whatever that may be).
As far as I have been able to see, wine doesn't come with support for odbc. One has to install it from somewhere, somehow and nobody I have looked at seems to have been able to find out how to do it. I could modify my programs to use odbc instead of oledb if I could get this working.
This surprises me because I would have thought that many, many applications use this sort of thing. Apparently I'm wrong!

---

### Post by gjosef on 2009-07-17
> **gwm said:**
> This is my special interest at the moment. So far I also haven't had any concrete results from my queries or from searching the web. I have just seen a link to winehq that said msaccess (xp) installs and runs fine under wine. I was thinking to do that in the hope that the installation will also give me what I need to make oledb work (whatever that may be).

Nice to see that there are more people concerned by this issue!

> As far as I have been able to see, wine doesn't come with support for odbc. One has to install it from somewhere, somehow and nobody I have looked at seems to have been able to find out how to do it. I could modify my programs to use odbc instead of oledb if I could get this working.


I think it's important to point out that there are two potential types of Linux/Access communications. The first is to allow Access to access data hosted in the non-wine system, sort of inbound ODBC (the ODBC layer in wine can access databases outside of wine, letting wine apps use them). The second, which is the one I'm looking for does the opposite; it lets non-wine applications access a wine-based database engine through the help of ODBC (a sort of export from wine). In other words, any ODBC-enabled app running on ubuntu would be able to read data from an Ms Access database. I think the chances of finding a working solution for the first situation are higher than for the second one...

> This surprises me because I would have thought that many, many applications use this sort of thing. Apparently I'm wrong!

---

