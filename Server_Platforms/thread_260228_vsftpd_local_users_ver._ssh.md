---
title: "vsftpd local users ver. ssh"
date: 2006-09-18
forum: Server Platforms
---

### Post by mslonik on 2006-09-18
Dear All,

Problem that I encounter was already touched on the forum, but left not answered yet:

On my machine (Kubuntu 6.06.01 Dapper Drake) there is vsftpd server installed. There are several local users. I would like for local users to have access to ftp accounts but NOT to let them log to shells remotely (i.e. with use of ssh clients).

I have already tried to change shells of local users to /bin/false or /bin/true. Neither of them let to authenticate local users to vsftpd accounts. How to solve this problem?

Any help is very appreciated.

Regards,
mslonik

---

### Post by bswilson on 2006-09-18
Did you try changing their login shell to /bin/nologin?

---

### Post by mslonik on 2006-09-18
Thanks for reply.

Yes, I did. In fact there is no /bin/nologin or /sbin/nologin application in Kubuntu system.

Other clues?
mslonik

---

