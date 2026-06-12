---
title: "Media mount locations have changed?"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by tricky76 on 2012-10-06
In 12.04, my USB external drives would all mount under /media

For instance
/media/server1

In 12.10, they are mounted under my user name as

/media/tricky76/server1

This creates havoc on my music playlists.  Is this a new thing for 12.10 or do I have permission issues?  I want all users to be able to access the drive.

thanks,
-t

---

### Post by cariboo on 2012-10-06
> **tricky76 said:**
> In 12.04, my USB external drives would all mount under /media

For instance
/media/server1

In 12.10, they are mounted under my user name as

/media/tricky76/server1

This creates havoc on my music playlists.  Is this a new thing for 12.10 or do I have permission issues?  I want all users to be able to access the drive.

thanks,
-t

Yes, this has been a part of Quantal for several months, with the new version of dbus.

---

### Post by mc4man on 2012-10-06
> **tricky76 said:**
> In 12.04, my USB external drives would all mount under /media

For instance
/media/server1

In 12.10, they are mounted under my user name as

/media/tricky76/server1

This creates havoc on my music playlists.  Is this a new thing for 12.10 or do I have permission issues?  I want all users to be able to access the drive.

thanks,
-t
The new way under udisks2 is to mount to /media/<username>/
Additionally if currently mounted by a logged in user then no other user will be granted access nor be able to mount the same to /media/<anotheruser>

The latter can be worked around by overriding some polkit policies To some extent, ie. allow users to unmount volumes mounted by others so they themselves can mount.
(there is a policy that allows a user to mount a volume already mounted on another seat with auth but doesn't come into play, at least in Ubuntu.

Your best bet may be to create a static mount point based on UUID, then craft an fstab entry. If the volume in question is vfat or ntfs then shouldn't be hard to have set as 1st. user (admin/sudo) having rw & all others r (access).
To allow all users rw you'd have to research/ask around

There could be alternates to an fstab thru udev, again research

This bug report, though not your issue/concern, contains some useful info, links to other bug, commits, ect. If you read thru then the current deal should be more apparent 

[https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1020759](https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1020759)

---

