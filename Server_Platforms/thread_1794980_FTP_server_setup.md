---
title: "FTP server setup"
date: 2011-07-01
forum: Server Platforms
---

### Post by LoneWolfJack on 2011-07-01
hi folks,

I have a problem getting vsftp to work properly on 10.04.

even if I stop vsftp, I can still log in via ftp. the ftp client also says something about time being localized, which is something I disabled 
in my vsftp.conf.

so it appears there either is a different ftp program running that I can't identify, or vsftp is constantly working with a different conf file (I only have one vsftpd.conf on my system though).

help?

---

### Post by LoneWolfJack on 2011-07-01
Ok, I knew I would figure it out myself as soon as I post here. Apparently, there is a sftp-server running by default (/usr/lib/openssh/sftp-server).

---

