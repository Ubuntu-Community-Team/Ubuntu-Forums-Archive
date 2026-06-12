---
title: "Samba server:  Shadow Copy Client blank, with error in logs"
date: 2006-11-28
forum: Server Platforms
---

### Post by Brazen on 2006-11-28
I have Ubuntu Server 6.06 set up as a Samba file server authenticating to Active Directory.  I've setup the shadow_copy VFS module and have taken and mounted the appropriate snapshots.  When viewing the previous versions of a file.  One computer will show the previous versions of files just fine, but every other computer I've installed the Microsoft Shadow Copy Client on will not show any previous versions.  The Previous Versions tab is just blank.  In the samba log, I get this:

[2006/11/28 12:02:02, 0] modules/vfs_shadow_copy.c:shadow_copy_opendir(81)
  shadow_copy_opendir: SMB_VFS_NEXT_OPENDIR() failed for [Folder/file.txt]

The clients are Windows XP SP2 and 2000 SP4.  I installed the Shadow Copy Client the same way on all machines, BUT the one that can access the previous versions was installed first and I used it before installing any of the others (not that this should matter).  I'm logging in as the same user account from all machines.  ](*,)

---

### Post by Brazen on 2006-11-28
Is this a bug?!

Ok, upon further investigation, I've discovered that the Previous Versions does not work when access the share through a "nested" drive mapping.  By "nested" I mean we have the H: drive in Windows mapped to \\SambaServer\share\DepartmentFolder.  If I create a drive mapping, say
X: drive to \\SambaServer\share, then the Previous Version show up when going through the X: drive (or the UNC path) but NOT when going through the H: drive.

However, I have found a fix for this (I'll get to it in a little bit), but it's sloppy.  This is a big problem for us, because all our users have the H: drive mapped to a folder below the share based on what department they are in.

So the fix is:  I created a symlink under the nested folder ("DepartmentFolder" in this case) that pointed to the same folder in the snapshot.  I gave the symlink the "@GMT-" name that the shadow_copy module requires, and of course created script that destroys and creates this link along with the snapshots.

I don't know if this is an issue with the Previous Versions client, but I would think the shadow_copy module could be patched so that it knows to look back at the root of the file share for the snapshot.

---

