---
title: "snort with ACID"
date: 2009-09-03
forum: Security
---

### Post by greyaline on 2009-09-03
Greetings all,

I have snort Version 2.8.4.1 , mysql Version 5.0.75-0ubuntu10.2   and ACID v0.9.6b2 installed on Ubuntu 9.04.  The problem is names of the signatures are being displayed as numbers!  :confused:  I have scroogled the heck out of it and only found solutions relating to barnyard.  Barnyard wont install - ERROR: unable to find mysqlclient library   
                                                   checked in the following places             
                                                       /usr/include/mysql/      -

This is a home setup so I don't think I need barnyard anyway... No errors on any of the mysql, apache2, syslog, messages logs relating to it.   Any clues would be appreciated, thanks.

---

### Post by TuckLive on 2009-09-03
Have you tried using BASE?  Acid is no longer supported and BASE has taken it's place.  Screenshot of BASE attached.

---

### Post by greyaline on 2009-09-04
Yes, I have tried base.  I also recreated the database and tables.  Still numbers for sig names. any one now an alternative to base/acid?

---

