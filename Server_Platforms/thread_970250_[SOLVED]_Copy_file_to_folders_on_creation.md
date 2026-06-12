---
title: "[SOLVED] Copy file to folders on creation"
date: 2008-11-04
forum: Server Platforms
---

### Post by baudday on 2008-11-04
Hi,

I have a main directory containing several directories with images in each. I also have an index.php file that automatically generates thumbnails for the images in each folder. I would like to know if there's a way that I can have it automatically copied into new directories inside the main directory. So say someone uploads an images directory into the main directory. I want it to automatically copy or create the index.php file inside the new directory. And chmod everything to 777.

---

### Post by baudday on 2008-11-05
Well I wrote one myself, I'm taking a Unix class right now :) and here's what I got.

```
#!/bin/sh
#Script Name: index.sh
#Author Name: Willem Ellis
#Date: Tues Nov 4 17:22:00 CST 2008
#Description: This is a file used to insert
# index.php into newly created
# sub-directories within a main
# directory.
cd /var/www/Pictures/
FILES=*
for f in $FILES
do
if [ -d "$f" ]
then
echo “Processing $f…”
chmod 777 “$f”
cd “$f”
pwd
cat “../noindex.php” > index.php
cd ..
elif [ ! -d "$f" ]
then
echo “Not a directory…”
fi
done
```

It runs through the directory, and if it finds a directory, it changes into it and creates index.php from a copy of noindex.php that's in the main directory.

---

### Post by Idefix82 on 2008-11-05
Alternatively use the find command:
```
find /var/www/Pictures/ -type d -execdir cat “../noindex.php” > index.php\;
```

Note: I haven't tested it so run at your own risk.

---

### Post by baudday on 2008-11-05
haha where were you when I started this thread. I will stick to what I have, because I understand it all, and haven't learned about the find command yet.

---

### Post by Idefix82 on 2008-11-05
I was probably doing what I should be doing right now as well: working :)
You can just create a folder with a couple of subfolders and run the command there to see what it does. Also, have a look at
```
man find
```

---

