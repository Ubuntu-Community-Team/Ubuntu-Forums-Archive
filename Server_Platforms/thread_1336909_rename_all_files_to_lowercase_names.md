---
title: "rename all files to lowercase names?"
date: 2009-11-25
forum: Server Platforms
---

### Post by Vegan on 2009-11-25
any easy way to rename all files to lowercase names?

---

### Post by KiLaHuRtZ on 2009-11-25
First, 'cd' into the directory with your files you want to change.  Then, run this...

```
ls | while read upName; do loName=`echo "${upName}" | tr '[:upper:]' '[:lower:]'`; mv "$upName" "$loName"; done
```

---

### Post by jacobs444 on 2009-11-25
or install thunar and use bulk rename, for the gui way to do it. You will have to use menu editor to see bulk rename under accesories.

---

### Post by Vegan on 2009-11-25
> **KiLaHuRtZ said:**
> First, 'cd' into the directory with your files you want to change.  Then, run this...

```
ls | while read upName; do loName=`echo "${upName}" | tr '[:upper:]' '[:lower:]'`; mv "$upName" "$loName"; done
```

Thanks, that did the trick for me.

For some reason files I restored from DVD using Roxio 2009 were renamed as all caps.

---

### Post by chocobanana on 2009-11-27
>  Originally Posted by KiLaHuRtZ  View Post
First, 'cd' into the directory with your files you want to change. Then, run this...

Code:

ls | while read upName; do loName=`echo "${upName}" | tr '[:upper:]' '[:lower:]'`; mv "$upName" "$loName"; done



Worked great for me too :D

Thanks!

---

### Post by natuk on 2011-01-18
And also if you replace

```
ls
```

from the above command with 

```
find ./*
```

it will happen recursively, although it will complain for non-capital names.

---

### Post by sisco311 on 2011-01-18
File names in Linux can contain any characters other than a slash (/) and the null character. So, I wouldn't use **ls | while read** or **for file in `ls`**. The first one fails if the file name contains a new line; the second one fails with files with spaces in their name too.

The proper way to write the script is:
```
#!/usr/bin/env bash

cd pat/to/dir
for file in *; do
  if [[ "$file" != "${file,,}" ]]; then
    mv -b -- "$file" "${file,,}"
  fi
done
```

Renaming the directories and files recursively is a little bit trickier:
```

while IFS= read -r -d '' file; do
  mv -b -- "$file" "${file,,}"
done < <(find path/to/dir -depth -name '*[A-Z]*' -print0)
```

---

### Post by mackiecc on 2012-05-17
The easiest way is imho (example from man rename):

```
rename 'y/A-Z/a-z/' *
```If you run it with the option '-n' it doesn't actually rename the files, but show you what it would have done.

---

### Post by LHammonds on 2012-05-17
haha...I got a laugh out of this thread.

KiLaHuRtZ - Knows enough to be dangerous
sisco311 - A programmer who likes writing his own functions
mackiecc - A business analyst who does not like re-inventing the wheel

I like mackiecc's solution. :guitar:

---

### Post by Elfy on 2012-05-17
Old thread closed.

---

