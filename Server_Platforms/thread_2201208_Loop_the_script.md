---
title: "Loop the script"
date: 2014-01-23
forum: Server Platforms
---

### Post by nerdtron on 2014-01-23
Or should I say "re-run the script."

I have this script:
```

#!/bin/bash
cd /root/processing
#loop to check if /root/processing folder still has files in it.
while [ `ls /root/processing | wc -l` -ne 0 ];
do
#This is where I put the command to process each file and add to database
file=`ls -tr1 | head -1`
word1=`awk '{print $1}' $file`
word2=`awk '{print $2}' $file`
echo "INSERT INTO database.table(username, value) VALUES ('$word1', '$word2');" | mysql -uuser -puser
#Move the file to completed directory.
mv $file /root/completed

done
echo "All files processed."

```

Basically, I have the folder /root/processing which contains text files to be added to the database in mysql. Then after processing the text file, it will be moved to the /root/processed folder. The script works fine if I run it.

Here's my question, when there are no longer files in the /root/processing folder, the script stops. How can I run the script again **automatically** in case I will put text files in the /root/processsing directory?

---

### Post by Lars Noodén on 2014-01-23
You might want to use [inotify](http://manpages.ubuntu.com/manpages/saucy/en/man7/inotify.7.html) to watch your directory instead.  It can trigger a script when files are added, changed or deleted in the directory.  You would set up your run conditions using [incron](http://manpages.ubuntu.com/manpages/saucy/en/man5/incrontab.5.html).  It is in the repository and does not need a PPA but the rest of the HowTo is ok:

[http://www.howtoforge.com/triggering-commands-on-file-or-directory-changes-with-incron](http://www.howtoforge.com/triggering-commands-on-file-or-directory-changes-with-incron)

The file format is a little confusing untill you see the pieces.

---

### Post by nerdtron on 2014-01-23
Thanks for incrontab. I think it would be a good solution. I'll look into it.

---

### Post by ian-weisser on 2014-01-23
Upstart-file-bridge, already part of Upstart. Example usage at [http://upstart.ubuntu.com/cookbook/#upstart-file-bridge](http://upstart.ubuntu.com/cookbook/#upstart-file-bridge)

---

### Post by SeijiSensei on 2014-01-24
Usually I just run the script from crontab with a short elapsed time like one or five minutes.  In cases like the one the OP describes, I rarely have a need for real-time processing.

If there's a chance the script may run longer than a minute, I write a lock file to /tmp.  Then any subsequent attempts to run the script stop after checking for the presence of the lock file.

```

#!/bin/bash
DEBUG=Y
LOCKFILE=/tmp/script.lock

if [ -f $LOCKFILE ]
then
    [ "$DEBUG" = "Y" ] && echo "Lock file $LOCKFILE found."
    exit 1
fi
touch $LOCKFILE

[etc.]

rm -f $LOCKFILE

exit 0


```

You might consider spltting up the script into two parts. Create a generic "wrapper" script that runs from cron to check for the presence of the files.  When found, the wrapper would write the lock file and invoke the SQL import script.  This gives you a convenient template for handing similar processes in the future if you use variables for things like the monitored directory and the subsidiary script's name.

---

