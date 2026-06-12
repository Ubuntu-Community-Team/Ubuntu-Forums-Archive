---
title: "VIP: Command Line Text Editing with Automatic Logged and Timestamped Backups"
date: 2007-12-25
forum: The Cafe
---

### Post by milkyspit on 2007-12-25
Hey all, I'm new to Ubuntu but have used CentOS, Mepis, and OS X for several years. During that time I've been a heavy user of vi from the command line (such as in an SSH terminal session)... eventually I wrote a little shell script that invokes vi to edit the given file, but first creates a backup copy of the file, applies a human-readable date and timestamp to the backup's name, AND logs the edit including filenames to a text file located in the user's home directory. I find it very useful, so thought I'd share it... hope it might help others, and of course, am always interested in comments, improvements, whatever...

Save the following script as 'vip' in a bin subdirectory off your home directory (assuming bin is in your path), and give the new 'vip' script execute permission...

```
#! /bin/sh

if [ $# -lt 1 ]
then
   echo "Usage: vip file_to_edit"
   echo ""
   echo "A record of all changed files appears in the ~/.vip.log file."
   echo ""
   exit 1
else
   FILENAME="$1"
fi

cp -f $FILENAME ${FILENAME}.$(date +%Y%m%d.%H%M%S)
echo "[$(pwd)] ${FILENAME}.$(date +%Y%m%d.%H%M%S) $FILENAME" >> ~/.vip.log
vi $FILENAME

exit 0
```

The name 'vip' stands for 'VI, Preserving' or something similar. Hey, the name seemed cool! ;)

The info in the log file turns out to be particularly useful for running a diff between versions of the file... in that sense it's like a poor man's version control system. Likewise, the backup files are easy to identify by virtue of the date and timestamp appended to the name.

Enjoy... Merry Christmas! :)

---

