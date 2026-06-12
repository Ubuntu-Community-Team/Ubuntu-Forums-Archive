---
title: "M3u Playlist Creator Scripts"
date: 2010-02-20
forum: Ubuntu Studio
---

### Post by Jose Catre-Vandis on 2010-02-20
Needed to find a way to make a playlist for mp3s for either:

a) a single directory
b) a set of nested directories (to include all sub folders)

**a) a single directory**

This was fairly straightforward:

```
#!/bin/bash
ls -d * | grep .mp3 > "${PWD##*/}.m3u"
```
This names the playlist with the name of the directory, and the file is placed inside the directory itself. The script has to be run from inside the directory.

**b) a set of nested directories (to include all sub folders)**
```
#!/bin/bash
touch ${PWD##*/}.m3u
export IFS=$'\n'
for i in $(find $1 -name "*.mp3" -type f)
do 
echo "$i" |sed 's/..\(.*\)/\1/' >> ${PWD##*/}.m3u
done

shuf ${PWD##*/}.m3u > ${PWD##*/}2.m3u
shuf ${PWD##*/}2.m3u > ${PWD##*/}.m3u
rm ${PWD##*/}2.m3u
```
This works from inside the top directory of the set of nested directories.Again it takes its name from the top line directory, and also shuffles the listing. Removing the last three lines removes the shuffle.

Note: both scripts are targeted at mp3 files only

Both of these scripts work fine as Thunar custom actions, but it would be good to find a single script that handled both scenarios above, from a right click on the chosen directory.

---

### Post by TyLLy_4 on 2010-07-09
don't get me wrong .. i really appreciate the script. :( but when i attempt to make a playlist it will make 4 files. 


so for example i right click in a dir called "a day to remember" (i put it in my nautilus scripts dir" it will make a bunch of files.

- a day to remember.m3u (empty)
-a (empty)
-day (rmpty)
-to (empty)
-remember (actual playlist) 


:( ... i tried to fix it but i quickly realized that i dont know jack about regular expressions and after breaking it for the third time I gave up. If i find a fix i will post here. THANKS

---

### Post by Jose Catre-Vandis on 2010-07-09
Quickest solution is to get rid of the spaces in your directory, or to replace them with underscores

---

### Post by TyLLy_4 on 2010-07-10
Thanks. Hadn't thought of that!

---

### Post by lutherhex on 2011-01-17
Rather than renaming directories and files that have spaces, just put quotes around the PWD command string. They are there on the single directory script, but missing from the subdirectory with shuffle script.

Version that works with spaces:
```
 
#!/bin/bash
touch "${PWD##*/}.m3u"
export IFS=$'\n'
for i in $(find $1 -name "*.mp3" -type f)
do 
echo "$i" |sed 's/..\(.*\)/\1/' >> "${PWD##*/}.m3u"
done

shuf "${PWD##*/}.m3u" > "${PWD##*/}2.m3u"
shuf "${PWD##*/}2.m3u" > "${PWD##*/}.m3u"
rm "${PWD##*/}2.m3u"

```

---

### Post by mexicanseaf00d on 2011-03-08
Very interesting!

How would one put the first script into a Nautilus Action? I cant figure out how to give the current nautilus path to the script. The parameters like %d or %m in ```
nautilus-actions-config
``` do nothing (it creates an empty %USER.m3u in my homedir)

---

### Post by Jose Catre-Vandis on 2011-03-13
Not sure as only use Thunar :(

However for my Thunar Custom Action I just use:

```
playlistmaker.sh
```

and only set to find mp3 files

---

