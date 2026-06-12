---
title: "restrict ssh/ftp/sftp users to home directory"
date: 2011-11-05
forum: Security
---

### Post by AskTell on 2011-11-05
what should i do to restrict my sftp users to home directory, does sftp follow the vsftpd.conf? I've followed some instructions found online but non of them have worked.

---

### Post by dirtrider1 on 2011-11-06
What you want is called a chroot jail for sftp users - [http://www.ericstockwell.com/?p=54](http://www.ericstockwell.com/?p=54)

---

### Post by AskTell on 2011-11-09
that did the trick, ty!

---

