---
title: "Is this right? 4.4 GB folder compressed to 898 MB?"
date: 2012-09-07
forum: Server Platforms
---

### Post by X1R1 on 2012-09-07
I am trying to make a backup of a folder which size is 4.4GB, this folder also contains subfolders that I need to backup, so I just figured I could tar the entire folder like this:

```
tar cvzf backup.tar.gz foldertobackup
```

Which yields a 898 MB file.

Can the compressing really be that good? I suspect something isn't being backed up here, how can I find out? 

thanks for the help!

---

### Post by darkod on 2012-09-07
I guess it depends on the format of files compressed. How about untarring it to another location and comparing them?

Also opening the .tar file with Archive Manager will show you the content. Right-click, open with archive manager.

PS. When I said right-click I forgot for a moment this is in the server section so you probably don't have a GUI. :)

---

### Post by bob-linux-user on 2012-09-07
The amount of compression you can get depends on a number of things amongst which is the file type you are compressing:
Jpg and pdf will usuallly hardly compress at all. Things like bitmaps and older word documents will compress considerably. Uncompress your compressed folder and do a file count is a quick and easy way to check.

Dirdiff will help you compare files and folder for a more thorough check. Data loss through compression and recompression would be most surprising.

---

### Post by jerome1232 on 2012-09-07
Do you have symlinks inside that folder? Tar doesn't follow them by default, it just copies them as symlinks. As others said compression will vary widely with what you are compressing.

---

### Post by X1R1 on 2012-09-07
Ok I copied the file to a different server via scp, and untarred, then did a:

```
du -hs uncompressedfolder
```

result: 4.4G

As I was still skeptic I did a du and counted the files:

```
du -h uncompressedfolder | wc -l
```

result: 8321

Did the same command on the original folder, and...result: 8321

amazing :D

---

### Post by SeijiSensei on 2012-09-07
Text files will often achieve 4:1 compression or better.  It also depends on how much variability the files have.  Many compression algorithms will replace a string of identical characters with a just one placeholder and a counter.  If the files have lots of spaces, they are very compressible.

Most things like graphics and video are already compressed and will show little improvement.  The highest levels of compression can be achieved by using the bzip2 algorithm, represented in tar with the "j" switch (don't ask me why it is "j"; maybe they were just running out of letters):

```
tar cjpvf mydirectory.tar.bz2 mydirectory
```

Basically you just use "j" instead of "z" to get bzip2 instead of gzip.  By the way, for archiving purposes, you should include the "p" switch to "preserve" all the permissions.  See "[man tar]("http://linux.die.net/man/1/tar")" for details.

---

### Post by X1R1 on 2012-09-07
@SeijiSensei

thanks for that informative post!

Indeed they are a lot of text files and there is also a PostgreSQL database in there, but I have no idea what the format for that is.

I have used bzip2 in the past, but find it that it takes a lot longer to decompress the data (of course, with better compression, longer decompression).

And thanks for that "p" switch, It looks really useful!

cheers

---

### Post by SeijiSensei on 2012-09-07
If you are compressing PG backups from pg_dump, then they will be very compressible.  They have a lot of spaces, tabs, etc.  If you're compressing /var/lib/pgsql, my guess is that it will much less so.

---

### Post by vexorian on 2012-09-07
A possibility is that maybe some binary files were full of 0 bytes. I have reached this kind of ratio when compressing ISO images that were actually full of zeros at the end. Usually files with such repetitions of a single byte like 0 or spaces are *very* compressible.

---

### Post by Stonecold1995 on 2012-09-07
Compression ratio depends heavily on how "random" the data to be compressed is.  Data that is very random, with a lot of "entropy" makes it hard for compression utilities to find patterns, whereas data that is the opposite is easier to compress.  Here's a small script I made to test how well different compression algorithms work on random data and zeros, but it'll probably serve to show how tremendous the variation in compression ratio is:
```
#!/bin/bash

prog=gzip

cd /tmp

echo -n "Size of random data before compression with $prog: "
(dd if=/dev/urandom of=randombytes &) &>/dev/null
sleep 1
killall -wq dd
ls -lh randombytes | awk {'print $5'}
echo -n "Size after compression: "
$prog randombytes
ls -lh randombytes.* | awk {'print $5'}
rm randombytes.*

echo -en "\nSize of zeros before compression with $prog: "
(dd if=/dev/zero of=zeros &) &>/dev/null
sleep 1
killall -wq dd
ls -lh zeros | awk {'print $5'}
echo -n "Size after compression: "
$prog zeros
ls -lh zeros.* | awk {'print $5'}
rm zeros.*

exit 0
```

Just an interesting fact I found out with this script, bzip2 compresses completely repetitive files thousands of times better than gzip does, but bzip2 creates a *bigger* size to random data then gzip does.

---

