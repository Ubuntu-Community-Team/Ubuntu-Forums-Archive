---
title: "Difficult file permissions Problem. Writable – not Deleteable"
date: 2008-04-08
forum: Server Platforms
---

### Post by kyriakos1977 on 2008-04-08
Here is the situation:
1. tmp directory I want users to be able to write everywhere in  tmp but not to delete.
2. Samba server with security = share which means all users use the same nobody:nogoup ownership 
3. Admin group (@admins) which CAN delete the content of tmp

The solution so far
A script that executes once a day
        chmod -R 775 /tmp
        chown -R :@admins /tmp                  #this makes everything readonly 
        find tmp -type d -exec chmod 1777 '{}' \;     #directories writable

drwxrwxrwt 2 nobody seires 4.0K 2008-04-08 02:31 .
drwxrwxrwt 4 root   seires 4.0K 2008-04-09 01:35 ..
-rwxrwxr-x 1 nobody seires  62M 2008-04-08 02:31 1-ubuntu_install.ogg

So users may write or delete the contents for one day then everything changes to readonly and the user still can write to ANY directory.
This complies with all the above except the 3. the admin group CANNOT delete anything because the sticky bit allows only the owner and root to change the file not he owner group.

The problem starts here
from samba howto
“Within the UNIX file system anyone who has the ability to create a file can write to it. Anyone who has write permission on the directory that contains a file and has write permission for it has the capability to delete it.”
So if user nobody owns the directory or directory permissions are 777 everyone can write and everyone can delete. The only thing I found is the sticky bit which does not apply to groups

from 'man chmod':
"STICKY DIRECTORIES
When the sticky bit is set on a directory, files in that directory may 
be unlinked or renamed only by root or their owner. Without the sticky 
bit, anyone able to write to the directory can delete or rename files. The 
sticky bit is commonly found on directories, such as /tmp, that are 
world-writable."
As far as I know there is not a sticky bit for groups. And the SGID doesn’t help 
“If the SGID (Set Group Identification) attribute is set on a directory, files created in that directory inherit its group ownership”

Here is the important part of smb.conf. 
Admin users access tmp through disks with samba username and password. 
security = share
[disks]
        path = /disks/
        browsable = no
        read only = no
[tmp]
        path = /disks/tmp
        browseable = yes
        read only = no
        guest ok = yes

I tried a lot of things but nothing seems to work 
Any ideas?

---

