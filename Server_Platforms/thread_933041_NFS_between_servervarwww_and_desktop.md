---
title: "NFS between server:/var/www and desktop"
date: 2008-09-29
forum: Server Platforms
---

### Post by botfish on 2008-09-29
I have two Ubuntu computers. One desktop and one server.

I have setup NFS on both computers so that I can share server:/var/www with the desktop.

All working great - BUT I only have read access to server:/var/www

I want to create/edit/delete files in server:/var/www

How do I correctly setup full read/write access? Am I correct to use NFS?

I have added myself to the "www-data" group but that did not give me write access. I see that server:/var/www is owned by root. Do I need to change this?

Thanks for any help.

---

### Post by kamaji792 on 2008-09-29
It looks like a permissions issue with the /var/www directory.  I am sure by default /var/www is only writeable by root.

If you want to change the group for /var/www to allow www-data to write to it try:
```
sudo chown :www-data /var/www
sudo chmod g+w /var/www
```

**chown** - command sets the group owner of /var/www to "www-data".
**chmod** - Gives the group write access to /var/www.

If that does not work post the output of:
```
ls -l /var/www
```

All the best.

---

### Post by botfish on 2008-09-30
I tried the suggested and I still have read only access


$ ls -l /var/www
-rw-r--r-- 1 root root   45 2008-09-29 18:23 index.html

$ ls -l /var
...
drwxrwxr-x  3 root www-data 4096 2008-09-29 19:17 www

Cheers

---

### Post by kamaji792 on 2008-09-30
> **botfish said:**
> I tried the suggested and I still have read only access


$ ls -l /var/www
-rw-r--r-- 1 root root   45 2008-09-29 18:23 index.html

$ ls -l /var
...
drwxrwxr-x  3 root www-data 4096 2008-09-29 19:17 www

Cheers

Thanks - in fact it was ls -l /var that I was really interested in.

I'm at a loss why you can't create a new file in the /var/www directory.  I can see why you would not be able to edit the index.html file.  That needs the **chown** and **chmod** treatment.
```
sudo chown :www-data /var/www/index.html
sudo chmod g+w /var/www/index.html
```

It may be linked with the group membership.  When you create a file it automatically sets a particular group (by default a group with the same name as the user)  you may need to set your main group to www-data.  I have never fully got to grips with groups but I believe there is a way of temporarily changing your default group.

Look at this page _[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)_ about half way down the page **Switching your default group:** or ** man newgrp**.  Not something I have done.

Hope this helps.

---

### Post by botfish on 2008-09-30
Thank you very much. I now have it working! In addition to your suggestions I also joined group www-data on my desktop. I can now create and delete file in in server:/var/www

Which leads to another question :-)

When I create a file in the NFS directory it is created with my default permissions -rw------- and user me.

Some how I need owner and permissions to default to what ever the server requires. IS it user root and -rw-rw-r-- ?

Cheers

---

### Post by kamaji792 on 2008-09-30
I am not sure what user the server acts as.  It's unlikely to be root.  But if you have the file permissions with **r--** at the end.  That means anyone can access them.

Sorry if you already know this about the file permissions but:
The 2nd to 4th characters define what the owner of the file can do.
The 5th to 7th define what group members can do.
The 8th to 10th define what everyone else can do.

All the best

---

### Post by lykwydchykyn on 2008-09-30
Ok, wait.  You do not want to give write access to www-data.  This is the account your web server runs as, which effectively means the web server (and thus users of that service) has write access to your files -- potential security issue there.

What you should do is change the owner and group of the files to your user.  If you have mulitple people who require access, create a group for them and give write permissions to the group.

To fix permissions on the directory, you need to run umask on it; that will force the default permissions to be whatever you want. 

umask 0002, for example, will force permissions to be 775 (owner and group full access, everyone else read&execute).  If you're mounting the nfs export via fstab, I believe you can specify this in the fstab.

---

### Post by botfish on 2008-10-01
It appears that there is no umask option for nfs.

I like to have umask on my desktop set to 077 but in my nfs mount I want umask set to 0002 to force permissions to 755

Must I change the permissions of every file after I've created it?

---

### Post by kamaji792 on 2008-10-02
A umask of 0002 will give you 775 as the permissions.  I must admit that I have not played around with umask much.  Try **man umask**.

lykwydchykyn makes a good point.  I have to admit that I was not sure what the **www-data** group was use for.

What you could do is create a new group for the users that want to write to the /var/www directory.  I need access to a running system to remind me what the commands are so that will have to wait for tomorrow.

All the best for now.

---

