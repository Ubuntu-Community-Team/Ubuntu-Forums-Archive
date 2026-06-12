---
title: "Samba Permission Setting"
date: 2010-03-27
forum: Server Platforms
---

### Post by STW on 2010-03-27
I am setting up a new file server using Ubuntu 9.10 server with Samba. The Ubuntu file server is connected to a small office LAN, with 14 other clients (all running Windows, either XP or Vista).

May I know whether it is possible to set the permission of the files & folders in the Ubuntu file server to prevent unauthorized copying of files by users (clients) which are only granted with the "read only" authority?

---

### Post by stlsaint on 2010-03-27
Copying is not editing so by giving users a read only access they will still be able to copy it. As far as my understanding goes.

---

### Post by STW on 2010-03-28
Is there anyway to set the permission, so that the user can only read the files on the Ubuntu file server, but can't copy the files?

---

### Post by fang0654 on 2010-03-29
I don't think that is possible - if you can read, you can copy.  Even if it is opening a file, then save as somewhere else, it is still copying.  What are you trying to accomplish?

---

### Post by Vegan on 2010-03-29
Short of coddling everything in a database with a special front end, you cannot prevent unauthorized copies.

That level of security is outside the usual security model in use today.

---

