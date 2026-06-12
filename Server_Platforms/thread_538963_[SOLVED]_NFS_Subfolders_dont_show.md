---
title: "[SOLVED] NFS Subfolders dont show"
date: 2007-08-30
forum: Server Platforms
---

### Post by toxicfeet on 2007-08-30
Ok, I have two ubuntu computers. One is my main rig, the other has been set up to act as my fileserver.

On my file server, I mounted 3 hard drives as so

/media/Storage I /dev/hdb1 (ext3)
/media/Storage II /dev/hdc1 (ext3)
/media/Storage III /dev/hdd1 (ext3)

When I used Windows on my main rig, I just used samba to share /media and navigated to the correct hard drive for my music or files.

However now that I'm using ubuntu, I can't use samba *well*, so I installed NFS on my server and main rig, sharing the same thing, /media.

The kicker is that I can only see this from my main rig:

[Storage I] [Storage II] [Storage III]

when I mount 192.168.1.1:/export/media /media/Files

How do I see my subfolders as well?

I am using Webmin, it makes it easier to fix

Thanks

---

### Post by toxicfeet on 2007-08-30
Please delete this thread. I am retarded.

---

### Post by Mud.Knee.Havoc on 2007-08-30
I don't think they'll delete the thread... but why not explain what you did wrong for the next guy who comes along with the same problem?

---

