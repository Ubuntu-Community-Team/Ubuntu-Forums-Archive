---
title: "Windows 10 Group Samba Sharing"
date: 2018-08-13
forum: Server Platforms
---

### Post by dogchow101 on 2018-08-13
Forgive me for I am new to Linux in general and am learning as I go. I work for a small company and have limited IT support, so I have thrown myself into the mix of people trying to fix things as needed.
We have Ubuntu 18.04 LTS server edition installed on a Dell Poweredge r910 server. We have shares set up (attempting to use groups to limit access to files), and are able to access/readwrite/excute files in the shared directories from our Windows clients. However we continue to experience files that are inaccessible. The issue typically happens when one person logged in under a different share username saves (updates and changes made to a file) that was created by another user. After the save command, the original creator of the file (or previous user with access) can no longer open the file.
A large majority of the time i have to update (with chown command) the user and group attributes of the file, then access is restored, until a user (which is within the group permission of the file of course)  makes changes and saves them, then the ability for any user other than the last person to save the file goes away.


- A few notes;
The smb.conf file has been customized
I have learned that the files that are being created have ACL information included on their attributes
I have learned that alot of the information available on the web about Samba and sharing is admittedly not relevant due to changes, one such change being that ACLs were not turned on by default in versions before 18.04 LTS server, however now they are.

I believe that ACLs being engaged is part of my issue, but I am not entirely sure.
If anyone has some thoughts on where to go from this point I would be most interested in hearing from you.

Thanks!!

---

