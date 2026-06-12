---
title: "JDK, JRE 1.5 on SPARC"
date: 2007-04-17
forum: Sun Sparc Users
---

### Post by gnudomain on 2007-04-17
Hi, to everyone.
I'm using Ubuntu-server for SPARC. I'm very glad, everything works fine, but there's a "problem".

Project [COLOR="Blue"][blackdown]("http://blackdown.com")[/COLOR] has ported jdk and jre until 1.4.1 version, but it seems that the project is completely dead and it isn't going to continue. The problem is that I need the jre 1.5 in order to run a benchmark (SPECjbb2005), and I would like to know if there's any chance for the project to be continued. From the other side I'ld like to know if there's any other form to get a similar environment with gnu software like Kaffe or Gij.
Thanks a lot. Im very sorry if my english level isn't very good.

[COLOR="Blue"][alfredo]("mailto://alfredo@gnudomain.org")
[gnudomain.org]("http://gnudomain.org")[/COLOR]

---

### Post by erm67 on 2007-04-17
The only options available I think are gcj/gij in main and sablevm  or kaffe  in universe, of course are not particularly compatible. gcj/gij+gnuclasspath should be fairly compatible with jre 1.4.
The last linux-sparc binaries from blackdown are here:
[ftp://ftp.gwdg.de/pub/languages/java/linux/JDK-1.4.1/sparc/beta/](ftp://ftp.gwdg.de/pub/languages/java/linux/JDK-1.4.1/sparc/beta/)
but I don't know if they work and they have security issues.

---

### Post by gnudomain on 2007-04-18
A lot of thanks :)  
I will probe for every option.

---

