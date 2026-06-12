---
title: "java, firefox, and apparmor"
date: 2011-06-02
forum: Security
---

### Post by manthony121 on 2011-06-02
I am required to use a web site that insists that I use the latest version of java.  I followed every instruction to download jre1.6.0_25, created the appropriate links, and removed the old IcedTea and OpenJDK links.  However, the new java would not show up in about:plugins.  Eventually, I looked at /var/log/messages, and found:

Jun  2 08:32:32 otto kernel: [134194.302741] type=1503 audit(1307017952.223:300):  operation="file_mmap" pid=7896 parent=1 profile="/usr/lib/firefox-3.6.17/firefox-*bin" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/java/jre1.6.0_25/lib/i386/libnpjp2.so"

Several copies of this message appears whenever I refresh the about:plugins page.  Further digging showed this to be the type of thing that apparmor would say when a program tries to do something it is not authorized to do.  I have never really looked at apparmor, but it seems unlikely that my system configuration is so unique that nobody else has had this problem.

As I learn the ins and outs of apparmor profiles today, I thought I would put up this request to see if anyone just knows an easy fix for this problem.  TIA.

Ubuntu 10.04.2 LTS, Firefox 3.6.17, Mozilla Firefox for Ubuntu canonical - 1.0

---

