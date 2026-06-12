---
title: "Limit User Directory Access"
date: 2007-08-08
forum: Server Platforms
---

### Post by xxdeusxx on 2007-08-08
i created a user that i use to login via ssh...
so there is only one user accessible from the outside...
I used the "limited" preset to create this user...

this user however can still access every file in other home folders...
how can i disable this?

---

### Post by thusi02 on 2007-08-08
Hi 

Users access to files/directories are controlled by the permissions for each file/directory. By default it is in the following form: 

Files: -rwxrwxrwx 
Directories: drwxrwxrwx

So if you do: sudo ls -alt /home/ you will get something like this: 

% sudo ls -alt /home/
total 2
drwxr-xr-x  2 userA      users     4096 2007-08-01 13:18 userA
drwxr-xr-x  2 userB      users     4096 2007-08-01 13:18 userB

What this tells you is that userA's home folder is owned by userA and his rights to this directory is specified after the 'd' flag. Which means that he has read write and execute. The 2nd 3 bits are for the group rights and the last 3 bits are for the others ( everyone) rights. So if you don't want this user that you just added to have access to all the other users home directories. Than you would have to run the following command: 

sudo chmod 750 /home/*

This would read: drwxr-x---: Meaning no one from the others group will have access into this directory. The - indicate that privilege being revoked. But do note that there could be files in the home directories that give access to others that this user may have so to prevent that you can run: 

sudo chmod -R 750 /home/* which will recurse through all the files and change the permissions on the files. Also you need to remove this user from the "users" group in /etc/group if he is there that is. 

I hope this helps. 

Cheers, 
Thusjanthan Kubendranathan

---

