---
title: "Samba Sub Directory Help"
date: 2011-08-18
forum: Server Platforms
---

### Post by latitude22 on 2011-08-18
I'm hoping someone can tell me if this is even possible.  

I want to give users access to a subfolder, but not the folder above it.

Folder1: user1, user2, user3 have access
----subfolder1: user1, user2, user3 and user4 have access

Is this possible or does user4 have to have some access to Folder1 to access subfolder1?

Thanks

---

### Post by hawk2010 on 2011-08-19
You can. Simply u can do this by group the users and then chown -R nobody.yourgroup foldername

---

### Post by Morbius1 on 2011-08-19
Just create 2 shares. For example:

> [Folder1]
path = /path/to/Folder1
valid users = user1, user2, user3

[subFolder1]
path = /path/to/Folder1/subFolder1
valid users = user1, user2, user3, user4It might be kind of confusing to users1,2,3 to have a subfolder of a  share they already have access to appearing as an available share  though.

Note: Shares within shares are generally a tricky thing. If your requirement was the opposite - user4 had access to Folder1 but not subFolder1 - then it wouldn't work. User4 would not be able to access the subFolder1 share directly but he could access the folder by accessing the Folder1 share.

---

### Post by latitude22 on 2011-08-19
I attempted it by doing two separate shares however in was unable to give user4 access to the subfolder without putting user4 in the same usergroups as the other users. I'm going to have to change ownership of the folders and give that a try.

---

