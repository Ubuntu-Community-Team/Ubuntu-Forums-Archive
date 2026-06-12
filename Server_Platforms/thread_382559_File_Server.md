---
title: "File Server?"
date: 2007-03-12
forum: Server Platforms
---

### Post by lawentzel on 2007-03-12
We (a friend of mine and myself) installed the Ubuntu server on an old server here at work.  I kept telling him it is primarily set up as a web server.  He would like to use it as a file server.  Can it be used as such?  If so, what services do you need to add or setup.  What would you need to do to setup multiple logins?  Any help in these matters would be greatly appreciated.  Thank you in advance.

Lee

---

### Post by Aberrix on 2007-03-12
try samba for filesharing.

otherwise if this is going to be strictly a fileserver and nothing more (ie: web/mail/etc) I would suggest [FreeNAS]("http://www.freenas.org").

---

### Post by cyris| on 2007-03-12
Samba is the way to go, or FTP

---

### Post by Brazen on 2007-03-12
Yeah, he just needs to install Samba to use it as a file server.  Information is in the official Ubuntu documentation.  I hope he is using Dapper Server.

---

### Post by rennen01 on 2007-03-12
> **Brazen said:**
> Yeah, he just needs to install Samba to use it as a file server.  Information is in the official Ubuntu documentation.  I hope he is using Dapper Server.

Should we not be using 6.10 as servers yet, in your opinion?

---

### Post by Mr. C. on 2007-03-12
How you share files depends on the needs of the clients.  There are many ways to share files, and others have already mentioned some (Samba, FTP, NFS, WebDav).  If you need more advice as to direction and how it will impact the web server (and vice versa), please share more details of your environment and your goals.

MrC

---

### Post by Brazen on 2007-03-12
> **rennen01 said:**
> Should we not be using 6.10 as servers yet, in your opinion?

correct.  There are many reasons to stick with Dapper.  Since it has LTS, it will be supported with security and bug fixes long after support for Edgy is dropped.  Also, Edgy was meant to be more cutting edge at release time than Dapper.  They wanted to try new things and new features, which is cool for testing or for desktop use, but not good for business use where reliability is number 1.

---

### Post by rennen01 on 2007-03-12
> **Brazen said:**
> correct.  There are many reasons to stick with Dapper.  Since it has LTS, it will be supported with security and bug fixes long after support for Edgy is dropped.  Also, Edgy was meant to be more cutting edge at release time than Dapper.  They wanted to try new things and new features, which is cool for testing or for desktop use, but not good for business use where reliability is number 1.

Thank you.  I will proceed using Dapper. :)

---

