---
title: "how to view samba group members?"
date: 2008-02-27
forum: Server Platforms
---

### Post by beaker15 on 2008-02-27
Hi, 
I'd just like to check my Samba groups contain the members that I want them to, is there a command to view group members? Like the 'members' command does for linux groups

thanks

---

### Post by astrotech226 on 2008-02-27
I use LDAP for my samba database backend and I use getent or members to see who are members of the group easily.  The members of the group in linux should be the same as the Windows users.  The only exception would be is that you can Linux members of a group that aren't Windows users.

It's a little harder, but the Samba way to dump the members of a group is like this:

```
net rpc group MEMBERS <your windows groupname> -U administrator -W <YOURDOMAINNAME>
```

---

### Post by beaker15 on 2008-02-28
thanks!

---

