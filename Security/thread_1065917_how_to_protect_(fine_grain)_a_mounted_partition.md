---
title: "how to protect (fine grain) a mounted partition"
date: 2009-02-10
forum: Security
---

### Post by josir on 2009-02-10
Hi folks, I want to mount a partition and give permission ONLY to a group of users. What I did:

1. Create a directory: mkdir dados
2. Grant access only to the group: 

chown josir:admin dados
chmod 775 dados
ls -ls

drwxrwxr-x 2 josir admin       4096 2009-02-06 20:36 dados

3. I add this line on /etc/fstab

/dev/sdb1 /vms/dados  ext3 	 defaults,user		 0     0

4. mount -a

After that, the permission became:

drwxrwxr-x 3 root  backup       4096 2009-02-06 20:49 dados

I read some topics and tutorials but I think I missed something...
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

My questions are:
1. why it change the ownership to root:backup ?
2. How can I do this fine grain when I boot the machine ?

Thanks in advance,
Josir.

---

### Post by cdenley on 2009-02-10
The permissions are stored on the mounted filesystem, not the mount point. If you want to set permissions on the root directory of the filesystem at /dev/sdb1, then you must do so after you mount it. If you want to change the permissions on new files which get created on that filesystem, I think you would need to use ACL's for ext3.

---

### Post by josir on 2009-02-10
Thanks for replying.

> The permissions are stored on the mounted filesystem, not the mount point. 

This is new for me: how can I set permission to a filesystem that was not mounted yet?

> If you want to set permissions on the root directory of the filesystem at /dev/sdb1, then you must do so after you mount it. 


Are you sure of that ?
1. Because after you mount -a, you cannot change permission to the mounted point anymore.
2. And if I can, what's the best place to do it - because fstab don't have any option for that, right ?

> If you want to change the permissions on new files which get created on that filesystem, I think you would need to use ACL's for ext3.
I heard that ACL is hell!!! Are you sure that Linux can't do it using regular permissions?

---

### Post by cdenley on 2009-02-10
> **josir said:**
> This is new for me: how can I set permission to a filesystem that was not mounted yet?

It's a little difficult to modify a filesystem which isn't mounted. I don't know of any programs which can do that.

> **josir said:**
> 
Are you sure of that ?

Pretty sure. Shouldn't be too hard to prove me wrong.
> **josir said:**
> 
1. Because after you mount -a, you cannot change permission to the mounted point anymore.

Seems to work with a regular mount command. Not sure why "mount -a" would be any different.
> **josir said:**
> 
2. And if I can, what's the best place to do it - because fstab don't have any option for that, right ?

It looks like there is no permissions options for mounting ext3 filesystems, which is why you would have to use ACL's if you want to change the permissions a file has when created. You can always change the permissions on existing files or directories using chmod.

> **josir said:**
> 
I heard that ACL is hell!!! Are you sure that Linux can't do it using regular permissions?
I haven't used it much, but it does seem rather complicated. If you want to use stuff like inheritance, or control access with lists rather than owners, then you need ACL's. I've always managed to get by with regular unix permissions.

Just to be clear, the permissions on the mount point is not necessarily the same as the permissions of the root directory of the filesystem you mount there. Once you mount the filesystem, the permissions of the mount point from before mounting is ignored. You can mount that same filesystem to a different mount point, and the root directory would still have the same permissions. All unix permissions for ext3 (even the root directory) are stored in the filesystem itself.

---

### Post by bodhi.zazen on 2009-02-10
You change the permissions with the partition mounted using sudo

```
sudo chown josir:admin /vms/dados
```

This should be a one time configuration.

=======

In answer to how to share a partition between users, it is not so easy, see these links :

Share directory : [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)
    Set Group ID : chmod g+s dirname

    OR (ACL works better)

    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)


ACL are not *that* hard to set up, :lolflag:

---

### Post by josir on 2009-02-10
Sorry cdenley, but I didn't understand what you are trying to explain:

You told at first place:
> The permissions are stored on the mounted filesystem, not the mount point.

I answered:
> This is new for me: how can I set permission to a filesystem that was not mounted yet?

Then you reply:
> It's a little difficult to modify a filesystem which isn't mounted. I don't know of any programs which can do that.

I was not asking about modify the unmounted filesystem - I was following your suggestion and asking how can I do that...

Did you mean the "parent directory" ?
In my case: /vms/dados has the same owners that I need for the mounting device.
>ls -ls /vms

4 drwxrwx---  3 josir admin  4096 2009-02-09 20:28 vms

Why Ubuntu set the permission to backup group??
Where is this group set??

---

### Post by josir on 2009-02-10
> **bodhi.zazen said:**
> You change the permissions with the partition mounted using sudo

```
sudo chown josir:admin /vms/dados
```

This should be a one time configuration.

Set Group ID : chmod g+s dirname


Thanks bodhi! It works at last!
Thanks also to cdenley - I didn't understand what you are saying but probably it was my english :P

---

