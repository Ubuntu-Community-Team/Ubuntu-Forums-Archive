---
title: "weird disk almost full issue"
date: 2011-07-13
forum: Server Platforms
---

### Post by surfer63 on 2011-07-13
Hi,

I've got an Ubuntu box on server version 10.04. I thought it was about time to upgrade and checked my system. All of a sudden (since 1-2 weeks?) my root system is almost full.
If I do a "df -h", I get:
```
/dev/sda4              17G   14G  1.6G  91% /
none                  493M  280K  493M   1% /dev
none                  498M     0  498M   0% /dev/shm
none                  498M  656K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw
/dev/sda6              29G  8.1G   19G  30% /opt
```
These are off course the locally mounted partitions.
The issue is off course the root partition having 17G and 14G in use. To my knowledge and experience this should be well below 8G instead of 14G.

When I do a "sudo du --max-depth=1 -xh /", I get the following:
```
4.0K	/mnt
595M	/var
8.0K	/export
13M	/etc
0	/sys
16K	/lost+found
0	/proc
200K	/srv
4.0K	/selinux
3.7G	/usr
29M	/boot
831M	/home
4.0K	/initrd
28K	/media
4.0K	/opt
25M	/data
2.0M	/tmp
5.6M	/root
7.3M	/sbin
0	/dev
5.2M	/bin
228M	/lib
5.4G	/
```
I'm really clueless. How is this possible? Where is the approximately extra 7-8G I expected to have free?

---

### Post by karlson on 2011-07-13
> **surfer63 said:**
> 
When I do a "sudo du --max-depth=1 -xh /", I get the following:
```
4.0K	/mnt
595M	/var
8.0K	/export
13M	/etc
0	/sys
16K	/lost+found
0	/proc
200K	/srv
4.0K	/selinux
3.7G	/usr
29M	/boot
831M	/home
4.0K	/initrd
28K	/media
4.0K	/opt
25M	/data
2.0M	/tmp
5.6M	/root
7.3M	/sbin
0	/dev
5.2M	/bin
228M	/lib
5.4G	/
```
I'm really clueless. How is this possible? Where is the approximately extra 7-8G I expected to have free?

Sometimes happens when an open file is removed.

You can run
```

sudo lsof | sort -k -n7

```

this will give you a list of files currently opened sorted in size order.

---

### Post by surfer63 on 2011-07-13
> **karlson said:**
> Sometimes happens when an open file is removed.

You can run
```

sudo lsof | sort -k -n7

```

this will give you a list of files currently opened sorted in size order.
Thanks, your command was not completely correct as I found out, but your command got me on the right track and with a little googling I found that I had to use ```

sudo lsof | sort -k 7

```
It gave me a huge list (4339) but all open "files" in there are OK.


I did some more googling and found [HOWTO: Recover Lost Disk Space](http://ubuntuforums.org/showthread.php?t=1122670). I found that Trash files can be a burden too, so I tried:
```
sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
du: cannot access `/opt/Network': No such file or directory
du: cannot access `Trash': No such file or directory
du: cannot access `Folder': No such file or directory
12K	/opt/.Trash-1000
12K	/root/.local/share/Trash
16K	/home/harryvanderwolf/.local/share/Trash
4.0K	/home/harryvanderwolf/.local/share/Trash/files
4.0K	/home/harryvanderwolf/.local/share/Trash/info
4.0K	/opt/.Trash-1000/files
4.0K	/opt/.Trash-1000/info
4.0K	/root/.local/share/Trash/files
4.0K	/root/.local/share/Trash/info
```
Nothing much there either.

And I forgot to mention earlier that I already did a file check (with -n for mounted file system) which came out clean
```
sudo fsck.ext3 -n /dev/sda4
e2fsck 1.41.11 (14-Mar-2010)
Warning!  /dev/sda4 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda4: clean, 212100/2174816 files, 3705542/4347590 blocks
```

Any other hints please?

---

### Post by karlson on 2011-07-13
> **surfer63 said:**
> Thanks, your command was not completely correct as I found out, but your command got me on the right track and with a little googling I found that I had to use ```

sudo lsof | sort -k 7

```


You're right but I actually meant:

```

sudo lsof | sort -n -k 7

```

Need to sort by numerical value.

> 
It gave me a huge list (4339) but all open "files" in there are OK.

I did some more googling and found [HOWTO: Recover Lost Disk Space](http://ubuntuforums.org/showthread.php?t=1122670). I found that Trash files can be a burden too, so I tried:
```
sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
du: cannot access `/opt/Network': No such file or directory
du: cannot access `Trash': No such file or directory
du: cannot access `Folder': No such file or directory
12K	/opt/.Trash-1000
12K	/root/.local/share/Trash
16K	/home/harryvanderwolf/.local/share/Trash
4.0K	/home/harryvanderwolf/.local/share/Trash/files
4.0K	/home/harryvanderwolf/.local/share/Trash/info
4.0K	/opt/.Trash-1000/files
4.0K	/opt/.Trash-1000/info
4.0K	/root/.local/share/Trash/files
4.0K	/root/.local/share/Trash/info
```
Nothing much there either.


Try emptying your trash but that will proabably not be enough.

> 
And I forgot to mention earlier that I already did a file check (with -n for mounted file system) which came out clean
```
sudo fsck.ext3 -n /dev/sda4
e2fsck 1.41.11 (14-Mar-2010)
Warning!  /dev/sda4 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda4: clean, 212100/2174816 files, 3705542/4347590 blocks
```

Any other hints please?

The removed open file would make the filesystem dirty as the directory structure and inodes remain intact.  The simplest way to clear up files like this is to restart the process holding the lock.  There is a way to get inodes in use but not in the directories, but I don't remember what it is.

---

### Post by sexymax15 on 2011-07-13
thx:guitar:

---

### Post by surfer63 on 2011-07-13
> **karlson said:**
> You're right but I actually meant:

```

sudo lsof | sort -n -k 7

```

Need to sort by numerical value.

Yes, that works.


> **karlson said:**
> Try emptying your trash but that will proabably not be enough.
That freed 15 MB.



> **karlson said:**
> The removed open file would make the filesystem dirty as the directory structure and inodes remain intact.  The simplest way to clear up files like this is to restart the process holding the lock.  There is a way to get inodes in use but not in the directories, but I don't remember what it is.
I restarted my server to free them: no change.
I used a live CD to boot my server, forced a check on my file system (sudo fsck.ext3 -f /dev/sda4): clean
Started the server normally again: no change.

By now I googled a lot of things but I still don't have a clue.

---

### Post by karlson on 2011-07-13
Just for my sanity does output of 

```

sudo du --max-depth=1 -xh 1 /

```

match output of

```

sudo du -skh /*

```

---

### Post by surfer63 on 2011-07-14
> **karlson said:**
> Just for my sanity does output of 

```

sudo du --max-depth=1 -xh 1 /

```

match output of

```

sudo du -skh /*

```
Not completely as the first command doesn't check my (remotely) mounted partitions.
```
sudo du --max-depth=1 -xh /
4.0K	/mnt
484M	/var
8.0K	/export
13M	/etc
0	/sys
16K	/lost+found
0	/proc
200K	/srv
4.0K	/selinux
3.7G	/usr
29M	/boot
837M	/home
4.0K	/initrd
36K	/media
4.0K	/opt
25M	/data
268K	/tmp
5.7M	/root
7.3M	/sbin
0	/dev
5.2M	/bin
227M	/lib
5.2G	/

```
```
sudo du -skh /*
5.2M	/bin
29M	/boot
4.0K	/CatalogManager.properties
0	/cdrom
25M	/data
272K	/dev
13M	/etc
8.0K	/export
0	/forcecheck
837M	/home
4.0K	/initrd
0	/initrd.img
0	/initrd.img.old
227M	/lib
16K	/lost+found
449G	/media
4.0K	/mnt
13G	/opt
du: cannot access `/proc/7939/task/7939/fd/3': No such file or directory
du: cannot access `/proc/7939/task/7939/fdinfo/3': No such file or directory
du: cannot access `/proc/7939/fd/3': No such file or directory
du: cannot access `/proc/7939/fdinfo/3': No such file or directory
0	/proc
5.7M	/root
7.3M	/sbin
4.0K	/selinux
200K	/srv
0	/sys
268K	/tmp
3.7G	/usr
485M	/var
0	/vmlinuz
0	/vmlinuz.old
148K	/zm-1.23.3.dump
```

---

### Post by karlson on 2011-07-14
> **surfer63 said:**
> 
```
sudo du -skh /*
5.2M	/bin
29M	/boot
4.0K	/CatalogManager.properties
0	/cdrom
25M	/data
272K	/dev
13M	/etc
8.0K	/export
0	/forcecheck
837M	/home
4.0K	/initrd
0	/initrd.img
0	/initrd.img.old
227M	/lib
16K	/lost+found
449G	/media
4.0K	/mnt
13G	/opt
du: cannot access `/proc/7939/task/7939/fd/3': No such file or directory
du: cannot access `/proc/7939/task/7939/fdinfo/3': No such file or directory
du: cannot access `/proc/7939/fd/3': No such file or directory
du: cannot access `/proc/7939/fdinfo/3': No such file or directory
0	/proc
5.7M	/root
7.3M	/sbin
4.0K	/selinux
200K	/srv
0	/sys
268K	/tmp
3.7G	/usr
485M	/var
0	/vmlinuz
0	/vmlinuz.old
148K	/zm-1.23.3.dump
```

Just as a thought have you by chance considered that you may have some files under your mounts?  Namely there are files in /media and /opt subtrees that are masked by mounts?

---

### Post by surfer63 on 2011-07-14
> **karlson said:**
> Just as a thought have you by chance considered that you may have some files under your mounts?  Namely there are files in /media and /opt subtrees that are masked by mounts?
Yes, I did. 
/opt is a totally diferent file system (root is /dev/sda4, /opt is /dev/sda6).
/media is where some of my NAS shares are mounted but there are no stray files.

But thanks for still thinking with me.

---

### Post by surfer63 on 2011-07-17
> **surfer63 said:**
> Yes, I did. 
/opt is a totally diferent file system (root is /dev/sda4, /opt is /dev/sda6).
/media is where some of my NAS shares are mounted but there are no stray files.

I feel quite stupid. I overlooked one of the mounts in /media and forgot to unmount that one. This morning I did the whole check again and didn't foget to unmount it. That single forgotten one was just the one that had 8.5GB underneath it.

Thanks for helping me.

---

