---
title: "[SOLVED] I want to make a anonymous FTP server."
date: 2008-07-24
forum: Server Platforms
---

### Post by Masoris on 2008-07-24
I tried to make a anonymous FTP server on my PC. So I did it:
[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

I could connect to my FTP server anonymously now. So I can read, write files. But I cannot delete file as anonymous.

Is there any guide to run perfect anonymous FTP server?

---

### Post by SNuxoll on 2008-07-24
Try asking in the server forums, you'll probably have better luck.

---

### Post by df6269 on 2008-07-24
Change the file permission.

---

### Post by Oldsoldier2003 on 2008-07-24
> **Masoris said:**
> I tried to make a anonymous FTP server on my PC. So I did it:
[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

I could connect to my FTP server anonymously now. So I can read, write files. But I cannot delete file as anonymous.

Is there any guide to run perfect anonymous FTP server?

Generally speaking anonymous/guest users aren't allowed to add and delete files, anonymous ftp is usually just file serving method. Adding and removing files is normally done via other methods such as scp/ssh/sftp from an authorized user/admin.

---

### Post by Oldsoldier2003 on 2008-07-24
Moved to server platforms, in order to gain more visibilty from the server gurus :)

---

### Post by wejick on 2008-07-24
Hai this is my first post! sorry for my bad in english :).
I think you can try vsftpd. You can setup a ftp server with a ```
man vsftpd
``` or ```
man vsftpd.conf
```

Oh and you must uncoment ```
#write_enable=YES
``` so it become ```
#write_enable=YES
``` and add this option  
```
anon_other_write_enable=YES
``` to enable allow anonymous user to burn your files.

---

