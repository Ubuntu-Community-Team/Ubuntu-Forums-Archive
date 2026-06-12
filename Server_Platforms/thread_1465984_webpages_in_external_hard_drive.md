---
title: "webpages in external hard drive"
date: 2010-04-29
forum: Server Platforms
---

### Post by blakep2 on 2010-04-29
I am trying to use my external hard drive to store webpages and on the webpages it is uploaded to the folder. When i navigate to the address it says it is forbidden. On another note I also noticed that it would not let me upload files from the browser in a page located on the actual disk it says i do not have permission. Can someone help me get passed the barriers. The hard drive is ntfs.

---

### Post by Kellemora on 2010-05-01
Hi Blake

I'm a TOTAL NOOB, but, I think I'm already doing what you are trying to do!

I have an external hard drive that I use as a file server, or more actually data storage, instead of on the computers themselves.

One of these file folder directories are my web page stuff, which includes some php and javascript lessons I'm working on.

FWIW:  I've also had this problem with RSYNC trying to do backups and the workaround works for it too......

Step ONE is to MOUNT your external harddrive, it will appear on your desktop.

Open your web folder and jot down the PATH it will probably be something like /home/user/desktop/externaldrive/webfolder/

Step TWO open a terminal, open gedit and work your way back to the root /var/www directory.
Once here you can type 
sudo ln -s /home/user/desktop/externaldrive/webfolder/
then hit enter.
This will create a symlink from /var/www TO the folder on your desktop which is your MOUNTED external hard drive.

If you reboot, you will have to MOUNT the external hard drive again, unless you have it set to automount at bootup.

Hope this helps!

TTUL
Gary

---

### Post by blakep2 on 2010-05-01
> **Kellemora said:**
> Hi Blake

I'm a TOTAL NOOB, but, I think I'm already doing what you are trying to do!

I have an external hard drive that I use as a file server, or more actually data storage, instead of on the computers themselves.

One of these file folder directories are my web page stuff, which includes some php and javascript lessons I'm working on.

FWIW:  I've also had this problem with RSYNC trying to do backups and the workaround works for it too......

Step ONE is to MOUNT your external harddrive, it will appear on your desktop.

Open your web folder and jot down the PATH it will probably be something like /home/user/desktop/externaldrive/webfolder/

Step TWO open a terminal, open gedit and work your way back to the root /var/www directory.
Once here you can type 
sudo ln -s /home/user/desktop/externaldrive/webfolder/
then hit enter.
This will create a symlink from /var/www TO the folder on your desktop which is your MOUNTED external hard drive.

If you reboot, you will have to MOUNT the external hard drive again, unless you have it set to automount at bootup.

Hope this helps!

TTUL
Gary
the hard drive dosent appear in the desktop folder.  But it does show up on the actual desktop

---

### Post by tgalati4 on 2010-05-01
I'm not sure how ntfs drives handle file and directory ownership, but apache is looking for www-data:www-data ownership for files and directories to be served.

---

### Post by blakep2 on 2010-05-01
> **tgalati4 said:**
> I'm not sure how ntfs drives handle file and directory ownership, but apache is looking for www-data:www-data ownership for files and directories to be served.
can you tell me how to change the ownership.

---

### Post by tgalati4 on 2010-05-02
sudo chown -R www-data:www-data /var/www/yourwebpage

---

### Post by blakep2 on 2010-05-02
> **tgalati4 said:**
> sudo chown -R www-data:www-data /var/www/yourwebpage
What returned:

blake@petermanserver:~$ sudo chown -R www-data:www-data /media/SEA_DISC/ourgraphchown: changing ownership of `/media/SEA_DISC/ourgraph/index.html~': Operation not permitted
chown: changing ownership of `/media/SEA_DISC/ourgraph/index.html': Operation not permitted
chown: changing ownership of `/media/SEA_DISC/ourgraph/test/test.html~': Operation not permitted
chown: changing ownership of `/media/SEA_DISC/ourgraph/test/test.html': Operation not permitted
chown: changing ownership of `/media/SEA_DISC/ourgraph/test': Operation not permitted
chown: changing ownership of `/media/SEA_DISC/ourgraph': Operation not permitted
blake@petermanserver:~$

---

### Post by tgalati4 on 2010-05-02
Like I said, I'm not sure if ntfs drives can handle linux-style ownership.  I don't use Windows, so I really don't remember.

It could also be that the ntfs drive has errors and mounted as read-only.

What is the output of:

sudo fsck /dev/sde1  (or whatever your /media/SEA_DISC is attached to)

---

### Post by blakep2 on 2010-05-03
> **tgalati4 said:**
> Like I said, I'm not sure if ntfs drives can handle linux-style ownership.  I don't use Windows, so I really don't remember.

It could also be that the ntfs drive has errors and mounted as read-only.

What is the output of:

sudo fsck /dev/sde1  (or whatever your /media/SEA_DISC is attached to)
root@petermanserver:~# sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sdb1: 4521 files, 460934/4853706 clusters
root@petermanserver:~#

---

### Post by tgalati4 on 2010-05-04
Are you sure the drive is NTFS?  fsck seems to think it's FAT32.  I don't think FAT32 can handle ownership designation (everything is ROOT) and therefore you might have issues trying to serve pages with user www-data and ROOT ownership.  Again, I don't know squat about how windows works.

---

### Post by blakep2 on 2010-05-04
> **tgalati4 said:**
> Are you sure the drive is NTFS?  fsck seems to think it's FAT32.  I don't think FAT32 can handle ownership designation (everything is ROOT) and therefore you might have issues trying to serve pages with user www-data and ROOT ownership.  Again, I don't know squat about how windows works.
i guess i tis fat32 sorry for the confusion,  is there anyway i can just use it for storing uploaded files or writing files.  I need to be able to recall these same files from the internet.

---

### Post by tgalati4 on 2010-05-04
Try:

sudo chmod -R 755 /media/yourexternalmediadisk

---

### Post by blakep2 on 2010-05-05
im sorry i dont think I was clear use the disc for uploading files from a web browser.

---

