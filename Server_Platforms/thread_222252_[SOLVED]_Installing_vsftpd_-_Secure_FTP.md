---
title: "[SOLVED] Installing vsftpd - Secure FTP"
date: 2006-07-24
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-07-24
Hey, I'm currently looking into installing SFTP through vsftpd, would this make it easier to use secure file transfer between the computers in my network?  I already have SSH servers running and security measures implemented for them.

Thanks for the help, in advance.

---

### Post by LordHunter317 on 2006-07-24
vsftpd doesn't implment SFTP.

SFTP is part of the SECSH (SSH) protocol.  It isn't FTP nor really related to FTP at all.

vsftpd implments FTP and FTP/SSL.  

If you already have SSH working, vsftpd will just be more complicated.

---

### Post by RavenOfOdin on 2006-07-24
Hmm  . . .sounded like it would have been more related to SFTP than anything else. :confused:

Okay.  I'll stick with SSH then.

---

