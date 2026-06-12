---
title: "server won't update?"
date: 2010-02-13
forum: Server Platforms
---

### Post by mendo on 2010-02-13
when i login to my ubuntu server via putty, it is telling me that 2 packages can be updated.  i run 'sudo apt-get update', but get no notice of any packages updating.  the next time i login to my server, there it is: '2 packages can be updated'  wtf?

thanks.

---

### Post by CharlesA on 2010-02-13
All that does is update the source list. You need to run "sudo apt-get upgrade" to install updates.

---

### Post by mendo on 2010-02-13
ok - so i ran sudo apt-get upgrade and that was what i was looking for.

---

