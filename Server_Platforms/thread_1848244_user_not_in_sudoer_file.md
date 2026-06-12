---
title: "user not in sudoer file"
date: 2011-09-22
forum: Server Platforms
---

### Post by mlinux on 2011-09-22
I just changed the "www-data" user name to "admin" via webmin and now I can not use my own user name to login to webmin. Also I was unable sudo to edit any system file nor shutdown the server. What can I do?

---

### Post by Lars Noodén on 2011-09-22
You may have to boot into rescue mode from the CD to undo the changes you made.

---

### Post by mlinux on 2011-09-22
Why changing the user "www-data" to "admin" void my sudo? I just wanted the system to send out the account activation email to user with the mail from "admin".

---

