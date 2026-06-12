---
title: "Bash script behaving differently in crontab vs manually run"
date: 2013-03-08
forum: Server Platforms
---

### Post by LHammonds on 2013-03-08
Greetings.

I have a script that purges files from a folder and I would like a record (log file) of what files were purged.

I wrote the following snippet and it works when executing it from the command line:

```

LOGFILE="/path/to/logfiles/purge-folder.log"
echo "`date +%Y-%m-%d_%H:%M:%S` - Script started." >> ${LOGFILE}
for file in "/path/to/folder/*.txt"
do
  echo " - INFO: Deleting ${file}" >> ${LOGFILE}
  rm ${file}
done
echo "`date +%Y-%m-%d_%H:%M:%S` - Script completed." >> ${LOGFILE}

```

When I run it from the command line, the log file looks like this (shows each file deleted individually):

```

2013-03-01_10:43:35 - Script started.
 - INFO: Deleting /path/to/folder/20130227.txt
 - INFO: Deleting /path/to/folder/20130228.txt
 - INFO: Deleting /path/to/folder/20130301.txt
2013-03-01_10:43:35 - Script completed.

```

When run from crontab, the log file looks like this (no matter how many files are deleted):

```

2013-03-02_10:00:01 - Script started.
 - INFO: Deleting /path/to/folder/*.txt
2013-03-02_10:00:01 - Script completed.

```

This is how my root crontab looks:

```

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
0 10 * * * /path/to/scripts/purge-folder.sh > /dev/null 2>&1

```

Any idea on how to get the script to behave in crontab like it does at the command-line?

Thanks,
LHammonds

---

### Post by schragge on 2013-03-08
Remove excessive quoting
```

LOGFILE="/path/to/logfiles/purge-folder.log"
echo "`date +%Y-%m-%d_%H:%M:%S` - Script started." >> ${LOGFILE}
for file in /path/to/folder/*.txt [COLOR=blue]# excessive double quotes removed from this line[/COLOR]
do
  echo " - INFO: Deleting ${file}" >> ${LOGFILE}
  rm ${file}
done
echo "`date +%Y-%m-%d_%H:%M:%S` - Script completed." >> ${LOGFILE}

```

---

### Post by LHammonds on 2013-03-08
I'll give that a shot but I added the quotes to see if that would help solve the problem. :)

**EDIT:** Ha!  That did it!  Not sure what I had done before since I added the quotes to see if that would resolve the problem but it is working now.  Thanks

---

### Post by schragge on 2013-03-08
Shell globs (*) don't get expanded inside double quotes. Besides, you will still get the message 
```
- INFO: Deleting /path/to/folder/*.txt
``` if there are _no_ files in the folder matching this pattern. You may choose to ignore it, or test for presense of any files to be deleted beforehand. If your script is bash (as opposite to /bin/sh), you also can set *shopt -s nullglob* before entering the loop.

---

### Post by LHammonds on 2013-03-08
Good point about the file check.  I should do that no matter what before an rm command.

Script modified as such:

```

LOGFILE="/path/to/logfiles/purge-folder.log"
echo "`date +%Y-%m-%d_%H:%M:%S` - Script started." >> ${LOGFILE}
for file in /path/to/folder/*.txt
do
  if [ -f ${file} ]; then
    echo " - INFO: Deleting ${file}" >> ${LOGFILE}
    rm ${file}
  fi
done
echo "`date +%Y-%m-%d_%H:%M:%S` - Script completed." >> ${LOGFILE}

```

---

### Post by schragge on 2013-03-08
If you don't have thousands of .txt files in the folder then I'd rewrite it like this (*sed* is optional, in case you don't like the output of *rm -v*)
```

LOGFILE="/path/to/logfiles/purge-folder.log"
echo "`date +%Y-%m-%d_%T` - Script started." >> ${LOGFILE}
rm -fv /path/to/folder/*.txt | sed 's/^removed/ - INFO: Deleting/'  >> ${LOGFILE}
echo "`date +%Y-%m-%d_%T` - Script completed." >> ${LOGFILE}

```

---

