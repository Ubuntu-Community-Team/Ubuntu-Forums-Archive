---
title: "Automatic Tarballing of folder content"
date: 2008-07-20
forum: Server Platforms
---

### Post by sadara on 2008-07-20
Hi all,
First post on Ubuntu forums, so be gentle. :P

Problem:
I need to create a folder, shared by Samba/NFS, that users can drop huge directories of files into, to be automatically tarballed. An by huge I mean between 10Meg and 10 Terrabytes, with 1 to 10 Million files. The file are mostly TGA (Targa images, a graphic format like BMP that compresses well)
I would prefer to use LZMA compression.

My Solution:
1)Run a cron job every 24 hours that scans the directory for new folders (or use incron (inotify cron))
2)Move the new folders to a tmp directory
3)compresses folder for archiveing (nice=19)
4)email user job is done

My problems
A) What if someone drops 1000 folders into directory, and spawns 1000 compression jobs? (LZMA is not very memory friendly when compressing)
B) copying 10TB of data takes more than 24hours, what happens if the copy isn't complete when the cron job starts

I think I can figure out the first problem (suggestions are welcome), it's the second that has me beat. 10TB takes about 3 weeks to compress, and I can't just run the cron job every three weeks. I need a way of checking that the file transfer has finished. Should I just repeatedly run du every 30 mins on the folder until the du results come back the same? There has to be a better way than that.

Thanks in advance for the help :P

---

### Post by scorp123 on 2008-07-23
With so many files and files *that* large you'd be better off to use a dedicated storage solution.

[IMG]http://www.sun.com/images/k3/k3_sunfire-x4540_5.jpg[/IMG]

We use above thingies (Sun Fire X4540 Storage servers) here and they work superb.

As for background compression so that the files eat less disk space ... There is a plugin for the FUSE system that compresses stuff on the fly. Maybe you could use this instead of archive files that are triggered via "cron"? The advantage would be that the files are compresses but also available "on the fly" to users, e.g. without the need to first download a possibly huge archive and then having to extract it ... "compfused" (that's the name of this plugin) would do all this on the fly.

The homepage is here:
[http://www.biggerbytes.be/](http://www.biggerbytes.be/)

> Here the main features for compFUSEd:

    * transparent read and write access to compressed data
    * modular architecture
    * support for multiple compression algorithms
    * no need to reformat
    * can be used part of filesystem as well as complete filesystem 

---

### Post by sadara on 2008-07-24
Sorry, should have mentioned in my first post that the tarballs are for archiving in storage.
btw, incron is a cron system that monitors filesystem changes, and acts on them

---

