---
title: "/var/www/ user permissions"
date: 2008-01-28
forum: Server Platforms
---

### Post by dacool25 on 2008-01-28
I have a new user called ftpuser that I would like to have access to all of my folders under /var/www 

The permissions right now are 755, however the user cannot write to a sub folder.  I don't want him to be the owner of the folder, and don't want to add him to the root group.  How can I fix this?

Thanks!

---

### Post by fimblo on 2008-01-28
perhaps create a new group? say you create a group ftpgrp:

[FONT="Courier New"]sudo groupadd ftpgrp[/FONT]

Then you give this group complete access to your directory:

[FONT="Courier New"]sudo chown -R ftpgrp /var/www[/FONT]

Now make your user ftpuser a member of ftpgrp

[FONT="Courier New"]sudo adduser ftpuser ftpgrp[/FONT]

Hope this helps.

---

### Post by dacool25 on 2008-01-28
When i try to do chown -R ftpgrp /var/www it says "chown: 'ftpgrp': invalid user

P.S. will this also chown the sub directories?

Thanks

---

### Post by fimblo on 2008-01-28
sorry I meant chgrp. And yes, the "-R" flag means do this recursively, that is, for all sub-directories.

/fimblo

---

### Post by dacool25 on 2008-01-28
so the command would be:

```
chgrp -R ftpgrp /var/www
```

Because I cannot delete files from that folder with that.

---

### Post by fimblo on 2008-01-28
yup, it should be chgrp.

If you cant delete files from the folder anymore, check if you are a member of the group using the command "id". It lists the groups you are a member of. if you want to know what groups ftpuser is a member of you can type "id ftpuser".

If you think you added yourself to the group but "id" dosnt show it, try logging out and logging in  again. That should do it.

/f

---

### Post by dacool25 on 2008-01-28
Okay so, the owner of the folder is root and the folder is ftpgrp and i know that ftpusr is part of that group.  Why can i not write to that folder?

---

### Post by dacool25 on 2008-01-28
Ahh!

For some reason i'm still getting permission denied from cyberduck.

After doing the ID, I can see that yes i'm part of the ftpgrp and I even redid the chgrp -R ftpgrp /var/www

Still permission denied.

---

### Post by dacool25 on 2008-01-28
My bad...

Had to chmod -R 775 /var/www so that group had write access =P

---

### Post by fimblo on 2008-01-29
just saw your reply- yes, you need to add write permissions for the group ftpgrp. btw, if you prefer symbolic mode changes instead of octal, you can write

chmod -R g+w /var/www

The above will just change the group permissions so that the group can write.

---

### Post by dacool25 on 2008-01-30
Thanks,  That worked beautifully!

---

### Post by kerryhall on 2008-06-24
I have done something similar, adding my main user to the group www-data and then changing the permissions of /var/www and group ownership to allow write access.

Two quick questions:

1. I made my main user a member of the www-data group, but not as their primary group. Should I make www-data the main group for this user? Or will secondary group work just as well?

2. How safe are 775 permissions vs 755? Any attacks I should know about? Any good information about this? I have heard that making permissions 777 is not safe. Why is this?

Thank you! :)

---

### Post by fimblo on 2008-06-30
> **kerryhall said:**
> Two quick questions:
1. I made my main user a member of the www-data group, but not as their primary group. Should I make www-data the main group for this user? Or will secondary group work just as well?

It will work just as well. If you set www-data the main group, the only difference will be that the default group owner of your main user's files will be www-data. That is, when you create a new file/dir, it will belong to group www-data.

> **kerryhall said:**
> 
2. How safe are 775 permissions vs 755? Any attacks I should know about? Any good information about this? I have heard that making permissions 777 is not safe. Why is this?

Thank you! :)

5= execute and read.
7= execute, read and write.

775= user can exec, read and write, group can exec read and write, and all other users can read and execute.
755= same as above, but group can only read and exec.

777= all users on your machine can do anything in files/dirs set with this acl. Remember, even if you are the only physical user on the machine, all processes (apache, ftpd, postfix, etc) are users on your machine and will be able to do bad stuff if 1) the code is buggy and happens to try to delete everything, or 2) if the process gets owned by evil hacker eddie.

---

