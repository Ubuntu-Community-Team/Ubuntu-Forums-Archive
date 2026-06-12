---
title: "Recomendations on webserver permissions setup?"
date: 2009-10-05
forum: Server Platforms
---

### Post by brentrussell on 2009-10-05
I have a user account (gbrent) that is a sudoer. I am using vsftp as a ftp server. Whenever I upload files via ftp, the group is adm and not www-data. Folders have many permission issues too when they are uploaded.

Furthermore, I am adding 2 more user accounts (danielk,gabeb) that will not be sudoers. I would like them to have write access to any file that I upload via ftp in the /var/www/www.site.com/html/ directory.

What user groups should I set on what users? What should I chmod /var/www/www.site.com/html/ to? And how do I set vsftpd to auto chmod uploaded files so that we can all read write?

-Brent

---

### Post by brentrussell on 2009-10-07
Can anyone help me out on this?

---

