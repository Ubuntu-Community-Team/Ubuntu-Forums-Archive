---
title: "How to recover lost files after you accidentally wipe your hard drive"
date: 2007-02-11
forum: The Cafe
---

### Post by RAV TUX on 2007-02-11
nice howto article if you need it:

[http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss](http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss)

---

### Post by rowanparker on 2007-02-11
May come in useful sometime.
I didn't know it was so "easy".

Thanks Jozef.

---

### Post by Polygon on 2007-02-11
i read that article when i was actually trying to figure out how to do this, but i didnt use it as it looked to me that it ONLY recovered files of the formats it supported:

> [ ] dbf  DBase 3, prone to false positive
[X]      FAT subdirectory
[X] doc  Microsoft Office Document (doc/xls/ppt/vis/...)
[X] dsc  Nikon dsc
[X] eps  Encapsulated PostScript
[ ] exe  MS executable
[X]      EXT2/EXT3 Superblock
[X] gif  Graphic Interchange Format
[X] gz   gzip compressed data
[X] jpg  JPG picture
[X] mdb  Access Data Base
[X] mov  MOV video
[X] mp3  MP3 audio (MPEG ADTS, layer III, v1)
[X] mpg  Moving Picture Experts Group video
[X] mrw  Minolta Raw picture

---

### Post by sk8dork on 2007-02-21
it should be noted that all of the files in the list, [X]'d or not, are supported. the guy posted the list to show what he selected versus what was available. so this utility won't be very useful for completely recovering all data on a drive, but most people consider the images, videos, or install files (exe's in the case of windows) to be most important. i know there are other important file types, but this is handy for free software. i did a bit of research when i had to recover some stuff from a formatted drive and i found that there wasn't anything available for free that would do the job. what i ended up using was restorer2000.

---

### Post by az on 2007-02-21
I submitted this for the next version of the Official Ubuntu BOok:

How do I recover deleted files or lost files from a corrupt filesystem?

Foremost is a command-line tool which can recover files from a number of filesystems, including fat, ext3 and NTFS.  It can be installed and run from the live cd.

Enable the universe repository and install foremost:

sudo apt-get install foremost

Assuming the lost files are on a USB drive (sda), you need to create a writeable directory on another drive where you can put the recovered files

sudo mount /dev/sdb1 /recovery
sudo mkdir /recovery/foremost

And then run foremost:
sudo foremost -i /dev/sda -o /recovery/foremost

The recovered files will then be owned by root.  Change their ownership so that you can use them:
sudo chown -R youruser:youruser /recovery/foremost




You can see the manpage ([http://foremost.sourceforge.net/foremost.html](http://foremost.sourceforge.net/foremost.html)) for what file types it can retrieve.

---

