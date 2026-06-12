---
title: "Transfer to new server."
date: 2008-01-22
forum: Server Platforms
---

### Post by jbMSU on 2008-01-22
We've just purchased a new dell blade server and installed fedora core 8 on it.  We need to transfer all of our information from the previous server to the new one in a way that's absolutely minimal on down time. 

Any suggestions on where to start?  What directories to carry over?  Which not to worry about?

---

### Post by fearevilleet on 2008-01-22
Guess it would depending what you need to transfer. If you have a lamp setup you should be able to just copy /var/www over to the new server. You will also need to make dumps of the mysql databases then transfer them over to the new server. Sounds like rsync via ssh would be the best way to do this.

---

### Post by jbMSU on 2008-01-23
Thanks.

---

