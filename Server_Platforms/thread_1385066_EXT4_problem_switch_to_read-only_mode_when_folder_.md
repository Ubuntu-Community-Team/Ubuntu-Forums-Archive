---
title: "EXT4 problem: switch to read-only mode when folder lost+found is accessed"
date: 2010-01-19
forum: Server Platforms
---

### Post by pvledoux on 2010-01-19
Hi,

I have a weird problem here with a 9.04 server. We have a raid 5 disk formatted in EXT4 which remounted automatically when we accessed to the lost+found folder which is in the root of that disk.

The error in the syslog is:

```
Jan 19 11:14:45 ipf-srv001 kernel: [ 5478.859996] EXT4-fs error (device sdb1): ext4_iget: bad extended attribute block 50599009714176 in inode #25338
Jan 19 11:14:45 ipf-srv001 kernel: [ 5478.860003] Aborting journal on device sdb1:8.
Jan 19 11:14:45 ipf-srv001 kernel: [ 5478.860051] Remounting filesystem read-only
```

I ran e2fsck but with no results.

I tried to delete it but I can't. It's a bit annoying because I have to prevent all users and backups to access to that folder.

Any idea how I can remove that folder?

Thanks!


Pv

---

### Post by yogesh.girikumar on 2010-01-19
Hi,


       First off, a bit of info about Lost+found directory. It's a directory that is created everytime a filesystem check is performed. If the file system check (fsck) finds any corrupt files, it dumps them into the lost+found folder so that you can look into the file dump and there could be a chance of data recovery.

Check this link out: [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

In your case, the directory could have been created every time you run e2fsck. Since the directory is owned by "root" you won't be able to delete it unless you become superuser.
       There are some issues with EXT4 that are waiting to be sorted out by the development team. There is also a possibility that your problem could be a bug. 

Like this one : [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all)

Here are some resources. [ Loong read ! ;-) ]


[LIST=1]
[*]Ext4 is faster but I'm not sure about its stability. 
[http://gmrpgsql.tumblr.com/post/73798984/initial-ext3-vs-ext4-results](http://gmrpgsql.tumblr.com/post/73798984/initial-ext3-vs-ext4-results)
[*]This is a blog by Theodore Ts'o, a kernel developer on Ext4: [http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/](http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/)
[*]A forum discussion about Ext3 vs. Ext4.: [http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)
[/LIST]
Meanwhile, you can try checking your filesystem for bad blocks, some filesystem hardware errors might cause a lot of data corruption which might result in frequent disk checks and consequently, large lost+found directories.

```
man badblocks
```Let me know if this helps.
--
Yogesh Girikumar

---

### Post by pvledoux on 2010-01-19
Thanks for your reply Yogesh.

The weird thing is that the disk switch to read-only when I just ls the lost+found folder. 
Indeed, it's probably linked to one of the bug reported about EXT4.

---

