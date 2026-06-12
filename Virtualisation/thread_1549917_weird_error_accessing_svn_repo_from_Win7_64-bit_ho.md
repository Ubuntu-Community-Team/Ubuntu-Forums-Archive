---
title: "weird error accessing svn repo from Win7 64-bit host on ubuntu 10.04 guest"
date: 2010-08-10
forum: Virtualisation
---

### Post by vanhoudn on 2010-08-10
I'm running Windows 7 64-bit as the host machine. It has Tortoise SVN running Subversion 1.6.11. I'm running VirtualBox 3.2.6 and hosting an Ubuntu 10.04 VM.

The Ubuntu guest is running svn, version 1.6.6 (r40053), to my knowledge the most recent version available through the repos. 

Since the two versions of svn match on the major and minor version number, I think that they should be able to play nicely with each other. 

If I create a repo on the Windows 7 host, and share that repo via vboxsf

```

$ cat /etc/fstab
...
winhome	/home/vanhoudn/winhome	vboxsf	rw,exec,uid=1000,gid=1000,dev	

```

I can checkout just fine:
```

$ svn checkout file:///home/vanhoudn/winhome/svnrepo/Documents/www workspace/www
A    workspace/www/amt
...
Checked out revision 102.

```

And I can modify a file on the working copy just fine: 
```

vanhoudn@gauze:~$ cd workspace/www
vanhoudn@gauze:~/workspace/www$ ls
amt  index.html  website
vanhoudn@gauze:~/workspace/www$ vi index.html 
vanhoudn@gauze:~/workspace/www$ svn status
M       index.html

```

But when I commit I get this weird error:
```

vanhoudn@gauze:~/workspace/www$ svn commit -m "A test Ubuntu to Windows commit"
Sending        index.html
Transmitting file data .svn: Commit failed (details follow):
svn: Can't read directory '/home/vanhoudn/winhome/svnrepo/db/transactions/102-3c.txn': Partial results are valid but processing is incomplete

```

And as far as I can tell it's not a permission error: 
```

vanhoudn@gauze:~/workspace/www$ ls -la /home/vanhoudn/winhome/svnrepo/db/transactions/
total 8
drwxrwxrwx 1 vanhoudn vanhoudn 4096 2010-08-10 11:36 .
drwxrwxrwx 1 vanhoudn vanhoudn 4096 2010-08-10 11:36 ..
drwxrwxrwx 1 vanhoudn vanhoudn    0 2010-08-10 11:20 101-3a.txn
drwxrwxrwx 1 vanhoudn vanhoudn    0 2010-06-17 12:43 88-2t.txn
drwxrwxrwx 1 vanhoudn vanhoudn    0 2010-06-17 12:48 89-2v.txn
drwxrwxrwx 1 vanhoudn vanhoudn    0 2010-06-17 12:49 89-2w.txn
drwxrwxrwx 1 vanhoudn vanhoudn    0 2010-06-17 12:49 89-2x.txn

```

Any thoughts on how to fix this? I'm open to any ideas.  

Cheers,

Nathan

---

