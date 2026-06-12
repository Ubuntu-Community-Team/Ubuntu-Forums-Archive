---
title: "Raid 1 as off-site backup solution"
date: 2011-10-17
forum: Server Platforms
---

### Post by swampface on 2011-10-17
I'll preface this by stating that this raid contains bacula storage volumes and not the data itself, and the data has other backups that aren't on this raid.

We're setting up an off-site backup solution and considering using a 3 drive Raid 1 array (with 2 other drives) as our off-site solution. The thinking is, when it's time to switch out the off-site drive, we unmount the array, fail the drive, replace it with the next one, add it back into the array and remount the raid.

While it would be nice to have the OS handle keeping the data on the drive synced, I'm wondering if rsynching the data to that drive would be better from a drive life standpoint. I know hard drives these days can do an amazing amount of work, but it seems like re-writing the entire thing a few times a week may be asking too much.

What I'm asking is which way would you do it? Is there another way to transfer the 2TB of backups to a 3rd drive I'm not thinking of?

---

