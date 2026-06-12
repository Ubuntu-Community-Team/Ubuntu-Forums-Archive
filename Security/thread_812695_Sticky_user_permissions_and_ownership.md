---
title: "Sticky user permissions and ownership"
date: 2008-05-30
forum: Security
---

### Post by Jaded Phoenix on 2008-05-30
Hi everybody!

I created a folder (say, '/media/shared') and set up permissions as follows: user - nobody; group - nogroup; permissions - 777.

Now I need to make these permissions 'sticky'. That is: any file or folder copied or moved here should belong to nobody/nogroup, whoever copied or moved it, and never mind the initial permissions.

Is it possible? How can I do it?

---

### Post by hyper_ch on 2008-05-30
run a cronjob that alters the ownership and file permissions

---

### Post by chrisccoulson on 2008-05-30
Use ACL's (Access Control Lists). You'll need to specify the 'acl' mount option in your fstab for them to work though.

```
sudo setfacl -R -m d:u::rwX /media/shared
sudo setfacl -R -m u::rwX /media/shared
sudo setfacl -R -m d:g::rwX /media/shared
sudo setfacl -R -m g::rwX /media/shared
sudo setfacl -R -m d:o::rwX /media/shared
sudo setfacl -R -m o::rwX /media/shared
```

This sets the permissions on all the current files to rwX for user, group and other, and also sets the default permissions for newly created files to rwX for user, group and other

---

### Post by Jaded Phoenix on 2008-05-31
Thanks all!
But still... The problem isn't solved:

1) Run a cron? How often? Once per second? Or maybe 1000 times a second? I think you understand it's definitely not a solution.

2) ACL... Thanks! I didn't know... still, the very same results would be if I set the permissions as 6777 (mainly, the 'sticky' bit is essential): all new files will belong to the group 'nogroup', only the owner will change the permissions, and so on.

But still. If I create a file in my home folder and move it into /media/shared, the file still belongs to me!

The only solution I found so far is to make a separate partition for /media/shared, format it as NTFS, and adjust permissions options in /etc/fstab.

Can anyone provide a better solution?

---

### Post by chrisccoulson on 2008-05-31
> **Jaded Phoenix said:**
> Thanks all!
But still... The problem isn't solved:

1) Run a cron? How often? Once per second? Or maybe 1000 times a second? I think you understand it's definitely not a solution.

2) ACL... Thanks! I didn't know... still, the very same results would be if I set the permissions as 6777 (mainly, the 'sticky' bit is essential): all new files will belong to the group 'nogroup', only the owner will change the permissions, and so on.

But still. If I create a file in my home folder and move it into /media/shared, the file still belongs to me!

The only solution I found so far is to make a separate partition for /media/shared, format it as NTFS, and adjust permissions options in /etc/fstab.

Can anyone provide a better solution?

You've misunderstood what the sticky bit does. It won't mean that all newly created files within that folder will inherit permissions of the parent. When the sticky bit is set on a folder, it means that a user can't rename, modify or delete other users files in that folder, even if they have write permissions to the folder. The sticky bit is used primarily for shared areas where you want all users to be able to write to but not tamper with files that have been created by other users (it is used on /tmp for instance).

Have a look at [http://en.wikipedia.org/wiki/Sticky_bit]("http://en.wikipedia.org/wiki/Sticky_bit")

---

### Post by Jaded Phoenix on 2008-07-24
Thanks a lot for the explanation.
Still using that buggy ntfs partition yet...


Thank you all anyway

---

### Post by hyper_ch on 2008-07-25
crons can be exectued max. once every minute

---

