---
title: "Bug in Webmin Samba module prevents groups to be recognized"
date: 2009-05-17
forum: Server Platforms
---

### Post by jesuspresley on 2009-05-17
Hi, 
I was struggling around with this for at least two days - so I think I have to let everybody know:

In the Samba module for webmin, I was not able to grant rights to user groups, because the syntax stored in the module is wrong. 
Instead of saving a line like:

```
valid user = @group1,@group2,user1,user2
```

the Samba module saves:

```
valid users = @group1,@group2,user1,user2
```

to the smb.conf

This works for single users, but the groups will not be recognized.
This applies to Samba module samba-1.140-1 in Webmin version 1.470 and Samba server version 3.028 

In case you have difficulties to access your shares on the server, you might consider changing the line manually.

BTW: 
Samba teamed with Kerberos is freakin' awesome: 
We have an Active Directory integrated Samba share in our network now.

---

### Post by jesuspresley on 2009-05-19
As often, this bug might be none. 
I watched my winbind log and notice an entry: 
```
  Unknown parameter encountered: "valid user"
```
So, in fact I seem to be allowing access to everybody for the share root folder.

---

### Post by jesuspresley on 2009-05-20
OK, sorry to panic around about this.
In fact, the samba access control was not suitable for my task, because we needed to simulate NTFS access controls.

I did that with Kerberos [Active directory integration] and the ACL system. If there are questions about that - simply ask.

Therefore it is totally OK to give enter full access in the Samba config, but do further user rights control with ACL [Access Control List]. 

By the way: I am doing this within Webmin with the ACL module. Very comfortable.

---

