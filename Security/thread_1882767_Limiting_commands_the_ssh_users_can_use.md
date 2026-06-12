---
title: "Limiting commands the ssh users can use"
date: 2011-11-17
forum: Security
---

### Post by clubbing80s on 2011-11-17
Hi.
A year a go I came across a script that replaced the /bin/bash user shell in /etc/password. When the user logged in they could only execute commands that where approved, in this case it was for git,svn,and cvs repositories. It was written in perl or python ....

Anyone know of such a script or something similar?

Thanks
G

---

### Post by Lars Noodén on 2011-11-18
Yes, a restricted shell (e.g. [rbash](http://manpages.ubuntu.com/manpages/precise/en/man1/rbash.1.html), rksh) can do that.  You'll also need to set all the allowed programs or links to them into a directory and then set their PATH to that directory.

---

