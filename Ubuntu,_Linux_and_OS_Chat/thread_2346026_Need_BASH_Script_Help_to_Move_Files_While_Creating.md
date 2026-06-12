---
title: "Need BASH Script Help to Move Files While Creating Directories"
date: 2016-12-10
forum: Ubuntu, Linux and OS Chat
---

### Post by jeff140 on 2016-12-10
I've got this script to loop through all folders and move files that are more than 2 years old.  I'm using the install command because it creates the necessary directories on the destination path and then I remove the source.  I'd like to change the script to use the mv command since it is much faster than copying the file then deleting it.  But I don't know how to get the path without the filename to pass to the mkdir -p command?   How should I modify the script?


for d in *; do


find  "$d" -type f -mtime +730 -exec sh -c '


echo "moving $d/{}" &&
 install -Dp "/data/Customer Files$d/{}" "/data/Customer Files Over 2 Years Old$d/{}" &&
 rm -f "/data/Customer Files$d/{}"' \;


done

---

### Post by &amp;KyT$0P# on 2016-12-10
Have you looked into using the [FONT=Courier New]dirname[/FONT] command?

---

