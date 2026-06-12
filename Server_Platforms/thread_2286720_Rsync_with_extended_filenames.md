---
title: "Rsync with extended filenames"
date: 2015-07-14
forum: Server Platforms
---

### Post by MOGuy78 on 2015-07-14
I have a question on how to sync these files/directories from one directory on my computer to a
backup directory on the same computer.

Is this the correct rsync command?  If not, what would it be?

rsync /hd-vids/Xmasvids    /Backup/Xmas


These are some of the directories/files that will be copied

/hd-vids/Xmasvids/Family 2015	  	
Mom.jpg			(File to copy inside     /.../Family 2015)
kids singing.mp4	(Video to copy inside    /.../Family 2015)


Will rsync even work to copy these extended directory names and extended filenames?
If not, what command could I use?

---

### Post by Lars Noodén on 2015-07-14
> **MOGuy78 said:**
> Is this the correct rsync command?  If not, what would it be?

rsync /hd-vids/Xmasvids    /Backup/Xmas


This should work for you:

```

rsync -a /hd-vids/Xmasvids/    /Backup/Xmas/

```

The -a tells [rsync](http://manpages.ubuntu.com/manpages/trusty/en/man1/rsync.1.html) to recursively (-r) copy, including symlinks (-l), preserving permissions (-p), preserving modification times (-t), preserving groups (-g) and owners (-o), and preserving any device or special files (-D).   You could write it as -rlptgoD but -a is shorter.  

The trailing slashes remind rsync to treat them as directories, something that it won't do otherwise.

---

### Post by MOGuy78 on 2015-07-17
Great, thanks!

Another question;  If I copy a new file to /hd-vids/Xmasvids and then run the above command, will it re-copy every file to /Backup/Xmas, or will it just copy the new file?

What if I edit a file already existing in the Backup/Xmas directory?  If I use that command, will it re-copy every file to /Backup/Xmas?

---

### Post by CharlesA on 2015-07-17
> **MOGuy78 said:**
> Great, thanks!

Another question;  If I copy a new file to /hd-vids/Xmasvids and then run the above command, will it re-copy every file to /Backup/Xmas, or will it just copy the new file?

It will only copy the new file.

---

### Post by Lars Noodén on 2015-07-17
In addition, one of the really clever things about rsync is that if you change an old file, only the changes get copied, not the entire file.  

[https://rsync.samba.org/how-rsync-works.html](https://rsync.samba.org/how-rsync-works.html)

---

### Post by MOGuy78 on 2015-07-18
Nice!  One last question.

Is there a way to use the rsync command over a local network?  This would be used to back up my family's home server (192.168.1.101) onto this backup server.

Maybe:

rsync -a /192.168.1.101/server/hd01/    /Backup/Network/hd01/

Is this a possibility?

---

### Post by Lars Noodén on 2015-07-18
The syntax would be something like this to copy from the remote machine to the local one:

```

 rsync -a moguy78@192.168.1.101/server/hd01/ /Backup/Network/hd01/

```

It runs over SSH by default these days to that does not have to be specified unless you are using special options or keys.

---

### Post by CharlesA on 2015-07-18
> **Lars Noodén said:**
> The syntax would be something like this to copy from the remote machine to the local one:

```

 rsync -a moguy78@192.168.1.101/server/hd01/ /Backup/Network/hd01/

```

It runs over SSH by default these days to that does not have to be specified unless you are using special options or keys.

In addition to that, it will prompt you for a password, which is why I use passphrase-less rsa keys if I am going to be running a backup job to a remote system via cron or whatnot.

---

### Post by MOGuy78 on 2015-07-19
Great!  I really only plan on syncing the network server 2 or 3 times a week, so I'll probably run it manually.

Anyway, thanks guys for all the help!

---

