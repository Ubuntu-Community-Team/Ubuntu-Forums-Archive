---
title: "Samba server question"
date: 2013-05-15
forum: Server Platforms
---

### Post by steventantan on 2013-05-15
My boss ask me to create a samba server, but he also give me a big difficult question.

The question is:

Can I set up a folder with group delete permission?

I guess it will be 3 people contain delete file permission, but not other group. If I use the folder permission with 1755, only 1 person can contain delete file permission. So how can I set it up?

Thanks.

---

### Post by SeijiSensei on 2013-05-15
Put the users in a Unix group and change the group ownership of the shared directory to that group.  Then use 775 privileges on the directory.

---

### Post by steventantan on 2013-05-16
I think i cannot set 775 on the directory. In the situation, we have 2 admin in admin group with read write exe and delete permission, 3 user in user group with read write exe but not delete permission.

So if i set the 775 on the directory, user_a can delete user_b's file. But if i set to 1755, there are only one people has delete permission.

Thanks for your help~^^

---

