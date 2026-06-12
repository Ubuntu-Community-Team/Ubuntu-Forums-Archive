---
title: "Giving specific permissions to users"
date: 2010-01-07
forum: Security
---

### Post by jebagnanadas on 2010-01-07
Hello all,

              I'm new ubuntu user and learning the basics now. So far it's been an awesome experience with ubuntu 9.04.. 

             Is there a way to restrict only a specific user from executing a specific application?? For example if my computer has three users user1,user2 and user3 i want to restrict firefox for user2 alone..  But when i log into user1 or user3 it should run as usual.. 

          Could you please explain me in detail.. Thanks in advance..

---

### Post by cdenley on 2010-01-07
> **jebagnanadas said:**
> Hello all,

              I'm new ubuntu user and learning the basics now. So far it's been an awesome experience with ubuntu 9.04.. 

             Is there a way to restrict only a specific user from executing a specific application?? For example if my computer has three users user1,user2 and user3 i want to restrict firefox for user2 alone..  But when i log into user1 or user3 it should run as usual.. 

          Could you please explain me in detail.. Thanks in advance..

Filesystem permissions are permissive, not restrictive. You specify which users can access, not which cannot. ACL's are much more flexible, but more complicated to use.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can create a group called firefox, then only allow members of that group to execute firefox.
```

sudo addgroup firefox
sudo adduser user1 firefox
sudo adduser user3 firefox
sudo chgrp firefox /usr/bin/firefox*
sudo chmod 755 /usr/bin/firefox*

```

---

### Post by jebagnanadas on 2010-01-14
> **cdenley said:**
> Filesystem permissions are permissive, not restrictive. You specify which users can access, not which cannot. ACL's are much more flexible, but more complicated to use.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can create a group called firefox, then only allow members of that group to execute firefox.
```

sudo addgroup firefox
sudo adduser user1 firefox
sudo adduser user3 firefox
sudo chgrp firefox /usr/bin/firefox*
sudo chmod 755 /usr/bin/firefox*

```
Thank you so much for your reply.. Thanks for the link..
I've got few questions(or need some clarifications) regarding creating groups and assigning permissions.. 
In the firstline you're adding a group called firefox to the existing groups? Is that right??
In the second command your'e adding two users to the group firefox..
When i referred some materials i found that chgrp stands for change group.. 
1)Are you changing the group from "x" to firefox?? (If so previously in which group it was in)
2)Since you've changed it to the newly created group will it  not affect the permissions given before by default??
3)Are u creating the group for this executable alone??
4)If i want to add another executable as above , do i have to create another group for that or i can add only the /ur/bin/* to the existing group..
Explain me in detail.. Thanks..

---

### Post by cdenley on 2010-01-14
1. I believe the group owner of the firefox binaries are "root" by default. I changed it to firefox.

2. No, the only member of the root group is root, which is also the owner, which shouldn't be running firefox anyway.

3. Yes. In order to restrict execution to only a specific group, the executable must be owned by that group. Otherwise, either everyone or noone except the owner can execute it.

4. You can change the permissions on other executables as well. Whether or not you create a separate group depends if you want to manage the group memberships seperately (user A can run application A but not B. user B can run application B but not A).

---

