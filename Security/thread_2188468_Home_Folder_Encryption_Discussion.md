---
title: "Home Folder Encryption Discussion"
date: 2013-11-17
forum: Security
---

### Post by SchnappiJedi on 2013-11-17
Assuming the physical security of a machine or VM is accounted for (aka VM hosted on a encrypted drive) does Home Folder encryption serve a purpose?

For example with home folder encryption a sudo user can still access the home folders of other non-sudo users (although I am unsure of the exact qualifications that allow an account to access other accounts home folders).

Does home folder encryption provides any security in terms of protecting a machine against an intruder already in the system? For example would an intruder accessing the system remotely with no sudo access have a harder time getting into the home folder of a sudo user if home folders are encrypted as opposed to if they aren't?

---

### Post by public3 on 2013-11-19
If the folder is encrypted, the user will need to put in HIS password to unencrypt it. Period. 
The root user won't be able to do anything until the home folder is unencrypted. 
That said, you typically unencrypt partitions BEFORE starting the machine. 

Home folder encryption will secure your files from prying eyes in the case that they force a restart of your computer (hoping to use an installation disc for example) and try to view your files by circumventing the currently logged in user. 

HTH

---

### Post by SchnappiJedi on 2013-11-25
> **public3 said:**
> If the folder is encrypted, the user will need to put in HIS password to unencrypt it. Period. 
The root user won't be able to do anything until the home folder is unencrypted. 
That said, you typically unencrypt partitions BEFORE starting the machine. 

Home folder encryption will secure your files from prying eyes in the case that they force a restart of your computer (hoping to use an installation disc for example) and try to view your files by circumventing the currently logged in user. 

HTH

What you stated has to be incorrect. I just logged in via SFTP with a sudo account and was able to open and view files in home folder of other users...

---

### Post by cariboo on 2013-11-25
IF you are logged into the system, and have unencrypted the partition, of course a user with elevated permissions is going to be able to view the contents. I'd suggest you log out of the target system, and try again.

Encrypting a partition/system only works if the user isn't logged in. Once the user logs in, anyone can access the partition, especially if you have the standard Ubuntu home partition permissions set.

---

