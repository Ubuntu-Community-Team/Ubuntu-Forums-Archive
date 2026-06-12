---
title: "tar.gz files are corrupt"
date: 2013-03-04
forum: Server Platforms
---

### Post by osaeris on 2013-03-04
Hi all,

I'm having a problem with tar.gz backups. Our Moodle server backs up the moodle2 database and folders then copies them over the network to a backup location. 

This has been working fine for quite some time but recently the backups have completed but the tar.gz files are corrupt.

I've used the following commands in a shell script to do the actual backups. The /backups folder is a samba share but I don't think that's relevant.

```
sudo mysqldump -uuser -ppass moodle2 > /tmp/moodle2_$Today.sql
sudo tar -zcpf /tmp/moodle2_$Today.tar.gz --exclude-vcs   /var/moodle2data /var/www/moodle2 /tmp/moodle2_$Today.sql
sudo cp /tmp/moodle2_$Today.tar.gz /backups/weekly/
```

The tar.gz file resulting is around 5Gb. When I try to extract I get unexpected end of file error. I tried with 7zip which says 'tar file is broken'.

```
strace gunzip /home/me/Desktop/moodle2_03_03_13.tar.gz
``` ends like this:

```
write(4, "\324\224\0\224\224\264P\2\203O\25\30\247\251\240\5\242\226\222\200\22\222\226\222\200\22\222\226\222\200\nz"..., 20098) = 20098
write(2, "\ngzip: ", 7
gzip: )                 = 7
write(2, "/home/me/Desktop/moodle2_03"..., 70/home/me/Desktop/moodle2_03_03_13.tar.gz: unexpected end of file
) = 70
rt_sigprocmask(SIG_BLOCK, [HUP INT PIPE TERM XCPU XFSZ], [], 8) = 0
close(4)                                = 0
unlink("/home/me/Desktop/moodle2_03_03_13.tar") = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
exit_group(1)      
```

I thought that the lines : 

```
write(2, "\ngzip: ", 7
gzip: )                 = 7
```

Looked a little strange with the new line.

Does anyone have a clue as to what could be happening ?

---

### Post by osaeris on 2013-03-04
Sorry to reply to myself but I've just noticed that the backup file is exactly the same size as the free space on the / partition. I'm going to use another location other than /tmp which has plenty of free space :oops:

---

