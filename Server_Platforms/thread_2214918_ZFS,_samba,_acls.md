---
title: "ZFS, samba, acls"
date: 2014-04-03
forum: Server Platforms
---

### Post by frankerooney on 2014-04-03
Hi. I'm not sure if this is very ambitious or has already been done. 
I want to create a file server to serve a windows only environment based on Samba. It needs to have volume shadow copies, which I believe can be easily done in either lvm, btrfs or zfs (maybe more), but also windows full acl support. This works fine with the acl_xattr vfs module but I've read that it's not quite that straightforward if using, for example, ZFS. There's a thread here on acls :
[https://github.com/zfsonlinux/zfs/issues/170](https://github.com/zfsonlinux/zfs/issues/170)
At the end, a patch has been submitted - does this mean that it should work, has anyone experience with it, and what samba vfs module should I use, and what zfs settings should I set (if using zfs). 
OR should I use btrfs? I'm not sure if it's still considered experimental, and that would make me nervous with 5000 people's files (work in a hospital).

The reasoning behind zfs / btrfs is that it's still rather hard, in my estimation, to extend the size of an lvm volume group - you can extend the partition of a physical disk underneath and create another partition, then add to the PV and VG, but it seems more tricky than even a basic resize of a native ext4 partition using fdisk, partprobe and resize2fs - but then I can't do snapshots!

Anyway, any thought gratefully accepted!
Andy

---

### Post by nerdtron on 2014-04-03
Maybe you can specify more of your requirements and then we can think of the possible architecture alternatives.
Why do you need ACLs?
Shadow copies means snapshots right?
How do the 5000 people access their files?

---

### Post by frankerooney on 2014-04-04
Hi,
  So the 5000 people access their files via smb at the moment - a mixture of people's office documents, some server backups, windows roaming profiles and so on.
I want to replace an aging windows 2008 storage server we are having issues with, either with another windows box (not keen because we have quite a few issues with performance and the OS being 2008 (not R2).
The easiest thing would be to move to 2012 but since MS axed storage server, we need cals for everyone even just to access their files - £15 * 5000 isn't a small amount.
So on windows we use volume shadow copies (previous versions) to get back recent files, then retrieve any older stuff from the equallogic sans we have via it's replication or snapshotting which is a longer process.
I wanted to set up a Samba server that would do the same job, and support full windows acls - some of our departmental level shares are very complicated in terms of acls and posix acls just wouldn't work.
At the moment with an ext4 file system this means using the acl_xattr or acl_tdb modules, which is fine, but quite a common occurrence is that we need to extend the volumes as things get bigger, with windows it's very easy in the disk management snap-in and we'd need it to be as easy in ubuntu, which it can be, but the snapshot requirements complicate things meaning we need to use lvm to get the snapshot. The tricky thing then is that giving more partition space to an lvm volume group isn't as easy as just extending a flat file system, you need to create another parition in the extra free space and then tie it to the VG. It just seems messier than it needs to be.
So .. I was looking at other file systems that can do in-volume snapshots, resize on the fly without an lvm type system and that hopefully support the extended windows acls we require. ZFS seems to fit in terms of it's flexibility as a file system but I'm not sure if the support for samba is quite as good in terms of acl support. The thread I posted seemed to indicate it might be ok now but it's not clear how i would go about settings it up.
Then, btrfs - is experimental. Perhaps not the best for a production system..
and the other alternative is using BSD I guess.
Any ideas?!
Thanks

---

### Post by lukeiamyourfather on 2014-04-04
ZFS on Linux would fit the bill. It supports POSIX ACLs, is easily expandable, copy on write so it has snapshots (can be configured to work as shadow copies), and is stable.

---

### Post by frankerooney on 2014-04-04
Ok.. I'm with it on most of the points .. but it doesn't (afaik) support full windows acls via filesystem attrs .. or does it?
I definitely need more than posix acls, which are just not going to fit the bill.

---

### Post by bab1 on 2014-04-04
> **frankerooney said:**
> Ok.. I'm with it on most of the points .. but it doesn't (afaik) support full windows acls via filesystem attrs .. or does it?
I definitely need more than posix acls, which are just not going to fit the bill.

Window's style ACL's are supported by both EXT and ZFS.  ZFS and LVM provide the ability for shadow copies.  Both of these are directly addressed by Samba VFS modules.  In other words both the FS's have the ability to respond to these Windows features because Samba provides them.  You can use LVM for the same reason.  LVM/EXT is the same concept as ZFS.  LVM provides the partition abstraction and EXT provides the FS.  ZFS provides both the partition and the FS.  Both understand Samba VFS modules.

See [here]("http://www.edplese.com/samba-with-zfs.html") for ZFS and Samba VFS. 
 See [here]("https://wiki.samba.org/index.php/Rotating_LVM_snapshots_for_shadow_copy") for LVM and shadow copies.  
See [here]("https://www.google.com/search?q=samba+shadow+volume&btnG=Go!#q=samba+shadow+copies") for general Samba shadow copy information.

---

### Post by frankerooney on 2014-04-05
ZFS looks good but I'd read that on linux it didn't have the extended filesystem attributes needed for complete acl support. I did read something about a setting "zfs set xattr=sa" but it's certainly not widely documented and one post cited issues with corruption.
I'm not willing to use acl_tdb, which is theory should work with any filesystem, just because this thing needs to scale.
I have also looked at maybe doing a cluster with cdtb, but am unclear whether it strictly needs a clustered filesystem underneath, or whether I could just use the cdtb to manage the cluster locking and export an iscsi san volume to all of the nodes. Surely if samba is doing the file locking, then there shouldn't be any issues there?
Anyway, I looked at ceph (seems to have poor performance), ocfs2 (snapshots are only at file level, designed for vms rather than cifs, where I'd want to export a whole folder/subfolder structure for snapshots), gpfs (proprietry, not free - needs to be really so I can do the research in the first place), glusterfs (no snapshots), lustre (lvm snapshots, with their performance problems and awkwardness).
This is a minefield! 
Any more suggestions on the cluster bit? Or should I just zfs and take the plunge?

---

### Post by frankerooney on 2014-04-07
..  Anybody done a ctdb cluster? What filesystem did they use? Did snapshots and resizing work ok? I guess I couldn't just deliver our shared iscsi storage to multiple hosts and get ctdb to do the locking because of the snapshots i.e. quiescing the filesystem on one host when another has no idea this is being done..
Thanks

---

### Post by OnlyWhisky on 2015-03-15
Hi! I'm trying to setup samba on zfs but getting errors about no ACLs on the filesystem. I set aclinherit=passthrough and acltype=posixacl but it still doesn't work. Is it possible at all to share ZFS volume via SAMBA on linux?

---

### Post by samsonluk on 2015-03-18
> **OnlyWhisky said:**
> Hi! I'm trying to setup samba on zfs but getting errors about no ACLs on the filesystem. I set aclinherit=passthrough and acltype=posixacl but it still doesn't work. Is it possible at all to share ZFS volume via SAMBA on linux?

Yes, I am currently doing this, what is your problem?

---

### Post by OnlyWhisky on 2015-03-23
I have, actually, solved my problem. I was trying to create a share using smb.conf but ended up using "zfs set sharesmb=true pool". I have another problem now though. When I create a file in some samba directory from windows box file has owners user_a:user_a. Thus other clients (let's say I have a linux group "users" for them) can't access these files. I'd like to know how can I make new files and folders to inherit either owner or group property from parent directory?

---

### Post by bab1 on 2015-03-23
> **OnlyWhisky said:**
> I have, actually, solved my problem. I was trying to create a share using smb.conf but ended up using "zfs set sharesmb=true pool". I have another problem now though. When I create a file in some samba directory from windows box file has owners user_a:user_a. Thus other clients (let's say I have a linux group "users" for them) can't access these files. I'd like to know how can I make new files and folders to inherit either owner or group property from parent directory?

The traditional way is to use ***sgid*** for groups and not worry about the owner.  If you really had to set the owner you can use ***suid***.  I do something like this when I do this for EXT file systems;  Create the directory (e.g. /tank/share) and set the owner:group (chown root:users /tank/share) then use chmod to set the sgid bit (chmod 2775 /tank/share).  The 2 is the sgid bit.  Now every subdirectory and file will have the group owner as "users".  

You might have problems with umask.  All of the latest Ubuntu versions have a umask of 0002 and thus permissions of 775 for the directories and 664 for the files.  This allows the group to have rw access.  Some Linux distros have a umask of 0022 and therefore have permissions of 755:644.  This yields ro access for groups.  So umask needs to be set to 0002 for this to work.  In addition, I always added the correct mask in the smb.conf to account for Windows users.

Here is the Oracle man page for the suid and sgid and the "sticky bit":
  [http://docs.oracle.com/cd/E19683-01/816-4883/secfile-69/index.html]("http://docs.oracle.com/cd/E19683-01/816-4883/secfile-69/index.html")

Here is the page on umask:
  [http://docs.oracle.com/cd/E19683-01/816-4883/secfile-62/index.html]("http://docs.oracle.com/cd/E19683-01/816-4883/secfile-62/index.html")

---

### Post by OnlyWhisky on 2015-03-28
> **bab1 said:**
> The traditional way is to use ***sgid*** for groups and not worry about the owner.  If you really had to set the owner you can use ***suid***.  I do something like this when I do this for EXT file systems;  Create the directory (e.g. /tank/share) and set the owner:group (chown root:users /tank/share) then use chmod to set the sgid bit (chmod 2775 /tank/share).  The 2 is the sgid bit.  Now every subdirectory and file will have the group owner as "users".  

You might have problems with umask.  All of the latest Ubuntu versions have a umask of 0002 and thus permissions of 775 for the directories and 664 for the files.  This allows the group to have rw access.  Some Linux distros have a umask of 0022 and therefore have permissions of 755:644.  This yields ro access for groups.  So umask needs to be set to 0002 for this to work.  In addition, I always added the correct mask in the smb.conf to account for Windows users.

Here is the Oracle man page for the suid and sgid and the "sticky bit":
  [http://docs.oracle.com/cd/E19683-01/816-4883/secfile-69/index.html]("http://docs.oracle.com/cd/E19683-01/816-4883/secfile-69/index.html")

Here is the page on umask:
  [http://docs.oracle.com/cd/E19683-01/816-4883/secfile-62/index.html]("http://docs.oracle.com/cd/E19683-01/816-4883/secfile-62/index.html")

Thank you for great advice and comprehensive explanation! It helped a lot! 

I actually switched back to smb.conf from zfs sharesmb. Instead of umask I'm using following flags (I wasn't able to verify which one does the trick):

```

   [myshare]
   map acl inherit = yes
   inherit permissions = yes
   inherit acls = Yes

```

---

