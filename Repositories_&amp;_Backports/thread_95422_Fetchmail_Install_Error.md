---
title: "Fetchmail Install Error"
date: 2005-11-26
forum: Repositories &amp; Backports
---

### Post by Corlian on 2005-11-26
Whenever I install anything, the following happens:

```
Preconfiguring packages ...
Selecting previously deselected package logjam.
(Reading database ... 74177 files and directories currently installed.)
Unpacking logjam (from .../logjam_4.4.1-2_i386.deb) ...
Setting up fetchmail (6.2.5-13ubuntu3.1) ...
chown: `fetchmail:nogroup': invalid group
dpkg: error processing fetchmail (--configure):
 subprocess post-installation script returned error exit status 1
Setting up logjam (4.4.1-2) ...

Errors were encountered while processing:
 fetchmail
dpkg run finished!
```

It seems similar to the problem here:

[http://ubuntuforums.org/showthread.php?t=53581&highlight=fetchmail+error](http://ubuntuforums.org/showthread.php?t=53581&highlight=fetchmail+error)

Which has a bugzilla entry here:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=13044](http://bugzilla.ubuntu.com/show_bug.cgi?id=13044)

Is the bugzilla answer the answer for me?  And if so, how might someone who doesn't know about init scripts go about fixing it?  It's annoying and stalls the computer.

I have Kubuntu Breezy updated from the extended repositories.  This problem seems to have been happening since the beginning of my recent fresh installation.

---

