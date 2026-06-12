---
title: "Sharing /home across network!!"
date: 2006-08-31
forum: Server Platforms
---

### Post by dragze on 2006-08-31
Hi, i would like to share the /home directory across the network of my linux machines, thus making it so that you could save a pic for example on machine 1 and then go on machine 2 and carry on using that pic or wotever. 

Now so far i have archeived this by sharing the /home directory on machine 1. and on machine 2. editing the /etc/fstab config to mount the home directory of machine 1.  This works fine and does just what i want untill i discovered a little problem, which is rather obvious that i would have this problem and that is programs like firefox access files from the home directory etc, which means i cant open firefox on machine 1. and machine 2. at the same time!! + i think this might cause problems wid ssh keys etc??

Im sure there must be a way round this but i dont know wot, so any suggestions on wot would be the best method??

Thanks in advance,
dragze.

P.S if u need any more info just shout! ;)

---

### Post by chrisfay on 2006-08-31
```
sudo apt-get install samba
```

Then make the directory a shared folder. You're other computers will be able to browse the directory if you give them permission to.

If you want to mount the shared samba folder on another pc you will need the samba files system.

```
sudo apt-get install smbfs
```

---

### Post by dragze on 2006-08-31
hi cheers for your reply, is there any particular reason you suggest using samba for this?? does using samba solve the issue of for example firefox using certain files stored in the /home directory, and pc1. using firefox and pc2.then not being able to use it like i explained in first post??

I am succesfully sharing /home using nfs at the moment but with the access problem explained in first post, can this problem not be solved when using nfs??

Cheers,
dragze.

---

### Post by chrisfay on 2006-08-31
Samba does not support files checked out by multiple users. I must have misread your post. According to Samba:

> Locks and Oplocks
Concurrent writes to a single file are not desirable in any operating system. To prevent this, most operating systems use locks to guarantee that only one process can write to a file at a time. Operating systems traditionally lock entire files, although newer ones allow a range of bytes within a file to be locked. If another process attempts to write to a file (or section of one) that is already locked, it receives an error from the operating system and will have to wait until the lock is released.

Samba supports the standard DOS and NT filesystem (deny-mode) locking requests—which allow only one process to write to an entire file on a server at a given time—as well as byte-range locking. In addition, Samba supports a locking mechanism known in the Windows NT world as opportunistic locking, or oplock for short.

You could configure check in/out of files so that when one user is finished with the file another will then be allowed to modify it. As far as programs that need certain files to run but use them from an external repository, I would just copy those necessary files to each system. What type of files specificallly is Firefox trying to access from your shared folder?

---

### Post by dragze on 2006-08-31
not sure at the moment can find out tomorrow, i understand the whole locking of files business and that is why im trying to find if there is a way around it i.e. setting it up so that the files that firefox for example need are in a different directory outside of /home. copying the files to each pc wont help because im mounting the shared /home directory which will make anything in local /home unaccessible. It is not just firefox though things like ur ssh keys are stored in each user of home, i know at uni they have ur userspace mounted and from what i remeber it is mounted in the /home directory. There must be a way of moving all the system files that are stored in /home to another directory outside of /home on each pc, then the problem will be solved.

I dont know its either that or i am just going to have to make a folder inside the /home directory with all the files i want sharing so then it wont actually be sharing sys files as well that are in /home, for eaxmple /home/user/share and only mount share in all the /home/user directories, at the moment im sharing /home and mounting /home on the other pc's, which is fine apart from the shared system files that are also stored in /home.

Need some advice here, surely there are plenty of people here who have a centralised /home area on one machine that is shared across and mounted on other pc's??

Thanks so far,
dragze

---

### Post by dragze on 2006-09-01
nobody got any suggestions then on the best way of doing this??

the other possibility i came up with was to give each user there own logon which would give them each there own /home area, then that wud solve the issue as long as they whernt logged on two machines at once.

Suggestions please!!

Cheers,
dragze.

---

### Post by harisund on 2006-09-01
I am not sure I am able to understand what you are saying .... 

what do you want shared and what do you *not* want shared? 

NFS seems to be a fine solution. What is happening that you don't want?

---

