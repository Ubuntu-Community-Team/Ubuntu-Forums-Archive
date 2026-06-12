---
title: "Subversion 1.2.x"
date: 2005-07-28
forum: Requests
---

### Post by bugmenot on 2005-07-28
Backporting Subversion 1.2.x from Breezy to Hoary would help Subclipse/Eclipse users, because they need Subversion 1.2.x for the latest Subclipse version (which also contains important bugfixes which are not available for old Subclipse versions).

---

### Post by dvarnes on 2005-08-03
Yes please, this is a real show-stopper for Eclipse/Subclipse users.  

If svn 1.2.x is backported can you please ensure that the JavaHL bindings are built by default in the package ?

thanks a lot for your work !
davidv

---

### Post by DarkSilver on 2005-08-15
UP !!!

please ...
it is my last blocking thing in Hoary.... and Breezy is still too buggy to be useable...

---

### Post by aouie on 2006-06-14
local repository with subclipse & javaHL for Dapper.

If you are using subversion and eclipse (and subclipse), and would like to access a local repository using the file:// protocol then you need to install libsvn-javahl. Then start eclipse with "eclipse -vmargs -Djava.library.path=/usr/lib/jni/".
I am using eclipse 3.1 (custom installation) with subclipse 1.0.2 and libsvn and libsvn-javahl from the Dapper repositories.
Sincerely,
Aouie

---

