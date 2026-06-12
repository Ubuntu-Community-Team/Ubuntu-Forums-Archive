---
title: "Easy way to upload files"
date: 2007-10-05
forum: Server Platforms
---

### Post by don_c on 2007-10-05
I have set up a LAMP server and all is running OK.  All I want to do now is setup FTP access to the relevant folder and start developing the website.  I have tried vsftpd and pure-ftpd - both allow me to login and download but not upload.  I only want access for me as a user - no anonymous access.

I assume I have set file/folder permissions correctly since I can edit files directly on the server.  However, when logged in remotely I can't create folders or upload files.

I have searched around and found lots of very complicated setup routines for proper FTP servers with separate folders and anonymous access.  I don't want this, only an easy way to get my files onto my webserver to do what I really want to do - develop PHP/MySQL websites...

Any help would be much appreciated...

---

### Post by MJN on 2007-10-05
Unless you have a specific reason for requiring it I would scrap the use of FTP and use something more secure, and simpler to configure, like SFTP.
 
If you install openssh-server you will get the SFTP subsystem by default. Then all you need to do is pick a client of your choice that supports SFTP (e.g. Filezilla - works on Linux and Windows) and you are good to go.
 
Mathew

---

### Post by don_c on 2007-10-05
Thanks - I threw away the FTP server(s) I was trying - SFTP through Filezilla works fine.

---

