---
title: "ownership error while running an ubuntu mirror site?"
date: 2010-08-07
forum: Server Platforms
---

### Post by supremedalek on 2010-08-07
So I setup an internal ubuntu mirror site using ubumirror. I setup the cron scripts and directories to be owned by www-data since that is who the webserver is being run as. During the last two days I have been getting messages saying the cron jobs are not being successfully run. So, I look at the bottom of one of the ubuarchive.log and find this:

```
deleting pool/universe/u/update-manager/auto-upgrade-tester_0.142.4_all.deb
deleting project/trace/atemoya.canonical.com

sent 454075 bytes  received 459730724 bytes  589602.56 bytes/sec
total size is 382786801558  speedup is 831.81
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1526) [generator=3.0.7]
Sat, 07 Aug 2010 00:16:16 -0400: Archive pool sync failed.
```

I looked in the log file further up and found the following entry:

```
pool/main/g/glew/
pool/main/g/glib1.2/
pool/main/g/glib2.0/rsync: send_files failed to open "/pool/main/g/glib2.0/libglib2.0-0_2.25.12-1ubuntu1_i386.deb" (in ubuntu): Permission denied (13)
pool/main/g/glibc-doc-reference/
pool/main/g/glibc/
pool/main/g/glibmm2.4/
```

Why wouldn't it be able to write to that directory? As mentioned before, that entire directory path is owned by www-data:www-data. Am I missing something here?

---

### Post by clrg on 2010-08-08
```
ls -ld /pool/main/g/glib2.0/
```

---

### Post by supremedalek on 2010-08-08
You are right; I should have included that in the original post instead of just stating it.
```
root@mirror:# ls -ld /export/mirror/ubuntu/pool/main/g/glib2.0
drwxrwsr-x 2 www-data www-data 20480 2010-08-07 16:12 /export/mirror/ubuntu/pool/main/g/glib2.0
root@mirror:# 
```
Do you see anything fishy?

---

### Post by clrg on 2010-08-08
The permissions seem fine (as long as the child rsync process runs as www-data). Does www-data have a valid shell? If so, su into the account and create a file in the directory in question. If it works, we know its not a permissions problem.

It could also be the filesystem (although I don't think so). If you are allowed to take the server down, do that and run a fsck.

---

### Post by supremedalek on 2010-08-09
I just checked and had no problems creating files and directories inside the said directory as www-data.

```
root@mirror:~# su - www-data
$ pwd
/var/www
$ cd /export/mirror/ubuntu/ubuntu/pool/main/g/glib2.0
$ touch nose
$ mkdir booger
$ rm -rf nose booger
$ echo $SHELL
/bin/sh
$ 
root@mirror:~# fgrep www-data /etc/passwd
www-data:x:33:33:www-data:/var/www:/bin/sh
root@mirror:~# 
```

---

### Post by clrg on 2010-08-09
Curious. I don't see why this shouldn't work.

The next time the sync is run, do a 

```
ps -ef | grep rsync
```

and check the user rsync is run as. It should be www-data.

---

