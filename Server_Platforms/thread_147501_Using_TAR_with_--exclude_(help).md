---
title: "Using TAR with --exclude (help)"
date: 2006-03-20
forum: Server Platforms
---

### Post by wgregori on 2006-03-20
I've tried using the --exclude command with TAR with little success.  I've tried
--exlcude=dir2
--exlcude=/tmp/dir2
--exlcude=/tmp/dir2/

But I can not make it work.  Can someone please tell me what I'm doing wrong.

Thanks,
Wayne

wayne@ubuntu:/tmp$ ls -l
total 24
drwxr-xr-x  2 root  root  4096 2006-03-20 07:31 dir1
drwxr-xr-x  2 root  root  4096 2006-03-20 07:29 dir2
drwxr-xr-x  2 root  root  4096 2006-03-20 07:41 dir3
drwxr-xr-x  2 root  root  4096 2006-03-20 07:29 dir4
-rw-------  1 wayne wayne 8145 2006-03-20 07:33 zmanpjtxrD


wayne@ubuntu:/tmp$ sudo tar -zcvpf dir3/dirs.tar.gz /tmp --exclude=dir2
tar: Removing leading `/' from member names
/tmp/
/tmp/dir1/
/tmp/dir1/test.txt
/tmp/dir2/
/tmp/dir3/
/tmp/dir3/dirs.tar.gz
/tmp/dir4/
/tmp/zmanpjtxrD
tar: --exclude=dir2: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors

---

### Post by LordHunter317 on 2006-03-20
You have to give the path tar sees.   That would be /tmp/dir2 in this case.

---

### Post by wgregori on 2006-03-20
I tried that too... no dice.  

thanks for the reply.


wayne@ubuntu:/tmp$ sudo tar -zcvpf dir3/dirs.tar.gz /tmp --exclude=/tmp/dir2
Password:
tar: Removing leading `/' from member names
/tmp/
/tmp/dir1/
/tmp/dir1/test.txt
/tmp/dir2/
/tmp/dir3/
/tmp/dir3/dirs.tar.gz
/tmp/dir4/
/tmp/zmanpjtxrD
tar: --exclude=/tmp/dir2: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors

---

### Post by wgregori on 2006-03-20
I've spent all day playing with this but I can't seem to get it to work.  Can someone verify that I'm not going crazy and see if they can make this work on Ubuntu server

$ cd /tmp/testdir
$ ls
dir1 dir2 dir3
$ tar -zcvpf dir3/dirs.tar.gz --exclude=dir2 --exclude=dir3 .
./
./dir1/
./dir1/file0
./dir1/file1
./dir1/file2
./dir1/file3
./dir1/file4

Thanks

---

### Post by colo on 2006-03-20
--exclude accepts a shell-style wildcard for a pattern not to incorporate into the archive. The following should give you a clue on how to make use of this:
```
colo@zealot ~/tmp/tartest $ ll
total 24
drwxr-xr-x  2 colo users 4096 Mar 21 01:23 dir1
drwxr-xr-x  2 colo users 4096 Mar 21 01:23 dir2
drwxr-xr-x  2 colo users 4096 Mar 21 01:23 dir3
drwxr-xr-x  2 colo users 4096 Mar 21 01:23 dir4
drwxr-xr-x  2 colo users 4096 Mar 21 01:23 dir5
drwxr-xr-x  2 colo users 4096 Mar 21 01:23 dir6
colo@zealot ~/tmp/tartest $ tar -cf archive.tar --exclude="dir[135]" *
colo@zealot ~/tmp/tartest $ tar -tf archive.tar 
dir2/
dir4/
dir6/
colo@zealot ~/tmp/tartest $ 
```

--exclude="*dir2*" (for example) should yield you what you need.

---

### Post by wgregori on 2006-03-21
Thank you Colo but I had to move the "--eclude=" parameter to the begining of the statement to make it work.  

tar --exclude=dir2 -cvzf /test/dir3/test.tar.gz /test

This version of TAR would not accept the exclude statement at the end of the TAR statement as is seen in most examples.

Thanks,
Wayne

---

### Post by sdyson on 2006-03-26
[QUOTE=wgregori]Thank you Colo but I had to move the "--eclude=" parameter to the begining of the statement to make it work.  

tar --exclude=dir2 -cvzf /test/dir3/test.tar.gz /test

This version of TAR would not accept the exclude statement at the end of the TAR statement as is seen in most examples.

Thanks,
Wayne[/QUOTE]
I feel your pain Wayne. I had pretty much the same problem as you with a tar command I know I have used successfully before because I use it to back up my home directory. Your tip to move the exclude to the beginning worked so I thank you for saving me some time. I can only assume this is a recently introduced bug.

---

### Post by Basfriends on 2006-05-09
Hey your tip is working for me as well. Thnx i was getting desperate...

---

### Post by Boelcke on 2006-06-17
I've been fiddling with Heliode's simple method of completely backing up the system...
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)
...and couldn't get it to work until discovering this fact.  --exclude must go first!

---

### Post by sql on 2008-02-04
tar -cvzpP --file=/distr/backup.tar.gz --exclude={/dev/*,/proc/*,/sys/*,/srv/*,/distr/*,/tmp/*} /


tar work with directory "/"  except for
/dev
/proc
/sys
/srv/
/distr
/tmp

:)

and it really works :)

---

