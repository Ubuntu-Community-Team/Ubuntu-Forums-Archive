---
title: "File server with NFS"
date: 2010-09-23
forum: Server Platforms
---

### Post by ozzyprv on 2010-09-23
Is there any way to implement NFS in this way:
folder1, owned by user1 (UID 1001), @server1
is accessed with rw privileges by two (or more) users
user2 (UID 1002) @clientA, and by
user3 (UID 1005) @cllientB ?

I want to set a file server that holds files accessible (rw) to several users at different clients.
I am having problems getting this to work with NFS....suggestions?

Thanks.

---

### Post by scrooge_74 on 2010-09-23
Maybe someone can correct me but Im pretty sure you should create the users in the server with same name as the users in the clients. That way they can write to their files.

Another way, but I havent try it is using LDAP to authenticate the users and owners of the files. <-- which I think is the correct way to go

Question: are the users only going to log from same PC always? Or they will be moving around ? That is important to know to get the right setup

---

### Post by SeijiSensei on 2010-09-23
Put the users into groups, then give the groups write privileges.

For instance, suppose user1 and user2 are both in the group "sharers". Now suppose user1 owns files in the exported share, /home/user1/sharedfiles, to which user2 needs access.  Then, in a Terminal, run

sudo chgrp sharers /home/user1/sharedfiles -R   
sudo chmod g+rwx /home/user1/sharedfiles
sudo chmod g+rw /home/user1/sharefiles/* -R

Now all the files in /home/user1/sharedfiles will be accessible to user2 because they're both in the same group which has write privileges to the share.

NFS just enforces normal *nix permissions.  Just make sure /etc/passwd and /etc/group are synchronized between the systems, or use a network authentication method like NIS or LDAP.

---

### Post by scrooge_74 on 2010-09-23
> **SeijiSensei said:**
> Put the users into groups, then give the groups write privileges.



Simple, but brilliant less work involved

+1

---

### Post by Lucky. on 2010-09-23
> Another way, but I havent try it is using LDAP to authenticate the users and owners of the files. <-- which I think is the correct way to go

I have been so curious as to how this works!  LDAP seemed way too confusing for me, so I went with NFSv4 and Kerberos.  Working beautifully, but now everybody tells me that I went way overboard and that NFSv4 is way more complicated than LDAP.

Gotta love open source, so many choices and so many opinions.

---

### Post by SeijiSensei on 2010-09-23
> **scrooge_74 said:**
> Simple, but brilliant less work involved

It's just standard Unix.  All the infrastructure to support users and groups has been in every Unix version since the 1970's.

> **Lucky. said:**
> LDAP seemed way too confusing for me, so I went with NFSv4 and Kerberos.  Working beautifully, but now everybody tells me that I went way overboard and that NFSv4 is way more complicated than LDAP.

I'm impressed you got Kerberos running.  I've taken a few stabs at OpenLDAP over the years, and it seems like a very difficult system to get running.  I've never tried setting up a Kerberos server, though, because neither I nor my clients have needed the whole cookie method that Kerberos entails.  Perhaps I should give it another look; it's always seemed like overkill in the types of environments in which I work.

Did you look into NIS?  Is Kerberos really easier to set up than that?

---

### Post by Lucky. on 2010-09-23
> I'm impressed you got Kerberos running. I've taken a few stabs at OpenLDAP over the years, and it seems like a very difficult system to get running. I've never tried setting up a Kerberos server, though, because neither I nor my clients have needed the whole cookie method that Kerberos entails. Perhaps I should give it another look; it's always seemed like overkill in the types of environments in which I work.

Did you look into NIS? Is Kerberos really easier to set up than that?

Thanks!

I never tried NIS.  I didn't know what I was doing, so I kind of worked backwards.  Instead of finding an authentication mechanism first, I was really just trying to get a secure network file share.  So I went Samba, then NFS, then SSHFS, then NFSv4 + Kerberos.  It really wasn't until I hit Kerberos that I realized "Hey wait, there's a big difference between authentication and resources, and people use this authentication for much more than just files."  Whoops.

---

### Post by ozzyprv on 2010-09-26
> **SeijiSensei said:**
> Put the users into groups, then give the groups write privileges.

Thank you all. I will give it a try setting the groups as suggested. I thought the UID had to be the same too. no?

---

### Post by SeijiSensei on 2010-09-26
> **ozzyprv said:**
> Thank you all. I will give it a try setting the groups as suggested. I thought the UID had to be the same too. no?

Yes, all the user and group IDs should be identical on the server and clients.  That's a reason for using a centalized network authentication method like LDAP or NIS.  However, you can also take the approach of synchronizing /etc/passwd, /etc/shadow, and /etc/group on all the machines.  I once had to do this for a particular network I supported and wrote this simple script for the purpose:

```

#!/bin/sh

# requires rsync and SSH shared key authentication 
# or rsync in daemon mode to run unassisted; 


# update files (0) or just go through the motions (1)
DEBUG=0

# work directory
WORK=/root/pwimport

# logging
LOG=/var/log/pwimport.log

# location of rsync
RSYNC=/usr/bin/rsync

# common password files here
SOURCE_HOST=myserver
# if using rsync daemon on server, enter name of share
#SOURCE_SHARE=etc

# send report here
MAILTO=me@example.com

###  END OF CONFIGURATION ###


# work in this directory
mkdir -p $WORK
cd $WORK


# initialize the log for this run
echo -n `date` >> $LOG
echo -n ": "   >> $LOG

# delete stale files from last run
rm -f *.old

MYSOURCE="$SOURCE_HOST:/etc"
[ "$SOURCE_SHARE" != "" ] && MYSOURCE="$SOURCE_HOST::$SOURCE_SHARE"

# get copies of the server's password files
$RSYNC -a "$MYSOURCE/passwd" .
$RSYNC -a "$MYSOURCE/group"  .
$RSYNC -a "$MYSOURCE/shadow" .

# exit     # enable to debug testing of transfer

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

# create unique local root entry on this host
mv -f shadow shadow.old
grep ^root /etc/shadow > shadow
grep -v ^root shadow.old >> shadow


[ $DEBUG == 1 ] && exit 1

# replace the old files in /etc
cd /etc
# quit if can't write to /etc
rm -f passwd-
cp -f passwd passwd-

if [ ! -s passwd- ]
then
    echo "No space left on device.   TERMINATING!" >> $LOG
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

exit 0

```

This code requires that rsync be installed and that the root user on all the machines have shared-key authentication via ssh.  An alternative is to configure rsync to run in daemon mode on the NFS server and export /etc as a share.  Then the rsync commands would replace "$SERVER:/etc" with "$SERVER::$SHARE" where SHARE is the name of the rsync share on the NFS server.  "man rsync" for details.  

Put this script in a directory in root's path (I prefer /usr/local/sbin), mark it executable by root with "chmod u+x name_of_script", then go to /etc/cron.hourly and create a symlink to the script.  It will then synchronize the password data once each hour.  If you need more frequent updates than that, you'll need to add a crontab entry in /var/spool/cron/root.

[NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") is pretty simple to set up and was designed by Sun to complement the original NFS protocol.  [Kerberos]("https://help.ubuntu.com/community/SettingUpNISHowTo") that Lucky uses is another alternative.

---

