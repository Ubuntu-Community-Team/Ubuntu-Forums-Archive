---
title: "Web Server Backups"
date: 2013-03-13
forum: Server Platforms
---

### Post by Jonny87 on 2013-03-13
The Server in question is actually my friends CentOS Web server. But as I'm not apart of the CentOS forums as I don't use it, I thought I'd ask here.

My question is; What backup methods or software do people recommend for backing up a Web Hosting Server? It needs to be easy to restore either individual files and the full backup. And also be able to backup to a local network share.

In the past I have always used tar as explained in [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) and have had no trouble with it, I now currently use Deja-dup on my own personal desktop. However I want to know is this still a good valid method for a web server? or can someone suggest something better. I'd like to be able to do occasional full backups as well as on going incremental backups.

---

### Post by SeijiSensei on 2013-03-13
I use rsync to transfer the web directories to an offsite machine, and a script that runs pg_dump to back up my PostgreSQL databases to text files.  I then suck those over with rsync as well.

Tar is fine, but you need to untar to archive if you want to restore a specific file.

If you want to have rotations, then you'd need to write a script that creates a new directory each day and copies that day's snapshot to the backup server with rsync.

---

### Post by Jonny87 on 2013-03-13
I had thought about using rsync. how do you get rsync to copy to another dir for each day and only copy the updated file instead of everything? 

Also you mentioned that you ran a seperate script for you SQL databases, is that needed to back them up or do you just preffer it? Would it work for MYSQL?

---

### Post by SeijiSensei on 2013-03-15
Backing up a MySQL or PostgreSQL database works best if you use their respective "dump" programs to create a plain-text version of the database.  I posted a script for MySQL [here](http://ubuntuforums.org/showthread.php?t=1580676&p=9882114&viewfull=1#post9882114).  If you read the code in that script, you'll see how I created date-named backup files.  For directories, you could use something like:

```

TODAY=$(date +%Y%m%d)
STALE=$(date +%Y%m%d --date='8 days ago')
cd /path/to/backup/directory
rmdir $STALE
mkdir $TODAY
cd $TODAY
rsync -av ...

```

---

### Post by Jonny87 on 2013-03-15
> **SeijiSensei said:**
> Backing up a MySQL or PostgreSQL database works best if you use their respective "dump" programs to create a plain-text version of the database.  I posted a script for MySQL [here]("http://ubuntuforums.org/showthread.php?t=1580676&p=9882114&viewfull=1#post9882114").  If you read the code in that script, you'll see how I created date-named backup files.  For directories, you could use something like:

```

TODAY=$(date +%Y%m%d)
STALE=$(date +%Y%m%d --date='8 days ago')
cd /path/to/backup/directory
rmdir $STALE
mkdir $TODAY
cd $TODAY
rsync -av ...

```

Thank you, I'm familiar with creating dirs in that method, though what I want to know is it possible to have rsync only copy the new and updated files into that days folder? Wont that create a full copy in to the TODAY folder? 
I'd like to try and save space and only copy the files that are new or modified since the first rsync.
Something like this;

/backups/20130301/[INDENT]File-One
File-Two
File-Three
File-Four
File-Five
[/INDENT]

/backups/20130302/
[INDENT]File-Four
[/INDENT]

/backups/20130303/
[INDENT]File-Three
File-Five
[/INDENT]

Does this make sense? Is this possible or will rsync only do a full copy if it's into a new dir?

---

### Post by CharlesA on 2013-03-16
> **SeijiSensei said:**
> I use rsync to transfer the web directories to an offsite machine, and a script that runs pg_dump to back up my PostgreSQL databases to text files.  I then suck those over with rsync as well.

Tar is fine, but you need to untar to archive if you want to restore a specific file.

If you want to have rotations, then you'd need to write a script that creates a new directory each day and copies that day's snapshot to the backup server with rsync.

Seconding this as it is what I use (or used) when my site was getting updated frequently.

I have used cp -al and rsync -ai to create incremental backups of my files on my server. I don't see why that couldn't work for a web server.

EDIT: Thanks for posting the date +%Y%m%d --date='8 days ago' command. I didn't know date could do that and it'll save me from going thru my backups and deleting stuff that is older than 6 months.

---

### Post by SeijiSensei on 2013-03-16
> **Jonny87 said:**
> Thank you, I'm familiar with creating dirs in that method, though what I want to know is it possible to have rsync only copy the new and updated files into that days folder? Wont that create a full copy in to the TODAY folder? 

No, as the name says it's designed to synchronize two directory trees.  If you want to do incremental backups, one possibility is to identify each day's files with the "find" command using the "-anewer" option to identify files more recent than a baseline file.  I used this in the past where I'd write a tarball each night based on identifying files newer than the previous night's tarball.  See "man find" for more details.

> **CharlesA said:**
> EDIT: Thanks for posting the date +%Y%m%d --date='8 days ago' command. I didn't know date could do that and it'll save me from going thru my backups and deleting stuff that is older than 6 months.

The --date option is remarkably flexible and is able to parse all sorts of human-readable date specifications like "days ago".

---

### Post by chrisguk on 2013-03-16
I know this is probably a late for a reply, I always use bacula.  Some may say its a bit of an over kill but if you spend the time to figure how to configure it then it will serve you well.  For MySQL dumps I wrote my own script when I let the crontab take care of.  So at least for MySQL I have 30 days worth of backups to use just in case.

There are literally tonnes of options for backing up a server/web server and mostly its personal preference, depending on how much time you want to invest in the configuration.

For my web server, mainly because the content is so valuable, I backup to an external device and an offsite cloud just in case.  The main server backup just sits on an external device.  Plus of course because I run everything inside ESXi I have all my VMs backup anyway to a Flash drive.

---

### Post by Jonny87 on 2013-03-16
Thanks every one for your input.

If I use tar, do i need to have a script to do the MYSQL dumps a some have said they do? or will tar still backup the MYSQL side of things fine? 

This my current plan;

> / >> Root.tar
/home >> Home.tar
    Create a uncompressed tar of / and /home have it updated on a daily bases. This keeps an up to date backup that can be easily and quickly restored. Also allowing single file      extraction.
    Or possibly rsync for this stage.

> Root.tar >> /Archives/Root/$DATE.tar.bz2
Home.tar >> /Archives/Home/$DATE.tar.bz2
    After the updates are complete, then create a compressed copy of the updated tar so that there is a backup for each day. Will also look at using date to remove older archives as suggested above.

I don't suppose anyone knows how to use that date option to create a pattern of something like,
> Keep all for the last 7 days,
Keep one per week for the last 4 weeks,
Keep one per month for the last 24 months,
Keep one per years for all years.
This would give my friend some flexibility to back date to almost any point in time if needed. This ofcourse will all depend on how much space he wants to dedicate to Backups.

What are peoples thoughts on this? I have plenty of experience writing tar backup scripts for my own personal computers, but not for a web server, looking for advice from those with experience in this field.

---

### Post by chrisguk on 2013-03-16
Hi,

The things that you are asking for with date labelled backup scripts etc are fairly easy to do with a simple bash script.  I wrote one for my own use but it can be adapted within any buntu environment.  I'm living in Germany and I'm yet to sleep so if you can wait ill send you a link to the script I wrote to carry out this task. Btw you will also need to have a crontab script too but I'll bundle that for you too.  Hope that helps

---

### Post by Jonny87 on 2013-03-16
Thanks, that would be real handy. Year I was already aware that it will need to be setup in crontab. Waiting for my mate to get back to me on final details though i.e location of backup server share, How often he wants it to run, how many he wants to keep etc.

He wants to set it up around the end of the month sometime but I'm just getting the script ready now so I can just upload it and set it to run. 

It's is server and his web hosting company, I'm just his Linux "Expert" Consultant/Assistant as he doesn't really know Linux and I do. I've already helped him migrate the server form the Windows to Linux as he was having issues with Apache on Windows. Its been fine since the migration. And recently I've been pushing him to make sure he gets a backup system in place, I offered to set up a script if he wanted. 
He hosts my site for free so I work for him in return.

---

### Post by SeijiSensei on 2013-03-17
If you want to preserve a backup, just do a test of the day of the week or month and skip the deletion step if it matches the criterion.  For instance

```

if [ "$(date +%w)" != "0" ]
then
    rm -f /path/to/backups/somefile.tgz
fi

```

That skips the deletion on Sundays when "date %w" returns zero.

---

### Post by Jonny87 on 2013-03-17
> **SeijiSensei said:**
> Backing up a MySQL or PostgreSQL database works best if you use their respective "dump" programs to create a plain-text version of the database.  I posted a script for MySQL [here]("http://ubuntuforums.org/showthread.php?t=1580676&p=9882114&viewfull=1#post9882114").  If you read the code in that script, you'll see how I created date-named backup files.  For directories, you could use something like:

```

TODAY=$(date +%Y%m%d)
STALE=$(date +%Y%m%d --date='8 days ago')
cd /path/to/backup/directory
rmdir $STALE
mkdir $TODAY
cd $TODAY
rsync -av ...

```

OK, so with;
```
STALE=$(date +%Y%m%d --date='8 days ago')
```
could that be applied with months or years, i.e.
```
STALE=$(date +%Y%m%d --date='8 months ago')
```

---

### Post by SeijiSensei on 2013-03-17
Yes.  From the "man" page for date:
> The --date=STRING is a mostly free format human readable date string such as "Sun, 29 Feb 2004 16:21:42 -0800" or "2004-02-29 16:21:42" or even "next Thursday". A date string may contain items indicating calendar date, time of day, time zone, day of week, relative time, relative date, and numbers. An empty string indicates the beginning of the day. The date string format is more complex than is easily documented here but is fully described in the info documentation.

Might I suggest experimentation as a method for answering questions like this? 
```

$ date --date='8 months ago'
Tue Jul 17 09:17:11 EDT 2012

```

---

### Post by CharlesA on 2013-03-17
> **SeijiSensei said:**
> Yes.  From the "man" page for date:


Might I suggest experimentation as a method for answering questions like this? 
```

$ date --date='8 months ago'
Tue Jul 17 09:17:11 EDT 2012

```

+1. I did that as soon as I saw you could mess with the date like that.

---

### Post by Jonny87 on 2013-03-17
> **SeijiSensei said:**
> Yes.  From the "man" page for date:


Might I suggest experimentation as a method for answering questions like this? 
```

$ date --date='8 months ago'
Tue Jul 17 09:17:11 EDT 2012

```

Yes sorry I should have thought to experiment around with it like that.

---

### Post by Jonny87 on 2013-04-03
So this is what I have so far, I'm yet to get the full address of backup location from my friend so I have it represented by * for the time being.

```
#! /bin/sh

## Things to do first
##    mkdir */RootAchives
##    mkdir */HomeAchives
##    mkdir */Logs
##    mkdir */Logs/Root
##    mkdir */Logs/Home


#+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
# VARIABLE PATHS


DATE="`date +%d/%m/%Y`"
ROOT="**/UpdatingRootBackup"
HOME="**/UpdatingHomeBackup"
ROOT_ARCH="**/RootAchives/$DATE"
HOME_ARCH="**/HomeAchives/$DATE"
SRC_ROOT="/"
SRC_HOME="/home"
LAST_ROOT="**/LastRootUpdate"
LAST_HOME="**/LastHomeUpdate"
ROOT_LOGS="**/Logs/Root/$DATE.txt"
HOME_LOGS="**/Logs/Home/$DATE.txt"
STALE=$(date +%Y%m%d --date='8 days ago')


#+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


#======================================================================================================
# ROOT
#Change Backup Dir Name.
mv $LAST_ROOT $ROOT 


#Back up the root drive.
rsync -rtpogvuzs --progress --delete --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home --exclude=/media $SRC_ROOT $ROOT | cat > $ROOT_LOGS 


#Archive the Root Update.
tar -cvpjf  $ROOT_ARCH $ROOT


#Change Update Dir Name
mv $ROOT $LAST_ROOT


#======================================================================================================
# HOME


#Change Backup Dir Name.
mv $LAST_HOME $HOME 


#Back up the home drive
rsync -rtpogvuzs --progress --delete  $SRC_HOME $HOME | cat > $HOME_LOGS


#Archive the Root Update.
tar -cvpjf  $HOME_ARCH $HOME


#Change Update Dir Name
mv $HOME $LAST_HOME


#======================================================================================================
# Remove Old Backups


rm **/RootArchives/$STALE
rm **/HomeAchives/$STALE
```
Can any one see anything wrong with this backup process? Does anyone have any further suggestions?

---

### Post by spynappels on 2013-04-04
You might also look at rdiff-backup, it uses rsync but allows incremental backups and restore from a point in time.

---

### Post by Jonny87 on 2013-04-04
Yea I had thought about that. I might still go with that.[COLOR=#000000]
[/COLOR]

---

### Post by pedor on 2013-04-04
I use and recommended [http://www.rsnapshot.org/](http://www.rsnapshot.org/) . rsnapshot is a complete rsync backup solution and i very easy to restore

---

### Post by Jonny87 on 2013-04-04
OK so I tried the script on the server last night and it came back with permission issues. An yes I made sure the perms on the share were open for writing, 777 in fact. But when I ran the script, rsync ran but came back with permission denied. When I check the perms again the backup folded used in the script still have the correct perms but the ones copied by rsync were 
> drw - -
I'm wondering if it's to do with the mounting of the samba share. I'm using the following command to mount the share;
> mount -t cifs //192.168.1.60/Backups /mnt/Backups -o user=****,password=*******

Is there anything that anyone can see thats wrong? Its been a while since I've dealt with mounting samba shares via CLI.

---

### Post by SeijiSensei on 2013-04-04
What are the ownership and permissions on /mnt/Backup before the mount occurs?  How about afterwards? 

I'd do everything as root, with /mnt/Backup owned by root:root with 755 permissions.

However your original post said this was a CentOS server.  Why are you using Samba?  Rsync will copy files without having the remote server be mounted at all.  If you do want to mount a share on a remote running Linux, use NFS.  it will be faster, and all the *nix permissions will be preserved.  If NFS seems daunting, then use sshfs.  A quick Google search will bring up documentation for both these options.

---

### Post by Jonny87 on 2013-04-04
I went with samba because it's what I know best. I was thinking I sould go with one of those other methods. What would be best? nfs or sshfs?

---

### Post by CharlesA on 2013-04-04
Go with NFS if you can handle it, otherwise just do sshfs.

---

### Post by spynappels on 2013-04-05
I'd go for NFS too, here is the Ubuntu Community Documentation:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Ask away if you have specific questions.

---

### Post by Jonny87 on 2013-04-14
The following is the final copy that I have started running;
```
#! /bin/sh

## Things to do first


# mount Share
sudo mount -t nfs 192.168.1.60:/Backups /mnt/Backups


#+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
# VARIABLE PATHS


DATE="`date +%d%m%Y`"
ROOT="/mnt/Backups/UpdatingRootBackup"
HOME="/mnt/Backups/UpdatingHomeBackup"
ROOT_ARCH="/mnt/Backups/RootAchives/$DATE"
HOME_ARCH="/mnt/Backups/HomeAchives/$DATE"
SRC_ROOT="/"
SRC_HOME="/home"
LAST_ROOT="/mnt/Backups/LastRootUpdate"
LAST_HOME="/mnt/Backups/LastHomeUpdate"
ROOT_LOGS="/mnt/Backups/Logs/Root/$DATE.txt"
HOME_LOGS="/mnt/Backups/Logs/Home/$DATE.txt"
STALE=$(date +%Y%m%d --date='8 days ago')


#+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


#======================================================================================================
# ROOT
#Change Backup Dir Name.
mv $LAST_ROOT $ROOT 


#Back up the root drive.
rdiff-backup --force --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home --exclude=/media $SRC_ROOT $ROOT | cat > $ROOT_LOGS 


#Archive the Root Update.
tar -cvpjf  $ROOT_ARCH $ROOT


#Change Update Dir Name
mv $ROOT $LAST_ROOT


#======================================================================================================
# HOME


#Change Backup Dir Name.
mv $LAST_HOME $HOME 


#Back up the home drive
rdiff-backup --force $SRC_HOME $HOME | cat > $HOME_LOGS


#Archive the Root Update.
tar -cvpjf  $HOME_ARCH $HOME


#Change Update Dir Name
mv $HOME $LAST_HOME


#======================================================================================================
# Remove Old Backups


rm /mnt/Backups/RootArchives/$STALE
rm /mnt/Backups/HomeAchives/$STALE


# unmount share 
umount /mnt/Backups
```

Can anyone see anything wrong with it? or are there going to be any issues to restore it any of it?

---

### Post by CharlesA on 2013-04-14
Looks good. The only thing I'd change would be the capitalization of the variables. System variables are capitalized, but it isn't that big of a deal if the script works fine.

See here:
[http://stackoverflow.com/questions/673055/correct-bash-and-shell-script-variable-capitalization](http://stackoverflow.com/questions/673055/correct-bash-and-shell-script-variable-capitalization)

---

### Post by Jonny87 on 2013-04-14
> **CharlesA said:**
> Looks good. The only thing I'd change would be the capitalization of the variables. System variables are capitalized, but it isn't that big of a deal if the script works fine.

See here:
[http://stackoverflow.com/questions/673055/correct-bash-and-shell-script-variable-capitalization](http://stackoverflow.com/questions/673055/correct-bash-and-shell-script-variable-capitalization)

Thanks CharlesA, I'll keep that in mind. I have seen other script where people had used uppercase and thought that perhaps that was the proper way of doing it. Thanks for letting me know.

---

