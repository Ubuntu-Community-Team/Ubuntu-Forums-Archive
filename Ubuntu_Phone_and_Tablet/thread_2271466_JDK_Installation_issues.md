---
title: "JDK Installation issues"
date: 2015-03-30
forum: Ubuntu Phone and Tablet
---

### Post by Lutz_Fechner on 2015-03-30
Hi,

I was trying to install any form of SDK (Oracle, OpenJDK - doens't matter to me) from the repositories.

That failed miserably. First, because the fiel system was read-only. Second, because it apears that some dependencies for OpenJDK are broken. Third, becuase I might be too stupid :-)


Anyone succeeded with this - or has any hint?

---

### Post by Lutz_Fechner on 2015-03-31
Managed to get Java working.

It suddently worked after doing "apt-get install build-essential".

Actually was trying to compile it from source myself - But seems like that way it is working fine.


At least "java -version" now returns:
java version 1.7.0_65
OpenJDK Runtime Environment


But "apt-get install tomcat7" fails again with some dependency issues. Will download it from the website and try if it starts.

I know I might be abusing the mobile as a linux playground. But that was exactly why I got one of the bq phones. It is a bit like a portable Raspberry (without GPIO - will see if it supports host USB and can use an Arduino to compensate missing IO).

---

