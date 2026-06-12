---
title: "HOWTO: Backup with rsync, just like I do."
date: 2007-01-23
forum: Server Platforms
---

### Post by Underpants on 2007-01-23
I figured I'd share a shell script that I just got finished tweaking. Should help out those to wish to perform incremental backups of their system. You should know how to create a shell script and make it executable. For this to run you'll need to run it as root, so "$ sudo ./backup.sh"

It's laid out pretty basic. I stole the script from oreilly.com but have edited to simplify it so it looks pretty in a text editor. You can easily add more increments in step 2 if you need. You can also easily change the source and destination to fit your needs. (such as only needing to back up your personal /home folder)

My goal here isn't to explain how any of it works. I figured it out all by myself. I've changed it so anyone else should be able to look at it and easily use a man page or a --help to figure out what's going on pretty easily.

I believe there is an issue with timestamps using this method, so I think just to do things "right" someone needs to add a 'touch' section to the end that keeps things tidy. It doesn't bother me for this box, but if anyone would like to contribute.... 

```

# rotating snapshots of /home
# step 1: delete the oldest snapshot, if it exists:
if [ -d /media/usbdisk/hourly.3 ] ; then rm -rf /media/usbdisk/hourly.3 ; fi;

# step 2: shift the middle snapshots(s) back by one, if they exist
if [ -d /media/usbdisk/hourly.2 ] ; then mv /media/usbdisk/hourly.2 /media/usbdisk/hourly.3 ; fi;
if [ -d /media/usbdisk/hourly.1 ] ; then mv /media/usbdisk/hourly.1 /media/usbdisk/hourly.2 ; fi;


# step 3: make a hard-link-only (except for dirs) copy of the latest snapshot, if that exists

if [ -d /media/usbdisk/hourly.0 ] ; then cp -al /media/usbdisk/hourly.0 /media/usbdisk/hourly.1 ; fi;

# step 4: rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first. If it were not so, this would copy over the other
# snapshot(s) too!


rsync -vax --delete --delete-excluded --exclude-from="/home/aaron/.backup_exclude" / /media/usbdisk/hourly.0 ;



```

---

### Post by elst on 2007-01-24
Check out rdiff-backup, it uses (lib)rsync under the bonnet, with compressed deltas to store as many versions of files as you need without multiplying the storage space required. pyBackpack provides a graphical interface for it (if you want one). Like rsync, rdiff-backup can use SSH to work over network connections.

---

### Post by MJN on 2007-01-24
Given how cheap storage it I don't see any advantage in compressing backups. Indeed I'd prefer them to be as close a copy (identical) to the original as possible, not least given the problems associated with a small corruption of a compressed file having disproportional damaging effects on the contents.

I also want the backups to be as simple as possible to reconstruct, and not having to necessarily rely on the tool that made the backup. Having been through a couple of system restorations now it's relative bliss to have what is effectively an identical copy (in all senses of the word) of the system being backed up - good to physically swap directly in with the minimum of tweaking required.

Horses for courses of course, but my course calls for nothing more than rsync! ;)

Mathew

---

### Post by elst on 2007-01-24
rdiff-backup does something interesting in this respect - the latest version is stored as-is, complete and uncompressed, whilst previous versions are rendered into compressed diffs. So you keep the ability to just grab a file out of a directory, whilst gaining the facility to retrieve previous versions as well.

I've recently been experimenting with using Subversion to provide backup and versioning for my stuff instead, and do miss the reassurance of being able to look in a directory and see all of my files there, so I know what you mean.

---

### Post by MJN on 2007-01-25
Ah, that sounds good then. If the latest backup is a full untouched version then the historical files are obviously a bonus on what I've currently got. Will check it out!
 
Mathew

---

### Post by kosmic on 2007-01-25
Why dont you keep the file permisions when doing the backup (using --perms) ??

---

### Post by MJN on 2007-01-26
The -a archive flag implies the -p option (equivalent to -rlptgoD).
 
Mathew

---

