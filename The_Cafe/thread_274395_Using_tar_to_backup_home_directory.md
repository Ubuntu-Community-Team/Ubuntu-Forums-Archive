---
title: "Using tar to backup home directory"
date: 2006-10-09
forum: The Cafe
---

### Post by raublekick on 2006-10-09
sorry, i wasn't sure exactly where to post this, so mods feel free to move it where appropriate.

i want to use tar to backup my home directory, but i have a little discrepancy i want to solve before i actually test it out. here is the command:

tar -cvzf ~/backup.tar.gz ~/

that will make the file backup.tar in my home directory, and uses my home directory as the backup source. will this work with no problems? i can't shake the feeling that it wouldn't work because the .tar.gz file is being created in the directory that is being tar'd.

---

### Post by Demio on 2006-10-09
Well, try it and you'll find out. :P

Make a directory with a couple of files and try to tar it from within.

I'm almost sure it will work, but you can't be sure until your try it ;)

---

### Post by raublekick on 2006-10-09
derr... good suggestion on trying it out. i even tested tar out earlier to see if it would get hidden .whatever folder and keep their hiddenness by default. why did i not think of this??

well here goes!

<edit> well i tried it out, the last two lines of output were this:
/home/andrew/testing/testing.tar.gz
tar: /home/andrew/testing/testing.tar.gz: file changed as we read it

and when i tried to open it with ark, it just crashed right away. i guess i have to create it somewhere else and then copy it back to my home directory.

---

### Post by ComplexNumber on 2006-10-09
use rsync instead.

---

### Post by IYY on 2006-10-09
Or something like this:

tar -cvzf /tmp/backup.tar.gz ~/ && mv /tmp/backup.tar.gz ~

---

### Post by raublekick on 2006-10-09
> **ComplexNumber said:**
> use rsync instead.

eh? can rsync make tar.gz archives? what i want to do has nothing to do with networks either.


but i also just realized that tar has a --exclude=PATTERN flag, so i can probably just exclude the archive i am making

tar -cvzf testing.tar.gz --exclude=testing.tar.gz /home/andrew/testing                      
did the trick

---

### Post by raublekick on 2006-10-09
things i just learned:

1. if i'm going to backup my home directory, i should throw my ripped CDs onto my external hard drive where they belong

2. in the script i am making, i should be sure to exclude all files beginning with "backup" and ending in ".tar.gz"

3. i should also exclude all files ending in ".iso"

---

### Post by matthew on 2006-10-10
Here's a sample of what I do.

```
tar cvpzf /home/matt/backup-matt/20061010home.tgz --exclude=/home/matt/music --exclude=/home/matt/.Trash --exclude=/home/matt/backup-matt --exclude=/home/matt/.thumbnails --exclude=/home/matt/vmware  /home/matt
```The backs up my /home into /home/matt/backup-matt as 20061010home.tgz and excludes my mp3's, thumbnails cached on the drive, and my very large /vmware folder with different distros I'm playing with.

To exclude a specific type of file in a specific directory use --exclude=/directoryname/*.file-extension

Play with it a while and you'll get the idea.

---

### Post by drucer on 2006-10-10
Yeah, look at Matt's example! It is ESSENTIAL to notice that Matt uses "p" command line parameter with tar command (p=permissions).

This ensures that the files will have the right permissions when you extract the tar archive.

"tar" comes from "tape archive" - so it's been used to make backups of Unix systems for many, many years. I myself took full backup of my Linux system with tar and when I tested it (extracted the tar archive to a new hard drive) everything worked. However, full system backup with tar was made when I had rebooted the computer with Live CD so the system was not in use when I created the tar backup of it.

---

### Post by raublekick on 2006-10-10
> **matthew said:**
> Here's a sample of what I do.

```
tar cvpzf /home/matt/backup-matt/20061010home.tgz --exclude=/home/matt/music --exclude=/home/matt/.Trash --exclude=/home/matt/backup-matt --exclude=/home/matt/.thumbnails --exclude=/home/matt/vmware  /home/matt
```The backs up my /home into /home/matt/backup-matt as 20061010home.tgz and excludes my mp3's, thumbnails cached on the drive, and my very large /vmware folder with different distros I'm playing with.

To exclude a specific type of file in a specific directory use --exclude=/directoryname/*.file-extension

Play with it a while and you'll get the idea.

excellent, thanks for the suggestions! does --exclude=  accept regular expressions?  i see * used a lot, but never anything else.

---

### Post by matthew on 2006-10-10
> **raublekick said:**
> excellent, thanks for the suggestions! does --exclude=  accept regular expressions?  i see * used a lot, but never anything else.I have to confess I don't know. I've never tried any others, but it seems reasonable to me that they should work. I suppose you could create a small folder with a few things in it and test it.

---

### Post by raublekick on 2006-10-10
yeah i'll test it tonight when i get home, i'm not home now so i can't test it. 

however, my need for regular expressions is alleviated by your method of putting backup files and ISOs into directories hehe

---

### Post by blanks on 2006-10-19
tar supports some limited pattern matching, but not full blown regexps.  See the 'Wildcards Patterns and Matching' setcion of the tar info pages.

Of course you could also pipe grep output to tar...

---

