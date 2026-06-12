---
title: "Restoring default files permissions issue"
date: 2006-11-01
forum: Server Platforms
---

### Post by Guard on 2006-11-01
Greetings for You, please enjoy the discussion!
Once, surfing my Ubuntu as root I had execute a command with mistake in it's logical syntax:
**chmod u+rwx,g+rwx,o-rwx / -R**After this many daemons and services are working incorrectly.
Samba and Apache2 are running, but I can't connect, also I can't logon from user different to root.
I had written a few scripts, one of them are saving permissions of folder content: 
#first script
#cat save_perm.sh
#!/bin/sh
if [ "$1" = "" ]; then
       exit
fi
perm=`stat -c %a $1`
file=$1
echo -e "${file}\t${perm}" >> perm.cfg

#second script
#cat get_perm.sh
#!/bin/sh
if [ "$1" = "" ]; then
       echo "Usage: $0 <snapshot_directory>"
       echo "Example: $0 /"
       exit
fi
find $1 -exec ./save_perm.sh {} $1 \;

And other, that restores saved permissions.
Here it is:
#third script:
#cat restore_perm.sh
#!/bin/sh
if [ "$1" = "" ]; then
       echo "Usage: $0 <snapshot_directory>"
       echo "Example: $0 /"
       exit
fi
cat perm.cfg | while read line; do
       file=`echo $line | awk '{print $1}'`
       perm=`echo $line | awk '{print $2}'`
       chmod $perm $file
done

I have an Ubuntu v 5.10 on my server, but I’m not able to run this version from Live CD on my or other workstations. And I save permissions for main directories like etc, lib, usr, bin, sbin ... from Ubuntu v 5.04 Live CD. After that, I’ve restored permissions on my server (i know that is not especially correct, because a directory structure of these versions are different),
but the system is still working incorrectly.
**Does anyone knows, how to restore default permissions of files automatically?**Excuse me for my pure English.
With best regards from Guard.

---

