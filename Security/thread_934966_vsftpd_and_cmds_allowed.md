---
title: "vsftpd and cmds_allowed"
date: 2008-10-01
forum: Security
---

### Post by jm1610 on 2008-10-01
Hi people,

I have a problem configuring vsftpd.

When I add the following line to vsftpd.conf:
cmds_allowed=USER,PASV,PORT,SYST,RETR,QUIT,DIR,STOR,CWD,LIST,PWD

I can connect through the terminal on both Ubuntu and XP, but I get a 'WARNING! XXXX bare linefeeds received in ASCII mode' and the download is corrupted. 

Further,  I get a 550 permission denied error when trying to simply connect through Firefox or IE.

When I remove the line, I can connect fine through all and there are no download problems.

Basically, I want to allow uploads but disable the delete and this should be the way to do it????.

I suspect I am missing additional commands, but which?

Thanks all,

Jon.

---

