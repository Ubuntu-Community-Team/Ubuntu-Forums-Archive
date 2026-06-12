---
title: "Network folder permissions"
date: 2018-09-09
forum: Server Platforms
---

### Post by timonoj on 2018-09-09
Hi guys!

I'm having a bit of issues with shared folders in the NAS. I recently had to enable advanced ACL in the share in order to have a bit of granularity on a folder with some permissions. But now I'm having trouble on the remaining folders. If the server has permission to write to that folder, then somehow the desktop machines can't access it. All shares are mounted via NFS on Linux and SMB on Windows. If I change the owner from the Linux desktop, then that machine can access the folder, but no one else can. chmod to allow user and group to rw doesn't help (should be the same user, right?).
There's the same username/password on the server and laptop/desktop.

EDIT: chmod 777 seems to finally authorize all of them to access...but is there a way to limit it to only that specific user (but on every machine)?

---

### Post by TheFu on 2018-09-10
Depends on the NAS. Some NAS devices didn't implement the full versions of NFS or Samba, so expecting them to follow the standards for NFS and CIFS is a fools errand.   I've always found CIFS security to be confusing because it effectively ignores Unix permissions, IME.  

In the Windows world, local storage permissions and networked storage permissions aren't the same.  They use permissive and most restricted access based on the access permissions.

I suspect to get useful help, you'll need to provide extremely concrete examples with uid/gid/permissions spelled out and probably the CIFS configuration for the shared storage too.  And perhaps all the ACLs.

---

