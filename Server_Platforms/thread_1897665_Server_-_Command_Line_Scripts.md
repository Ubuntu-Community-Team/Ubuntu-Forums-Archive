---
title: "Server - Command Line Scripts"
date: 2011-12-19
forum: Server Platforms
---

### Post by sibleytr on 2011-12-19
I am in the process of converting for Windows to Ubuntu (Linux). Part that conversion includes converting those ever handy little scripts from Windows to the Ubuntu Command Terminal.
Does anyone have some good reference material for creating command line scripts (bash files)?

In Windows I have a backup script that did the following
1 - Create a file containing all of a directory's subfolders
dir /b /o:n C:\me > fldrLst.ini
2 - Read the list from the files and zip the individual folders
For /f %%a in (fldrLst.ini) do (zip -r c:\bkup\%%a.zip c:\me\%%a)

---

### Post by samosamo on 2011-12-19
> **sibleytr said:**
> I am in the process of converting for Windows to Ubuntu (Linux). Part that conversion includes converting those ever handy little scripts from Windows to the Ubuntu Command Terminal.
Does anyone have some good reference material for creating command line scripts (bash files)?

In Windows I have a backup script that did the following
1 - Create a file containing all of a directory's subfolders
dir /b /o:n C:\me > fldrLst.ini
2 - Read the list from the files and zip the individual folders
For /f %%a in (fldrLst.ini) do (zip -r c:\bkup\%%a.zip c:\me\%%a)

google "bash for loops" it will look something like this:

```
for x in $(find /path); do
  zip $x
done
```

another way:

```
find /path | while read x; do
  zip "$x"
done
```

You gave me one simple concept, I gave you two simple methods, the rest is up to you! Good luck

---

### Post by sisco311 on 2011-12-19
Check out the links in my signature and stay away from other on-line bash/shell guides. Most of them are relatively poor and they will teach you how to write bugs, not scripts.

```
shopt -s nullglob

for file in ./*
do
    if [ -d "$file" ]
    then
        zip **whatever the syntax of zip is ;)**
    fi
done


```


If you want to save the directory names in a file, you will have to separate the file names with a NUL character:
```
find ./ -mindepth 1 -maxdepth 2 -type d -print0 > dirs

while IFS= read -r -d '' file
do
    zip **whatever**
done < dirs

```

See: BashFAQ 001 and 020
 
> **samosamo said:**
> google "bash for loops" it will look something like this:

```
for x in $(find /path); do
  zip $x
done
```

another way:

```
find /path | while read x; do
  zip "$x"
done
```

You gave me one simple concept, I gave you two simple methods, the rest is up to you! Good luck

Check out BashPitfalls 001. ;)

---

### Post by sibleytr on 2011-12-20
Thank you very much - this will definitely help to get me started.

---

