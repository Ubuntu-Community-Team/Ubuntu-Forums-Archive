---
title: "File sharing and windows clients"
date: 2010-02-22
forum: Server Platforms
---

### Post by Chrisso101 on 2010-02-22
I'm learning to use ubuntu server and I've created a data folder on a machine running ubuntu server 9.10 and shared it using samba so that it's visible to all users when they log on to a windows client.

I would like to share the users' home directory also, but when I create a homes directory share using samba the  home directories of all users are visible and  browseable (apart from the home directory of the original user whose account was created when installing ubuntu, where it is visible but access is denied).

Do I need to use a replaceable parameter or something in the 'directory to share' path in the 'Create file share' page in webmin? The path is ' /home ' at the moment and, of course, all home directories are visible.

Thanks

---

### Post by Vegan on 2010-02-22
Not the best idea to share /home like that unless your the only client.

I have several user accounts and do things different, I use a /public for public shares and I have account based shares for the user accounts.

A bit more complex but it works for me.

---

