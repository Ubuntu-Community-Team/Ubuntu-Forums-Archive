---
title: "Backup a VPS?"
date: 2012-02-25
forum: Server Platforms
---

### Post by d4m1r on 2012-02-25
Hey guys, I have root access to a OpenVZ VPS running Ubuntu 11.04 (no GUI) and I am wondering about options to backup my data/system files? I'd like to backup ALL files and directories on my VPS into a single file (compressed preferably) and then download the file to my PC through FTP.

Is that possible or any other recommendations?

---

### Post by CharlesA on 2012-02-25
Do you have ssh access? If you do, rsync might be a better idea.

I believe you can tar the whole directory structure except for /dev and /proc

---

### Post by d4m1r on 2012-02-26
> **CharlesA said:**
> Do you have ssh access? If you do, rsync might be a better idea.

I believe you can tar the whole directory structure except for /dev and /proc

I do, but rsync seems mainly to be used to offload a backup to another server, not create a local copy (in a single file).

---

### Post by CharlesA on 2012-02-26
Tar would be the best option then.

---

### Post by spynappels on 2012-02-26
> **CharlesA said:**
> Tar would be the best option then.

+1 and don't forget to gzip it too and if your local pc is a Linux desktop you can still initiate the rsync job from the local PC to copy it back.

---

### Post by CharlesA on 2012-02-26
> **spynappels said:**
> +1 and don't forget to gzip it too and if your local pc is a Linux desktop you can still initiate the rsync job from the local PC to copy it back.
Indeed. I'd go with either scp, sftp or rsync, with rsync being the ideal way to transfer the file.

---

### Post by Lars Noodén on 2012-02-26
> **CharlesA said:**
> Tar would be the best option then.

You can run [tar](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tar.1.html) on the remote system and still save the results locally.  Here is a simple example, yours will obviously have to be more complex to exclude various directories.

```

ssh d4m1r@vps.example.org "tar zcf - /var/www/" >  www-backup.tgz

```

That will avoid the trouble of having a temporary tarball taking up space on the remote machine.  That is especially relevant if you were going to back up the whole machine as you mentioned.

---

### Post by Irregular Joe on 2012-02-29
Rsync is your best option as only files that have changed (or have been deleted) will be sync'd.  If you tar/zip the files, then the entire archive would have to be moved, which would be of significant size.

I use rsync to give me a complete backup of each server.  The initial backup takes awhile (6G of OS files and data), but once that has finished, it only takes a minute or less to replicate the changed data.

Another similar option is rdiff-backup as you can get incremental backups (what did this file look like 2 weeks ago?).  It automatically manages the increments and only replicates parts of files that have changed.  You always have the equivalent of the latest rsync output at your destination, plus the addition of an 'rdiff-backup-data' directory that holds just the changes.  If I screw something up, I can just use rsync from the backup to restore the file to the latest backup state.  There are options for rdiff-backup to recover past versions of files/directories.  Very nice!

Hope this helps!

---

### Post by d4m1r on 2012-02-29
> **Irregular Joe said:**
> Rsync is your best option as only files that have changed (or have been deleted) will be sync'd.  If you tar/zip the files, then the entire archive would have to be moved, which would be of significant size.

I use rsync to give me a complete backup of each server.  The initial backup takes awhile (6G of OS files and data), but once that has finished, it only takes a minute or less to replicate the changed data.

Another similar option is rdiff-backup as you can get incremental backups (what did this file look like 2 weeks ago?).  It automatically manages the increments and only replicates parts of files that have changed.  You always have the equivalent of the latest rsync output at your destination, plus the addition of an 'rdiff-backup-data' directory that holds just the changes.  If I screw something up, I can just use rsync from the backup to restore the file to the latest backup state.  There are options for rdiff-backup to recover past versions of files/directories.  Very nice!

Hope this helps!

I believe neither of those apply to OpenVZ containers, which are virtual environments. Also, when I made a complete backup of my VPS (found a shell script), the backup was only ~700MB.

---

