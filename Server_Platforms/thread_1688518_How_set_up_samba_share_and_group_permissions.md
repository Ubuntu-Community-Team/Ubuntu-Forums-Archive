---
title: "How set up samba share and group permissions?"
date: 2011-02-15
forum: Server Platforms
---

### Post by MightyMe on 2011-02-15
I have a couple of user accounts where each member belongs to a group i have created: Each user access the share using their own user account credentials.
 How can I configure Samba in a way so that each modification done on the share gets the owner of the user and my group instead of  the user and the users own group? I would also like the access rights to be 770 to each modification.

In other words, today each modification by "userA" get the owner "userA.userA" and I would like it to be "userA.MyGroup" with "rwxrwx---" permissions.

Any help would be much appreciated.

---

### Post by MightyMe on 2011-02-17
bump

---

### Post by Morbius1 on 2011-02-17
Add the following to the share definition in smb.conf:
```
force group = mygroup
force create mode = 0770
create mask = 0770
force directory mode = 0770
directory mask = 0770
```

---

### Post by MightyMe on 2011-02-21
Thanks. I'll try that.

---

