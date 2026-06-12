---
title: "unix-to-samba password sync (and vice versa)"
date: 2010-07-28
forum: Server Platforms
---

### Post by z61P on 2010-07-28
I'd like for the server (10.04) to keep samba passwords and unix passwords "in sync"; i.e. when a user changes his unix password (via passwd), his Samba password is automatically changed to match the unix password. Similarly, when a user changes his samba password (via smbpasswd), then his unix password is changed to match. 
 
smb.conf seems to make provision for this; following are the applicable entries from my smb.conf: 
 
```
 
obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
 

``` 
 
libpam-smbpass is installed
smbclient is installed 
 
However, there does not seem to be any password sync-ing in either direction. As a non-root user I can change my unix password successfully, but it doesn't appear to have any effect on the smb password. This, as evidenced by the fact that I can continue to access my share from Windows without being prompted to enter a new password. 
 
Also, I'm unable to change my smb password at all: 
 
tpmoore@ubuntu1:~$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE
 
What have I missed? :( 
 
Thanks,
z

---

### Post by flatline on 2010-07-28
I'd suggest running through the steps here: _[http://jaka.kubje.org/infodump/2007-05-14-unix-samba-password-sync-on-debian-etch/](http://jaka.kubje.org/infodump/2007-05-14-unix-samba-password-sync-on-debian-etch/)_

---

### Post by z61P on 2010-08-01
Ach!  I think the password sync has worked fine all along; I think it was my test methods that were faulty. I was using a Windows PC to run my tests, adding and deleting a file from the share. I was expecting the server (Ubuntu) to prompt the Windows user for the new password, but it did not; it continued to add and delete files. 

When I tested using the smbclient from another Ubuntu box, I got the expected behavior as I changed passwords using "passwd" and "smbpasswd". I still don't understand everything I saw from the Windows PC, but the Samba password sync clearly works quite well as is. 

Best Rgds,
z

---

