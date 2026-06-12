---
title: "Delete ubuntu server but leave the home folders?"
date: 2011-04-21
forum: Server Platforms
---

### Post by Melonking on 2011-04-21
I am switching to a new harddrive however I have a few client home folders on my currant system that I want to keep. My initial plan would be to just install the new system beside my old one then delete all the system files from the old system by hand and leave the home folders. Then after that setup new users on the new install and link them to there old home folders. Does this sound like a good plan?

Edit: Alternately I could clone just the system from the old install to the new harddrive in a similar way to deleting the old one.

---

### Post by elico on 2011-04-21
just replicate the current drive and change the fstab + grub settings.
with the rest of the free space decide later what to do not?

---

### Post by arrrghhh on 2011-04-21
Yea, or stand up both servers and rsync the data across.  Either way.

---

