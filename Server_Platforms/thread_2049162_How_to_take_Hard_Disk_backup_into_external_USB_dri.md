---
title: "How to take Hard Disk backup into external USB drive ?"
date: 2012-08-28
forum: Server Platforms
---

### Post by honey_bee on 2012-08-28
hi,
     I am using squid server on my Ubuntu box. I want to take full backup of my hard disk (All partitions & Data) into the externel usb drive.The reason is in case of crash of data I just roolback my ubuntu with its partitions and data.
 
Is there any builtin command in linux ?
 
Thanks,
honey

---

### Post by darkod on 2012-08-28
You can use fsarchiver for example. It's in the repositories so you can install it with apt-get.

For more details about the program you can see here:
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by coldraven on 2012-08-28
I have not used it for quite a while but Clonezilla might be worth a look.
[http://clonezilla.org/](http://clonezilla.org/)

You  boot Clonezilla up from CD or USB and clone your drive to an image.
Remember that an external USB drive is normally formatted FAT32 and you cannot create files bigger than 4GB. 
You may need to reformat it to NTFS  or EXT4.

---

### Post by Moif_Murphy on 2012-08-28
There's a Help page which describes your options here:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

:)

---

### Post by darkod on 2012-08-28
I forgot to mention that fsarchiver backs up unmounted partitions. Clonezilla is similar since to boot with the clonezilla cd you need to power off the system. So, if downtime of the server is a problem, you will need to look for different solution like maybe rsync, etc.

---

### Post by honey_bee on 2012-08-28
thanks for the replies. Well what do say about dd command ? Some one told me  that with dd command i can take backup ! is it correct ?

---

### Post by darkod on 2012-08-28
> **honey_bee said:**
> thanks for the replies. Well what do say about dd command ? Some one told me  that with dd command i can take backup ! is it correct ?

Yes, but you have to be very careful with it, and what i don't like about dd is that it copies all sectors, even empty ones. So your backup will take longer and take much more space. dd will copy the whole partition including the empty space.

---

### Post by honey_bee on 2012-08-28
thanks for the reply. Well can you write the the complete command of "dd"by which i may take backup. 

[FONT=Verdana][SIZE=1][SIZE=2]dd if=/dev/hdx of=/dev/hdy

and if i use "[/SIZE][/SIZE][/FONT]rsync" command with dd command then it will be the affect ?

thanks,
honey

---

