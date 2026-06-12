---
title: "Backup &amp; Recovery"
date: 2007-01-08
forum: Windows
---

### Post by adewale on 2007-01-08
is there any program that can be used to backup my computer cause i'd like to repartition my hard disk. Also is there a way to recover some files that got lost as a result of an accidental formatting thanks

---

### Post by seuaniu on 2007-01-08
Certainly lots of choices available for backup.  If you're a desktop user without an entire network to backup, I'd recommend sbackup.  Its a no-brainer to setup, and has a nice set of features, and a nice graphical interface, so you don't have to bother learning bash to backup your files.

Edit:  here's a link:  [sbackup.sourceforge.net]("http://sbackup.sourceforge.net")

---

### Post by adewale on 2007-01-08
sorry i meant for windows cause i think that link is for gnome and i don't have access to linux now. also what do u suggest for recovery? thnx

---

### Post by hal10000 on 2007-01-08
There are billions of backup tools.
If you want to make an image of your partitions I suggest partimage.

A tool to recover lost files (or partitions and many other features) is testdisk.

You can use these tools from the live cd to backup your windows files and partitions too.

---

### Post by adewale on 2007-01-08
thanks but how do i get it

---

### Post by smoker on 2007-01-08
> **adewale said:**
> thanks but how do i get it

partimage is here:[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
though i don't think ntfs partitions are fully supported.

the ultimate boot cd is here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
it has utilities like hdclone, and also active@partition recovery. there are a lot of other apps and full info at the link above,

---

### Post by tagra123 on 2007-01-08
sysrescue cd.

There are some how to's you can print of before getting started.

Suggest defrag windows before using partimage.

If partimage backups without any errors it should restore.

I posted a decent how to 

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

If you print it you should be able to get through. My how-to is for Ubuntu's live cd --mostly the same for sysrescue cd but you wont need the apt-get partimage because its alread included.

sysrescuecd is only about 140mb to download.

---

### Post by adewale on 2007-01-09
thanks i'll let u know how it goes

---

