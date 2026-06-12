---
title: "SFTP and FTPS on same box?"
date: 2014-01-10
forum: Server Platforms
---

### Post by LHammonds on 2014-01-10
I setup FTPS (FTP + SSL) using vsftpd.

Now I need SFTP (SSH + FTP) but don't know if it is best to create it on a separate server or if they will co-mingle on the same server.  vsftpd was very finicky when I set it up and I'm slightly worried that making changes now could cause my existing service to be interrupted.

Any thoughts?

Thanks,
LHammonds

---

### Post by volkswagner on 2014-01-10
Doesn't SFTP simply utilize SSH protocol?  Do you need user management, quota and other features?

---

### Post by Kirk Schnable on 2014-01-10
SFTP just uses SSH.  I know of no reason why having both running on your box would cause any conflicts.

---

### Post by houstonbofh on 2014-01-11
I have both on some boxes.  And I use sftp on boxes with no ftp server.  It just uses ssh.

---

### Post by LHammonds on 2014-01-20
Thanks for your replies.  I was indeed able to add SFTP to my FTPS server without messing up SSH or vsftpd!

I took notes as I was doing it so I will eventually append my FTPS tutorial in my sig to include them.

Thanks,

LHammonds

---

