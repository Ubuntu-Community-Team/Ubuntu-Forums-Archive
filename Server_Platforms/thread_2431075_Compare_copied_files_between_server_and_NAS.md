---
title: "Compare copied files between server and NAS"
date: 2019-11-11
forum: Server Platforms
---

### Post by sed_faster on 2019-11-11
Hello,

I used the folling command to copy folder and files between server (ubuntu) and Qnap:

```
$ scp -rvp data/ user@192.168.1.50:/share/Public
```

I want to know if all files have been successfully copied. Through windows I consulted the Properties window (using the right mouse button) and the result was as follows:

**--Server Ubuntu**
Size: 3.07 TB (3,384,578,889,263 bytes)
Size on disk: 4.57 TB (5,027,498,351,616 bytes)
Contains: 1,797,813 Files, 169,392 Folders

**--Qnap**
Size: 2.50 TB (2,757,571,816,744 bytes)
Size on disk: 2.51 TB (2,761,236,037,632 bytes)
Contains: 1,646,925 Files, 163,526 Folders

I want to identify if this difference is due to some windows limitation or if not all files were copied after all.
I searched for web solutions and read about the "test", "diff", "rsync" program, but I don't know if these are the best options for manipulating this amount of data.

Thanks

---

### Post by TheFu on 2019-11-11
rsync is what I'd use.  Actually, I would have used rsync to perform the copy.
```
rsync -avz data user@192.168.1.50:/share/Public/
```

rsync is picky about trailing '/' characters.  My version above will create a "/share/Public/data/" directory.  If you don't want the 'data' directory, replace 'data' with 'data/' in the command.  
I don't think the trailing '/' on the target is important, but I always add it for clarity.

If the 'user' matches on both systems, then it isn't needed for the rsync or the scp.
rsync uses ssh for authentication, so if ssh-keys have been setup, then rsync will authenticate like scp, sftp, ssh.

rsync has test options, progress and statistics options.  Just depends on what you'd like as output.

---

### Post by LHammonds on 2019-11-14
I'm with TheFu on this one.  rsync can do the copy for you AND give you a verification report once the job is done so you can have peace of mind that it "actually" finished the entire task.  Another nice thing is that if you want files to be identical on both systems, it can do that as well and ONLY copy the differences each time it runs...not the entire data set so it does not matter if you are adding a few megabytes to a terabyte repository.

LHammonds

---

### Post by sed_faster on 2019-12-03
Hello,

I executed this command:
```

sudo scp -rvp data/ user@192.168.1.50:/share/Public

```

I want to make sure all files have been copied. I am trying execute this command:
```

sudo diff -ryq user@192.168.1.50:/share/Public/data/ /home/user/data/ 

```

But I received this message:
```

diff: admin@192.168.1.4:/share/Public/data/: No such file or directory

```

I was searching about this behaviour and I read about symlinks. So I tried to execute the command with the parameter:
```

sudo diff -ryq --no-dereference user@192.168.1.50:/share/Public/data/ /home/user/data/ 

```

But the result it is the same. How can I handle this problem?

Note: [http://man7.org/linux/man-pages/man1/diff.1.html](http://man7.org/linux/man-pages/man1/diff.1.html)
Regarding the ours suggestion I had not seen before trying again with the scp and diff program. But how can I generate a report with rsync? I've been reading the manual and searching but haven't found a command where the output was a server and client comparison report. ([https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync))

Thanks

---

### Post by TheFu on 2019-12-03
Use **rsync** instead of scp.

If you don't want to actually copy any files, use the --dry-run option with all the normal options to rsync.

I didn't know that diff supported remote system parameters and don't see any mention of that capability in the diff manpage. diff doesn't support --no-dereference according to the manpage either.  Can't just make up options.  

Instead of looking at manpages on the internet, use the ones actually installed on YOUR system.  It does take a few months to learn to read manpages, but once you do, they are usually brilliant. The layout is what someone who understands manpages needs.  Summary at the top, to help people already familiar with a specific command, then more details as we get farther into the manpage.

Anyway, running rsync shouldn't cause any harm if the directories are already all copied over.

Might add *--status --progress* options to the already provided options.

---

### Post by Doug S on 2019-12-03
> **sed_faster said:**
> But how can I generate a report with rsync? I've been reading the manual and searching but haven't found a command where the output was a server and client comparison report. ([https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync))It sounds as though you want more than the standard output:
```
doug@s15:~/backup_smythies.com_03$ rsync --delete --archive [COLOR="#FF0000"]--verbose[/COLOR] --dry-run --progress --exclude 'ext-20*\.bin*' --exclude 'int-20*\.bin*' --exclude 'big' doug@smythies.com:/home/doug ./

receiving incremental file list
doug/
doug/.bash_history
doug/access.log
doug/access.log.1
doug/access.log.2
doug/access.log.3
doug/auth.log
doug/auth.log.1
doug/error.log
doug/error.log.1
doug/error.log.2
doug/error.log.3
doug/mail.err
doug/mail.log
doug/mail.log.1
doug/zz.log
doug/zz.txt
doug/tcpdump/109/
doug/test2/zzxxtest.data

sent 3,914 bytes  received 20,239,890 bytes  941,572.28 bytes/sec
total size is 117,705,867,687  speedup is 5,814.41 (DRY RUN)

```You can play with verbosity to get way way more information, if you want:

```
doug@s15:~/backup_smythies.com_03$ rsync --delete --archive [COLOR="#FF0000"]-vv[/COLOR] --dry-run --exclude 'ext-20*\.bin*' --exclude 'int-20*\.bin*' --exclude 'big' doug@smythies.com:/home/doug ./
receiving incremental file list
delta-transmission enabled
doug/.bash_logout is uptodate
doug/.bashrc is uptodate
doug/.bzr.log is uptodate
doug/.htkes is uptodate
...
doug/config/etc/bind/named.conf.local is uptodate
doug/config/etc/bind/named.conf.local.001 is uptodate
doug/config/etc/bind/named.conf.local.doug is uptodate
doug/config/etc/bind/named.conf.local.original is uptodate
doug/config/etc/bind/named.conf.options is uptodate
doug/config/etc/bind/named.conf.options.doug is uptodate
doug/config/etc/bind/named.conf.options.doug1 is uptodate
doug/config/etc/bind/named.conf.options.original is uptodate
doug/config/etc/bind/named.conf.options.test is uptodate
...
doug/public_html/linux/single-threaded/sweep/power.png is uptodate
doug/public_html/linux/single-threaded/sweep/teo.csv is uptodate
doug/public_html/linux/sort_order/index.html is uptodate
doug/public_html/linux/ubuntu-docs/index.html is uptodate
doug/public_html/linux/ubuntu-docs/langs.htm is uptodate
doug/public_html/linux/ubuntu-docs/load-trace.html is uptodate
doug/public_html/linux/ubuntu-docs/upstream_yelp.html is uptodate
doug/public_html/linux/ubuntu-docs/help.ubuntu.com/compile_desktop_help.txt is uptodate
...

```

---

