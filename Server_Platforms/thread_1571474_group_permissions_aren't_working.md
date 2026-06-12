---
title: "group permissions aren't working"
date: 2010-09-09
forum: Server Platforms
---

### Post by mortona42 on 2010-09-09
i created a directory in my webserver as well as a group "webdevs" which I want to give write permissions to, and include my user so that i can edit.

i used [addgroup webdevs] then [adduser MYUSER webdevs].

then [sudo chown root:webdevs MYDIR]
then [sudo chmod 774 MYDIR]

when I try to cd to MYDIR under MYUSER, I get permission denied.

what did I do wrong?  thanks.

---

### Post by spjackson on 2010-09-09
You need to log in again for you to get the webdevs group.

---

### Post by jbrown96 on 2010-09-09
It would be better to set the permissions on the folder to be 2774, so that any newly created folders will be owned by $USER:webdevs

---

### Post by bodhi.zazen on 2010-09-09
> **spjackson said:**
> You need to log in again for you to get the webdevs group.

Or start a new shell ;)

---

