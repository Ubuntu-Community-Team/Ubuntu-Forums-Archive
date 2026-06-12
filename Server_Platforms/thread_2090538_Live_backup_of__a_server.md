---
title: "Live backup of  a server"
date: 2012-12-02
forum: Server Platforms
---

### Post by lseg on 2012-12-02
Hi,

based on the proposals in [http://ubuntuforums.org/showthread.php?t=2089093](http://ubuntuforums.org/showthread.php?t=2089093), I would like to use a separate Hard disk or USB stick for everything except the Home directory.

My system looks like this:
Filesystem      1K-blocks      Used  Available Use% Mounted on
/dev/md0        103211224   9595268   88373132  10% /
udev              1943272         4    1943268   1% /dev
tmpfs              780912      2516     778396   1% /run
none                 5120         0       5120   0% /run/lock
none              1952272       152    1952120   1% /run/shm
/dev/md1       4637234520 660814044 3742717412  16% /home

First thing I would like to do is make a copy of everything on /dev/md0, to a new drive, without having to shutdown the server.

After this I would like to boot to this new drive (basically adapting Grub), this I can do.

Second thing I need your advice for is probably same as for first question.

I would like to make sure /dev/md0 would stay an exact copy of this new HDD. So in case this new HDD fails, I can fall back on /dev/md0 again.
So basically I would like to make a live copy of / except /home using crontab.

Is it actually possible ?

Kind regards,

Luc

---

### Post by jamesr on 2012-12-02
Hi Luc,

I do not know if this is what you are looking for but, personally, I would suggest that you look at the mondorescue.org website. 

I use MondoArchive/Rescue to back up my servers, so that I can do a bare metal recovery if necessary. There is an option to back up to USB key which becomes bootable. Therefore fairly instant recovery if needed. One could combine with crontab to do a backup weekly, as I do or daily if necessary. 

You can also exclude directories if you require. 

My method is slightly different in that I backup to another pc with an external harddrive as CD sized iso's The first of the list is the bootable cd and I would burn to a CD or convert to a USB key so I can boot then I would recover the rest from the harddrive. Equally one could use DVDs

Best Wishes
 Jim

---

### Post by lseg on 2012-12-03
Hi,

I have the impression Mondo rescue is meant to make a snapshot of a live system, storing on a CD/DVD/... or in a Tar or whatever format on a HDD. You would first have to do a restore action to a new drive before, you can boot to this new drive.

My preference would go to keep a sync from the boot drive in the existing md0, so in case of failing of the single drive, I just have to change the boot sequence (and mounting) to be up and running again. Not needing a restore action.

I searched the web, and found following link:
[https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)

But I have to be honest I am not fully understanding it yet.

Please give your opinion.

Kind regards,

Luc

---

### Post by thnewguy on 2012-12-03
I would definitely recommend using rsync. There are a lot of options for the rsync command, but in most cases you can get by with something farily straight forward like this:

rsync -auv /source-dir /destination-dir

Basically that tells rsync to copy any new files from the source directory to the destination, skipping any old files or files which have not changed. You can use "exclude" filters to avoid copying certain files or directories, like /home. For example

rsync -auv --exclude='/home*' --exclude='/media' /media/external-disk

This should sync all of your files, except those in the /media and /home folders and send your files to a disk mounted at /media/external-disk. I honestly haven't tried using rsync with multiple excludes like this, but I think it will work. You can get more info by reading the rsync manual page and looking at the --exclude and --exclude-from parameters.

---

