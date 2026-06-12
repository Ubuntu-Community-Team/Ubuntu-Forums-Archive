---
title: "Brilliant people, please help me create a script to backup"
date: 2010-07-17
forum: The Cafe
---

### Post by neoargon on 2010-07-17
I wish to backup my files regularly . For that Iam planning to write files(in folders) to dvds . The problem is:

How do I know whether a file is already backed up after some time? In time, I'll add files to the existing folders . 

The idea in my mind is to create 1 or 2 script/s to automate the process .
1. The script must first write to a text file(say "index" file) the structure of a folder (which means the name of sub folders and files in that folder as well as their modification date) I wish to backup .
2.The script should be able to compare another such index file and find out what extra files/folders are there in the second one . 
3.If I create another index file after some days, and if I compare it with the one I created earlier, I can find out what the not backed up files are , and can write only those files to DVD .

I don't know the commands to do that . I know that there are a lot of brilliant people here . If you tell me the commands, I would be grateful .

Just the commands to create index file and compare the index files are enough

 If you have any better idea, please tell that too

I reinstall ubuntu every 6 months , so I don't wish to use any backup application since the configuration and log files will be lost when Ubuntu is re installed

---

### Post by Penguin Guy on 2010-07-17
That's way too complicated, just get a second hard drive to back stuff up onto.

---

### Post by handy on 2010-07-17
**@neoargon:** Have a search for "cron" on the web, reading up on it will broaden your horizons on the topic of your interest. The man page will also be helpful, though you may find other sources to be more friendly initially. :)

---

### Post by koenn on 2010-07-17
the way you're planning this, you will not backup a file that has been modified after it has been backed up. Is that what you want to do ?

Also, a probably easier way is
- let your backup script create a file after the backup is done,
- the next time the backup script runs, first check the modify-time of that file (= date/time of your previous backup). Then only backup files newer than that date (eg find newer that the reference file), or modified later than that date.

---

### Post by oldfred on 2010-07-17
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh
Code:

#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."

rsync -auvP /home /media/backup
rsync -auvP /share /media/backup
rsync -auvP /media/floppy /media/backup
rsync -auvP /etc /media/backup
echo "done"
exit 0

make it executable
Code:

chmod +x mybackup.sh

run it
Code:

./mybackup.sh

---

### Post by Kimm on 2010-07-17
> **koenn said:**
> Then only backup files newer than that date (eg find newer that the reference file), or modified later than that date.

+1 This sounds exactly like what he is looking for, and its quite an elegant solution

---

### Post by neoargon on 2010-07-17
> **koenn said:**
> the way you're planning this, you will not backup a file that has been modified after it has been backed up. Is that what you want to do ?

Also, a probably easier way is
- let your backup script create a file after the backup is done,
- the next time the backup script runs, first check the modify-time of that file (= date/time of your previous backup). Then only backup files newer than that date (eg find newer that the reference file), or modified later than that date.

You have a point . I should think that too 
I use multiple operating systems (>2) and reinstall ubuntu every 6 months, so can I believe the modification date? What if I add a file created before the last backup to a folder ?

I think both the modification date and name should be checked

---

### Post by neoargon on 2010-07-17
@**handy**: , Thanks
@**koenn**: I'll check that . Thanks

---

### Post by Penguin Guy on 2010-07-17
You could use md5sums.

---

### Post by neoargon on 2010-07-17
> **oldfred said:**
> Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh
Code:

#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."

rsync -auvP /home /media/backup
rsync -auvP /share /media/backup
rsync -auvP /media/floppy /media/backup
rsync -auvP /etc /media/backup
echo "done"
exit 0

make it executable
Code:

chmod +x mybackup.sh

run it
Code:

./mybackup.sh

If I re install Ubuntu, how would rsync know whether some files are already backed up?

---

### Post by neoargon on 2010-07-17
> **Penguin Guy said:**
> You could use md5sums.
Can you please explain?

---

### Post by Barrucadu on 2010-07-17
FWIW here's my backup script. It's probably a bit more complex than what you need, as it backs up multiple computers and keeps me notified of the progress via Jabber:

```
#!/bin/zsh

# Backup script:
#   Takes full and incremental backups, to a local directory, using rsync.
#   SSH transfer requires root login be allowed on the client, and SSH keys
#   be exchanged for passwordless login. This script should be run as root.
#
# To set up a new host:
#   * Update the COMPUTERS list with the hostname.
#   * Set up client SSHD to allow passwordless restricted login from Eihort.
#   * Copy validate-ssh script to new client
#   * Copy getparts script to new client

################################## VARIABLES ###################################

# General-purpose variables:
#  COMPUTER:   hostname of the backup server.
#  COMPUTERS:  hostnames of computers (other than localhost) to back up.
#  BACKUPDEV:  device to store the backup on.
#  BACKUPDIR:  directory to store the backup in
#  TYPE:       the type of backup (full, inc)
COMPUTER=`hostname`
COMPUTERS=(azathoth randolph archhurd.org)
BACKUPDEV=/dev/disk/by-label/BackupHDD
BACKUPDIR=/media/BackupHDD
TYPE=$1
LOGFILE=/var/log/backup.log

# sendxmpp-related variables:
#  SENDXMPP: path to sendxmpp
#  SRVADMIN: JID of server administrator
SENDXMPP=/usr/bin/perlbin/site/sendxmpp
SRVADMIN=mike@barrucadu.co.uk

# rsync-related variables:
#  FULLDIR:   directory for last full backup
#  DIR:       directory to store current backup
#  EXCLUDE:   path of global rsync excludes files
#  RSYNCARGS: arguments passed to rsync
#  FULLARGS:  arguments passed to rsync in a full backup
#  INCARGS:   arguments passed to rsync in an incremental backup
#  SSHARGS:   arguments passed to rsync in a backup over SSH
FULLDIR=`date +%Y-%m`
DIR=`date +%Y-%m-%d`

if [[ "$TYPE" == "full" ]]; then
    DIR=$FULLDIR
fi

EXCLUDE=/etc/backup.d/
RSYNCARGS=(-avz --numeric-ids --delete --exclude-from=${EXCLUDE}global --stats)
FULLARGS=()
INCARGS=(--link-dest=../$FULLDIR/)
SSHARGS=(-e ssh)

################################# MAIN SCRIPT ##################################

function sendmsg()
{
    msg=$1
    echo "[backup] $msg" | $SENDXMPP $SRVADMIN
    echo "`date --rfc-3339=seconds` $msg" >> $LOGFILE
}

function sendnotice()
{
    sendmsg "notice: $1"
}

function senderr()
{
    sendmsg "error: $1"
}

function checkhost()
{
    host=$1
    if ping -c1 $host &>/dev/null; then
        return true
    else
        senderr "$host offline."
        return false
    fi
}

function backuphost()
{
    host=$1
    ssh=$2
    source=/
    args=$FULLARGS
    args2=()

    if $ssh; then
        source="root@$host:/"
        args2=$SSHARGS

        ssh root@$host -t '/root/getparts' > $BACKUPDIR/$host/partitions-$DIR && \
        sendnotice "$host partitions backed up"
    else
        sfdisk -d $(ls /dev/sd[a-z]) > $BACKUPDIR/$host/partitions-$DIR && \
        sendnotice "$host partitions backed up"
    fi

    if [[ "$TYPE" == "inc" ]]; then
        args=$INCARGS
    fi

    if [[ ! -d $BACKUPDIR/$host/$DIR/ ]]; then
        mkdir -p $BACKUPDIR/$host/$DIR/
    fi

    rsync $RSYNCARGS $args $args2 --exclude-from=${EXCLUDE}${host} $source $BACKUPDIR/$host/$DIR/ && \
    sendnotice "$host data backed up"
}

if [[ "$TYPE" != "full" ]] && [[ "$TYPE" != "inc" ]]; then
    senderr "Usage: backup [full|inc] ($TYPE given)."
    return 1
fi

if [[ -e $BACKUPDEV ]]; then
    if ! mount -o remount,rw $BACKUPDEV &>/dev/null; then
        if ! mount -o rw $BACKUPDEV &>/dev/null; then
            senderr "$BACKUPDEV will not mount."
            return 1
        fi
    fi
else
    senderr "$BACKUPDEV not found."
    return 1
fi

sendnotice "Backup started."

if [[ "$2" != "" ]]; then
    backuphost $2 $3
else
    backuphost $COMPUTER false
    for host in $COMPUTERS; do
        checkhost $host && backuphost $host true
    done
fi
sendnotice "Backup ended."

mount -o remount,ro $BACKUPDEV
```

However it should give you some ideas.

---

### Post by neoargon on 2010-07-17
> **Barrucadu said:**
> FWIW here's my backup script. It's probably a bit more complex than what you need, as it backs up multiple computers and keeps me notified of the progress via Jabber:

```
#!/bin/zsh

# Backup script:
#   Takes full and incremental backups, to a local directory, using rsync.
#   SSH transfer requires root login be allowed on the client, and SSH keys
#   be exchanged for passwordless login. This script should be run as root.
#
# To set up a new host:
#   * Update the COMPUTERS list with the hostname.
#   * Set up client SSHD to allow passwordless restricted login from Eihort.
#   * Copy validate-ssh script to new client
#   * Copy getparts script to new client

################################## VARIABLES ###################################

# General-purpose variables:
#  COMPUTER:   hostname of the backup server.
#  COMPUTERS:  hostnames of computers (other than localhost) to back up.
#  BACKUPDEV:  device to store the backup on.
#  BACKUPDIR:  directory to store the backup in
#  TYPE:       the type of backup (full, inc)
COMPUTER=`hostname`
COMPUTERS=(azathoth randolph archhurd.org)
BACKUPDEV=/dev/disk/by-label/BackupHDD
BACKUPDIR=/media/BackupHDD
TYPE=$1
LOGFILE=/var/log/backup.log

# sendxmpp-related variables:
#  SENDXMPP: path to sendxmpp
#  SRVADMIN: JID of server administrator
SENDXMPP=/usr/bin/perlbin/site/sendxmpp
SRVADMIN=mike@barrucadu.co.uk

# rsync-related variables:
#  FULLDIR:   directory for last full backup
#  DIR:       directory to store current backup
#  EXCLUDE:   path of global rsync excludes files
#  RSYNCARGS: arguments passed to rsync
#  FULLARGS:  arguments passed to rsync in a full backup
#  INCARGS:   arguments passed to rsync in an incremental backup
#  SSHARGS:   arguments passed to rsync in a backup over SSH
FULLDIR=`date +%Y-%m`
DIR=`date +%Y-%m-%d`

if [[ "$TYPE" == "full" ]]; then
    DIR=$FULLDIR
fi

EXCLUDE=/etc/backup.d/
RSYNCARGS=(-avz --numeric-ids --delete --exclude-from=${EXCLUDE}global --stats)
FULLARGS=()
INCARGS=(--link-dest=../$FULLDIR/)
SSHARGS=(-e ssh)

################################# MAIN SCRIPT ##################################

function sendmsg()
{
    msg=$1
    echo "[backup] $msg" | $SENDXMPP $SRVADMIN
    echo "`date --rfc-3339=seconds` $msg" >> $LOGFILE
}

function sendnotice()
{
    sendmsg "notice: $1"
}

function senderr()
{
    sendmsg "error: $1"
}

function checkhost()
{
    host=$1
    if ping -c1 $host &>/dev/null; then
        return true
    else
        senderr "$host offline."
        return false
    fi
}

function backuphost()
{
    host=$1
    ssh=$2
    source=/
    args=$FULLARGS
    args2=()

    if $ssh; then
        source="root@$host:/"
        args2=$SSHARGS

        ssh root@$host -t '/root/getparts' > $BACKUPDIR/$host/partitions-$DIR && \
        sendnotice "$host partitions backed up"
    else
        sfdisk -d $(ls /dev/sd[a-z]) > $BACKUPDIR/$host/partitions-$DIR && \
        sendnotice "$host partitions backed up"
    fi

    if [[ "$TYPE" == "inc" ]]; then
        args=$INCARGS
    fi

    if [[ ! -d $BACKUPDIR/$host/$DIR/ ]]; then
        mkdir -p $BACKUPDIR/$host/$DIR/
    fi

    rsync $RSYNCARGS $args $args2 --exclude-from=${EXCLUDE}${host} $source $BACKUPDIR/$host/$DIR/ && \
    sendnotice "$host data backed up"
}

if [[ "$TYPE" != "full" ]] && [[ "$TYPE" != "inc" ]]; then
    senderr "Usage: backup [full|inc] ($TYPE given)."
    return 1
fi

if [[ -e $BACKUPDEV ]]; then
    if ! mount -o remount,rw $BACKUPDEV &>/dev/null; then
        if ! mount -o rw $BACKUPDEV &>/dev/null; then
            senderr "$BACKUPDEV will not mount."
            return 1
        fi
    fi
else
    senderr "$BACKUPDEV not found."
    return 1
fi

sendnotice "Backup started."

if [[ "$2" != "" ]]; then
    backuphost $2 $3
else
    backuphost $COMPUTER false
    for host in $COMPUTERS; do
        checkhost $host && backuphost $host true
    done
fi
sendnotice "Backup ended."

mount -o remount,ro $BACKUPDEV
```However it should give you some ideas.
Yeah . That helps

---

### Post by SaintDanBert on 2010-07-17
> **neoargon said:**
> I wish to backup my files regularly . For that Iam planning to write files(in folders) to dvds.
...


What we call [highlight]backup[/highlight] is really a mash-up of several things. 
[list]
[*]In one case we are protecting files against catastrophic failure of their disk drive or human misadventure. This approach typically involves cloning of mirroring files from the active drive to some other drive or optical drive or tape. I call this copy, FAILSAFE.
[*]The other case is long term storage of data for various reasons, not the least of which is legal requirements. Since you have this data copy as catastrophe protection, it is easy to store that copy for long term file ARCHIVE, but that is not really effective. 
[/list]

A failsafe copy, will see some file "/some/file/path/filename". If you have multiple copies, you will see this exactly same filename.
An archive would know details about file content or context and be able to select one over another. Consider the case of a writer who has several manuscripts in the works. Failsafe would see "article-1", ..., "article-27" etc. An archive would see those same files, but would know which articles had been submitted for publication and which were actually published.

With all this said, today's prevailing approach for end-users uses externally connected drives and "cloning" from active disk to external drive. They create a failsafe every time. External drives are so inexpensive compared to the time and effort to do something else.

Another approach uses **rsync** to create a mirror of the active files onto the external drive.  I use [LuckyBackup]("http://luckybackup.sourceforge.net/"). The **rsync** utility looks at folders and files at the source and compares them with the target. The program then copies files around so that both sets of files are synchronized. Nicely, either the target or the source might be remote -- on the network -- from the workstation running the command.

The most clever approach I've seen used **make**. Most folks think of make in terms of building software from source files. However, in the general case, the command **make target** says:
[list]
[*] find **target** in the controlling Makefile.
[*] use the Makefile to discover all of the parts involved
[*] if any of the parts are newer than the target, use the commands to create an up-to-date copy of **target**.
[*] since each **part** may itself be another target, the processing is recursive so that everything becomes current.
[/list] 
With this in mind, a target might be a CD or DVD or tar-ball for some of your files. Make then scans for "what is newer" than the backup target. Since today's backup does not exist, everything is newer and make decides to create the target. Click-whirr and a backup happens.
You can create marker files using **touch filename** so that the newer-than decisions remember when you made backup recently.

Just some thioughts,
~~~ 0;-Dan

---

### Post by cariboo on 2010-07-17
Rsync compares the source and target directories every time it runs. The one thing it doesn't automagically do is remove files/directories that no longer exist in the source directory. 

I was looking for a file the other day, and found my backup directory contained over 180GB of data while my home directory only contained 80GB.

There is an rsync option to delete files/directories that no longer exist, but I would suggest you use it carefully.

---

### Post by koenn on 2010-07-17
> **Kimm said:**
> +1 This sounds exactly like what he is looking for, and its quite an elegant solution


thanks.
I've used that approach to keep track of changes in config files.
touch a file after OS setup, then 'find -newer' in ./etc -> copy those files : saves you the trouble of taking notes of what files you edited and why (tweaks, workarounds, customization), especially if you add comments to your changes.

---

### Post by oedipuss on 2010-07-17
You might also want to check out [rdiff-backup]("http://rdiff-backup.nongnu.org/") . It's in the repos and pretty much does incremental backups with very little tweaking.

---

### Post by neoargon on 2010-07-17
I will not buy an external drive soon and Iam going to write only to DVDs . Since the space in DVD is limited,once it is filled,I can't use it again.  So  I'll be using a fresh disk when I backup the next time . 
So the comparison of source and designation files won't work . That's why I thought of creating index file . Is there a way to create an index file ?

If the data to be backed up is larger than the size of a DVD , I'll have to write to multiple disks . That cannot also be done with a backup program

---

### Post by neoargon on 2010-07-17
Is there a command to list files (and the files in the subdirectories) inside a directory?

---

### Post by cariboo on 2010-07-18
> **neoargon said:**
> Is there a command to list files (and the files in the subdirectories) inside a directory?

Open a terminal and type man ls

---

