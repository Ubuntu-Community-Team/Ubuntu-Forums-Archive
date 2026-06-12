---
title: "Preventing inherited rights on existing subdirectories"
date: 2007-04-13
forum: Server Platforms
---

### Post by hurtman on 2007-04-13
Is there a way to prevent users/groups from accessing subdirectories from directories they have access?  For example, lets say that user "bob" has access to the "top" directory but I don't want him to have access to the "bottom" directory which is a subdirectory of "top".  This situation is coming from migrating from a windows server to a linux server.  I just want to copy and past the folders from the windows server to the linux server and set up permissions the same as they were on the windows server.

Thanks,
Jeff H.

---

### Post by aquavitae on 2007-04-13
Assuming you're working on a linux file system, you should be able to use chown and chmod on the subdirectories to modify permissions.  e.g, to make user 'root', group 'users' the owner of the subdirectory 'dir', type 'chown root:users dir'.  To allow all in the group access to the directory, use 'chmod 0775'.  I think I've got that right but its a while since I've used it, you can check the man pages to make sure.  Alternately, some GUI systems provide nice little checkboxes to do it in if you right click the file.

Hope this helps!

---

### Post by hurtman on 2007-04-13
Thanks for the quick reply and answer to my question.  Your solution of using chown and chmod worked for me.

---

