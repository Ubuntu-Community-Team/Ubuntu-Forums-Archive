---
title: "samba_backup tar: ./private: file changed as we read it error"
date: 2013-11-19
forum: Server Platforms
---

### Post by clayb226 on 2013-11-19
I have tried to use the back up utility that comes, packaged, with Samba4, and keep getting this error. It was my understanding that I should be able to run the backup while online, and I did get it to run, but not consistently, every time. I was curious if anyone else has used this utility, and if so, did you have this problem, did you have to develope a work around??? Thanks.

---

### Post by nerdtron on 2013-11-19
I think it would be a lot safer if you stop accessing your samba share or stop the samba service first so that no files will be changed while you do the backup.

---

