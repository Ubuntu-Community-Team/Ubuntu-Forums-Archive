---
title: "How to disable Wine for some users"
date: 2009-09-12
forum: Wine
---

### Post by UranUtan on 2009-09-12
Hi,

Using Ubuntu 9.04 x32 and Wine 1.1.29. On this machine User1 has admin rights and User2 is a low privileged user.

I would like to disable the usage of Wine for User2. This user must not be able to run any Windows exec.

It is possible to hide Wine menu item. However, the user can still go on the web, use Firefox and download a Windows executable and select "Open with Wine".

I have tried to look if there is a Group dedicated to Wine but there is none. With VirtualBox for example, you can select which user can use VirtualBox by making them members of the vboxusers group. Is it possible to implement similar logic to Wine ?

Thanks in advance for any help.

---

### Post by jasonditz on 2009-09-13
How about giving User 1 ownership of /usr/bin/wine using chown and then:

chmod 700 /usr/bin/wine

---

