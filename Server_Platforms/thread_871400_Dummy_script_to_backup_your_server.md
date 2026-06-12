---
title: "Dummy script to backup your server"
date: 2008-07-26
forum: Server Platforms
---

### Post by udienz on 2008-07-26
hi...
i have little script to backup my server and this backup reported by email. let's see..
```
#!/bin/sh
####################################
#
# Script to creating Backup File
# save fo /usr/sbin/backup.sh
# inspired from ubuntu-serverguide
# thanks to Ubuntu Documentation Team!
# please send me e-mail if you want to recode again!
# thank's before
# Mahyuddin Susanto aka udienz email = udienz@gmail.com
#
####################################

# What a backup?
#DIRECTORY="/var/www /var/spool/mail /etc /boot"
DIRECTORY="/var/www /etc /boot"
EMAIL=udienz@gmail.com
CCEMAIL=udienz@ubuntu.com
# Where to backup to.
TARGET="/tmp/backup"
if test -d $TARGET;
    then EXISTS="yes"
else
    mkdir -p $TARGET
fi

# Create archive filename.
DAY=$(date +%F)
HOST=$(hostname -i)
ARCHIVE="$HOST-$DAY.tgz"

# Print start status message.
echo "Backing up $DIRECTORY to $TARGET/$ARCHIVE"
date
echo

# Backup the files using tar.
tar czf $TARGET/$ARCHIVE $DIRECTORY
md5sum $TARGET/$ARCHIVE >> $TARGET/md5sum.$ARCHIVE.txt
# i dont'know how wo make file contain dirrefent both directory
# diff -rNu /where/come/ /want/toa/ > different$DAY.diff
# dpatch patch-template -p "different$DAY" "different directory" < different$DAY.diff > different$DAY.patch
#maybe, i think using method patching package into good, maybe [IMG]http://udienz.immteknik.org/wp-includes/images/smilies/icon_biggrin.gif[/IMG] 

# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
# ls -lh $TARGET

# Crontab, backingup every sunday
# 0 0 0 * * bash /usr/local/bin/backup.sh

TMPFILE=`mktemp`
exec > "$TMPFILE"
echo "From: \"Backup report $HOST\" "root@$HOST""
echo "To: $EMAIL"
echo "Cc: $CCEMAIL"
echo "Subject: Information about backingup $HOST"
echo ""
echo "Hello mr/mrs $EMAIL and $CCEMAIL!"
echo ""
echo "If you get this email it mean that back-up proses at $HOST,"
echo "is succes, more information about back-up is:"
echo ""
echo "Directory to backup is = $DIRECTORY"
echo "and saved to $TARGET/$ARCHIVE"
echo "finished at `date`"
echo "have MD5SUM `md5sum $TARGET/$ARCHIVE | cut -f1 -d ' '`"
echo ""
echo "`ls -lh $TARGET/`"
echo ""
echo "Best Regard"
echo "............"
exec
/usr/sbin/sendmail -t -i < $TMPFILE
rm -f $TMPFILE
#ls -lh $TARGET/

# END Of Script
```any idea to rebuild this script?

---

