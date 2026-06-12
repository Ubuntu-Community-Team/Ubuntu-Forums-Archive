---
title: "Strange user group behaviour"
date: 2009-04-26
forum: Security
---

### Post by girtsn on 2009-04-26
Hello.

Just installed Ubuntu 9.04.
When assigning "users" group to some of the users (including mine), I noticed that I can't modify files/folders with chmod set to 771, chgrp users, where I am not an owner.

Checked out what is happening in the terminal
id myusername showed that I am included in the "users" group.
id without username did not.
Same happened with another new group that I created, so its not specific to "users"  group only.

---

### Post by bodhi.zazen on 2009-04-26
I can not discern anything abnormal in your post.

you changed the ownership and permissions to allow members of these groups to make changes on these files.

See: [FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

If you have a specific question about a specific file or directory , post the details of 

ls -l
groups user

where "user" is the user in question (your log in).

---

### Post by girtsn on 2009-04-26
"groups" command returns what is expected, and I can modify the files (I guess the issue was because of NFS sync time). I guess this topic can be closed - although did not understand the reason on "id" and "id username" not being identical. Thank you.

---

