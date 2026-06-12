---
title: "Possible false positive; chkrootkit"
date: 2014-05-05
forum: Security
---

### Post by maperry on 2014-05-05
Platform here is Ubuntu 12.04 LTS.  A routine run of chkrootkit gave a warning of the following hidden file:    /usr/lib/jvm/.java-1.6.0-openjdk-i386.jinfo A check against the Debian Package manager ( dpkg -S ) seemed to recognise this file so the warning may well be a false positive. However, for my own peace of mind, can somebody tell me: 1.   Did chkrootkit show a false positive? 2.  If so, what is the pupose of the file .java-1.6.0-openjdk-i386.jinfo and why does it have to be hidden? Thanks in advance for any helpful answers. Mike. --

---

### Post by claracc on 2014-05-05
Please see: [http://ubuntuforums.org/showthread.php?t=1876109](http://ubuntuforums.org/showthread.php?t=1876109)

It seems a well known false positive.

I think, you had to ask the question in the security subforum, for more specialized advice. You can ask a moderator to move the thread there.

---

### Post by oldos2er on 2014-05-05
Moved to Security Discussions.

---

