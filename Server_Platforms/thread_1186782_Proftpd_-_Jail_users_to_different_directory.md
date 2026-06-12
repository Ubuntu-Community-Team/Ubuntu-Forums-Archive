---
title: "Proftpd - Jail users to different directory"
date: 2009-06-13
forum: Server Platforms
---

### Post by ubila on 2009-06-13
Hello :D

Im trying to jail ftp users to a different directory other then home.

At the moment users can successfully log in to ftp using their ubuntu system username and password. But this jails them to /home/theirusername

Im trying to setup ftp accounts for my hosting.
So i need the accounts to jail them to their webfiles 

eg:
/var/www/client/clientname/

Had a good search around cant seem to find how to do it.
Any help would be appreciated

Thanks

---

### Post by ubila on 2009-06-14
17 views and no ideas ? :(

---

### Post by HermanAB on 2009-06-14
The easiest way is to use the user wizard or usermod and change the home directory of the user to whereveryouwant.

---

