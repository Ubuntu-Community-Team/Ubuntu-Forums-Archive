---
title: "set permission for future public files/folders"
date: 2010-01-02
forum: Server Platforms
---

### Post by zereshk on 2010-01-02
Hi, I just set up an VPS with ubuntu. I made a user1 and gave it ownership 

```
chown -R user1 /home/www
```This user also have been given all the root privileges (I know it is not recommended!)

The problem is that each time I make new site, and user1 wants to upload (through ftp) files to /home/www/newsite I need to redo the the above command in order to be enable user1 to upload. Not only this, I need to rework permissions (744 for folders and 644 for files), otherwise the newsite throws permission errors message.

These are so cumbersome and I am sure there should be a way around it, but I don't know how to do can be done. Any hints please?

---

### Post by noway2 on 2010-01-03
Try creating a group and setting the group permissions to allow write access.  Then you can add each of the users to the group rather than individually setting all of the permissions.  You should also be able to avoid giving everyone sudo capability that way too.

---

### Post by BkkBonanza on 2010-01-03
You can set the set-uid or set-gid bits for the /home/www directory. This causes files created in the directory to be created with the same owner/group as the directory owner/group rather than the user who created the files.

I usually use owner myname, group www. Then, chmod u+s,g+s /home/www

---

