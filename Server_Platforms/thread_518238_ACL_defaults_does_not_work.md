---
title: "ACL defaults does not work"
date: 2007-08-05
forum: Server Platforms
---

### Post by onon_onon on 2007-08-05
Hi, friends.

I'm having trouble setting ACL in a shared folder.

If I do this:

```
#setfacl -m d:u::rwx,d:g:share:rwx,d:o:r,d:m:rwx dir
```

the result of

```
#getfacl dir
```

will be

```
# file: dir
# owner: me
# group: me
user::rwx
group::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:share:rwx
default:mask::rwx
default:other::r--
```

what is exactly what I want.
But if I copy any file into dir, the result of getfacl will not have the 
expected result, as below:

```
# file: dir/copied_file
# owner: me
# group: me
user::rwx
group::rwx                      #effective:---
group:share:rwx      #effective:---
mask::---
other::---
```

My /etc/profile has umask 002, because group must have full access.
But "mask::---" is wrong, setting the user and share groups with 
absolutely no access to the file. Created files receive correct permissions. What is wrong here?

As "dir" will receive photos from a digital camera and all users must 
see them, I am in trouble.

Thanks in advance and sorry my english.

---

### Post by onon_onon on 2007-08-07
The record of not answered threads is mine? lol

Nobody here uses ACL to share files?

---

### Post by ruibernardo on 2007-08-10
Hi onon_onon,

I don't use ACL, but I've bookmarked a very good post about ACL some time ago, may it helps you someway. 

[http://ubuntuforums.org/showpost.php?p=832721&postcount=9](http://ubuntuforums.org/showpost.php?p=832721&postcount=9)

Take a look at the "mount" part. In a glance, you don't talk about it, so maybe that's the trouble.

Hope that helps you somehow. :)

---

### Post by onon_onon on 2007-08-10
Thanks, epimeteo, but my ACL is configured and working fine. Maybe this copy issue is a bug, but I really don't know because google did not return anything like that.
If someone know any other way to configure group permissions than ACL, it will be great, because I only need to copy files with inherit permissions.

Thanks and sorry my english again.

---

### Post by grof on 2008-02-08
Hello,

I have the same problem with inheriting ACL defaults.

But if I try this in kubuntu 7.10, all works fine.

In ubuntu work only if you create new dir into existing one with ACL default permissions. If you try to copy or move one to that dir - do not work. Why? It is mystery for me by now...

---

### Post by ABX on 2008-03-10
If you move files on the same disk you don't create a new one, you just move the pointer where the files are stored on the disk. This is why they keep the old value.

but I have another problem.

If I use  setfacl I get this error:
#setfacl -dm o:rwx space/
#setfacl: space: Operation not supported

#mount
/#dev/sda2 on /media/sda2 type ext3 (rw,acl)


but if I remount using 
#mount -o remount,acl /dev/sda2

#mount
/dev/sda2 on /media/sda2 type ext3 (rw,acl,acl)  #note the double acl
then it starts to work until the next reboot

---

### Post by astrotech226 on 2008-03-10
> **onon_onon said:**
> 
```
# file: dir/copied_file
# owner: me
# group: me
user::rwx
group::rwx                      #effective:---
group:share:rwx      #effective:---
mask::---
other::---
```


I do this all the time and I just ran some tests and this works for me in Ubuntu 7.10.  What version are you running?

There is one thing I can think of that might affect this.  How are you copying the files?  Have you tried copying a file from your / partition into "dir" and see what happens?  Copy /etc/hosts as that has world readable permissions.

If you are using "cp", make sure you aren't using the -a or -p flags.  They will obliterate your default acls and use what the original file had.

If you are using just plain "cp" with no flags, check to be sure it's not an alias.

```
type cp
```

---

### Post by Eiríkr on 2008-04-01
> **astrotech226 said:**
> I do this all the time and I just ran some tests and this works for me in Ubuntu 7.10.  What version are you running?

A question for your, astrotech266 --

Did you have to add the "acl" option to your fstab file?  I try adding a default ACL to a new directory, and it fails out:
```
user@ubuntu:~$ sudo setfacl -dm g::rwx /data/shared
setfacl: /data/shared: Operation not supported
user@ubuntu:~$
```

Running [font=courier]mount[/font] shows that the "acl" option is not present:
```
mount
...
/dev/sda6 on /data type ext3 (rw)
...
```

I'm happy modifying /etc/fstab if that's what's required, but I certainly don't want to bork anything, so any input you might have (or anyone else for that matter) would be appreciated.

Cheers,

Eiríkr

---

### Post by astrotech226 on 2008-04-01
> **Eiríkr said:**
> 
I'm happy modifying /etc/fstab if that's what's required, but I certainly don't want to bork anything, so any input you might have (or anyone else for that matter) would be appreciated.


Yes, you need to add 'acl' to the fstab file, or you can do a quick remount to test.

```
mount  -o remount,rw,acl /data
```

---

### Post by Eiríkr on 2008-04-01
Thanks for the confirmation, Mark!  There was nothing in the man pages (at least the ones I'd looked at) that mentioned having to add this, so I thought I'd ask before diving in.  :D

Cheers,

Eiríkr

---

### Post by astrotech226 on 2008-04-01
No problem!!  I agree...  I remember the first few times I tried to do acls that I struggled with this part as well as making the get and setfacl work correctly.  The other problem you might run into is mounting this particular fs over NFS and/or rsyncing.  There's a few things you need to do differently for those cases as well.

Good luck!

---

### Post by Eiríkr on 2008-04-01
Funny you should mention that, as NFS sharing is exactly what I'm doing.  I've been slowly puzzling out the various details of permissions and how to effectively set up group access without having to cheat and set an insecure umask.  So do you have any hints or gotchas about sharing an ACL-attributed directory over NFS, specifically to Ubuntu and Mac clients?

Cheers,

Eiríkr

---

### Post by astrotech226 on 2008-04-02
Ubuntu's kernel does not support nfs access control lists by default.  The good news is that it's not that bad to add it.  I simply followed the instructions from the ubuntu kernel documentation and enabled nfs version 3/4 acls.  You compile the kernel and install it.  Make sure grub is the way you want it and reboot.  Once that is done, you can share that partition with nfs and the clients will see the extended file permissions (assuming the nfs client can use acls as well).

[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

---

