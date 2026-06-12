---
title: "Group rights problem"
date: 2009-08-14
forum: Server Platforms
---

### Post by snopyland on 2009-08-14
Hi,
 
I have configured ldapclient in my ubuntu 9.04 to authenticate against Novell ldap server. In ubuntu,  I can successfully login and run "getent group" to get the ldap groups informaton.
 
I can get the following entry if I run "getent group ldapgp1"
 
ldapgp1:*:506:ac1,ac2
 
and I have directory "dir1" 
 
rwxrwx---+ 2 root    ldapgp1   1024 2009-08-14 12:31 /dir1
 
 
I think that if I can login ac1, I can access /dir1 as ac1 is a member of ldapgp1
 
However, I cannot access /dir1 by using ac1 account. It shows permission denied.
 
Anyone can give me some hints ?? 
 
How can I make use of the ldap group membership to access the directory in my ldapclient?
 
 
Any comments are appreciated.
 
Thanks.

---

### Post by cdenley on 2009-08-14
Did you login AFTER changing the group membership?

---

