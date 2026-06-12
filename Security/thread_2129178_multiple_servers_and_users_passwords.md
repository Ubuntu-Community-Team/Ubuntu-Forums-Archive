---
title: "multiple servers and users passwords"
date: 2013-03-25
forum: Security
---

### Post by cbillson on 2013-03-25
Anyone else faced this challenge and found a solution.

You have a dozen branch offices, each with an Ubuntu box hosting an application. You have a support team of ten people.

You need to implement a password policy where users passwords expire and are reset fairly frequently.

The issue i face is keeping consistent user passwords across the estate. I dont fancy having to log onto each box and reset users passwords, nor does relying on each user to do so. I can see a situation quickly where passwords are a mess and inconsistent. 

Are there any tools that could assist on either centrally authenticating the users, or for pushing out password changes, or to maintain a common password file?

---

### Post by mvs1207 on 2013-03-25
You could try running a LDAP or NIS server on one of the machines.. and the other machines become NIS clients  [How to Setup NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo")

---

### Post by SeijiSensei on 2013-03-25
NIS is a good solution and not hard to implement.

I've also handled this problem with a bash script that distributes /etc/passwd, /etc/group, and /etc/shadow across the various machines using rsync.  With Ubuntu, you might need to distribute /etc/sudoers as well.  Each server ran a cron job that checked every hour or so to see if the local files needed updating.  It's yours for the taking, though you'll notice it was written for RedHat machines.

```

#!/bin/sh
# SCRIPT TO GET PASSWORD FILES FROM A CENTRAL SERVER
# version 1.1 - updated to support RH7.3 directory structure

# update files (0) or just go through the motions (1)
DEBUG=0

# work directory
WORK=/root/pwimport
# logging
LOG=/var/log/pwimport.log
# location of rsync
RSYNC=/usr/bin/rsync

# source host must be running rsyncd
SOURCE_HOST=name.of.central.server
# name of rsyncd share where password files located
SOURCE_SHARE=name.of.the.share  # see "man rsyncd for details"

# send report here
MAILTO=you@example.com

# root's unique entry for this machine in /etc/shadow
# not needed with Ubuntu if you rely on sudo; 
# if root has a password in /etc/shadow, place that entry here
# it is likely that each machine will need a unique entry#ROOT='root:$1$QL.GB1Cr$qQJt0/QvVJp/B9iemXM3k/:13616:0:99999:7:::'
ROOT=''

###  END OF CONFIGURATION ###

# work in this directory
mkdir -p $WORK
cd $WORK

# initialize the log for this run
echo -n `date` >> $LOG
echo -n ": "   >> $LOG

# delete stale files from last run
rm -f *.old

# get copies of the server's password files
# may need sudoers as well and in the if statement below
$RSYNC -a $SOURCE_HOST::$SOURCE_SHARE/passwd .
$RSYNC -a $SOURCE_HOST::$SOURCE_SHARE/shadow .
$RSYNC -a $SOURCE_HOST::$SOURCE_SHARE/group  .

# exit # enable to debug testing of transfer

# rm -f *  # enable to debug testing of file existence checking

# don't do anything if you can't get the update files!
if [ ! -s passwd ] || [ ! -s shadow ] || [ ! -s group  ]
then    
    echo -n "*** ERROR: No files imported.  NO CHANGES MADE! ***" >> $LOG
    echo -n "*** WARNING: Password files may no longer be correct. ***" >> $LOG
    echo "" >> $LOG
    mail -s "PWIMPORT ERROR" $MAILTO < $LOG
    exit
fi

cp -f group group.old
cp -f passwd passwd.old

if [ "$ROOT" != "" ]
then
    # create unique local root entry on this host
    mv -f shadow shadow.old
    echo "$ROOT" > shadow
    grep -v root shadow.old >> shadow
fi

[ "$DEBUG" = "1" ] && exit 1

# replace the old files in /etc
cd /etc
# quit if can't write to /etc
rm -f passwd-
cp -f passwd passwd-

if [ ! -s passwd- ]
then
    echo "Cannot write password files.   TERMINATING!" >> $LOG
    echo "" >> $LOG
    mail -s "PWIMPORT ERROR" $MAILTO < $LOG
    exit
fi

# backup existing
cp -f passwd passwd-
cp -f shadow shadow-
cp -f group  group-

# copy new
mv -f $WORK/passwd .
mv -f $WORK/group  .
mv -f $WORK/shadow .

chmod go-rwx $WORK/*
chmod 0600 /etc/shadow


echo -n "Password files UPDATED" >> $LOG
echo "" >> $LOG


```

---

### Post by WhaleVPS on 2013-03-26
NIS is great for this. 

Just make sure you set it up securely.

---

