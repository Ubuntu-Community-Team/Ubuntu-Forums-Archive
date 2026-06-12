---
title: "yet another permissions question"
date: 2011-12-27
forum: Server Platforms
---

### Post by jperz09 on 2011-12-27
So I know this is a very popular question, and trust me I've looked for the answer. But anyway, 
I've got a ubuntu 11.10 server set up with samba.
 
I've created a directory called "/share" 
 
I've got two Windows 7 VMs set up. One with a user on"jon" and one with a user of "jonny." 
 
The goal is to be able to for both jon, and jonny to have access to the share, with full permissions, which i have set up, and working for the most part.
 
So I've get up a group named "shareusers," both jon, and jonny are group members, made "shareusers" the owner of the /share directory.
 
So at this point, if jon makes a directory, jonny can add things to it, and vise versa. But if jon makes a text document, and puts it in the /share, jonny can read it, and type into it, but cannot save it. So i'm sure some of you have run into this, if there's a good solution, please let me know.
 
Thanks
 
**Just to add to it, under either user jon, or jonny, i can delete anyfile i want. So if jon makes a text doc, i can log in as jonny a delete it, but cannot edit it. weird**

---

### Post by brighty22 on 2011-12-27
There'll be a way to do it with ACLs, but I'm not very experienced with them. In the meantime, try adding the following under the share in smb.conf:

```
create mask = 0770
directory mask = 0770
```

That should make everything new accessible by both users.

---

### Post by jperz09 on 2011-12-27
that did it! 
thanks!

---

