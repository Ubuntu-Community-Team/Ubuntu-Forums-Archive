---
title: "Samba - how to setup directory permissions?"
date: 2008-10-13
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2008-10-13
Another Samba question, on our server at work I have 5 primary shares setup (Jobs, Proposals, General, etc).  Everyone has access to these shares via their samba username and password.  I have them mapped to the user's Windows machines.  Within each of these shares there are certain jobs and whatnot that some people do not need access to.

I'd like to setup a group that is named the same as the job number that I can add members to and allow access to those directories that way.

I tried to do something like that by greating a group and adding the unix users that the samba users are mapped to to the group then giving that group ownership of the folder.  It didn't work though.  Noone could access the folders after I made the change.

What did I do wrong?

---

### Post by lykwydchykyn on 2008-10-13
Can you give a concrete example?  Also, can you show an ls -l listing on one of the directories, showing who owns what and what permissions they have?

Also, what security mode is Samba running in?  I presume user mode?

---

### Post by 47_MasoN_47 on 2008-10-13
Here's a screenshot of the ls -l output containing the main shares.  There are thousands of folders inside each of these, so I can't really ls -l all those, but they should all have the same permissions as these root folders.

Samba is running in user mode.

Thanks!

---

### Post by lykwydchykyn on 2008-10-13
Looks like the group on all of them is "administrator".  I thought you changed the group?

---

### Post by 47_MasoN_47 on 2008-10-14
Well that's the group for the main directories.  Inside those directories are other directories that I tried to change the group to.  It didn't work though so I set them back to administrator.

---

