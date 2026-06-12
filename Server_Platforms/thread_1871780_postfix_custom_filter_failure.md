---
title: "postfix custom filter failure"
date: 2011-10-29
forum: Server Platforms
---

### Post by apix on 2011-10-29
Greetings,

I am trying to filter all incoming messages from my postfix server through a filtering script of my own. I have searched the web on how to do it, and here is what i have done so far:


```
server /var/spool/filter $ cat post_filter.sh
#!/bin/sh

# Simple shell-based filter. It is meant to be invoked as follows:
#       /path/to/script -f sender recipients...

# Localize these. The -G option does nothing before Postfix 2.3.
INSPECT_DIR=/var/spool/filter
SENDMAIL="/usr/sbin/sendmail -G -i" # NEVER NEVER NEVER use "-t" here.

# Exit codes from <sysexits.h>
EX_TEMPFAIL=75
EX_UNAVAILABLE=69

# Clean up when done or when aborting.
trap "rm -f in.$$" 0 1 2 3 15

touch /tmp/lalala.$RANDOM #check if anyone is calling this script
# Start processing.
cd $INSPECT_DIR || {
        echo $INSPECT_DIR does not exist; exit $EX_TEMPFAIL; }

        cat >in.$$ || {
                echo Cannot save mail to file; exit $EX_TEMPFAIL; }

# Specify your content filter here.
/var/spool/filter/filter.sh <in.$$ || {
   echo Message content rejected; exit $EX_UNAVAILABLE; }

   $SENDMAIL "$@" <in.$$

   exit $?
```

and the actual filder.sh is listed bellow
```
#!/bin/bash

FILE=/var/spool/filter/email.$RANDOM
while read line; do
        echo "--> $line" >> $FILE
done
```

I have created a user named emailfilder and gave him access to all the needed directories
```
server /var/spool/filter $ pwd
/var/spool/filter
server /var/spool/filter $ ls -al
total 20
drwxr-xr-x  2 emailfilder root        4096 2011-10-29 16:15 .
drwxr-xr-x 10 root        root        4096 2011-10-29 15:41 ..
-rw-r--r--  1 emailfilder emailfilder   92 2011-10-29 16:06 email.test
-rwxr-xr-x  1 emailfilder emailfilder  102 2011-10-29 16:02 filter.sh
-rwxr-xr-x  1 emailfilder emailfilder  799 2011-10-29 16:15 post_filter.sh
```

After all the above, i created a rule in /etc/postfix/master.cf with the following line 
```
filter    unix  -       n       n       -       10              pipe
    flags=Rq user=emailfilder argv=/var/spool/filter/post_filter.sh -f ${sender} -- ${recipient}
``` and then i restarted postfix and send an email to it, but it does not seem to work. New emails are not created though my folder.sh script, emails get delivered as usual to the users and there are no error logged in postfix logs.

Am i missing anything major here ? Any help appreciated.

Postfix + system infos
```
 postconf -d | grep mail_version
mail_version = 2.7.0
uname -a
Linux server 2.6.18-128.2.1.el5.028stab064.8PAE #1 SMP Sat Oct 31 11:13:46 MSK 2009 i686 GNU/Linux
 cat /etc/issue
Ubuntu 10.04.1 LTS \n \l
```



Thanks,
apix.

---

