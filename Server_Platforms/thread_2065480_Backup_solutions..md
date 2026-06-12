---
title: "Backup solutions."
date: 2012-10-02
forum: Server Platforms
---

### Post by marjoh05 on 2012-10-02
Im using 12.04 ubuntu.

I want a simple backup for my server.

I want a differential backup of my disk to an external hdd.

Anyone got any tip? :)

Regards!

---

### Post by Drenriza on 2012-10-02
You could make a simple cron job with rsync to take a backup of specific file paths. And place them in a folder you create on the hdd example Okt -> 02Okt2012

That is probably how i would do it for a fast and efficient solution.

---

### Post by hasan.akgoz on 2012-10-02
using clonzilla server is perfect backup.

---

### Post by marjoh05 on 2012-10-02
Thank you.

I use Clonezilla. Clonezilla require that you boot from CD and you need to do it manually.)
Any way i can get this to work automatically?

Does Rsync work differential?
the backup is is at about 1TB, if i take a new copy every time. You get the idea hehe :)

---

### Post by Drenriza on 2012-10-02
> **marjoh05 said:**
> Thank you.

I use Clonezilla. Clonezilla require that you boot from CD and you need to do it manually.)
Any way i can get this to work automatically?

Does Rsync work differential?
the backup is is at about 1TB, if i take a new copy every time. You get the idea hehe :)

You can custom the rsync command to only take the changes.

---

### Post by hasan.akgoz on 2012-10-02
Can you review link ? [http://www.clonezilla.org/related-articles/008_Batch_mode_Clonezilla_on_hard_drive/file/HOWTO-clonezilla-live-hard-drive.htm](http://www.clonezilla.org/related-articles/008_Batch_mode_Clonezilla_on_hard_drive/file/HOWTO-clonezilla-live-hard-drive.htm) ;)

---

### Post by marjoh05 on 2012-10-02
Thank you again all :)

I will check out Rsync first, easier to plug in an external hdd than buildan an image server for the image server ;) (Yes, this server is an image server, hehe)

---

### Post by kgatan on 2012-10-02
You can also checkout rsnapshot. Its based on rsync but also handles incremental archiving.

Very easy to use.

---

### Post by LHammonds on 2012-10-02
I use rsync to copy data files to a backup partition.  I then compress them into an archive and store off the server as snapshots of the data.

I also have all partitions inside LVM (except /boot) and have a bit of unused space in the volume.  I use this extra space to create LVM snapshots and use FSArchiver to create archives of the system (including /boot) while it is running.  My backup system is 100% automated and I can restore individual files from various archives back in time or I can completely restore to a new server using the FSArchiver backups (which restores the entire partition).

I have all this documented (and my scripts) in my signature below (look at the Ubuntu Server link)

LHammonds

---

### Post by usalug on 2012-10-03
> **marjoh05 said:**
> Im using 12.04 ubuntu.

I want a simple backup for my server.

I want a differential backup of my disk to an external hdd.

Anyone got any tip? :)

Regards!

There are many ways to backup stuff on your linux box :)  So many that there is even a book about it (768 pages worth)
[http://shop.oreilly.com/product/9780596102463.do](http://shop.oreilly.com/product/9780596102463.do)  It's a pretty in depth book, but it covers almost all the methods. Personally, I too like rsync the best for what I do.

---

### Post by Akita on 2012-10-03
Take a look at rsnapshot is the repos. It uses rsync and implements most of the "dirty rsync tricks" the books will tell you to use ;)

---

### Post by mjjones on 2012-12-07
If you're looking for cloud backup check out ElephantDrive - just released the linux installer. 

[http://home.elephantdrive.com/linux/](http://home.elephantdrive.com/linux/)

Matt

---

### Post by sandyd on 2012-12-07
If you want incremental backups, checkout rdiff-backup

---

