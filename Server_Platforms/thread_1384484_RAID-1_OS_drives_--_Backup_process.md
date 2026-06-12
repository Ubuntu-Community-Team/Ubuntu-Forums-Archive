---
title: "RAID-1 OS drives -- Backup process"
date: 2010-01-18
forum: Server Platforms
---

### Post by joeinbend on 2010-01-18
Hi all,
Many of you know me from the RAID-5 arena, and I'm breaking into the OS drive side with RAID-1 now. I have my server set up with a pair of 80 GB drives, mirrored (RAID-1) and have been testing the fail-over and rebuild process. Works great physically failing out either drive. Great! My next quest is setting up a backup procedure for the OS drives, and I want to know how others are doing this.

Here's what I was thinking, and I'd love some feedback: Fail one of the disks out of the RAID-1, then image it to a file, saved on an external disk, using the dd command (if memory serves, it would be something like "sudo dd if=/dev/sda of=backupfilename.img")

Then, re-add the failed disk back into the array. In the event I needed to roll back to one of those snapshots, I would just use the "dd" command to dump the image back on to an appropriate hard disk, boot to it, and rebuild the RAID-1 from that. 

Does that sound like a good practice, or is there a better way?

A couple notes: I do not have the luxury of a stack of extra disks, so I cannot just do the standard mirror breaks and keep the disks on-hand, and using something like a tape drive is also not an option.

---

### Post by pirateghost on 2010-01-18
i absolutely love backuppc.... i run backups of my entire network every night.  all my servers (/etc /var /opt /home), personal files stored on the NAS, music directory, etc.  compression, de-duplication, ability to restore to other servers, specify days to restore files from....

---

### Post by joeinbend on 2010-01-18
Do you back up your OS drive? My concern is making sure that "live" mounted, operating data is properly backed up, which can be tricky, thus my idea of dismounting one of the mirrored disks in order to back it up. If I can just use backuppc that would be awesome!

---

### Post by pirateghost on 2010-01-18
> **joeinbend said:**
> Do you back up your OS drive? My concern is making sure that "live" mounted, operating data is properly backed up, which can be tricky, thus my idea of dismounting one of the mirrored disks in order to back it up. If I can just use backuppc that would be awesome!

i dont ever backup the full OS, just the parts i feel that i need to get a new system up and running quickly.  nearly all of my linux installs are in ESXi so i have a snapshot of the baseOS install and can very quickly revert to that, but vmware snapshots dont help when i screw up a config file and have to revert that one file back to last nights backup...

---

### Post by joeinbend on 2010-01-18
I'm with you there. In my case, This is my physical server, running Ubuntu 9.10 Server, with VMware Server on top. For the sake of quick recovery, it seems to me the quickest thing is to have a full backup of the drive, so i can quickly dump it to a disk to get it back online asap, or roll back to a previous state (sort of physical snapshotting) if something goes horribly wrong.

---

