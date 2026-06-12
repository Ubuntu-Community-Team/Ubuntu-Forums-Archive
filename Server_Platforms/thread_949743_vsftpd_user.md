---
title: "vsftpd user"
date: 2008-10-16
forum: Server Platforms
---

### Post by vegas588 on 2008-10-16
What is the "best" way to create a user with a password for ftp (vsftpd) and give that user read/write access to the ftp folder, which in this case is /home/ftp

I have read that you need to create a local user, assign password, but how do I apply that user to the vsftpd config?

---

### Post by HermanAB on 2008-10-16
The easiest way is to create a new user and set his home directory to /home/ftp

Yes, it really is that simple!

Cheers,

Herman

---

### Post by eurohim on 2008-10-16
How about just add the new user the FTP users group that vsftpd creates?

---

