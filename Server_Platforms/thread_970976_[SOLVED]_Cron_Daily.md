---
title: "[SOLVED] Cron Daily"
date: 2008-11-04
forum: Server Platforms
---

### Post by baudday on 2008-11-04
I have the following shell script:

```
# !/usr/bin/bash
# This is a file used to insert
# index.php into newly created
# sub-directories within a main
# directory.
cd /var/www/Pictures/Willem\ Sr\ Pictures/
DIRS=*
for f in $DIRS
do
 if [ -d "$f" ]
  then
   echo "Processing $f..."
   chmod 777 "$f"
   cd "$f"
   pwd
   cat "../noindex.php" > index.php
   cd ..
 elif [ ! -d "$f" ]
  then
   echo "Not a directory..."
 fi
# cat $f
done
```

And I would like that to run every day at whatever time. I put it in the cron.daily folder and get then do crontab -e. Here's what my crontab looks like.

```
# m h  dom mon dow   command
36 14  *   *   *     '/etc/cron.daily/index'

```

For some reason it will not run. I've tried it without the single quotes. I just figured you're supposed to put the command exactly as you would type it. That could be wrong, but just be aware I have tried it the other way.

---

### Post by tonyh6243 on 2008-11-04
If your bash script requires root access it will not run in the folder you put it. Try putting it in the root folder. You can test it by running it from there once you have moved it. Make sure to update your crontab to reflect the change in folders.

---

### Post by baudday on 2008-11-04
you mean just in / ?

---

### Post by tonyh6243 on 2008-11-04
Go to Places -> Computer -> Filesystem -> root

---

### Post by baudday on 2008-11-04
I don't have a GUI.

---

### Post by jakupl on 2008-11-04
> **tonyh6243 said:**
> Go to Places -> Computer -> Filesystem -> root

That is /root

---

### Post by baudday on 2008-11-04
okay so i have it in there and i changed crontab to ```
04 15  *   *   *     /root/index
``` and it still doesn't work

---

### Post by tonyh6243 on 2008-11-04
Did you make the bash file executable

sudo chmod -x *filepath*

---

### Post by baudday on 2008-11-04
Yes I did. But only for the owner, does it need to be more?

---

### Post by tonyh6243 on 2008-11-04
I am working under the assumption that your bash script is correct. I am by no means an expert in that field. Considering the recent advice did not resolve the issue I would assume it is an issue with the script.

---

### Post by MJN on 2008-11-04
> **baudday said:**
> And I would like that to run every day at whatever time. I put it in the cron.daily folder and get then do crontab -e. Here's what my crontab looks like.It sounds like you are mixing up the system cron files with that of users.

If you drop a script into /etc/cron.daily/ it will get executed as per the timings in /etc/crontab. There is no need to influence cron in any other way (i.e. through crontab -e, for example).

A few things to check - make sure the script has its executable bit set, remove the space between # and ! on the shebang in the script, and double check the location of your script interpreter (are you sure it is /usr/bin/bash and not /bin/bash? It may well be... I'm on 6.06 so things might've moved on...).

Mathew

---

### Post by baudday on 2008-11-04
Well I really appreciate the help, it was a little bit of my file that was incorrect, that first line, and then where I was trying to execute it. It ended up like this.

```
#!/bin/sh
#Script Name: index.sh
#Author Name: Willem Ellis
#Date: Tues Nov 4 17:22:00 CST 2008
#Description: This is a file used to insert
# index.php into newly created
# sub-directories within a main
# directory.
cd /var/www/Pictures/Willem\ Sr\ Pictures/
DIRS=*
for f in $DIRS
do
 if [ -d "$f" ]
  then
   echo "Processing $f..."
   chmod 777 "$f"
   cd "$f"
   pwd
   cat "../noindex.php" > index.php
   cd ..
 elif [ ! -d "$f" ]
  then
   echo "Not a directory..."
 fi
done
```

And what I had to do was exactly what MJN said, I had to set the job in /etc/crontab instead of doing the crontab -e thing. And there I set it to execute as root, and it had no problem. So thanks again for the help.

---

### Post by MJN on 2008-11-05
> **baudday said:**
> And what I had to do was exactly what MJN said, I had to set the job in /etc/crontab instead of doing the crontab -e thing. And there I set it to execute as root, and it had no problem.No! :-)
 
You should not be editing /etc/crontab at all.
 
The act of dropping your script into /etc/cron.daily/ is all you need to do. The script will then be executed daily in accordance with the 'daily' line on /etc/crontab.
 
Mathew

---

