---
title: "file permission inherit from folder"
date: 2011-12-27
forum: Server Platforms
---

### Post by nunkstop on 2011-12-27
Hi everybody,

I use ubuntu server 11.04

I have a bit problem

I create /home/shared folder , and i use root to config permission for folder /home/shared and i need when other user log in to server and create file in /home/shared, so that file will inherit permission from /home/shared, but i try to some tuts to config , it still not work

I append " umask xxx" to ~/.bashrc with xxx is number like 002

but it just work when i use current user root to create folder and when i switch to other users and create file in that folder, it not inherit permission from /home/shared, it still inherit default permission as when i do not config.

Anyone could help me solve this? 

Thanks!

---

### Post by Karlchen on 2011-12-27
Hello, nunkstop.

There is no such things as inheritage in Linux.

Whenever a user A creates a file, user A will always be the file owner, no matter who is the owner of the folder where he creates the file.
So there are only ways of making sure that other users get the access permissions which you want them to have:
User A has got to grant other users the permissions.
Either you make sure that all users logging in to this machine use a umask of 000. (Hm. Not so good, because it will not only affect objects created in /home/shared)
Or you make sure all users who create files in /home/share grant permissions to other useres explicitly. (chmod u+rw filename). Not too convenient, either. And some users will simply forget to do so.
Or you create a root cronjob which assigns the intended permissions to all files and folders in /home/shared every X minutes. (Not too elegant, either)

Kind regards,
Karl

---

### Post by Lars Noodén on 2011-12-27
These might help.

```

# create group
sudo addgroup sharers

# add user to group
sudo gpasswd --add nunkstop sharers

# set group membership for directory
sudo chgrp -R sharers /home/shared

# set group permissions including sticky bit
sudo find /home/shared -type d -exec chmod g=rwxs "{}" \;

```

Then add the other users to the same group.

---

### Post by Karlchen on 2011-12-27
Hello, Lars.
> These might help. Yes, it does. :D 
With a minor correction: *webmasters* should be *sharers* in one commandline. Error caused by copy and paste I assume. ;)
```
# create group
sudo addgroup sharers
# add user to group
sudo gpasswd --add nunkstop sharers
# set group membership for directory
sudo chgrp -R [COLOR=Blue]*sharers*[/COLOR] /home/shared
# set group permissions including sticky bit
sudo find /home/shared -type d -exec chmod g=rwxs "{}" \;
```You may have just solved a very old nuisance here and sent my dirty little workaround to retirement.
Thanks a lot.

Karl

---

### Post by Lars Noodén on 2011-12-27
Yes, it was a copy-paste error.  The question comes up often enough that it probably should be worked in to some documentation somewhere.

---

