---
title: "Upstart service ownership - when does it change?"
date: 2012-08-01
forum: Server Platforms
---

### Post by Bobbus on 2012-08-01
Best practice says that each process should be owned by it's own individual user. For example: Apache is owned by the apache user, Postfix is owner by the postfix user.

Lets say I've installed pure-ftp and created a 'pureftp' system user that I want to own the pure-ftpd daemon.

Since it's launched at boot time by upstart, the files are owned and run by root.

At what point, and how, do I set the ownership of pure-ftpd to the prureftp system user?


Thanks for taking the time to look at this.

---

### Post by spjackson on 2012-08-01
Does [this ]("http://upstart.ubuntu.com/wiki/UnprivilegedUsers")help?

---

### Post by Bobbus on 2012-08-01
Thanks for the link.

I could hack the pure-ftpd init.d script to launch it under a different user …… but neither apache not Postfix do it this way this way within their scripts.

There must be a more elegant way of doing this?

---

