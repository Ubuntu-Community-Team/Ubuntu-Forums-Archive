---
title: "Can not change attributes via FTP"
date: 2006-06-07
forum: Server Platforms
---

### Post by skafiskafnjak on 2006-06-07
I do not have permission to create folder in **WWW** directory via **FTP**.

I use **vsftpd **

Is it because of **vsftpd.conf** or because of system settings?

Can anybody help? I want to be able to upload and manage files in WWW via FTP.

(Dapper LAMP)

Thanks

---

### Post by mrcowcow on 2006-06-07
Chmod the /var/www folder to 777 (assuming that is your www directory). You will be able to read/write files in that directory then.

---

