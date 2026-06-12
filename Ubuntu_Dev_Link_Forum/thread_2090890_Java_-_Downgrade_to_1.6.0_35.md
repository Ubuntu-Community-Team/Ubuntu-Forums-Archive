---
title: "Java - Downgrade to 1.6.0_35"
date: 2012-12-03
forum: Ubuntu Dev Link Forum
---

### Post by Marcus_Ophiuchus on 2012-12-03
I'm writing a java program in Eclipse, but it turns out that my distro is too recent for the target machine, which is running 6u35.

How do I downgrade to 1.6.0_35? I went to Oracle's website and the Ubuntu help for installing java and I found out that there's not an easy way to do it for Ubuntu anymore.

---

### Post by flavouride on 2012-12-03
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by QIII on 2012-12-03
May I ask why you wouldn't simply upgrade the target machine?

Java 6 reaches EOL in April 2013 (I noticed just now that I need to update the wiki since that has changed since I added that section) and it is also rife with security vulnerabilities.

---

### Post by Marcus_Ophiuchus on 2012-12-03
Target machine isn't mine to upgrade, it belongs to my school.

---

### Post by Jason80513 on 2012-12-05
If you want to use Oracle Java, it should be easy. The hard part is navigating the site to find the distribution you want. But basically, you extract the files and run Java. 

One alternative would be to put a copy of the later version of Java on the target machine. Then use that to run your application. There is no problem with running any number of different versions of Java on the same machine.

One thing though - you didn't say which version of Java you were starting from. Perhaps if you are on Java 7 and want to run on Java 6, you can just compile with a target of 1.6? If you haven't used Java 7-specific APIs and extensions, that might work for you.

---

