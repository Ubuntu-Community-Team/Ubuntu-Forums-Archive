---
title: "Versioned backup"
date: 2009-07-06
forum: Server Platforms
---

### Post by vetanix on 2009-07-06
I have about a dozen of servers running ubuntu, and I would like to backup certain configuration files (mostly files in /etc /var /root) to a central machine. Preferably, I will be able to restore any previous version of any backed up file. 

For my windows machines, I already have a solution that works quite well, but I have been unable to find anything on the Linux side. The closest thing I've found to what I need is bazaar, but there are certain things I don't like about it, among which is the fact that I have to install the bazaar client on each machine. Also I thnk that it will be an overkill to use a full-fledged distributed version control system for such a basic task. 

Has anyone here tackled this problem before?

---

### Post by eas on 2009-07-06
Check out rsnapshot.  It uses rsync, can backup files on remote servers, and creates a versioned backup snapshot of the backed up files.

---

### Post by HermanAB on 2009-07-06
Howdy,

It sounds like you need a versioning system.  If you are the only person using it, then RCS may be good enough:
[http://aeronetworks.ca/rcs-howto.html](http://aeronetworks.ca/rcs-howto.html)

---

### Post by windependence on 2009-07-06
Bacula or Amanda would work well for you here. AFAIK, Bacula has a GUI front end also.

In case you just want something short and compact, this is not bad either:

```
#! /bin/bash 
# 
##################################################  #################
# This is a script to run my backups. Put together from sources all over the 'net, it will,                     # 
# in theory, wake up the remote server, perform an rsync-style incremental backup, then shut         # 
# the the server down. This script is a modified version of one found in an article of Linux                # 
# Journal in Jan 06 titled 'Build a Home Terabyte Backup System'. I am not sure who the                      ## author was, but their script was a modified version of one created by rsync creator Andrew           # 
# -Windependence # 
##################################################  #################

###########  
# VARIABLES # 

 
# Login name 
LOGIN=backup

# Backup server name 
BUSRVR=backups

# Backup server MAC address 
BUMAC=xx:xx:xx:xx:xx

# Directory to be backed up 
BUSRC=/home/ron/test/

# Directory on server to back up to 
BUDEST=/backups/ron/rsync.test

# This is the backup subdirectory, dictated by date and time 
BUSUBDIR=`date +%A`  

# Log file location 
LOGLOCATION=/home/ron/Desktop

# Options to pass to rsync 
OPTS="--delete -vv --modify-window=2 --force --ignore-errors --backup --backup-dir=$BUDEST/ -az --stats --partial-dir=RSYNC.PARTIAL --progress -e ssh"  

########### 
# Commands   # 
###########

# Dump output to log 
date > $LOGLOCATION/backuplog.$BUSUBDIR.txt

#  Wake up the remote server 
sudo /usr/local/bin/ether-wake $BUMAC  

#  Wait an amount of time to allow the server to boot and get ready for data transfer 
sleep 180 

# This section deletes the last week's incremental backups
[ -d /tmp/emptydir ] || mkdir /tmp/emptydir
rsync --delete -a /tmp/emptydir
$LOGIN@$BUSRVR:$BUDEST/$BUSUBDIR/
rmdir /tmp/emptydir 

# Actual file transfer 
rsync $OPTS $BUSRC $LOGIN@$BUSRVR:$BUDEST/current >> $LOGLOCATION/backuplog.$BUSUBDIR.txt


```

You have to create a user "backup" with the proper privileges to run this.

-Tim

---

### Post by vetanix on 2009-07-07
I appreciate your help. I decided to go with rsnapshot.

---

