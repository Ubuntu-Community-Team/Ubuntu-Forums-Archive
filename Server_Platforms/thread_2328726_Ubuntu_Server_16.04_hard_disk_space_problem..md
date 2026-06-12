---
title: "Ubuntu Server 16.04 hard disk space problem."
date: 2016-06-23
forum: Server Platforms
---

### Post by Rusz_Tams on 2016-06-23
[SOLVED]
Hello everybody!
When i installed first my Ubuntu Server i noticed, that it has got a very minimal space left on it. I reinstalled it, and it has got 27 gb-s out of 30, which is occupied. What can i do?
Please help!
Tamás


[IMG]http://kepfeltoltes.hu/160624/help_www.kepfeltoltes.hu_.png[/IMG]

---

### Post by TheFu on 2016-06-23
Find what is using all the space and remove it.

I'd use **df -h** then **du -sh /path/to/hog** directory - over and over and over moving deeper and deeper until the hogging files are found.

BTW, posting an image here is not so nice to people with limited bandwidth. Posting a link to the image would be kinder.

I may be a little fuzzy, but that looks like Windwos to me.

---

### Post by oldfred on 2016-06-23
This includes /home but none of the data folders as they  are linked into another partition.
```
/dev/sda6        24G  7.3G   16G  32% /
```

So you have something taking a lot of space.

---

### Post by Rusz_Tams on 2016-06-24
```
rusztmas@ubuntu:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         478M     0  478M   0% /dev
tmpfs                        100M   11M   89M  11% /run
/dev/mapper/ubuntu--vg-root   30G  2.3G   27G   8% /
tmpfs                        497M  4.0K  497M   1% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        497M     0  497M   0% /sys/fs/cgroup
/dev/sda1                    472M  101M  347M  23% /boot
tmpfs                        100M     0  100M   0% /run/user/1001
tmpfs                        100M     0  100M   0% /run/user/1002

```
i've got 27gb empty space lol

---

### Post by TheFu on 2016-06-24
a) gotta understand the tools being used and what they are really showing. We've all be caught misunderstanding stuff.
b) please use "code tags" in the future, so things line up. The easier your posts are to read, the more likely someone will help becomes.

Oh - and welcome to the forums.
Please mark this thread as **SOLVED** to help others - both trying to help and looking for answers.

---

### Post by Rusz_Tams on 2016-06-24
Thank you!
How can i mark this post as a solved problem?

---

