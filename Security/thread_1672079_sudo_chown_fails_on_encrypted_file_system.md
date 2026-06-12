---
title: "sudo chown fails on encrypted file system"
date: 2011-01-20
forum: Security
---

### Post by lister171254 on 2011-01-20
I'm trying to set the permission on a directory, but get the following error:

chown: cannot access `/home/llist/personal/Misc': Permission denied

Only thing I can think of is that /home/llist/personal is an encrypted file system

I could of course also be missing something stupidly obvious

---

### Post by tgm4883 on 2011-01-20
> **lister171254 said:**
> I'm trying to set the permission on a directory, but get the following error:

chown: cannot access `/home/llist/personal/Misc': Permission denied

Only thing I can think of is that /home/llist/personal is an encrypted file system

I could of course also be missing something stupidly obvious

Whats the full command you are trying to run?

---

### Post by lister171254 on 2011-01-21
>> ls -lsa on the encrypted drive shows
4 drwx------   3 llist llist  4096 2010-12-06 16:21 Misc

I change group access by
>> sudo chown :root /home/llist/personal/Misc

or

>> sudo chgrp -v root /home/llist/personal/Misc

the result for both is
chown: cannot access `/home/llist/personal/Misc': Permission denied
chgrp: cannot access `/home/llist/personal/Misc': Permission denied
failed to change group of `/home/llist/personal/Misc' to root

---

### Post by Dave_L on 2011-01-21
What's the output from

```
stat /home/llist/personal/Misc
```

?

---

### Post by lister171254 on 2011-01-22
File: `/home/llist/personal/Misc'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 17h/23d	Inode: 417818      Links: 3
Access: (0700/drwx------)  Uid: ( 1000/   llist)   Gid: ( 1000/   llist)
Access: 2011-01-22 11:22:59.092948990 +1100
Modify: 2010-12-06 16:21:07.073823391 +1100
Change: 2010-12-06 16:21:07.073823391 +1100

---

### Post by cariboo on 2011-01-22
Just out of curiosity, why are you trying to set the group to root in your home directory?

---

### Post by lister171254 on 2011-01-22
The access is not form my home directory, but for misc which is on an an encrypted file system. I want some cron jobs (run as root) to write the log files to the encrypted drive

---

### Post by cariboo on 2011-01-22
As far as I  know, you can't set the the group to one that your user isn't a member of, so unless your user is a member of the root group, it's never going to work.

---

### Post by psusi on 2011-01-22
> **lister171254 said:**
> The access is not form my home directory, but for misc which is on an an encrypted file system. I want some cron jobs (run as root) to write the log files to the encrypted drive

You can't do that.

If it is encrypted, it is for your use only.  It can only be accessed by you, and while you are logged in.

---

### Post by lister171254 on 2011-01-22
thanks psusi. makes sense, I guess.

---

