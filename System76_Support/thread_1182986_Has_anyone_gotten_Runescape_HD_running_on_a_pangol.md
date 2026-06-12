---
title: "Has anyone gotten Runescape HD running on a pangolin performance?"
date: 2009-06-09
forum: System76 Support
---

### Post by xakh on 2009-06-09
Ever since Jaunty, I've been trying after every update, but I still can't get the signed Java Applet required for Runescape to run in high detail mode. I could really use some help here. Anyone got an idea on how to fix it?

---

### Post by thomasaaron on 2009-06-09
Have you downloaded Java's sun...

sudo apt-get install sun-java6-jre

...and configured it to be the primary java...

sudo update-alternatives --config java

?

---

### Post by xakh on 2009-06-09
the output of that second thing was this:
  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-4.3
          4    /usr/lib/jvm/java-gcj/jre/bin/java

It was set to 1, which wasn't working, so I tried setting it to 2. Still nothing.

---

### Post by thomasaaron on 2009-06-09
Check out this thread. It looks like these guys got it running in HD.
[http://ubuntuforums.org/showthread.php?t=844997](http://ubuntuforums.org/showthread.php?t=844997)

---

### Post by xakh on 2009-06-09
Just to be clear, it worked fine in 8.10. Once I upgraded to 9.04, the signed app went to heck. All the stuff in that thread applies to 8.04 and 8.10, which isn't really my problem.

---

### Post by thomasaaron on 2009-06-10
Ah, I see what you mean now. It looks like there was definitely some regression in Jaunty. There are threads all over the place concerning the HD version in Jaunty.

---

