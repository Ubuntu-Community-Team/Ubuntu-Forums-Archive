---
title: "Thinking of something new for Ubuntu Linux, cloud like backup to HDD."
date: 2023-08-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Omnios on 2023-08-04
So thinking of something new for Ubuntu Desktop that deals with hard drive storage or rather backing up files on a separate hard drive for important files and photos etc. Generally this would work mostly in the desktop home environment with a right click option to backup the chosen file to a separate hard drive for backup storage and keep still keep a copy in the home environment another option could be to back up to a NAS. Generally this should be quick and easy to use. The hole idea is to be able to use backup storage for important files such as pictures etc. Also could have the option of backing up your back up files for a storage USB stick. One important thing is that this should be easy to use and should be able to be done quickly.

---

### Post by Quarkrad on 2023-08-05
There are many many ways of doing this using various tools. There are GUI tools such as Déjà Dup that you download - perhaps do a google search and see what each does.  On a more personalised level you can write simple scripts to have a more bespoke backup model that can be actioned by a single click on an icon on your Desktop or Panel.  (I action my backups automatically when I power down).  Backing up is simple, or can be complicated, in terms of what you want to do (rarely changing files maybe different to fast changing file like spreadsheets where you might want to back up versioned copies so you can 'go back' if there is an error).  I would suggest you search this forum for Backup and read the many posts on this subject and look at the various tools available.  Then work out your strategy/method of what you would like to do.  At this point there are many people that can help you achieve what you want to do.  Essentially you can do what you are asking - the devil is in the detail of what you specifically want to do.  (E.g.  I do not have my Backup HD mounted/connected to my system when I boot to my Desktop - it is only mounted/connected when I actually perform the Backup).

---

### Post by aljames2 on 2023-08-05
+1 Quarkrad

> **Omnios said:**
> ...Also could have the option of backing up your back up files for a storage USB stick. One important thing is that this should be easy to use and should be able to be done quickly.

I just add that USB sticks "pen drives" are not ideal for backup storage, even a backup of a backup.  They are designed more for portability, like moving that fun file, or files, from computer A to computer B quickly.  I think most of them are natively formatted using the FAT32 file system, which anticipates most users will move them around from machine to machine, between Linux, Windows, Mac, etc.  However, FAT32 does not retain file permissions & ownerships, which is certainly important when backing up system files.  If you operate mostly in the Linux world, you will likely want to consider a file system like ext4 which does handle file attributes, there are others as well.  For backup storage media I prefer internally connected drives, and also use a few USB connected hdds & ssds in enclosures, but not sticks.

Search these forums, read, and have fun.  Start another thread in the the support areas if you get stuck or need help getting started. :)

---

