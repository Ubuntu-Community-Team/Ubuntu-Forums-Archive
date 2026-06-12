---
title: "CIFS mounts, odd size limitation"
date: 2016-01-17
forum: Server Platforms
---

### Post by QIII on 2016-01-17
I recently upgraded my server from 12.04 to 14.04.  Now I have an odd problem I have never encountered before.

This share on the server, for instance

```
/dev/sdb1       932G   97M  932G   1% /mnt/Odin
```

which is an NTFS partition so that the Windows machines in the house can read it, is mounted as ntfs-3g on the server in /mnt.  (The issue that follows occurs if mounted at /media or a directory in my /home.)  There, the size is correctly reported.

I mount it on my desktop as cifs in fstab.

There, however,

```
df -h /mnt/Odin
```

gives

```
Filesystem                                              Size  Used Avail Use% Mounted on
/dev/disk/by-uuid/<uuid>                                 28G   16G   11G  62%   /
```


I can move files back and forth, so it is mounted.  But on the desktop the properties show the size of the share as 27.4GB with 10.2 free -- in fact this happens for all four of the 1TB drives on the server.  As a result, moving large file sets fails with the message that there is not enough space on the drive.

Using sshfs to mount the shares on my desktop, the sizes are correctly reported and I can move large file sets.

There have been no changes to fstab on either the desktop or the server, yet it worked perfectly well before upgrading the server to 14.04.

***Of Note:*** Mrs QIII's Windows 10 laptop has a local drive mapped to one of the drives (for her backups) and it still shows a capacity of 1TB.

Has anyone else encountered this using cifs?

---

### Post by bab1 on 2016-01-18
> **QIII said:**
> I recently upgraded my server from 12.04 to 14.04.  Now I have an odd problem I have never encountered before.

This share on the server, for instance

```
/dev/sdb1       932G   97M  932G   1% /mnt/Odin
```

which is an NTFS partition so that the Windows machines in the house can read it, is mounted as ntfs-3g on the server in /mnt.  

There is no reason for you to NTFS format a locally mounted partition on an Ubuntu Samba server.  The formatting is for the local OS, not for the remote mounting.  In fact the remote user always mounts the partition using SMB(CIFS) drivers (modules) on Windows or Linux hosts.  My best guess is that the ntfs-3g and CIFS modules are creating the porblem.
> 
...
Using sshfs to mount the shares on my desktop, the sizes are correctly reported and I can move large file sets.

This kind of confirms the above thought
> 
There have been no changes to fstab on either the desktop or the server, yet it worked perfectly well before upgrading the server to 14.04.

There have been minor changes in the NTFS-3g package, so this is more indication that you have a module issue.
> 

***Of Note:*** Mrs QIII's Windows 10 laptop has a local drive mapped to one of the drives (for her backups) and it still shows a capacity of 1TB.

Drive?  Partition?  What are we saying here?  In Windows speak a drive is what Linux users know as a partition.
> 
Has anyone else encountered this using cifs?
In the end I think your problems started with retaining the NTFS formatting on a locally mounted Linux system.  The remote mount also has some interaction.  So we have Ubuntu (Linux) to NTFS (2 versions) to CIFS.  Adding to that is the fact that the df command also makes assumptions about the parameters it is looking at.

I would not worry about what was (12.04) and focus on the new (14.04).  I would format any of your partitions that are mounting locally by Ubuntu as ext4.  Then your Samba install will present the shared parts as CIFS shares to be mounted on remote hosts.  The formatting (including permissions) do not follow across the network.  The remote CIFS mount sets that up.

---

### Post by darkod on 2016-01-18
+1 about not formatting local disks with ntfs. I was just discussing that on another thread where the OP similarly reason that "because windows clients use it, I thought it better be ntfs"... Which makes no sense of course because of accessing over samba anyway. On the contrary, I expect more issues compared to using linux filesystem made for linux permissions, etc...

---

### Post by QIII on 2016-01-18
> Drive? Partition? What are we saying here? In Windows speak a drive is what Linux users know as a partition.

Forgive me.  Yes, I am quite well aware of this.  I mixed my metaphors because I was going between her Windows machine (where you map a network *drive* -- Windows speak is, in fact, drive here) and the *partition* on the Linux server.  I think you could have dispensed with the lesson about terminology I have been using for decades.  Clearly an oversight.

---

### Post by bab1 on 2016-01-18
> **QIII said:**
> Forgive me.  Yes, I am quite well aware of this.  I mixed my metaphors because I was going between her Windows machine (where you map a network *drive*) and the partition on the Linux server.  I think you could have dispensed with the lesson about terminology I have been using for decades.
The clarification is for the others that will read this thread later on down the road.

---

### Post by QIII on 2016-01-19
After many years of dual-booting and mounting NTFS shares that way because the disks common to both OSes, in the interest of both being able to access them from both OSes, were mounted ntfs.  I had come under the misapprehension that this was the appropriate file system to use. But I dug out some old notes and examples only to have to kick myself for realizing that you are entirely correct and I ought to have known better.  That's exactly the point of cifs for a server. 

In any case, reformatting the partitions to ext4 *did not* solve the issue.  That turned out to be a red herring with regard to solving the immediate issue of reported/available space specifically.

However, removing password protection/group restrictions on the shares (whatever their file type) did.  Strangely, the remote machines were always able to mount the shares, but the reported sizes were wrong -- except in the case of Mrs. QIII's Windows machine.  Obviously it is far from a happy situation to have all the doors flung open so.

I'll keep fiddling with this.

---

### Post by bab1 on 2016-01-19
> **QIII said:**
> After many years of dual-booting and mounting NTFS shares that way because the disks common to both OSes, in the interest of both being able to access them from both OSes, were mounted ntfs.  I had come under the misapprehension that this was the appropriate file system to use. But I dug out some old notes and examples only to have to kick myself for realizing that you are entirely correct and I ought to have known better.  That's exactly the point of cifs for a server. 

In any case, reformatting the partitions to ext4 *did not* solve the issue.  That turned out to be a red herring with regard to solving the immediate issue of reported/available space specifically.

However, removing password protection/group restrictions on the shares (whatever their file type) did.  

Strangely, the remote machines were always able to mount the shares, but the reported sizes were wrong -- except in the case of Mrs. QIII's Windows machine.  Obviously it is far from a happy situation to have all the doors flung open so.

This is entirely possible with restrictive share permissions.  If *df or similar tools* can't see something, it can't report on it.  If I don't know how you have structured your shares, I can't comment on them either.  :-)
> 
I'll keep fiddling with this.
Want some help?

---

### Post by QIII on 2016-01-19
If there have been updates, the restrictions I had in place may no longer work as expected.

As for help, I think I'm on the right track now.  Time for me to sweat a bit.  That's usually my most effective way to truly learn stuff.

Thanks for waking a slumbering old man!

---

### Post by bab1 on 2016-01-19
> **QIII said:**
> If there have been updates, the restrictions I had in place may no longer work as expected.

As for help, I think I'm on the right track now.  Time for me to sweat a bit.  That's usually my most effective way to truly learn stuff.

Thanks for waking a slumbering old man!Good deal.  This old man needs to get some sleep after a long day.

If I may; Let me give you one rule of thumb I use for file sharing with Samba.  The username should be the same on both the Samba server and the remote host.  I make the Samba server file system the primary arbiter of the file system rights.  We are talking authorization here, not authentication.  Then the share can be simple with very few parameters.  PM me if you want.  I will gladly show you what I do.

---

### Post by QIII on 2016-01-19
Thanks for the offer, but PMing keeps the discussion away from the rest of the members.  

I'll post whatever resolution I come to here when (if?) I come to it.

I suspect that I have been doing something just slightly wrong all along with regard to authority and it finally bit me with recent changes.

This sounds like a good job for my Odroid so I don't mess up my server.

---

### Post by bab1 on 2016-01-19
> **QIII said:**
> Thanks for the offer, but PMing keeps the discussion away from the rest of the members.  

I'll post whatever resolution I come to here when (if?) I come to it.

I suspect that I have been doing something just slightly wrong all along with regard to authority and it finally bit me with recent changes.

This sounds like a good job for my Odroid so I don't mess up my server.
The PM was for your comfort.  If your Samba installation is for a standalone file server then the smb.conf file configures everything SMB wise.  Just make a backup copy before you do anything.  At the worst all you need to do to revert to the SMB config you have right now is to copy back the backup of the smb.conf file and restart the smbd daemon.

The file system can be tested out on by creating a test file system branch (maybe something like /srv/test).

---

