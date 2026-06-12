---
title: "User Permission"
date: 2011-02-10
forum: Server Platforms
---

### Post by judo23 on 2011-02-10
Can someone tell me if it is easier to set up permissions for users on the server or on the desktop?

---

### Post by Tyler27 on 2011-02-10
Its a lot easier on the Desktop than the server because the permission command is chmod <777> <username>. much simpler and fast. compared to the server command which i have no idea what that is

---

### Post by judo23 on 2011-02-10
Thanks Tyler, with that command I will be able to allow certain users to have different control? :confused:

---

### Post by acelino on 2011-02-10
```
sudo chmod -R 777 /dir
```

---

### Post by cariboo on 2011-02-10
There is no difference in the way permissions are set between the desktop and the server. The only differences between the two is one has a gui, and the other hasn't, and the server uses a slightly different kernel.

---

### Post by cjhabs on 2011-02-10
> **judo23 said:**
> Thanks Tyler, with that command I will be able to allow certain users to have different control? :confused:

You have 3 levels of control - user, group and other. Each can have read, write and execute set.
Set the owner of the file using "chown username file"
Set the group using "chgrp groupname file"
or if you want to be fancy and do both at the same time:
chown user:group file
Finally, chown sets the permissions:
777 = rwx (read write execute) for owner group & other
700 = rwx just for owner
4 = read
2 = write
1 = execute
add them together to get the appropriate permission
Put your users into groups to to take advantage of group permissions

Other is anyone that is not the owner or in the owning group

---

