---
title: "Revert everithing installed/updated by some scripts"
date: 2017-02-28
forum: Server Platforms
---

### Post by upcast.visitor on 2017-02-28
Hello, I have some Python scripts for installing and updating some packages on my Ubuntu Server 16.04.1 LTS. How can I revert back all the work that these scripts did? Thank you in advance.

---

### Post by howefield on 2017-02-28
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by Habitual on 2017-02-28
Have a look at /var/log/dpkg.log

---

### Post by upcast.visitor on 2017-02-28
I've seen this log. May be it's possible to parse it and write a new script to undo all the work. But this is not an easy way. May be in Unix exist command like 'user@comp:~$ uninstall_all_packages -from_datetime 'datetime'' ?

---

### Post by Habitual on 2017-02-28
Sorry, "easy" got you in this mess.
That's all I have.

---

