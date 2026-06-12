---
title: "no rights, read only rights and read &amp; write rights to a file"
date: 2009-03-01
forum: Security
---

### Post by latev on 2009-03-01
What is the best way to implement the following scenario in Linux and in Samba in particular:

A file secrets.txt exists and I'd like to have 3 different levels of access rights in effect to it, that is 3 different groups - Group1, Group2 and Group3, where

* Group1 has no rights at all to that file - no read, no write nothing
* Group2 has read only rights and
* Group3 has read and write rights

That way depending on what rights I decide to assign to a particular user I can just add that user to be a member of the appropriate group

So what permissions, groups etc should I create and assign to the secrets.txt file?

/I don't want these groups rights to interfere in any way with the original owner of the secrets.txt file - ie if user1 is the original creator of the secrets.txt file I wouldn't want user2 who is a member of the Group3 (all access) to be able to modify or even read user1's files/

---

### Post by bodhi.zazen on 2009-03-01
I think your best bet is to use acl :

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741) 
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)

Otherwise, there is really no way to do this with basic permissions. Your other options work be more complex such as using SELinux or Apparmor or some such.

---

