---
title: "FTP access denied"
date: 2011-08-23
forum: Server Platforms
---

### Post by kollol on 2011-08-23
Hello,

i have configured vsftpd on my ubuntu server and configured PAM for authentication. the login process is working fine but the user cannot write anything on its own home directory. is there any other setting required that probably i have missed?

can anyone guide me on this please!!

Regards,
Kollol

:(

---

### Post by Sanados on 2011-08-23
just replied to another thread which i mentioned an information that could be viable for you aswell.


What shell do those users have?
If those users have /bin/false as shell you need to add /bin/false to /etc/shells for ftp-users need a valid shell to be able to login, but shall not have a bash to prevent ssh login.

---

### Post by kollol on 2011-08-23
Hello,

The user have /bin/bash shell and there will not be any issue with the ssh access. but in the /etc/passwd file i can see a user "ftp" whose shell is /bin/false. do i need to change the users shell to /bin/false and then add /bin/false to /etc/shells? or only adding /bin/false to /etc/shells will work?

Kollol

---

### Post by Sanados on 2011-08-23
seems no work needs to be done.

user ftp ist generic is of no interest :)

does the user get a directory listing?
(next would be to check the directory permissions if the user actually has the right to write to those directory.

On the other hand if you remap the logging user to a defined user/group combination ... make sure that that user is allowed to write to the directories.

And more info in the logs?

---

