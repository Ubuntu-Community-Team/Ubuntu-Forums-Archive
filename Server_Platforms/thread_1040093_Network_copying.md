---
title: "Network copying"
date: 2009-01-15
forum: Server Platforms
---

### Post by any.linux12 on 2009-01-15
Hi!

I have a crashed server that I'm in with knnopix live cd to access the HD and I need to backup all the data to the new server.

The problem is that when I log in via ssh it only allows me to copy files until 2GB, and I've a lot of big files like vmware disks.

How should I copy the files??

thanks in advance

---

### Post by aaron.d on 2009-01-15
scp shouldnt die after 2 gigs. 

Is this local, though a router/firewall, or anything else?

If I were in the same situation myself, i would do one of two things:

1 - use 'rsync'

There are a lot of options, so be prepared to do some reading, but rsync is your friend.

[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

or

2 - pop the drive into another system.

---

### Post by any.linux12 on 2009-01-15
> **aaron.d said:**
> scp shouldnt die after 2 gigs. 

Is this local, though a router/firewall, or anything else?

If I were in the same situation myself, i would do one of two things:

1 - use 'rsync'

There are a lot of options, so be prepared to do some reading, but rsync is your friend.

[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

or

2 - pop the drive into another system.

I mounted the servers in my desktop and now I can do it. thanks anyway

But maybe you know how to sync folders in a network. Couse there are some files that won't be transfered and so I will need to backup by hand (that's because they 700 permission)

Or

It could be also good to tell me if it is possible to do a Find per permission mode such that I can find all files with 700 permission

---

### Post by albinootje on 2009-01-15
> **any.linux12 said:**
> I mounted the servers in my desktop and now I can do it. thanks anyway

But maybe you know how to sync folders in a network. Couse there are some files that won't be transfered and so I will need to backup by hand (that's because they 700 permission)


Use
```
 
rsync -azvu source-dir/ destination-dir/   (on the same disk)
rsync -azvu username@ip-address:source-dir/ destination-dir/   (over the network)

```
> 
It could be also good to tell me if it is possible to do a Find per permission mode such that I can find all files with 700 permission

```

find / -perm 700

```

---

### Post by aaron.d on 2009-01-16
yeah, what he said ^.

Also, it's pretty easy to figure out of you read the man pages for find, or any other command you have questions about. I would get in the habit of using man.

---

### Post by any.linux12 on 2009-01-16
ok. I did a script to find the 700 files and it gave me 5000 so then I did a script to chmod. Everything ok no errors Thanks ;)

Now I need a command to compare those big folders like this:

the data was in the folder data and I created other data in the new server. The files are coppying but as I need 101% sure that they are all there I need a sync tool to do a remote compare.

I would be nice to have a (synctool) (compare_option) source /data and compare with the other server /data
and of course give the verbose 

Any help Please?
thanks

---

### Post by albinootje on 2009-01-16
> **any.linux12 said:**
> The files are coppying but as I need 101% sure that they are all there I need a sync tool to do a remote compare.


If I were you I would run a :
```

ls -laR

```
on both sides, and then compare with some diff tool.

Here are a few GUI diff tools mentioned :
[http://kdiff3.sourceforge.net/links.html](http://kdiff3.sourceforge.net/links.html)

---

### Post by aaron.d on 2009-01-16
that is pretty much what the rsync -a option is for, it basically intelligently mirrors the data from source to dest, preserving everything (perms, owners, group etc ... called archive mode) recursively. Then you dont have to worry. 

from the man:

>  -a, --archive
              This is equivalent to -rlptgoD. It is a quick way of saying you want recursion and want to preserve almost everything (with -H being a notable omission).  The only  exception
              to the above equivalence is when --files-from is specified, in which case -r is not implied.

              Note that -a does not preserve hardlinks, because finding multiply-linked files is expensive.  You must separately specify -H.

---

