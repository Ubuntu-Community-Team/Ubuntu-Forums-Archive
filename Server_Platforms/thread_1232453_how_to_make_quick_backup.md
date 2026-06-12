---
title: "how to make quick backup?"
date: 2009-08-05
forum: Server Platforms
---

### Post by jdakhayman on 2009-08-05
Real quick question. I have a lamp server up and running. (Ubuntu 9.04) It has a dedicated drive just for the OS, and a secondary drive dedicated just for the data. I have considered purchasing a 1tb external usb 2.0 drive to utilise as a on-site backup of my  data drive that I can unplug and take with me in the evening. I wont the backup to occur automatically at the same time. How is this done using rsync and crontab? I know how to mount the drive and list it in fstab. I just wont to make a complete full back up of the data drive everyday at 4:00 so that I can unplug it and take it home every night. Just in case of fire or other disaster etc...

Any advise and/or help in this matter is greatly appreciated.



jdakhayman

---

### Post by ajgreeny on 2009-08-05
Use crontab -e to edit the crontab time and command and then type 
```
0 4 * * * rsync options /dev/sdx#/source/pathway /dev/sdx#/destination/pathway
```The options you use will depend on what exactly you want of the backups.  Have a look at ```
man rsync
``` to see what they all mean.
Note that this will perform the backup at 0400hrs (early morning).  If you want it at 4pm, the figure 4 should be 16.

---

### Post by giggins on 2009-08-05
I'd say check out 'pdumpfs'. Its a pretty good package to do simple backups.

```
sudo apt-get install pdumpfs
```To make use of this though, you've got to have a filesystem that supports hard-links (like ext2, ext3, ext4, reiserfs, xfs, jfs, etc) on your USB device. You can achieve this by formatting the drive. Assuming the drive is on '/dev/sda', then you can run the following command:

```
sudo mkfs.ext3 /dev/sda1
```Careful though, this will delete all data on your USB drive (or whatever volume is /dev/sda1). You can double check its the correct volume by running the 'mount' command and looking for where its mounted.

After you've got pdumpfs installed and a volume to save your backups to, you need to mount your volume somewhere:

```
sudo mkdir /mnt/backups
sudo mount /dev/sda1 /mnt/backup
sudo mkdir /mnt/backup/$HOSTNAME
```You can create your first backup by running this:

```
sudo pdumpfs /var/www /mnt/backup/$HOSTNAME
```This will store your data based on your web server's host name, so you can use the same volume for mulitple servers, if you want.

Now, to make the backups occur automatically every night, use cron:

```
sudo nano /etc/crontab
```Add the following to the bottom of the file:

```
# pdumpfs backup(s)
00 01   * * *   root    pdumpfs /var/www /mnt/backup/$HOSTNAME
```This will backup the system every night at 1AM.

pdumpfs is nice because it creates a sliding window of backups, and allows you to go 'back in time' to a previous version of the file. It's also a lot more efficient than full backups.

---

