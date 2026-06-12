---
title: "rsync raid problem"
date: 2010-03-01
forum: Server Platforms
---

### Post by ccreese on 2010-03-01
Hello.

I'm running a LaCie 4Big Quadra in RAID5 on a LaCie eSATA II PCI Card ([http://www.lacie.com/us/products/product.htm?pid=11217](http://www.lacie.com/us/products/product.htm?pid=11217)) as a backup destination for an internal hard drive on a data server running 8.10.

I use rsync to create hourly copies of the internal data drive, and cp -al to hard link weekly, monthly, and yearly copies. I use rsync with the --link-dest option so as to copy only files that have changed, and to hard-link the rest:

rsync -aP --exclude-from=$excludes --link-dest=$backuproot/current $directory $backupdestination/backup-$date

When I run it manually (normally I have it running on cron), it looks like it should, i.e. it goes quickly, and reports a speedup of several thousand, which should mean that it hardlinked, rather than copied, most of the files. 

When I compare files that I know have not changed, however, using ls -ial, they have different inodes, and are only linked once (except those that have been linked to daily or weekly images created by cp -al). Furthermore, the total disk usage of the directory containing the hourly images is the same as the size of each image * the number of images. 

What gives?

---

### Post by ccreese on 2010-03-15
To any interested, I found the problem, and it has nothing to do with the RAID, as I discovered with a diagnosis of the same problem on my home computers not on RAID.

After creating a backup, rather than leave all permissions intact - ensured by using archive mode - I wanted backups to be non-writeable by all. So I threw in a 'chmod -R a-w' immediately following the rsync command. I was unaware that this somehow prevents hardlinking of the file, leaving me with a very fast rsync process that creates a duplicate file with a different inode - and hence double the space. By simply changing this to 'chmod go-w', the problem was solved. 

So the moral of the story: apparently at least owner write permissions are necessary to hard-link a file. Don't ask me why.

---

