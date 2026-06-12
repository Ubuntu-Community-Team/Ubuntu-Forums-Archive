---
title: "samba: permission between linux user and samba user"
date: 2009-11-03
forum: Server Platforms
---

### Post by tisungho on 2009-11-03
Hi,

I'm quite new to samba. I have a samba server running in ubuntu server box. Everything is configured and running. However, sometimes I find it uncomfortable to modify/delete files/directories between linux and windows. For example, user1 in linux creates a file, but user2 from windows can't modify this file. What I can do is to manually set chmod 777 to the file.
My question is how to have full permission between 2 users in my samba?

Thanks!

---

### Post by Vegan on 2009-11-03
I see I need to post anther article on my site, how to make SAMBA work properly with *ix, Windows and so on.

---

### Post by tisungho on 2009-11-04
> **Vegan said:**
> I see I need to post anther article on my site, how to make SAMBA work properly with *ix, Windows and so on.

You sounded like you know how to solve it, right? Please give me some answer here!!!

---

### Post by Iowan on 2009-11-04
Unfortunately, I don't have the absolute answer you seek, but one option involves making both users members of the same group, then setting  (forcing?) group privileges for the file/directory/share.

---

### Post by tisungho on 2009-11-05
Hi,

I notice that the some rules in smb.conf file are applicable from windows client only. For example if I had a rule: directory mask = 0777, I could only get the rule working by creating a folder from windows client. It doesn't have 777 permission when I create a directory from Linux.
Any idea?

---

### Post by doas777 on 2009-11-05
I'm still grappling with this myself but, I think the answer is SetGID. when you setGID on a folder, the files within it should default to being owned by the user:group, rather than the normal user:user. since both users are part of the same group, it should work.

also there are two settings in samba.conf (create mask and directory mask) that you should set to 774 or whatever, so that new items created via samba take on those permissions by default.

---

### Post by tisungho on 2009-11-05
hi,

The directory I use for samba is /data. Permission = 777. user1 and user2 have the same group called home. user1 creates a file in /data, let say: touch a.txt. Permission of a.txt is: -rw-r--r--  1 user1  home

This means setGID that you mentioned can't be still application to a file or a directory.

---

### Post by tisungho on 2009-11-05
Hi again,

umask does the trick ;)

---

