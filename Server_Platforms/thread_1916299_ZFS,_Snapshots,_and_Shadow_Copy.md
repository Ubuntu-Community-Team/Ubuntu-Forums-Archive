---
title: "ZFS, Snapshots, and Shadow Copy"
date: 2012-01-27
forum: Server Platforms
---

### Post by random_id on 2012-01-27
I think that the answer is no, but I will ask..

Is there any way to get a Windows Samba client to be able to use Shadow Copy to view/restore ZFS snapshots?

I am running Ubuntu 11.10 with ZFS-Fuse.  I have successfully created a ZFS pool, and now have snapshots automated.  I think my roadblock is I am not able to make the snapshot directory (/.zfs) visible, and I therefore can't use Samba's shadow copy to pass it through to the Windows client.  For a while, I had it working great on a FreeNAS box, but I gave up on FreeNAS since I also need a server for backup, FTP, bittorrent, and a few other things.

---

