---
title: "move home directory to different location (not partition)"
date: 2009-06-18
forum: Server Platforms
---

### Post by tomasch on 2009-06-18
Hi guys.. Quick question

Ubuntu 9.04 server 

I have an external drive setup with a single partition that holds all my data. It's mounted under '/mnt/data'
This drive get's backed up nightly.

I want to move my /home directory so it's on my external drive
something like '/mnt/data/home'

I know how to put my /home directory on it's own partition and mount it with proper fstab entries, but I'm not sure how to get the '/homes' to point to my '/mnt/data/home'

Any ideas/pointers?

Thanks in Advance

Tom

---

### Post by Cheesemill on 2009-06-18
Maybe a symbolic link?
```
ln -s /mnt/data/home /home
```
should do it.

---

### Post by Cheesemill on 2009-06-18
Just to add to the above, I think you'll have to boot your machine in single-user mode to make sure that none of the files in /home are in use when you attempt to move them to the external drive. You want to make sure that the /home directory is empty before deleting it and creating the symlink.

---

### Post by tomasch on 2009-06-18
Thanks CheeseMill - I'm trying it now...

Any thoughts on using the ln -d option as opposed to the ln -s option?

---

### Post by tomasch on 2009-06-18
so the ln -s works.  There are some permission problems but nothing that a chmod -R 777 cannot fix ;-)
Thanks Cheesemill.

(although I'm still cheching out the ln -d option

---

### Post by Cheesemill on 2009-06-18
I've never been able to get hard links to work for me, not sure why though.

---

### Post by koenn on 2009-06-18
> **Cheesemill said:**
> I've never been able to get hard links to work for me, not sure why though.
ard links don't work across filesystems, i.e you can't hardlink to a file/directory on a different partition, disk, ...

> **tomasch said:**
>  There are some permission problems but nothing that a chmod -R 777 cannot fix ;-)

ugly ....



> **tomasch said:**
> 
I know how to put my /home directory on it's own partition and mount it with proper fstab entries, but I'm not sure how to get the '/homes' to point to my '/mnt/data/home'

The home dir is a property of the user account that can be modifies with the usermod command

```
usermod -d /path/to/homedir  userloginname
```
The value is stored in /etc/passwd so it can also be edited there.

---

### Post by nanog on 2011-01-20
thanks koenn!

i'm migrating all my roots to mirrored grubed flash drives and  
usermod allowed me to move many, many homes directories to an nfs-mounted raid array (with croned tars to an offsite raid6 array, of course).

---

### Post by hawk2010 on 2011-01-21
You can easily edit /etc/passwd and change the path there.

---

