---
title: "tar over ssh died at 16 GB remote file as expected"
date: 2009-07-28
forum: Server Platforms
---

### Post by dragos2 on 2009-07-28
What I did:

- I started on one server a full # tar zcvf - / | ssh [EMAIL="root@mybackup.com"]root@mybackup.com[/EMAIL] "cat > /backup/sda3.tar.gz"

and guess what on the backup server:

backup:/backup# ls -l
total 15690444 -rw-r--r-- 1 root root 16051315923 2009-07-28 13:19 sda3.tar.gz

backup:/backup# ls -lh
total 15G -rw-r--r-- 1 root root 15G 2009-07-28 13:19 sda3.tar.gz


It died at 16 GB, the maximum allowed size for a file on ext3 with 1 KB
block size I guess.


Any ideas of how to overcome this ? Better compression(network speed and cpu
are not a problem), other aproach ?

---

### Post by regala on 2009-07-28
> **dragos2 said:**
> 
Any ideas of how to overcome this ? Better compression(network speed and cpu
are not a problem), other aproach ?

Use another compression algorithm ?
```

tar cvf - / | lzma -9c | ssh root@mybackup.com "cat > /backup/sda.tar.lzma"

```
(this will take longer and _really_ more memory, but be really better compressed)

---

### Post by Brazen on 2009-07-28
Is switching file systems an option?  You could use XFS on the destination file system.

Otherwise, I believe if your read 'man tar' there are some options for having tar split archives into chunks on the fly.

---

### Post by grantemsley on 2009-07-28
Back it up in sections:

tar cvf - /usr | lzma -9c | ssh [email]root@mybackup.com[/email] "cat > /backup/sda-usr.tar.lzma"

tar cvf - /home | lzma -9c | ssh [email]root@mybackup.com[/email] "cat > /backup/sda-home.tar.lzma"

etc.

---

### Post by dragos2 on 2009-07-29
> **regala said:**
> Use another compression algorithm ?
```

tar cvf - / | lzma -9c | ssh root@mybackup.com "cat > /backup/sda.tar.lzma"

```(this will take longer and _really_ more memory, but be really better compressed)

It seems to block or running very slow on 8 cores.

---

### Post by dragos2 on 2009-07-29
> **Brazen said:**
> Is switching file systems an option?  You could use XFS on the destination file system.

Otherwise, I believe if your read 'man tar' there are some options for having tar split archives into chunks on the fly.

No, I will remain to ext3 for now. I have xfs on one server but I still prefer ext3.
Thanks for suggestion.

---

### Post by dragos2 on 2009-07-29
> **grantemsley said:**
> Back it up in sections:

tar cvf - /usr | lzma -9c | ssh [EMAIL="root@mybackup.com"]root@mybackup.com[/EMAIL] "cat > /backup/sda-usr.tar.lzma"

tar cvf - /home | lzma -9c | ssh [EMAIL="root@mybackup.com"]root@mybackup.com[/EMAIL] "cat > /backup/sda-home.tar.lzma"

etc.

Thanks for suggestion.

---

### Post by dragos2 on 2009-07-29
The backup blocked at /proc/kcore, it seems that it will read from RAM forever, it is
a good idea to exclude from the backup the /proc ?

---

### Post by juancarlospaco on 2009-07-29
Split or EXT4 :)

---

### Post by grantemsley on 2009-07-29
I generally exclude /proc, /sys, and /dev from the backups.  They are all automatically generated.  Make sure you keep the directories, just not the contents.

---

