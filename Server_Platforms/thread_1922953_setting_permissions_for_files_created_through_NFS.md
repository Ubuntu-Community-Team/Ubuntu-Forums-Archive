---
title: "setting permissions for files created through NFS"
date: 2012-02-09
forum: Server Platforms
---

### Post by cdbahls on 2012-02-09
I have an NFS problem that's stumped me, and I'm hoping there's a simple fix that I'm just missing.

I've got an NFS share set up on a central file server, and 2 remote machines mount the shared directory on boot.

Here's the line from /etc/exports on the file server:
```
/share remote1(rw,sync,subtree_check) remote2(rw,sync,subtree_check)
```And here's the fstab entry on the remote machines:
```
server:/share /local nfs rw,intr 0 0
```The problem is that when a file is written by the remote machine to the NFS share, it sets the permission to 644.  However, I need this to be 775.  I can't figure out where to change this.

Any suggestions?

Thanks in advance for the help!
-Chris

---

### Post by SeijiSensei on 2012-02-12
The "umask" parameter in /home/user/.profile controls the permissions given to a file created by that user.  This is true if the file is created on the local filesystem or one mounted via NFS.

The default umask is 022; you subtract this number from 777, for directories, or 666 for files to determine the eventual permissions.  In this case it would be 755 for directories and 644 for files.  That gives the user full permissions to the directory or file, and read permissions to group members and others.

It sounds like you want group members to have the same privileges as the file's creator.  If so, change the umask value in .profile to 002.

By the way, you generally don't want files to have the execute bit set by default.  Directories always have the execute bit set; it means the directory is listable.  So 755 permissions are common for directories, but 644 permissions are the norm for ordinary files.

If you want to make "umask=002" the norm for new users, you can change the value in /etc/skel/.profile, which is the template for new users' home directories.

---

### Post by cdbahls on 2012-02-13
Great, this worked perfectly.  My problem was definitely with umask settings and not with the NFS configuration.

Thanks for the help!!

---

