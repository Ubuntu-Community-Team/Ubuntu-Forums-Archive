---
title: "World of Warcraft HDD space issue"
date: 2009-03-24
forum: Wine
---

### Post by raaste on 2009-03-24
I was trying to install WoW with wine, everything went fine until I had to choose the path to install to. Well the problem is, that my main partition, in which ubuntu is installed, only has 4 gigs of free space. So I figured I'd just install it on another ext3 partition, which has a couple hundred gigs of free space. But since this partition is mounted at /media/disk/, the wow installer doesn't recognize that as an individual partition and says that it needs to have 15gigs of free space. Is there any way to go around this other than resizing the main partition?

EDIT: The above was with the download installer.
EDIT2: Installing from the original CD:s seems to work, though it's what I wanted to avoid.. well, think I'm up and running in a few hours. This thread can be considered solved, I guess.

---

### Post by oedipuss on 2009-03-24
Well,  I guess you solved it, but in case this happens again, perhaps making a new drive in winecfg and assigning it to the /media/disk path would do the trick. Then you'd point the installer to G: or whatever the new drive is.

---

### Post by 1BigBore on 2009-03-25
How do you solve this, if you no longer have the disks?

---

