---
title: "how to allow r,w,x to group but stop from deleting my files"
date: 2009-02-27
forum: Security
---

### Post by donaldd on 2009-02-27
The permissions on a directory of mine are 770 which I believe  allows users who are members of my group to read write and execute files that belong to it.
Please could someone tell me if there is a way to prevent any members of the group deleting my files although okay for them to create there own.
Thanks in advance.

---

### Post by movieman on 2009-02-27
Sticky bit?

---

### Post by bodhi.zazen on 2009-02-28
It is not clear from your post what you are wanting exactly. If someone can rw your file they can delete the contents of the file (even though sticky bits may prevent the user from deleting the file, it would be empty).

See :

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html) 
    Set Group ID : chmod g+s dirname 
 
    OR (ACL works better) 
 
    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741) 
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)

---

### Post by donaldd on 2009-03-01
Thanks all for the answers I added an acl

---

