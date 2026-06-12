---
title: "Alias to clean up old .txt~ files"
date: 2009-08-01
forum: The Cafe
---

### Post by Buce on 2009-08-01
Dunno if this is an old trick or not, but I just now discovered it playing around with BASH and thought I'd share.

If you're like me, you've got tons of backup files ending in .txt~ from back in the days when you used gedit. You've since moved on to a real editor like vim, but those old .txt~ files are still all over your home directory, hidden in subfolders of subfolders you've long since forgotten. Sure, every once in a while you'll happen to ls a few rogue .txt~ files, and stamp em out with a quick rm *~, but who knows how many there are left.

The following two commands will quickly let you see and remove every single *.txt~ file that resides in whatever directory (and all its subdirectories) you happen to be in.

```
ls `find . | egrep '\.txt~$'` #shows files to be deleted
rm `find . | egrep '\.txt~$'` #deletes the files
```

Essentially, this is equivalent to a recursive ls *.txt~ followed by a recursive rm *.txt~. If, instead,  you want to do a recursive ls *~; rm *~, then you would use the following:

```
ls `find . | egrep '~$'`
rm `find . | egrep '~$'`
```

And if you want to be able to use these on a regular basis, you can add aliases to your .bashrc:

```
alias garbage="ls `find . | egrep '~$'`"
alias cleanup="rm `find . | egrep '~$'`"
```

---

### Post by v8YKxgHe on 2009-08-01
You only need to use 1 command to do this, which is 'find' by its self:

```
find . -name "*.txt~" -delete
```

---

### Post by sisco311 on 2009-08-01
I wrote a little bash+zenity script:
```
#!/bin/bash

# size of the window:
WIDTH="400"
HEIGHT="400"

# set this to FALSE if you don't want to auto-select the files
CHECK="TRUE"

# search directory
DIR="$HOME"

# text displayed :)
TEXT="Select files..."

find $DIR -name "*~" | sed "s/\(.*\)/"$CHECK"\n\1/" > /tmp/deltilde

IFS="
"

zenity --list --text "$TEXT" --column "Delete" \
--width $WIDTH --height $HEIGHT \
--checklist --multiple --separator "
" \
--column "File" $(cat /tmp/deltilde) | xargs -d "
" rm
rm /tmp/deltilde

exit 0

```

THERE IS NO WARRANTY FOR THE SCRIPT, use it on your own risk. :evil:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122369&stc=1&d=1248542924[/IMG]

---

