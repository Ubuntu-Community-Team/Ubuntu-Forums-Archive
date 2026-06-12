---
title: "Disable google authenticator for FTP user"
date: 2015-01-20
forum: Server Platforms
---

### Post by Rusty-83 on 2015-01-20
Hi, 
I'm in the process of setting up my first server, for non key-based SSH I have password + google authenticator however for FTP (vsftpd) I just want password no google auth for a dedicated FTP user.
Is this possible?

Thanks.

---

### Post by nerdtron on 2015-01-21
The way we are using google ftp upload it through scripts or ncftpput command. It's not secure as you will need to provide the password through the script itself or a separate file.

---

