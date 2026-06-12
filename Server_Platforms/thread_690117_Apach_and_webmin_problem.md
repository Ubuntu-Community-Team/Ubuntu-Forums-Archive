---
title: "Apach and webmin problem"
date: 2008-02-07
forum: Server Platforms
---

### Post by ubacct3 on 2008-02-07
I've installed both, and I can access webmin, but when I try to apply a change, the computer hangs forever.

I think it has something to do with not having root access to log into webmin.  I can have sudo access, but I'm not sure how to log in with that permission in webmin since it's web based.

Any ideas?

---

### Post by freebeer on 2008-02-07
I'm no expert, but it sound like a permissions issue.  Webmin is trying to update a file(s) without the right permissions.  Check the ownships of the files you're trying to change and compare that with the group that webmin is running with.  You might also want to check to see if the webmin user is also a member of the "admin" group (which will give it sudo privileges.)

---

