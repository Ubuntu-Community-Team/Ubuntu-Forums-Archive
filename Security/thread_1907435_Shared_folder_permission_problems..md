---
title: "Shared folder permission problems."
date: 2012-01-11
forum: Security
---

### Post by KevinIN72 on 2012-01-11
I have a computer setup running Ubuntu 10.10 that has a shared folder set up for different people to access the folders. The sharing system is working perfectly only some people have access to directories and are able to put files in them. The issue I am having is when a file is created on a desktop then moved to the shared folders it is not setting permission properly. An example of this is when a spreadsheet is made and placed in the first level of the shared system, people with access to the first level and open the spreadsheet but it is only read only. I am trying to find a way so when files are placed in a directory the permission set on the directory apply to the files inside. I have been manually reapplying permission to the files in the directory but I would like to find a solution, I have been looking into setting up ACL's with Eiciel but I am not sure if this is the correct route to fix my issue. 

Setup information:
Mixed networking including Windows XP and Windows 7
Ubuntu 10.10 set up with VPN access and Samba sharing
Shared setup:
/shared/level1 > level 1 group access
/shared/level2 > level 1 and 2 group access
/shared/level3 > level 1, 2 and 3 group acess

---

### Post by lemming465 on 2012-01-21
Having the "set group id" bit on will improve the situation some, as it will encourage creation of files where the group owner is the directory group owner rather than the user group owner (BSD semantics, rather than AT&T).  E.g. ```
 find /shared -type d -execdir chmod g+s . \;
```

However, that won't get around the problem that file permission bits and groups are strongly influenced by the creator's umask and groups.  If the file isn't created with group write permission in the first place, and is moved (same inode) within a filesystem rather than copied (new inode), you may have to fix it up after the fact.
Making /shared or its subdirectories being mount points for separate partitions will encourage copying rather than moving.

---

