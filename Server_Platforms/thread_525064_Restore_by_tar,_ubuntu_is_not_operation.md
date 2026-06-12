---
title: "Restore by tar, ubuntu is not operation"
date: 2007-08-13
forum: Server Platforms
---

### Post by nothingelse on 2007-08-13
Hello everybody,
I install Ubuntu 7.04, LAMP, Postfix, Squirrellmail, Dovecot. I backup by command tar.
[root@deep] /# cd /
[root@deep] /# tar  cpf /backups/full-backup-`date '+%d-%B-%Y'`.tar \ --directory / --exclude=proc --exclude=mnt --exclude=backups \ --exclude=cache --exclude=*/lost+found .

After, I format / and  install Ubuntu 7.04 again. I mount /backups and start restore.
[root@deep] /# cd /
[root@deep] /# tar xpf /backups/full-backup-Day-Month-Year.tar

I reboot computer. Show errors:
Loading, please wait...
[4.436833] sda:assuming drive cache :write through
[4.436983] sda:assuming drive cache :write through
Check root=bootarg cat /proc/cmdline
or missing modules, device: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/cfd6cd86-bf8b-4f03-9185-df98e8d77a69 does not exist. Dropping to a shell!
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh : can't access tty; job control turned off
<initramfs>

Please help me trouble shoot for error. 
Thanks a lot,

---

### Post by Mr. C. on 2007-08-14
You backed up the /dev directory, and restored those devices; those are special "files" that you can't simply overwrite.

I believe you are going to have to recover via the recovery CD.

The lesson here - don't overwrite files that you don't understand.

MrC

---

### Post by lavinog on 2007-08-14
your backup most likely overwrote config files like fstab
generally you don't want to overwrite any of the files in system directories
one reason is you will down grade your install and could really mess things up

the other reason is that there are things that are unique to each install
such as the uuid

you could do a recovery and manually correct the problems, but you would save hours of frustration by just reinstalling, and partially restore your files.

Really you should only need to restore your home folder
then install the programs you had using apt-get
then you should backup the default config files for each program you install (cp configfile.conf configfile.conf.backup is all you need to do) this way if the next step screws it up you can go back to default and manually edit it

then restore each config individually

---

### Post by cookfromfrozen on 2007-08-17
you overwrote fstab.  it's still looking for the partition with the old uuid and it doesn't exist because you made a new file system with a new uuid.

you need to get into fstab from a live cd or somethign and point the partitions to their device names rather than uuids (like /dev/hda1)

or you could use blkid to find out the actual uuid and put that into fstab

---

