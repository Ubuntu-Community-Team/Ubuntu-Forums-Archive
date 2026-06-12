---
title: "renaming files recursively"
date: 2011-03-26
forum: Server Platforms
---

### Post by speedy18us on 2011-03-26
i'm trying to rename files recursively from a folder. i want to delete the & from every filename. i've searched the net and found the following script:

```
#!/bin/bash

dir=/whatever/directory

for file in `ls $dir` ; do
   # ANYCASE TO UPPERCASE:
   newname=`echo $file | tr '[a-z]' '[A-Z]'`

   mv $dir/$file $dir/$newname
done
```

and changed it:

```
#!/bin/bash

dir=/home/test

for file in `find $dir -type f` ; do

        #rename files containing &
        newname=`echo $file` | tr '[&]' ''

        mv $dir/$file $dir/$newname

done
```

but the for loop explodes the filename after each & sign, so i don't have a whole filename. if the file is named lorem & ipsum, the for loop will break it in 3 parts.

---

### Post by AlphaLexman on 2011-03-26
Change:
> **speedy18us said:**
> newname=`echo $file` | tr '[&]' ''

to:
```
newname=`echo $file | tr '[[COLOR="Red"]=[/COLOR]&[COLOR="red"]=[/COLOR]]' ''`
```
EDIT: Note the backtick location!

---

### Post by rubylaser on 2011-03-26
I'm not sure exactly what you're trying to do because you don't provide any actual examples of filenames and what you'd like the output to look like.  But, you could just use sed in your bash loop to remove the ampersands like so...

```
Admins-MacBook-Pro ~ $ echo "AB & CD.mp4" | sed -e 's/\&//g'
AB  CD.mp4
Admins-MacBook-Pro ~ $ echo "AB & CD & EF.mp3" | sed -e 's/\&//g'
AB  CD  EF.mp3
'
```

The echo line is just an example of a filename.  Obviously, you'd need to incorporate sed into your loop.  But, I think this is what you're trying to accomplish.

---

