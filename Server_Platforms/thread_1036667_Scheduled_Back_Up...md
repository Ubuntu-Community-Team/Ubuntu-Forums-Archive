---
title: "Scheduled Back Up..?"
date: 2009-01-11
forum: Server Platforms
---

### Post by narijayu on 2009-01-11
Ubuntu Rocks..!!! 

Hi guys..!! 

I have been working on ubuntu a couple of months.. I have installed  Vicidial (an open source call center solution) on 8.04 Server edition.. Its working pretty fine without any problem.. 

I am looking for a small help from you guys.

There is a folder /var/lib/asterisk/monitor/Done

Which saves all the recording files of calls.

Now what I want is that It should have a schedule backup by off hours so that It copies all the file to some other computer in network as (Which uses Ubuntu Desktop 7.10 or 8.04) and removes the file from the server... 

Guys Please Help me on this...

Regards & Thanks in advance..!!

Cheers..!!

---

### Post by btmiller on 2009-01-11
I'd suggest writing a simple shell script to copy the file to another machine, and then run it out off cron. The script could look something like this:

-- begin script --
#!/bin/sh

NOW=`date +%Y-%m-%d-%H:%m`
REMOTE_SERVER=your.servers.name
REMOTE_PATH=/directory/where/you/want/the/backup/call-backup-$NOW

# the mktemp command SECURELY creates a temporary file (or directory in this case)
TMPDIR=`mktemp -d` 

# the amin +1 in the find command only gets files accessed > 1 minute ago,
# to avoid trying to move file that are still being copied into the directory.
find /var/lib/asterisk/monitor/Done -amin +1 -exec mv {} $TMPDIR \;

# copy the backup directory, the user running this MUST be able to do a 
# passwordless scp!!!
scp -pr $TMPDIR ${REMOTE_SERVER}:${REMOTE_PATH}

# check exit status to make sure that the scp worked.
if [ "$?" -ne "0" ]; then
  echo "Failed to copy $TMPDIR !!!" > /tmp/errorlog
  mail -s "SCP BACKUP FAILED!!!" [email]your@email.addres[/email]s < /tmp/errorlog
else
  # all OK, remove the temp dir.
  rm -rf $TMPDIR
fi
-- end script --

You can set up ssh host keys so that the scp command can complete without requiring a password. You might want to use the -B flag to scp to put it into batch mode which won't ask for a password (it will just fail silently IIRC). You could also mount the backup directory via NFS and just do a regular copy of the file.

Fair warning: I haven't tested this script at all. So you should run it manually (and change the mv of the files to a cp just in case) to make sure it works. Once you're convinced it works OK, set up a cron job to run it (the user that runs it must have all appropriate permissions to do the moving and to use passwordless scp to the remote server). Reading the information in crontab(5) should help you set up the cron job.

---

### Post by ehorton on 2009-01-11
Another option might be to install sbackup.  I have used this program for some time.  It allows the ability to select include and exclude directories.  Should be standard in the repositories with sudo apt-get install sbackup

---

