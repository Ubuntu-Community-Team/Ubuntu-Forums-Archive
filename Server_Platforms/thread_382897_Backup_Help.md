---
title: "Backup Help"
date: 2007-03-12
forum: Server Platforms
---

### Post by cyris| on 2007-03-12
Hey everyone,

I have a few directories (which use extended acls) that need backup daily 

/usr/file_manager
/home

can someone recommend an application that would make backups easy ? gui would be nice but anything will work.

tar doesn't backup extended acls so thats out of the question :S

---

### Post by gostek_1 on 2007-03-13
You can try to avoid using acl, but if you need to you can use your favorite archiver and backup acl's using getfacl.
i.e. you try to backup a /home to /mnt/bakups/
you tar /home to /mnt/backups/home_date.tar
and then you do something like this:
getfacl --skip-base --absolute-names -R /home > /mnt/bakups/home_acls_date
 if you need to restore an archive you use tar or whatever and do something like this:
setfacl --restore /mnt/backups_home_acls_date

This method gives you an option to archive files an acls into diferent files. If you have loads of acls you can gzip the acls backup file

---

### Post by cyris| on 2007-03-13
Hey, thanks for your reply.

Unfortunately we need to use ACL's so just not using them is not an option :D

Redirecting the output of getfacl to a ascii file and restoring it is an awesome idea, however I'm hoping theres at least a CLI tool available or something with tar that will just automatically back up my extended acls.

Anyone know?

---

### Post by Mr. C. on 2007-03-13
I thnk there is an "star" somewhere.  Search google for this.

MrC

---

### Post by cyris| on 2007-03-14
I'm sorry, what do you mean by "star" ?

---

### Post by Mr. C. on 2007-03-14
Sorry, it is s tar, a version of tar that claims to handle ACLs.

[http://cdrecord.berlios.de/old/private/star.html](http://cdrecord.berlios.de/old/private/star.html)
[http://www.vanemery.com/Linux/ACL/star-acl-readme.txt](http://www.vanemery.com/Linux/ACL/star-acl-readme.txt)

MrC

---

### Post by rplantz on 2007-03-14
There is a discussion here
[http://michael-prokop.at/blog/2007/01/12/rsync-and-access-control-lists/](http://michael-prokop.at/blog/2007/01/12/rsync-and-access-control-lists/)
of a Debian Etch version of rsync that supports extended ACLs.

I have a script that uses rsync to make snapshots. Let me know if you would like to see a copy.

---

### Post by cyris| on 2007-03-14
Mr. C and rplantz thanks for your posts!

rplantz yes please post your script.

---

### Post by rplantz on 2007-03-14
First, I'm a newbie at scripting. So please check this for errors, crummy code, etc. It gives an error message, but I haven't bothered to figure it out. Please feel free to "plagiarize" my code as you wish, but I would appreciate your sharing any critique with us. :)

Second, notice that I've adapted this from another person. It's been a year, but as I recall, he had a lot of useful information on his site. I ran across it when I was helping a friend develop a backup scheme for several Macintoshes. It turns out that there were some real problems with the rsync that was shipped with OS X. I don't know if they have been worked out.

This has worked well on my Ubuntu system. It simply backs up to an external usb disk. Notice that it uses hardlinks to the previous snapshot to save time. The first backup takes a while, but subsequent are much shorter, depending on how many changes you've made. 
```

#!/bin/bash
# ----------------------------------------------------------------------
# Adapted from mike's handy rotating-filesystem-snapshot utility
# www.mikerubel.org/computers/rsync_snapshots/
# 
# by: Robert Plantz - 20 April 2006
#     Cleaned up and added comments - 20 March 2007
# ----------------------------------------------------------------------

# ------------- file locations -----------------------------------------
# Assume that the destination volume is mounted. I use an external
# usb disk that mounts automatically when plugged in.
DESTINATION=/media/usbdisk
# Default is to backup my home directory. Other files and
# directories excluded or included are listed in this file.
# See "FILTER RULES" and "INCLUDE/EXCLUDE PATTERN RULES"
# sections in the rsync man page for the format of this file.
SOURCE=/home/bob
EXCLUDES=backup_exclude
# make sure user did "sudo"
if (( `id -u` != 0 )); then
   echo "Sorry, you must run this script with sudo.  Exiting..."; exit;
fi

# If a temporary snapshot exists, delete it, then
# shift the snapshots(s) back by one, if they exist
if [ -d $DESTINATION/ubun.tmp ] ; then
   sudo rm -rf $DESTINATION/ubun.tmp
   echo "Deleted ubun.tmp"
fi
 
if [ -d $DESTINATION/ubun.3 ] ; then
   sudo mv $DESTINATION/ubun.3 $DESTINATION/ubun.tmp
   echo "Created ubun.tmp"
fi

if [ -d $DESTINATION/ubun.2 ] ; then
   sudo mv $DESTINATION/ubun.2 $DESTINATION/ubun.3
   echo "Created ubun.3"
fi

if [ -d $DESTINATION/ubun.1 ] ; then
   sudo mv $DESTINATION/ubun.1 $DESTINATION/ubun.2
   echo "Created ubun.2"
fi

if [ -d $DESTINATION/ubun.0 ] ; then
   sudo mv $DESTINATION/ubun.0 $DESTINATION/ubun.1
   echo "Created ubun.1"
fi

# rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
# See rsync man page for options. The time saver here is
# --link-dest. If a file has not changed from the copy in
# the specified directory, a hard link is created to the
# already existing copy rather than recopy the entire file.
# This saves both time and disk space.
if [ -d $DESTINATION/ubun.1 ] ; then
   echo "Creating ubun.0 based on ubun.1 on $DESTINATION"
   sudo time rsync -o -g -v -a --delete    \
        --exclude-from=$EXCLUDES           \
        --link-dest=$DESTINATION/ubun.1    \
        $SOURCE $DESTINATION/ubun.0/
else
   echo "Creating a new ubun.0 on $DESTINATION"
   sudo time rsync -o -g -v -a --delete    \
        --exclude-from=$EXCLUDES           \
        $SOURCE $DESTINATION/ubun.0/
fi
echo "rsync exit code is "$?
# update the mtime of ubun.0 to reflect the snapshot time
touch $DESTINATION/ubun.0

```

---

### Post by cyris| on 2007-03-15
Thanks for posting your script. 

I'm not that great at creating scripts either but I get the job done. You seem to know what your doing :D

Can you help me out in writing my own as I don't think mine needs to be as complicated as yours 

All I'm looking to do is to do a full backup once a week, but do daily snap-shot-like backups with rsync.

Your script kinda blows my mind away so I'm not learning anything from it haha...

Thanks

---

### Post by rplantz on 2007-03-20
> **cyris| said:**
> 
Can you help me out in writing my own as I don't think mine needs to be as complicated as yours

All I'm looking to do is to do a full backup once a week, but do daily snap-shot-like backups with rsync.

Your script kinda blows my mind away so I'm not learning anything from it haha...

Thanks
I fixed a couple of errors in my script and made the changes in my post above. I added some comments, hoping this will help your understanding.

It still creates the new snapshot with "root" as owner and group. But you can still access all the files, so it works.

Regarding "full backup," people take that to mean different things. I imagine that you want basically a copy of your entire disk when you do a "full backup." I sorta figured that if something happened that I needed to restore my entire disk, I would do it from a fresh install.

---

